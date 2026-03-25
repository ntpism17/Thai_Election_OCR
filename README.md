🗳️ Thai Election OCR — Automated Vote Extraction

📌 Project OverviewManual data entry from scanned election result documents (Form สส.6/1) is slow and prone to human error. This project implements an end-to-end pipeline to automatically extract, clean, and validate vote counts from Thai election forms using Cloud AI and fuzzy string matching.

🚀 Key FeaturesTable Extraction: Utilizes Azure Document Intelligence (prebuilt-layout) to handle complex table structures and merged cells without manual coordinate tuning.Numeral Normalization: Custom engine to convert Thai numerals ($๐-๙$) to Arabic digits ($0-9$).3-Tier Fuzzy Matching: Implements a fallback matching logic (Exact → Substring → Levenshtein Distance) to reconcile OCR typos with official party name templates.Buddhist Era (B.E.) Filtering: Smart regex to distinguish between 4-digit vote counts and Buddhist years (e.g., 2566).

🛠️ Technical ArchitectureThe pipeline follows a modular design to ensure high accuracy despite low-quality scans:Image Pre-processing: Base64 encoding and submission to Azure AI.Structural Analysis: Detecting the "Votes" and "Party" columns based on cell content density.Data Cleaning: Stripping prefixes (e.g., "พรรค") and removing non-numeric noise.Validation: Cross-referencing results against a submission template.

📊 Performance & ResultsMetric: Mean Levenshtein Distance (Lower = Better).Accuracy: Successfully matched ~92% of party-vote pairs in the test dataset.Efficiency: Processes one document (multi-page) in under 15 seconds.

💻 Tech StackLanguage: Python 3.xLibraries: Pandas, NumPy, Requests, DifflibAPI: Azure Document Intelligence (Cognitive Services)
