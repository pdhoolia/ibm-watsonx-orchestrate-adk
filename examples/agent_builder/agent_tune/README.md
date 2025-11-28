# Agent-Tune integration Example

## Import Tools

```bash
orchestrate tools import -f examples/agent_builder/agent_tune/tools/health-insurance-tools-api.yml -k openapi
```

## Import Agent

```bash
orchestrate agents import -f examples/agent_builder/agent_tune/agents/health_insurance_agent.yaml
```

## Setup Observability & start server with telemetry support

```bash
orchestrate server start --with-ibm-telemetry -e .env

orchestrate settings observability langfuse configure \
    --url "https://cloud.langfuse.com/api/public/otel" \
    --api-key "LANGFUSE_API_KEY" \
    --health-uri "https://cloud.langfuse.com" \
    --config-json '{"public_key": "LANGFUSE_PUBLIC_KEY"}' \
    --project-id "LANGFUSE_PROJECT_ID"
```

## Chat with the Agent

```bash
orchestrate chat start
```

Try asking the agent:

- Show my approved claims. My memberId is 375491186.
- Get in-network cardiologists near me. My memberId is 375491186. I am at location: [latitude: "33", longitude: "-118"].
