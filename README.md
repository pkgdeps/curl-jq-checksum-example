# jq checksum example

```bash
#!/bin/bash

declare JQ_VERSION="1.6"
# Download binary and checksum
curl -sLO https://github.com/stedolan/jq/releases/download/jq-${JQ_VERSION}/jq-linux64 && \
curl -sL https://raw.githubusercontent.com/stedolan/jq/master/sig/v${JQ_VERSION}/sha256sum.txt -o jq.sha256sum
# Verify the checksum
grep jq-linux64 jq.sha256sum | shasum -a 256 -c - || (echo "Error: Not match jq SHA256." && exit 1)
# dd executable permission and Rename to jq
chmod 755 jq-linux64 && ln -sfnv jq-linux64 jq
```

## Test