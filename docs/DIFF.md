# Missing from adk-go (compared to adk-python)

Granular, implementation-detail-level breakdown of everything missing from adk-go.

Based on:
- [`adk-go`](https://github.com/google/adk-go/tree/d8e57c0898f6): `da1d6a560463aba60c28bee44ab1ece320c29c83`
- [`adk-python`](https://github.com/google/adk-python/tree/9d155177b956): `9d155177b956f690d4c99560f582e3e90e111f71`

## 1. Model / LLM Provider Integrations

| Feature | Python | Go |
|---------|--------|----|
| **Anthropic Claude LLM** | `AnthropicLlm` with full tool-use support | Not implemented |
| **LiteLLM multi-provider proxy** | `LiteLlm` supporting 100+ providers via litellm | Not implemented |
| **Gemma LLM** | `GemmaLlm` for local Gemma models | Not implemented |
| **Apigee LLM** | `ApigeeLlm` for Apigee-routed models | Not implemented |
| **Model registry/factory** | `Registry` class for model name → LLM instance resolution | Not implemented; model creation is manual |
| **Context cache manager** | `GeminiContextCacheManager` for Gemini context caching | Not implemented |
| **`previous_interaction_id`** | Interactions chaining via `LlmRequest.previous_interaction_id` | Not in `LLMRequest` |


## 2. Tools — Entirely Missing

| Tool | Python module | Description |
|------|---------------|-------------|
| **`AuthenticatedFunctionTool`** | `tools/authenticated_function_tool.py` | Function tools with built-in auth credential injection |
| **`BashTool`** | `tools/bash_tool.py` | Shell command execution |
| **`SetModelResponseTool`** | `tools/set_model_response_tool.py` | Override LLM response programmatically |
| **`GetUserChoiceTool`** | `tools/get_user_choice_tool.py` | Prompt user to select from choices |
| **`TransferToAgentTool`** | `tools/transfer_to_agent_tool.py` | Explicit agent transfer tool (Go has `agenttool` but different design) |
| **`LoadWebPageTool`** | `tools/load_web_page_tool.py` | Load and parse web pages |
| **`UrlContextTool`** | `tools/url_context_tool.py` | Extract context from URLs |
| **`ComputerUseTool`** | `tools/computer_use_tool/` | Computer automation (mouse, keyboard, screen) |
| **`DataAgentTool`** | `tools/data_agent_tool/` | Data interaction agent |
| **`LoadMcpResourceTool`** | `tools/load_mcp_resource_tool.py` | Load MCP server resources as tool context |
| **`ExampleTool`** | `tools/example_tool.py` | Tool backed by few-shot examples |
| **`SkillToolset`** | `tools/skill_toolset.py` | Compose skills as tools |
| **`AgentSimulator`** | `tools/agent_simulator/` | 7-file agent simulation framework |
| **`OpenAPI Toolset`** | `tools/openapi_tool/` | Dynamic REST API tool generation from OpenAPI specs, with auth (API key, OAuth2, Bearer) |
| **`Google API Toolset`** | `tools/google_api_tool/` | Auto-generate tools from Google Discovery API |
| **`APIHub Toolset`** | `tools/apihub_tool/` | API Hub integration |
| **`Application Integration Toolset`** | `tools/application_integration_tool/` | Google Application Integration connector |
| **`CrewAI Tool`** | `tools/crewai_tool.py` | CrewAI framework integration |
| **`LangChain Tool`** | `tools/langchain_tool.py` | LangChain framework integration |


## 3. Tools — Google Cloud Data Toolsets

| Toolset | Python module | Files |
|---------|---------------|-------|
| **`BigQueryToolset`** | `tools/bigquery_tool/` | 9 files: `DataInsightsTool`, `MetadataTool`, `QueryTool`, `SearchTool` |
| **`BigtableToolset`** | `tools/bigtable_tool/` | 7 files: `MetadataTool`, `QueryTool` |
| **`CloudSpannerToolset`** | `tools/cloud_spanner_tool/` | 9 files: `MetadataTool`, `QueryTool`, `SearchTool` |
| **`PubSubToolset`** | `tools/pubsub_tool/` | 6 files: `MessageTool` |


## 4. Tools — RAG / Retrieval

| Tool | Python module | Description |
|------|---------------|-------------|
| **`BaseRetrievalTool`** | `tools/retrieval/base_retrieval_tool.py` | Abstract retrieval tool |
| **`FilesRetrieval`** | `tools/retrieval/files_retrieval.py` | File-based RAG |
| **`LlamaIndexRetrieval`** | `tools/retrieval/llama_index_retrieval.py` | LlamaIndex integration |
| **`VertexAiRagRetrieval`** | `tools/retrieval/vertex_ai_rag_retrieval.py` | Vertex AI RAG retrieval |


## 5. Tools — Search / Discovery

| Tool | Python module | Description |
|------|---------------|-------------|
| **`GoogleSearchAgentTool`** | `tools/google_search_agent_tool.py` | Google Search with agent delegation |
| **`DiscoveryEngineSearchTool`** | `tools/vertex_ai_search_tool.py` | Vertex AI Discovery Engine search |
| **`EnterpriseSearchTool`** | `tools/enterprise_search_tool.py` | Enterprise search |
| **`VertexAiSearchTool`** | `tools/vertex_ai_search_tool.py` | Vertex AI Search |


## 6. Auth & Credential Subsystem (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`AuthCredential`** | `auth/auth_credential.py` | Credential representation (API key, OAuth2, service account, etc.) |
| **`AuthHandler`** | `auth/auth_handler.py` | Authentication flow orchestration |
| **`AuthPreprocessor`** | `auth/auth_preprocessor.py` | Pre-request auth injection |
| **`AuthTool`** | `auth/auth_tool.py` | Tool for auth flows in agent conversations |
| **`AuthSchemes`** | `auth/auth_schemes.py` | Auth scheme definitions (OpenID, OAuth2, API key) |
| **`CredentialManager`** | `auth/credential_manager.py` | Credential lifecycle management |
| **`BaseCredentialService`** | `auth/credential_service/base_credential_service.py` | Abstract credential storage |
| **`InMemoryCredentialService`** | `auth/credential_service/in_memory_credential_service.py` | In-memory credential store |
| **`SessionStateCredentialService`** | `auth/credential_service/session_state_credential_service.py` | Session-backed credential store |
| **`OAuth2CredentialUtil`** | `auth/oauth2_credential_util.py` | OAuth2 token utilities |
| **`OAuth2Discovery`** | `auth/oauth2_discovery.py` | OAuth2 OIDC discovery |
| **Credential exchangers** | `auth/exchanger/` | Token exchange implementations |
| **Credential refreshers** | `auth/refresher/` | Token refresh implementations |


## 7. Code Executor Subsystem (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`BaseCodeExecutor`** | `code_executors/base_code_executor.py` | Abstract executor interface |
| **`BuiltInCodeExecutor`** | `code_executors/built_in_code_executor.py` | Local Python execution |
| **`UnsafeLocalCodeExecutor`** | `code_executors/unsafe_local_code_executor.py` | Unrestricted local execution |
| **`VertexAiCodeExecutor`** | `code_executors/vertex_ai_code_executor.py` | Vertex AI Workbench |
| **`ContainerCodeExecutor`** | `code_executors/container_code_executor.py` | Docker-based execution |
| **`GkeCodeExecutor`** | `code_executors/gke_code_executor.py` | Kubernetes-based execution |
| **`AgentEngineSandboxCodeExecutor`** | `code_executors/agent_engine_sandbox_code_executor.py` | Sandboxed execution |
| **`CodeExecutorContext`** | `code_executors/code_executor_context.py` | Execution context management |


## 8. Planner Subsystem (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`BasePlanner`** | `planners/base_planner.py` | Abstract planner interface |
| **`BuiltInPlanner`** | `planners/built_in_planner.py` | Default thinking-based planner |
| **`PlanReActPlanner`** | `planners/plan_re_act_planner.py` | Plan-then-act with reflection loop |
| **Planner integration in `LlmAgent`** | `llm_agent.py` field `planner` | `LlmAgent.planner` field triggers planning flow |


## 9. Evaluation Subsystem (entirely missing beyond stub route)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`EvalCase` / `EvalSet` / `EvalResult`** | `evaluation/eval_case.py`, `eval_set.py` | Core evaluation data types |
| **`EvalMetrics` / `EvalRubrics`** | `evaluation/eval_metrics.py` | Metric and rubric definitions |
| **`AgentEvaluator`** | `evaluation/agent_evaluator.py` | Agent-specific evaluator |
| **`TrajectoryEvaluator`** | `evaluation/trajectory_evaluator.py` | Multi-turn trajectory evaluation |
| **`ResponseEvaluator`** | `evaluation/response_evaluator.py` | Single-response evaluation |
| **`SafetyEvaluator`** | `evaluation/safety_evaluator.py` | Safety assessment |
| **`LlmAsJudge`** | `evaluation/llm_as_judge.py` | LLM-based scoring |
| **`RubricBasedEvaluator`** | `evaluation/rubric_based_evaluator.py` | Rubric-driven evaluation |
| **`CustomMetricEvaluator`** | `evaluation/custom_metric_evaluator.py` | User-defined metrics |
| **Specialized metrics** | `evaluation/` | `FinalResponseMatchV1/V2`, `HallucinationsV1`, `RubricBasedFinalResponseQualityV1`, `RubricBasedToolUseQualityV1` |
| **`BaseEvalService`** | `evaluation/base_eval_service.py` | Abstract eval service |
| **`LocalEvalService`** | `evaluation/local_eval_service.py` | Local evaluation execution |
| **`VertexAiEvalFacade`** | `evaluation/vertex_ai_eval_facade.py` | Vertex AI evaluation integration |
| **`EvalSetsManager`** | `evaluation/eval_sets_manager.py` | Test set management (Local, GCS, InMemory) |
| **`EvalSetResultsManager`** | `evaluation/eval_set_results_manager.py` | Result tracking and storage |
| **`MetricEvaluatorRegistry`** | `evaluation/metric_evaluator_registry.py` | Metric registration |
| **`EvaluationGenerator`** | `evaluation/evaluation_generator.py` | Test case generation |
| **User simulators** | `evaluation/simulation/` | `StaticUserSimulator`, `LlmBackedUserSimulator`, `PreBuiltPersonas` (10 files) |


## 10. Optimization Subsystem (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`AgentOptimizer`** | `optimization/agent_optimizer.py` | Agent optimization orchestrator |
| **`SimplePromptOptimizer`** | `optimization/simple_prompt_optimizer.py` | Automated prompt tuning |
| **`GepaRootAgentPromptOptimizer`** | `optimization/gepa_root_agent_prompt_optimizer.py` | GEPA-based prompt optimization |
| **`LocalEvalSampler`** | `optimization/local_eval_sampler.py` | Evaluation sampling for optimization |


## 11. Skills Subsystem (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **Skill models** | `skills/models.py` | Skill data structures |
| **Skill utilities** | `skills/utils.py` | Skill discovery and loading |
| **Skill prompting** | `skills/prompt.py` | Skill-based prompting |
| **`SkillToolset`** | `tools/skill_toolset.py` | Expose skills as tools |


## 12. App Container & Runtime Policy (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`App`** | `apps/app.py` | First-class app container with plugins, resumability, compaction, context cache |
| **Event compaction** | `apps/compaction.py` | Compact event history to reduce context size |
| **`LlmEventSummarizer`** | `apps/llm_event_summarizer.py` | LLM-based event summarization |
| **`BaseEventsSummarizer`** | `apps/base_events_summarizer.py` | Abstract event summarizer |


## 13. Live / Bidirectional Execution (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`run_live`** | `runners.py` | Live multi-agent audio execution mode |
| **`LiveRequestQueue`** | `agents/live_request_queue.py` | Queue for live request/response |
| **`ActiveStreamingTool`** | `agents/active_streaming_tool.py` | Tools that stream results in real-time |
| **Audio transcription** | `flows/llm_flows/audio_transcriber.py` | Audio transcription flow |
| **Audio cache** | `flows/llm_flows/audio_cache_manager.py` | Audio content caching |
| **Transcription manager** | `agents/transcription_entry.py` | Transcription data management |
| **Realtime blob saving** | `run_config.py` field `save_input_blobs_as_artifacts` | Save live audio/video as artifacts |


## 14. Event System Gaps

| Feature | Python | Go status |
|---------|--------|-----------|
| **`rewind_before_invocation_id`** | Rewind session to a prior invocation | Not implemented |
| **Event compaction metadata** | `compaction_metadata` on events | Not in `session.Event` |
| **`agent_state` on `EventActions`** | Workflow-level agent state tracking | Not in `EventActions` |
| **`end_of_agent` on `EventActions`** | Agent completion signaling | Not in `EventActions` |
| **`requested_auth_configs` on `EventActions`** | Auth config requests from tools | Not in `EventActions` |


## 15. RunConfig Gaps

| Feature | Python field | Description |
|---------|--------------|-------------|
| **`speech_config`** | `SpeechConfig` | Speech synthesis configuration |
| **`input_audio_transcription`** | `AudioTranscriptionConfig` | Input audio transcription |
| **`output_audio_transcription`** | `AudioTranscriptionConfig` | Output audio transcription |
| **`realtime_input_config`** | `RealtimeInputConfig` | Realtime input handling |
| **`proactivity`** | `ProactivityConfig` | Proactive agent behavior |
| **`session_resumption`** | `SessionResumptionConfig` | Session resume support |
| **`context_window_compression`** | `ContextWindowCompressionConfig` | Compress context to fit window |
| **`save_input_blobs_as_artifacts`** | `bool` | Save live blobs as artifacts |
| **`max_llm_workers`** | `int` | Thread pool control for parallel LLM calls |


## 16. Flow Pipeline Gaps

| Processor | Python module | Description |
|-----------|---------------|-------------|
| **`ContextCacheProcessor`** | `flows/llm_flows/context_cache_processor.py` | Context caching in LLM flow |
| **`InteractionsProcessor`** | `flows/llm_flows/interactions_processor.py` | Interactions chaining |
| **`CompactionProcessor`** | `flows/llm_flows/compaction_processor.py` | Event compaction in flow |
| **`NlPlanning`** | `flows/llm_flows/nl_planning.py` | Natural language planning flow |
| **`CodeExecution`** | `flows/llm_flows/code_execution.py` | Code execution flow |
| **`AudioTranscriber`** | `flows/llm_flows/audio_transcriber.py` | Audio transcription flow |
| **Auth preprocessing** | stub in Go `other_processors.go` | Actually functional in Python |


## 17. Session / Storage Gaps

| Feature | Python | Go status |
|---------|--------|-----------|
| **Schema migration** | `sessions/migration/` with `migration_runner.py` | Not implemented |
| **Schema versioning** | `v0.py`, `v1.py` schema definitions | Not implemented |
| **`FileArtifactService`** | Filesystem-based artifact storage | Only GCS backend exists |
| **`VertexAiMemoryBankService`** | Vertex AI Memory Bank backend | Not implemented |
| **`VertexAiRagMemoryService`** | Vertex AI RAG memory backend | Not implemented |
| **User-scoped artifacts** | `user_id` dimension in artifact storage | Not implemented |


## 18. Plugin Gaps (Go has plugin framework but fewer built-ins)

| Plugin | Python module | Description |
|--------|---------------|-------------|
| **`BigQueryAgentAnalyticsPlugin`** | `plugins/bigquery_agent_analytics_plugin.py` | Agent analytics to BigQuery (110KB) |
| **`GlobalInstructionPlugin`** | `plugins/global_instruction_plugin.py` | Global instruction injection |
| **`ContextFilterPlugin`** | `plugins/context_filter_plugin.py` | Context filtering/trimming |
| **`SaveFilesAsArtifactsPlugin`** | `plugins/save_files_as_artifacts_plugin.py` | Auto-save files as artifacts |
| **`MultimodalToolResultsPlugin`** | `plugins/multimodal_tool_results_plugin.py` | Multimodal tool result handling |
| **`RequestIntercepterPlugin`** | `plugins/request_intercepter_plugin.py` | Request interception |


## 19. Registry & Integration Gaps

| Feature | Python module | Description |
|---------|---------------|-------------|
| **`AgentRegistry`** | `integrations/agent_registry/` | Remote agent registry for discovery |
| **`ApiRegistry`** | `integrations/api_registry/` | API tool registry backed by Google registries |


## 20. Agent Type Gaps

| Agent | Python module | Description |
|-------|---------------|-------------|
| **`LangGraphAgent`** | `agents/langgraph_agent.py` | LangGraph framework integration |
| **`McpInstructionProvider`** | `agents/mcp_instruction_provider.py` | Dynamic instructions from MCP server |
| **Built-in CLI agents** | `cli/built_in_agents/` | `AdkAgentBuilderAssistant` for scaffolding |


## 21. CLI / Server Gaps

| Feature | Python module | Description |
|---------|---------------|-------------|
| **`adk create`** (scaffolding) | `cli/cli_create.py` | Agent project scaffolding |
| **`adk deploy`** | `cli/cli_deploy.py` (51KB) | Deploy to Cloud Run, Agent Engine, GKE |
| **`adk eval`** | `cli/cli_eval.py` | Evaluation runner CLI |
| **`AgentGraph`** | `cli/agent_graph.py` | Agent graph visualization |
| **FastAPI integration** | `cli/fast_api.py` | FastAPI app generation |
| **Service registry** | `cli/service_registry.py` | Service factory/discovery |
| **Browser integration** | `cli/browser/` | Browser-based debugging |
| **Hot reload** | CLI feature | Auto-reload on code changes |


## 22. Few-Shot Examples System (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`BaseExampleProvider`** | `examples/base_example_provider.py` | Abstract example provider |
| **`VertexAiExampleStore`** | `examples/vertex_ai_example_store.py` | Vertex AI example storage |
| **`ExampleUtil`** | `examples/example_util.py` | Example utilities |
| **`ExampleTool`** | `tools/example_tool.py` | Tool backed by examples |


## 23. Features / Flags System (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`FeatureDecorator`** | `features/feature_decorator.py` | Feature decoration |
| **`FeatureRegistry`** | `features/feature_registry.py` | Feature flag management |


## 24. Platform Shims (entirely missing)

| Component | Python module | Description |
|-----------|---------------|-------------|
| **`platform.time`** | `platform/time.py` | Overridable time for testing |
| **`platform.uuid`** | `platform/uuid.py` | Overridable UUID for determinism |
| **`platform.thread`** | `platform/thread.py` | Overridable thread creation |


## 25. Structured Error Types (entirely missing)

| Error | Python module | Description |
|-------|---------------|-------------|
| **`AlreadyExistsError`** | `errors/` | Duplicate resource error |
| **`InputValidationError`** | `errors/` | Input validation failure |
| **`NotFoundError`** | `errors/` | Resource not found |
| **`SessionNotFoundError`** | `errors/` | Session not found |
| **`ToolExecutionError`** | `errors/` | Tool execution failure |


## 26. Telemetry Gaps

| Feature | Python module | Go status |
|---------|---------------|-----------|
| **`SqliteSpanExporter`** | `telemetry/sqlite_span_exporter.py` | Not implemented |
| **`ExperimentalSemconv`** | `telemetry/experimental_semconv.py` (14.6KB) | Not implemented |
| **Google Cloud tracing** | `telemetry/google_cloud.py` | Not implemented |


## Summary by Impact

| Priority | Category | # Missing Items |
|----------|----------|-----------------|
| **High** | Auth & credentials | 13 components |
| **High** | Evaluation subsystem | 20+ components |
| **High** | Code executors | 8 components |
| **High** | Model providers (Anthropic, LiteLLM, etc.) | 5 providers |
| **High** | Tool ecosystem (OpenAPI, data tools, retrieval) | 30+ tools |
| **Medium** | Planner subsystem | 3 components |
| **Medium** | App container & compaction | 4 components |
| **Medium** | Live/bidirectional execution | 7 components |
| **Medium** | CLI commands (create, deploy, eval) | 6 features |
| **Medium** | Flow pipeline processors | 7 processors |
| **Low** | Optimization | 4 components |
| **Low** | Skills | 4 components |
| **Low** | Few-shot examples | 4 components |
| **Low** | Platform shims, feature flags, error types | 10+ components |
| **Low** | Plugin built-ins | 6 plugins |
