clean:
	rm -rf ./bin

build: clean
	# cd ../.. && make protoc
	go mod tidy
	go build -o ./bin/server ./cmd

run: build
	TRAFFIC_GENERATOR_HOSTNAME=localhost \
	TRAFFIC_GENERATOR_GRPC_PORT=32001 \
	TRAFFIC_GENERATOR_TIMEOUT=10s \
	TRAFFIC_GENERATOR_NUM_INSTANCES=1 \
	TRAFFIC_GENERATOR_REQUEST_INTERVAL=1s \
	TRAFFIC_GENERATOR_DATA_SIZE=1000 \
	TRAFFIC_GENERATOR_RANDOMIZE_BLOBS=true \
	./bin/server

build2: clean
	# cd ../.. && make protoc
	go mod tidy
	go build -o ./bin/server2 ./cmd2

run2: build2
	TRAFFIC_GENERATOR_LOG_FORMAT=text \
	TRAFFIC_GENERATOR_DISPERSER_HOSTNAME=localhost \
	TRAFFIC_GENERATOR_DISPERSER_PORT=32003 \
	RETRIEVER_HOSTNAME=localhost \
	RETRIEVER_GRPC_PORT=32003 \
	RETRIEVER_BLS_OPERATOR_STATE_RETRIVER=0x5f3f1dBD7B74C6B46e8c44f98792A1dAf8d69154 \
	RETRIEVER_EIGENDA_SERVICE_MANAGER=0x851356ae760d987E095750cCeb3bC6014560891C \
	RETRIEVER_TIMEOUT=10s \
	TRAFFIC_GENERATOR_NUM_WRITE_INSTANCES=1 \
	TRAFFIC_GENERATOR_WRITE_REQUEST_INTERVAL=1s \
	TRAFFIC_GENERATOR_DATA_SIZE=1000 \
	TRAFFIC_GENERATOR_SIGNER_PRIVATE_KEY_HEX=AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA \
	TRAFFIC_GENERATOR_PRIVATE_KEY=AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA \
	TRAFFIC_GENERATOR_METRICS_HTTP_PORT=9101 \
	TRAFFIC_GENERATOR_GRAPH_URL=http://localhost:8000/subgraphs/name/Layr-Labs/eigenda-operator-state \
	TRAFFIC_GENERATOR_THE_GRAPH_URL=http://localhost:8000/subgraphs/name/Layr-Labs/eigenda-operator-state \
	TRAFFIC_GENERATOR_G1_PATH=../../inabox/resources/kzg/g1.point \
	TRAFFIC_GENERATOR_G2_PATH=../../inabox/resources/kzg/g2.point \
	TRAFFIC_GENERATOR_CACHE_PATH=../../inabox/resources/kzg/SRSTables \
	TRAFFIC_GENERATOR_SRS_ORDER=3000 \
	TRAFFIC_GENERATOR_SRS_LOAD=3000 \
	TRAFFIC_GENERATOR_CHAIN_RPC=http://localhost:8545 \
	./bin/server2
