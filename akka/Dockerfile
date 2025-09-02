FROM registry.akka.io/helloworld-agent-deps:0.1

COPY src /src
COPY pom.xml /
WORKDIR /

COPY <<EOF entrypoint.sh
#!/bin/sh
if test -f /run/secrets/openai-api-key; then
    export OPENAI_API_KEY=$(cat /run/secrets/openai-api-key)
fi
exec mvn -o compile exec:java

EOF

RUN chmod +x entrypoint.sh
ENTRYPOINT ["./entrypoint.sh"]

