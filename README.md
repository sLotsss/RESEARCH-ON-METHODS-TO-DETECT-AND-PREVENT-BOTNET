
### **1. Project Overview**
This research project was conducted by a group of Information Technology students at the **University of Economics and Finance (UEF)**. The primary objective was to investigate how **botnets**—networks of compromised "zombie" devices controlled by a "botmaster"—operate within web systems and to develop effective detection and prevention mechanisms.

### **2. The Botnet Threat**
The sources highlight that botnets are a significant threat because they automate malicious activities at a massive scale. Key threats include:
*   **Credential Theft & Account Takeover:** Using lists of leaked credentials to hijack user accounts.
*   **Resource Abuse:** Launching **Layer 7 DDoS attacks**, web scraping, and API abuse.
*   **Spam & Brute Force:** Automating unsolicited content generation and persistent password-guessing attacks.
*   **Evasion Techniques:** Modern botnets use IP rotation, headless browsers, and human-mimicking behaviors to bypass traditional security filters.

### **3. Proposed Layered Defense Strategy**
The project proposes a **layered detection approach** that integrates network-level monitoring with application-level behavior analysis.

#### **A. Network-Based Detection (Snort IDS)**
The team utilized **Snort**, an open-source intrusion detection system, to identify known attack patterns through predefined rules. Specific rules implemented included:
*   **DGA Detection:** Flagging suspicious DNS queries that are unusually long (greater than 100 bytes), which often indicates **Domain Generation Algorithms** used by botnets.
*   **Connection Rate Limiting:** Triggering alerts when a single source IP sends more than **50 TCP packets within 10 seconds**, a common sign of a botnet-driven attack or port scanning.

#### **B. Machine Learning-Based Analysis (Random Forest)**
To detect advanced or adaptive bots that bypass static rules, the project employed the **Random Forest algorithm**. 
*   **Dataset:** The model was trained on an IoT botnet dataset containing over **25,000 samples** with 117 different features.
*   **Feature Selection:** The team narrowed the 117 features down to the **11 most critical ones** (such as packet size variation and weight) to optimize performance.
*   **Performance:** The resulting model achieved an extremely high **accuracy score of 0.9983** in classifying traffic as "Benign" or "Botnet".

### **4. Experimental Results**
The system was tested using a **Kali Linux** environment where attacks were simulated using tools like `hping3`. The results demonstrated that:
*   **Snort** provided immediate alerts for rule-defined behaviors.
*   **Machine Learning** successfully identified bot behaviors even when they attempted to mimic legitimate traffic.
*   The **combination of both methods** significantly reduced false positives and improved overall security compared to using a single technique.

### **5. Conclusion and Future Work**
The researchers concluded that integrating signature-based detection (Snort) with intelligent behavior analysis (ML) is the most effective strategy for modern web protection. Future developments could include expanding rules for **encrypted traffic (HTTPS)** and implementing **automated response mechanisms** like dynamic IP blocking or real-time CAPTCHA enforcement based on risk scores.
