# Fine Tuning Whisper
This project is dedicated to fine-tuning OpenAI’s Whisper model to significantly improve its performance on Khmer (Cambodian) speech recognition tasks. It includes custom scripts, curated datasets, and an end-to-end training pipeline specifically designed for enhancing Whisper’s transcription accuracy on Khmer audio. The goal is to make Whisper more robust and reliable for real-world transcription scenarios and voice-driven applications in the Khmer language.

### Forced Alignment
Forced alignment plays a critical role in preparing training data by synchronizing audio recordings with their corresponding text transcriptions. This process divides each audio file into segments that precisely match the spoken words or phrases in the transcript. Proper alignment ensures the model can learn accurate temporal relationships between sound and text, which is essential for improving both training efficiency and final transcription quality.

```mermaid
graph TD
    %% Transcript Path
    subgraph Transcript_Processing [Transcript Path]
        T[Transcript] --> N[Normalization]
        N --> R[Romanization]
        R --> NU[Normalize Uroman]
        NU --> TOK[Tokenizer]
        TOK --> TS[Token Sequence]
    end

    %% Audio Path
    subgraph Audio_Processing [Audio Path]
        W[Waveform] --> M[Model]
        M --> EP[Emission Probabilities]
    end

    %% Convergence
    EP --> Aligner{Aligner}
    TS --> Aligner

    %% Output
    Aligner --> Final[Token with time stamps and score]

    %% Styling
    style T fill:#3b82f6,color:#fff
    style W fill:#3b82f6,color:#fff
    style N fill:#a855f7,color:#fff
    style R fill:#a855f7,color:#fff
    style NU fill:#a855f7,color:#fff
    style TOK fill:#a855f7,color:#fff
    style TS fill:#a855f7,color:#fff
    style M fill:#a855f7,color:#fff
    style EP fill:#a855f7,color:#fff
    style Aligner fill:#ec4899,color:#fff
    style Final fill:#10b981,color:#fff
```

- [Forced alignment for multilingual data](https://docs.pytorch.org/audio/main/tutorials/forced_alignment_for_multilingual_data_tutorial.html)
- [CTC forced alignment API tutorial](https://docs.pytorch.org/audio/main/tutorials/ctc_forced_alignment_api_tutorial.html)
