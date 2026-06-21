# aisecplus-week02-Odunuyitoluwalase
AI Model Risk Assessment — Gemma 4 12B Coder
AI Model Risk Assessment — Gemma 4 12B Coder
1. Executive Summary

This assessment evaluates Gemma 4 12B Coder, a 12-billion-parameter coding-focused language model derived from Gemma 4. The model is optimized for Python programming, reasoning, and code generation, and is assessed for use as a developer coding assistant.

The major risks identified include potential memorization of sensitive training data, inherited weaknesses from the base model, reduced safety alignment, and adversarial prompt abuse. Overall, the model is powerful for coding tasks but introduces moderate-to-high security risks if deployed without safeguards.

Verdict: Approve with Conditions — suitable for controlled coding environments with strict security controls.

2. Model Overview

Model Name: Gemma 4 12B Coder
Developer: Google AI / Community fine-tune by Hugging Face creator yuxinlu1

Type: Large Language Model (LLM) / Code Generation Model
Parameters: 12 Billion

Primary Use Case: Python code generation, debugging, and reasoning

License: Apache 2.0

Deployment Type: Local/offline or self-hosted via llama.cpp, Ollama, Docker

Assessment Use Case:
Assessing whether the model is safe to deploy as an internal enterprise coding assistant for software engineers.

3. Data Supply Chain

The model is based on Gemma 4, then fine-tuned using two datasets:

Primary Training Sources

Composer 2.5 Chain-of-Thought Dataset

Contains reasoning traces for Python coding tasks


Only successful code outputs that passed tests were retained

Fable 5 Dataset

Synthetic reasoning traces generated for difficult tasks

Used to improve performance on problems missed in Composer 2.5

Data Flow

Training Data → Base Gemma 4 Model → Fine-Tuning with Composer 2.5 + Fable 5 → Quantization (GGUF) → Deployment

Supply Chain Concerns
Full raw datasets are not publicly disclosed
Original source of all coding tasks is partially unclear
Possible inclusion of public repositories containing licensed code
Synthetic reasoning may introduce hallucinated logic patterns

4. Risk Matrix
Critical Risks
Inheritance vulnerabilities from base model
Adversarial prompt attacks / jailbreaks
High Risks
Poor data provenance
Sensitive code memorization
Legal licensing concerns
Limited transparency
Medium Risks
Dataset bias
Operational resource cost
		
5. Recommended Controls
I. Data Leakage Prevention
Scan outputs for secrets, API keys, and credentials
Apply DLP (Data Loss Prevention) filtering
II. Security Guardrails
Add prompt filtering against malicious instructions
Detect jailbreak attempts and adversarial prompts
III. Human Review
Require developer review before executing generated code
Never allow autonomous deployment to production
IV. Legal Compliance
Run generated code through license scanning tools
Ensure no copyrighted code is reused improperly
V. Usage Restriction

Use only for:

Code suggestions
Debugging
Internal development assistance

Avoid:

Security-critical systems
Sensitive customer data processing
Autonomous coding pipelines
6. Risk Verdict
Verdict: APPROVE WITH CONDITIONS

Gemma 4 12B Coder provides strong coding performance and reasoning capability, making it valuable as a software engineering assistant. However, the model has notable risks related to security, inherited vulnerabilities, data provenance, and legal exposure.

Deployment is acceptable only if strong monitoring, output filtering, and human oversight are enforced. Without these controls, the risk level becomes too high for enterprise production use.
