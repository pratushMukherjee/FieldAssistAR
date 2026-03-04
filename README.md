# 🌸 FragranceAR — XR AI Assistant

A Unity-based mixed reality assistant that integrates **OpenAI vision & chat** and **Meta Wit voice recognition** to identify and analyze IFF (International Flavors & Fragrances) products in real time. Point your headset at a product, speak a wake word, and get instant safety, storage, usage, and scent-profile information — spoken back via TTS.

---

## ✨ Key Features

- **Multi-role mode selection** — Tailored experiences for `LabTechnician`, `Perfumer`, `SalesTeam`, and `General` users, each with custom system prompts and conversation context
- **Voice-triggered interactions** — Wake-word listening powered by Meta Wit intent recognition
- **Vision-based product identification** — Captures webcam frames and sends them to GPT-4o for image + text analysis
- **Persistent conversation history** — Per-session memory scoped to the active user mode
- **Text-to-speech output** — Spoken responses via a `TTSSpeaker` component

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Engine | Unity 2020.3+ |
| AI / Vision | OpenAI GPT-4o (`OpenAIClient`) |
| Voice / NLU | Meta Wit.ai |
| Speech Output | Unity TTS (`TTSSpeaker`) |
| Camera Input | `WebCamTextureManager` |

---

## 🚀 Quick Setup

### Prerequisites

- Unity **2020.3+** (check `ProjectSettings/ProjectVersion.txt` for the exact version used)
- OpenAI SDK imported into the Unity project
- Meta Wit package imported into the Unity project
- Microphone and webcam/passthrough access at runtime

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/pratushMukherjee/FragranceAR.git
   ```

2. **Open in Unity Hub** — Add the cloned folder as an existing project

3. **Configure the `AIManager` component** in the scene Inspector:

   | Field | Description |
   |---|---|
   | `OpenAIConfiguration` | Your OpenAI API key and model settings |
   | `WakeWordManager` | Wake-word and intent hooks |
   | `WebCamTextureManager` | Live webcam source |
   | `aiCanvas` / `loadingCanvas` / `modeSelectionCanvas` | UI panel references |
   | `aiResponseText` / `describePicture` | Text display elements |
   | `labTechButton` / `perfumerButton` / `salesButton` / `generalButton` | Mode selection buttons |
   | `TTSSpeaker` | Speech output component |
   | `debugPicture` | *(Optional)* Static texture for Editor testing |

4. **Build for Android** — Switch platform to Android in Build Settings, connect your Meta Quest, and click **Build and Run**

---

## 🔐 API Key Security

> ⚠️ **Never commit API keys to version control.**

- Set your OpenAI key in `Assets/Resources/OpenAIConfiguration.asset` locally via the Inspector
- This file should be listed in `.gitignore` or the key field left blank in tracked files
- Regenerate any key that was previously exposed in a commit

---

## 🎙️ Usage

1. Launch the app and select a **user mode** from the mode selection UI
2. Speak the configured **wake word** to begin listening
3. Meta Wit parses your voice input into one of the supported intents:

   | Intent | Description |
   |---|---|
   | `describe_vision` | Identify and describe the product in view |
   | `safety_check` | Retrieve safety information |
   | `storage_info` | Get storage recommendations |
   | `usage_level` | Usage guidelines and concentrations |
   | `scent_profile` | Scent notes and olfactory profile |
   | *(general)* | Free-form chat routed to the GPT-4o chat endpoint |

4. The assistant responds in text (`aiResponseText`) and speaks the response via TTS

> **Editor testing:** Populate `debugPicture` with a static texture to test vision prompts without a live webcam.

---

## 🗂️ Relevant Files

- **AI logic & integrations** — [`Assets/AIManager.cs`](Assets/AIManager.cs)

---

## 🧑‍💻 Developer Notes

- Conversation history is stored **in-memory** (`conversationHistory`) and resets on mode switch
- The project targets `Model.GPT4o` — update the model constant in `AIManager.cs` if needed
- Image + text prompts are sent as mixed-content `Message` objects for vision requests

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| Image capture returns null | Ensure webcam is active and runtime permission is granted |
| OpenAI calls fail | Verify `OpenAIConfiguration` API key and network connectivity |
| Voice not triggering | Check microphone permissions and Wit.ai credentials in `ProjectSettings/wit.config` |
| Editor has no webcam | Assign a texture to `debugPicture` for static testing |

---

## 🤝 Contributing

Fork the repo and submit pull requests for bug fixes or features. Keep changes focused and add or update tests where applicable.

---

## 📄 License

Add your preferred license file to the repository (e.g. `LICENSE`).

---

## 👤 Author

**Pratush Mukherjee** · [GitHub](https://github.com/pratushMukherjee)# 🌸 FragranceAR — XR AI Assistant

A Unity-based mixed reality assistant that integrates **OpenAI vision & chat** and **Meta Wit voice recognition** to identify and analyze IFF (International Flavors & Fragrances) products in real time. Point your headset at a product, speak a wake word, and get instant safety, storage, usage, and scent-profile information — spoken back via TTS.

---

## ✨ Key Features

- **Multi-role mode selection** — Tailored experiences for `LabTechnician`, `Perfumer`, `SalesTeam`, and `General` users, each with custom system prompts and conversation context
- **Voice-triggered interactions** — Wake-word listening powered by Meta Wit intent recognition
- **Vision-based product identification** — Captures webcam frames and sends them to GPT-4o for image + text analysis
- **Persistent conversation history** — Per-session memory scoped to the active user mode
- **Text-to-speech output** — Spoken responses via a `TTSSpeaker` component

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Engine | Unity 2020.3+ |
| AI / Vision | OpenAI GPT-4o (`OpenAIClient`) |
| Voice / NLU | Meta Wit.ai |
| Speech Output | Unity TTS (`TTSSpeaker`) |
| Camera Input | `WebCamTextureManager` |

---

## 🚀 Quick Setup

### Prerequisites

- Unity **2020.3+** (check `ProjectSettings/ProjectVersion.txt` for the exact version used)
- OpenAI SDK imported into the Unity project
- Meta Wit package imported into the Unity project
- Microphone and webcam/passthrough access at runtime

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/pratushMukherjee/FragranceAR.git
   ```

2. **Open in Unity Hub** — Add the cloned folder as an existing project

3. **Configure the `AIManager` component** in the scene Inspector:

   | Field | Description |
   |---|---|
   | `OpenAIConfiguration` | Your OpenAI API key and model settings |
   | `WakeWordManager` | Wake-word and intent hooks |
   | `WebCamTextureManager` | Live webcam source |
   | `aiCanvas` / `loadingCanvas` / `modeSelectionCanvas` | UI panel references |
   | `aiResponseText` / `describePicture` | Text display elements |
   | `labTechButton` / `perfumerButton` / `salesButton` / `generalButton` | Mode selection buttons |
   | `TTSSpeaker` | Speech output component |
   | `debugPicture` | *(Optional)* Static texture for Editor testing |

4. **Build for Android** — Switch platform to Android in Build Settings, connect your Meta Quest, and click **Build and Run**

---

## 🔐 API Key Security

> ⚠️ **Never commit API keys to version control.**

- Set your OpenAI key in `Assets/Resources/OpenAIConfiguration.asset` locally via the Inspector
- This file should be listed in `.gitignore` or the key field left blank in tracked files
- Regenerate any key that was previously exposed in a commit

---

## 🎙️ Usage

1. Launch the app and select a **user mode** from the mode selection UI
2. Speak the configured **wake word** to begin listening
3. Meta Wit parses your voice input into one of the supported intents:

   | Intent | Description |
   |---|---|
   | `describe_vision` | Identify and describe the product in view |
   | `safety_check` | Retrieve safety information |
   | `storage_info` | Get storage recommendations |
   | `usage_level` | Usage guidelines and concentrations |
   | `scent_profile` | Scent notes and olfactory profile |
   | *(general)* | Free-form chat routed to the GPT-4o chat endpoint |

4. The assistant responds in text (`aiResponseText`) and speaks the response via TTS

> **Editor testing:** Populate `debugPicture` with a static texture to test vision prompts without a live webcam.

---

## 🗂️ Relevant Files

- **AI logic & integrations** — [`Assets/AIManager.cs`](Assets/AIManager.cs)

---

## 🧑‍💻 Developer Notes

- Conversation history is stored **in-memory** (`conversationHistory`) and resets on mode switch
- The project targets `Model.GPT4o` — update the model constant in `AIManager.cs` if needed
- Image + text prompts are sent as mixed-content `Message` objects for vision requests

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| Image capture returns null | Ensure webcam is active and runtime permission is granted |
| OpenAI calls fail | Verify `OpenAIConfiguration` API key and network connectivity |
| Voice not triggering | Check microphone permissions and Wit.ai credentials in `ProjectSettings/wit.config` |
| Editor has no webcam | Assign a texture to `debugPicture` for static testing |

---

## 🤝 Contributing

Fork the repo and submit pull requests for bug fixes or features. Keep changes focused and add or update tests where applicable.

---

## 📄 License

Add your preferred license file to the repository (e.g. `LICENSE`).

---

## 👤 Author

**Pratush Mukherjee** · [GitHub](https://github.com/pratushMukherjee)# 🌸 FragranceAR — XR AI Assistant

A Unity-based mixed reality assistant that integrates **OpenAI vision & chat** and **Meta Wit voice recognition** to identify and analyze IFF (International Flavors & Fragrances) products in real time. Point your headset at a product, speak a wake word, and get instant safety, storage, usage, and scent-profile information — spoken back via TTS.

---

## ✨ Key Features

- **Multi-role mode selection** — Tailored experiences for `LabTechnician`, `Perfumer`, `SalesTeam`, and `General` users, each with custom system prompts and conversation context
- **Voice-triggered interactions** — Wake-word listening powered by Meta Wit intent recognition
- **Vision-based product identification** — Captures webcam frames and sends them to GPT-4o for image + text analysis
- **Persistent conversation history** — Per-session memory scoped to the active user mode
- **Text-to-speech output** — Spoken responses via a `TTSSpeaker` component

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Engine | Unity 2020.3+ |
| AI / Vision | OpenAI GPT-4o (`OpenAIClient`) |
| Voice / NLU | Meta Wit.ai |
| Speech Output | Unity TTS (`TTSSpeaker`) |
| Camera Input | `WebCamTextureManager` |

---

## 🚀 Quick Setup

### Prerequisites

- Unity **2020.3+** (check `ProjectSettings/ProjectVersion.txt` for the exact version used)
- OpenAI SDK imported into the Unity project
- Meta Wit package imported into the Unity project
- Microphone and webcam/passthrough access at runtime

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/pratushMukherjee/FragranceAR.git
   ```

2. **Open in Unity Hub** — Add the cloned folder as an existing project

3. **Configure the `AIManager` component** in the scene Inspector:

   | Field | Description |
   |---|---|
   | `OpenAIConfiguration` | Your OpenAI API key and model settings |
   | `WakeWordManager` | Wake-word and intent hooks |
   | `WebCamTextureManager` | Live webcam source |
   | `aiCanvas` / `loadingCanvas` / `modeSelectionCanvas` | UI panel references |
   | `aiResponseText` / `describePicture` | Text display elements |
   | `labTechButton` / `perfumerButton` / `salesButton` / `generalButton` | Mode selection buttons |
   | `TTSSpeaker` | Speech output component |
   | `debugPicture` | *(Optional)* Static texture for Editor testing |

4. **Build for Android** — Switch platform to Android in Build Settings, connect your Meta Quest, and click **Build and Run**

---

## 🔐 API Key Security

> ⚠️ **Never commit API keys to version control.**

- Set your OpenAI key in `Assets/Resources/OpenAIConfiguration.asset` locally via the Inspector
- This file should be listed in `.gitignore` or the key field left blank in tracked files
- Regenerate any key that was previously exposed in a commit

---

## 🎙️ Usage

1. Launch the app and select a **user mode** from the mode selection UI
2. Speak the configured **wake word** to begin listening
3. Meta Wit parses your voice input into one of the supported intents:

   | Intent | Description |
   |---|---|
   | `describe_vision` | Identify and describe the product in view |
   | `safety_check` | Retrieve safety information |
   | `storage_info` | Get storage recommendations |
   | `usage_level` | Usage guidelines and concentrations |
   | `scent_profile` | Scent notes and olfactory profile |
   | *(general)* | Free-form chat routed to the GPT-4o chat endpoint |

4. The assistant responds in text (`aiResponseText`) and speaks the response via TTS

> **Editor testing:** Populate `debugPicture` with a static texture to test vision prompts without a live webcam.

---

## 🗂️ Relevant Files

- **AI logic & integrations** — [`Assets/AIManager.cs`](Assets/AIManager.cs)

---

## 🧑‍💻 Developer Notes

- Conversation history is stored **in-memory** (`conversationHistory`) and resets on mode switch
- The project targets `Model.GPT4o` — update the model constant in `AIManager.cs` if needed
- Image + text prompts are sent as mixed-content `Message` objects for vision requests

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| Image capture returns null | Ensure webcam is active and runtime permission is granted |
| OpenAI calls fail | Verify `OpenAIConfiguration` API key and network connectivity |
| Voice not triggering | Check microphone permissions and Wit.ai credentials in `ProjectSettings/wit.config` |
| Editor has no webcam | Assign a texture to `debugPicture` for static testing |

---

## 🤝 Contributing

Fork the repo and submit pull requests for bug fixes or features. Keep changes focused and add or update tests where applicable.

---

## 📄 License

Add your preferred license file to the repository (e.g. `LICENSE`).

---

## 👤 Author

**Pratush Mukherjee** · [GitHub](https://github.com/pratushMukherjee)# 🌸 FragranceAR — XR AI Assistant

A Unity-based mixed reality assistant that integrates **OpenAI vision & chat** and **Meta Wit voice recognition** to identify and analyze IFF (International Flavors & Fragrances) products in real time. Point your headset at a product, speak a wake word, and get instant safety, storage, usage, and scent-profile information — spoken back via TTS.

---

## ✨ Key Features

- **Multi-role mode selection** — Tailored experiences for `LabTechnician`, `Perfumer`, `SalesTeam`, and `General` users, each with custom system prompts and conversation context
- **Voice-triggered interactions** — Wake-word listening powered by Meta Wit intent recognition
- **Vision-based product identification** — Captures webcam frames and sends them to GPT-4o for image + text analysis
- **Persistent conversation history** — Per-session memory scoped to the active user mode
- **Text-to-speech output** — Spoken responses via a `TTSSpeaker` component

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Engine | Unity 2020.3+ |
| AI / Vision | OpenAI GPT-4o (`OpenAIClient`) |
| Voice / NLU | Meta Wit.ai |
| Speech Output | Unity TTS (`TTSSpeaker`) |
| Camera Input | `WebCamTextureManager` |

---

## 🚀 Quick Setup

### Prerequisites

- Unity **2020.3+** (check `ProjectSettings/ProjectVersion.txt` for the exact version used)
- OpenAI SDK imported into the Unity project
- Meta Wit package imported into the Unity project
- Microphone and webcam/passthrough access at runtime

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/pratushMukherjee/FragranceAR.git
   ```

2. **Open in Unity Hub** — Add the cloned folder as an existing project

3. **Configure the `AIManager` component** in the scene Inspector:

   | Field | Description |
   |---|---|
   | `OpenAIConfiguration` | Your OpenAI API key and model settings |
   | `WakeWordManager` | Wake-word and intent hooks |
   | `WebCamTextureManager` | Live webcam source |
   | `aiCanvas` / `loadingCanvas` / `modeSelectionCanvas` | UI panel references |
   | `aiResponseText` / `describePicture` | Text display elements |
   | `labTechButton` / `perfumerButton` / `salesButton` / `generalButton` | Mode selection buttons |
   | `TTSSpeaker` | Speech output component |
   | `debugPicture` | *(Optional)* Static texture for Editor testing |

4. **Build for Android** — Switch platform to Android in Build Settings, connect your Meta Quest, and click **Build and Run**

---

## 🔐 API Key Security

> ⚠️ **Never commit API keys to version control.**

- Set your OpenAI key in `Assets/Resources/OpenAIConfiguration.asset` locally via the Inspector
- This file should be listed in `.gitignore` or the key field left blank in tracked files
- Regenerate any key that was previously exposed in a commit

---

## 🎙️ Usage

1. Launch the app and select a **user mode** from the mode selection UI
2. Speak the configured **wake word** to begin listening
3. Meta Wit parses your voice input into one of the supported intents:

   | Intent | Description |
   |---|---|
   | `describe_vision` | Identify and describe the product in view |
   | `safety_check` | Retrieve safety information |
   | `storage_info` | Get storage recommendations |
   | `usage_level` | Usage guidelines and concentrations |
   | `scent_profile` | Scent notes and olfactory profile |
   | *(general)* | Free-form chat routed to the GPT-4o chat endpoint |

4. The assistant responds in text (`aiResponseText`) and speaks the response via TTS

> **Editor testing:** Populate `debugPicture` with a static texture to test vision prompts without a live webcam.

---

## 🗂️ Relevant Files

- **AI logic & integrations** — [`Assets/AIManager.cs`](Assets/AIManager.cs)

---

## 🧑‍💻 Developer Notes

- Conversation history is stored **in-memory** (`conversationHistory`) and resets on mode switch
- The project targets `Model.GPT4o` — update the model constant in `AIManager.cs` if needed
- Image + text prompts are sent as mixed-content `Message` objects for vision requests

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| Image capture returns null | Ensure webcam is active and runtime permission is granted |
| OpenAI calls fail | Verify `OpenAIConfiguration` API key and network connectivity |
| Voice not triggering | Check microphone permissions and Wit.ai credentials in `ProjectSettings/wit.config` |
| Editor has no webcam | Assign a texture to `debugPicture` for static testing |

---

## 🤝 Contributing

Fork the repo and submit pull requests for bug fixes or features. Keep changes focused and add or update tests where applicable.

---

## 📄 License

Add your preferred license file to the repository (e.g. `LICENSE`).

---

## 👤 Author

**Pratush Mukherjee** · [GitHub](https://github.com/pratushMukherjee)# 🌸 FragranceAR — XR AI Assistant

A Unity-based mixed reality assistant that integrates **OpenAI vision & chat** and **Meta Wit voice recognition** to identify and analyze IFF (International Flavors & Fragrances) products in real time. Point your headset at a product, speak a wake word, and get instant safety, storage, usage, and scent-profile information — spoken back via TTS.

---

## ✨ Key Features

- **Multi-role mode selection** — Tailored experiences for `LabTechnician`, `Perfumer`, `SalesTeam`, and `General` users, each with custom system prompts and conversation context
- **Voice-triggered interactions** — Wake-word listening powered by Meta Wit intent recognition
- **Vision-based product identification** — Captures webcam frames and sends them to GPT-4o for image + text analysis
- **Persistent conversation history** — Per-session memory scoped to the active user mode
- **Text-to-speech output** — Spoken responses via a `TTSSpeaker` component

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Engine | Unity 2020.3+ |
| AI / Vision | OpenAI GPT-4o (`OpenAIClient`) |
| Voice / NLU | Meta Wit.ai |
| Speech Output | Unity TTS (`TTSSpeaker`) |
| Camera Input | `WebCamTextureManager` |

---

## 🚀 Quick Setup

### Prerequisites

- Unity **2020.3+** (check `ProjectSettings/ProjectVersion.txt` for the exact version used)
- OpenAI SDK imported into the Unity project
- Meta Wit package imported into the Unity project
- Microphone and webcam/passthrough access at runtime

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/pratushMukherjee/FragranceAR.git
   ```

2. **Open in Unity Hub** — Add the cloned folder as an existing project

3. **Configure the `AIManager` component** in the scene Inspector:

   | Field | Description |
   |---|---|
   | `OpenAIConfiguration` | Your OpenAI API key and model settings |
   | `WakeWordManager` | Wake-word and intent hooks |
   | `WebCamTextureManager` | Live webcam source |
   | `aiCanvas` / `loadingCanvas` / `modeSelectionCanvas` | UI panel references |
   | `aiResponseText` / `describePicture` | Text display elements |
   | `labTechButton` / `perfumerButton` / `salesButton` / `generalButton` | Mode selection buttons |
   | `TTSSpeaker` | Speech output component |
   | `debugPicture` | *(Optional)* Static texture for Editor testing |

4. **Build for Android** — Switch platform to Android in Build Settings, connect your Meta Quest, and click **Build and Run**

---

## 🔐 API Key Security

> ⚠️ **Never commit API keys to version control.**

- Set your OpenAI key in `Assets/Resources/OpenAIConfiguration.asset` locally via the Inspector
- This file should be listed in `.gitignore` or the key field left blank in tracked files
- Regenerate any key that was previously exposed in a commit

---

## 🎙️ Usage

1. Launch the app and select a **user mode** from the mode selection UI
2. Speak the configured **wake word** to begin listening
3. Meta Wit parses your voice input into one of the supported intents:

   | Intent | Description |
   |---|---|
   | `describe_vision` | Identify and describe the product in view |
   | `safety_check` | Retrieve safety information |
   | `storage_info` | Get storage recommendations |
   | `usage_level` | Usage guidelines and concentrations |
   | `scent_profile` | Scent notes and olfactory profile |
   | *(general)* | Free-form chat routed to the GPT-4o chat endpoint |

4. The assistant responds in text (`aiResponseText`) and speaks the response via TTS

> **Editor testing:** Populate `debugPicture` with a static texture to test vision prompts without a live webcam.

---

## 🗂️ Relevant Files

- **AI logic & integrations** — [`Assets/AIManager.cs`](Assets/AIManager.cs)

---

## 🧑‍💻 Developer Notes

- Conversation history is stored **in-memory** (`conversationHistory`) and resets on mode switch
- The project targets `Model.GPT4o` — update the model constant in `AIManager.cs` if needed
- Image + text prompts are sent as mixed-content `Message` objects for vision requests

---

## 🐛 Troubleshooting

| Issue | Fix |
|---|---|
| Image capture returns null | Ensure webcam is active and runtime permission is granted |
| OpenAI calls fail | Verify `OpenAIConfiguration` API key and network connectivity |
| Voice not triggering | Check microphone permissions and Wit.ai credentials in `ProjectSettings/wit.config` |
| Editor has no webcam | Assign a texture to `debugPicture` for static testing |

---

## 🤝 Contributing

Fork the repo and submit pull requests for bug fixes or features. Keep changes focused and add or update tests where applicable.

---

## 📄 License

Add your preferred license file to the repository (e.g. `LICENSE`).

---

## 👤 Author

**Pratush Mukherjee** · [GitHub](https://github.com/pratushMukherjee)
