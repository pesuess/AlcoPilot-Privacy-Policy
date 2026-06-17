**Effective date:** 2026-06-17

This Privacy Policy describes how **Alcopilot** (the "App") processes personal data in accordance with the General Data Protection Regulation (GDPR / DSGVO).

---

## 1. Controller

The data controller responsible for this App is: 

Name: Peter Süßmeier  
Address: Neutorstraße 37, 55116 Mainz, Germany  
Email: betterlabs.apps@gmail.com

---

## 2. Data Processing Overview

The App primarily processes personal data **locally on your device**. However, certain optional features require transmitting limited data to third-party services.

The App does not use:
- User accounts
- Tracking technologies
- Third-party analytics services
- Advertising services
- Cookies

---

## 3. Data You Provide and How It Is Processed

### 3.1 Local Data Processing
You may enter the following data into the App:
- Body weight  
- Body height  
- Age  
- Biological sex  
- Metabolism rate (alcohol elimination rate)  
- Consumed drinks (name, volume, alcohol content, time)

This data is processed solely for the purpose of estimating blood alcohol concentration (BAC) and is **stored locally on your device**. None of this data is transmitted to external servers.

Additionally, the App stores basic usage counters locally on your device (e.g. number of app opens and drinks added). These counters are used exclusively to determine the appropriate time to show an in-app review prompt and are never transmitted to external servers.

### 3.2 AI-Powered Alcohol by Volume (ABV) Estimation
When you use the AI function to automatically determine the alcohol content (ABV) of a drink, the App transmits the **name of the drink** you entered (up to 60 characters) to a backend service. 

- **Data transmitted:** Only the text of the drink name. No personal identifiers, weight, sex, or other physiological data are transmitted.
- **Third-party services involved:**
  - **Google Cloud Functions:** Used as a secure backend to process the request.
  - **Google Generative AI (Gemini):** Used to analyze the drink name and return the typical ABV.
- **Processing location:** The data is processed on Google's servers. By using this feature, your device's IP address is also temporarily transmitted to Google to establish the connection, which is standard for any internet request.
- **Server-side logging:** In exceptional cases (e.g. unexpected AI responses or errors), the drink name may be temporarily recorded in Google Cloud Logging for debugging purposes. These logs are automatically deleted after 30 days.

### 3.3 AI Feedback (Optional)
After receiving an AI-generated ABV estimate, you may optionally provide feedback (thumbs up/down). If you choose to submit feedback, the following data is transmitted to **Google Cloud Firestore**:

- The drink name you entered
- The AI-estimated ABV value
- Your feedback rating (thumbs up or thumbs down)
- An optional feedback category (e.g. "too high", "too low")
- An optional free-text note (up to 200 characters)
- A server-generated timestamp

This data is stored persistently in Cloud Firestore to improve the quality of the AI estimates. **No personal identifiers** (such as name, device ID, or IP address) are stored alongside the feedback. The feedback data cannot be traced back to individual users.

### 3.4 App Integrity Verification (Firebase App Check)
To protect the backend services from abuse, the App uses **Firebase App Check**. This service verifies the authenticity of the app instance by transmitting a device attestation token to Google (via Android Play Integrity or Apple DeviceCheck). This process does not transmit any personal data or usage information, only a cryptographic proof that the request originates from a genuine instance of the App.

---

## 4. Purpose and Legal Basis

| Purpose | Legal Basis |
|---------|-------------|
| Calculation and display of an estimated blood alcohol concentration (local processing). | **Art. 6(1)(a) GDPR (Consent):** By voluntarily entering your physiological data and using the App, you consent to the local processing of this data. |
| AI-powered estimation of a drink's alcohol content (ABV). | **Art. 6(1)(a) GDPR (Consent):** Before using the AI feature for the first time, you are presented with a disclaimer that you must actively confirm. You may choose not to use this feature. |
| AI feedback submission. | **Art. 6(1)(a) GDPR (Consent):** Submitting feedback is entirely voluntary. By pressing the thumbs up/down button, you consent to the transmission and storage of the feedback data described in Section 3.3. |
| App integrity verification (Firebase App Check). | **Art. 6(1)(f) GDPR (Legitimate interest):** The controller has a legitimate interest in protecting its backend services from unauthorized access and abuse. |

---

## 5. Storage and Retention

### 5.1 Local Data
All physiological data and drink logs are stored locally on your device. Data remains stored until:
- you delete it within the App,
- you clear the App's data in your device settings, or
- you uninstall the App.

### 5.2 Transmitted Data (AI ABV Feature)
The transmitted drink name is processed in real-time to generate the ABV value and is not persistently stored by the App's backend. Server-side diagnostic logs (which may contain the drink name in error cases) are automatically deleted after 30 days. Google processes this data in accordance with their [Cloud Data Processing Addendum](https://cloud.google.com/terms/data-processing-addendum).

### 5.3 Feedback Data
Feedback reports submitted via the AI feedback feature (Section 3.3) are stored in Google Cloud Firestore for an indefinite period to support ongoing quality improvements. Since the feedback data is completely anonymous and does not contain personal identifiers, it is not possible to attribute specific feedback entries to an individual user, and therefore specific deletion requests cannot be fulfilled.

---

## 6. Data Sharing

Other than the strictly necessary transmissions described in Sections 3.2, 3.3, and 3.4, **no data is shared with third parties**.

The third-party services used are:

| Service | Provider | Purpose |
|---------|----------|---------|
| Google Cloud Functions | Google LLC | Backend processing for AI ABV estimation |
| Google Generative AI (Gemini) | Google LLC | AI model for ABV determination |
| Google Cloud Firestore | Google LLC | Storage of voluntary AI feedback reports |
| Firebase App Check | Google LLC | App integrity verification |

All Google services are operated under the [Google Cloud Data Processing Addendum](https://cloud.google.com/terms/data-processing-addendum), which includes Standard Contractual Clauses (SCCs) for international data transfers.

---

## 7. Your Rights

Under the GDPR, you have the right to:

- **Access** your data (Art. 15 GDPR)  
- **Rectification** of inaccurate data (Art. 16 GDPR)  
- **Erasure** of your data (Art. 17 GDPR)  
- **Restriction** of processing (Art. 18 GDPR)  
- **Data portability** (Art. 20 GDPR)  
- **Object** to processing (Art. 21 GDPR)  
- **Lodge a complaint** with a supervisory authority (Art. 77 GDPR)

Since your personal profiles and drink history are stored locally, these rights can be exercised directly via the App (by deleting the data) or by uninstalling the App.

For feedback data stored on our servers (Section 3.3), or if you have questions regarding your rights, you can contact the controller via email at betterlabs.apps@gmail.com.

The competent supervisory authority is:  
**Der Landesbeauftragte für den Datenschutz und die Informationsfreiheit Rheinland-Pfalz**  
Postfach 30 40, 55020 Mainz, Germany  
Website: [https://www.datenschutz.rlp.de](https://www.datenschutz.rlp.de)

---

## 8. Security

All locally stored data is protected by your operating system's standard security mechanisms. The transmission of data for the AI feature and feedback submissions is secured using industry-standard encryption (HTTPS/TLS). Access to backend services is restricted via Firebase App Check to prevent unauthorized use.

---

## 9. Disclaimer

The App provides only an **estimated value** based on the Widmark formula and standard assumptions. The AI-generated ABV values are estimations and may not always be perfectly accurate.

The calculated values are not medically or legally accurate and must not be used to determine fitness to drive or for legal purposes.

---

## 10. Changes

This Privacy Policy may be updated if legal or technical changes occur. The current version will always be available within the App.

---
