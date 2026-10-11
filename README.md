# CMD-I Public Releases

Public binary releases for [CMD-I](https://github.com/usaps/CMDI).

## Install via Homebrew

```bash
brew tap usaps/cmdi
brew install cmdi
```


## Use CMDI with AI

`cmdi mcp` is a local stdio MCP server. Claude Desktop, Cursor, and Grok on the same machine can dry-run an offload, start one verified copy, watch it, and re-check the destination against its ASC MHL.

The server never formats or deletes media. Eject and cancel of a running job need `confirm: true`. One job runs at a time. There is no queue.

The full tool list and the client config are in the source repo: [docs/mcp.md](https://github.com/usaps/CMDI/blob/docs/mcp-guide/docs/mcp.md) (pull request [usaps/CMDI#29](https://github.com/usaps/CMDI/pull/29), implementation [usaps/CMDI#28](https://github.com/usaps/CMDI/pull/28)). The 0.1.24 bottle has an earlier, smaller `cmdi mcp` tool set. Run `cmdi --version` and the client's tool list, and treat that as the truth for the binary you have.

Claude Desktop or Cursor (`claude_desktop_config.json` / `mcp.json`):

```json
{
  "mcpServers": {
    "cmdi": {
      "command": "/opt/homebrew/bin/cmdi",
      "args": ["mcp"]
    }
  }
}
```

Grok (`~/.grok/config.toml`):

```toml
[mcp_servers.cmdi]
command = "/opt/homebrew/bin/cmdi"
args = ["mcp"]
tool_timeout_sec = 120
```
