# RunAnywhere SDKs - Final Brief

## 1. Project Overview
**RunAnywhere SDKs** is a suite of privacy-first, on-device AI development kits designed to bring powerful Large Language Model (LLM) and Voice AI capabilities directly to mobile and desktop applications.

**Core Mission:** Enable intelligent AI execution with automatic optimization for performance, privacy, and cost by running models locally on user devices whenever possible, with intelligent routing to the cloud when necessary.

## 2. Platform Support & Status

| Platform | SDK Type | Status | Key Highlights |
| :--- | :--- | :--- | :--- |
| **iOS / macOS** | Swift Package | **✅ Available (Mature)** | "Source of Truth" architecture. Full Voice Pipeline, Text Gen, Structured Output, Thinking Models. |
| **Android / Desktop** | Kotlin Multiplatform | **⚠️ Beta (Active Dev)** | Text Gen, Structured Output, GGUF support. Rapidly evolving to match iOS parity (Voice pipeline in progress). |
| **React Native** | NPM Package | **🧪 Beta** | TypeScript API with native bridges (Nitro). Support for Text, STT, TTS. |
| **Flutter** | Dart Package | **🧪 Beta** | Dart bindings via platform channels. |

## 3. What You Can Build (Capabilities)

### 💬 Privacy-First Chat Applications
*   **On-Device Text Generation:** Run models like Llama 3, Phi-3, or Gemma directly on the phone. No internet required.
*   **Streaming Responses:** Real-time token streaming for low-latency feel.
*   **History Management:** Built-in context handling.

### 🗣️ Complete Voice Assistants (iOS Live, Android Planned)
*   **Voice Pipeline:** End-to-end orchestration of:
    *   **VAD (Voice Activity Detection):** Detects when user speaks.
    *   **STT (Speech-to-Text):** Transcribes audio locally (e.g., using WhisperKit).
    *   **LLM:** Processes the query.
    *   **TTS (Text-to-Speech):** Synthesizes vocal response.
*   **Real-time Interaction:** Low-latency voice conversations.

### 📋 Structured Data Extraction
*   **Type-Safe Output:** Force LLMs to generate valid JSON adhering to specific schemas (e.g., for filling forms, extracting data from queries) using `Generatable` protocol (iOS) or equivalent interfaces.

### 🧠 Advanced AI Features
*   **Thinking Models:** Support for models that output `<think>` tags for reasoning chains before answering.
*   **Intelligent Routing:** The SDK decides whether to run a prompt locally (privacy/cost) or route to the cloud (complexity/speed) - *Active Area of Development*.

## 4. Key Technical Features

*   **Model Management:** Automatic discovery, downloading (with integrity checks), and lifecycle management (loading/unloading) of GGUF and other model formats.
*   **Multi-Engine Support:**
    *   **iOS:** Llama.cpp, Core ML, MLX, WhisperKit.
    *   **Android:** Llama.cpp (via JNI), future support for ONNX/TFLite.
*   **Performance Analytics:** Real-time metrics on Token/sec, Time-to-first-token, RAM usage, and thermal pressure.
*   **Component Architecture:** Modular design allows swapping out components (e.g., switching STT providers) via a `ModuleRegistry`.

## 5. Architecture & Roadmap

### "iOS First" Principle
The **iOS SDK** serves as the **architectural source of truth**. All features, protocols, and architectural patterns (ServiceContainer, EventBus, Component Lifecycle) are defined there first and then ported to the Kotlin Multiplatform SDK.

### Current Roadmap (Key Items)
1.  **Android Voice Parity:** Implementing the full VAD/STT/TTS pipeline in Kotlin to match iOS capabilities (See `KOTLIN_SDK_MASTER_EXECUTION_PLAN.md`).
2.  **Hybrid Routing:** Enhancing the decision engine for seamless local/cloud offloading.
3.  **Vision Support:** Adding Vision Language Model (VLM) capabilities for image understanding.

## 6. Examples & Resources
*   **iOS Demo:** `examples/ios/RunAnywhereAI` - Full-featured chat & voice assistant.
*   **Android Demo:** `examples/android/RunAnywhereAI` - Text generation showcase.
*   **Flutter/RN Demos:** Basic integration examples.

**Documentation Locations:**
*   `sdk/runanywhere-swift/`: iOS API Refs.
*   `sdk/runanywhere-kotlin/`: Android/KMP API Refs.
*   `sdk/IOS_SDK_ARCHITECTURE_REFERENCE.md`: The definitive guide for SDK architecture.
