# HTTP and HTTPS Traffic Analysis Using Wireshark

## 1. Project Overview

This project focuses on capturing and analysing HTTP and HTTPS network traffic using Wireshark. The purpose is to understand how data travels across a network and observe the differences between unencrypted HTTP communication and encrypted HTTPS communication.

## 2. Objectives

- Capture HTTP and HTTPS network traffic.
- Identify HTTP requests and responses.
- Understand HTTP status codes such as 301 and 200.
- Observe the TLS handshake process.
- Identify encrypted application data.
- Understand why HTTPS provides better communication security than HTTP.

## 3. Tools Used

- **Wireshark:** Network protocol analyser.
- **Web Browser:** Google Chrome.
- **Operating System:** Windows.

## 4. Practical Investigation

### A. HTTP Traffic Analysis

Website used: `http://neverssl.com`

The following observations were made:

**1. HTTP GET Request**

- Method: GET
- Protocol: HTTP/1.1
- Resource requested: `/online/`
- The browser sent a request to the web server.
- The request headers were visible in Wireshark.

**2. HTTP 301 Response**

- Status: 301 Moved Permanently
- Server: Apache/2.4.68
- The response contained a Location header.
- This response indicated a redirect.

**3. HTTP 200 Response**

- Status: 200 OK
- Server: Apache/2.4.68
- Content-Type: text/html
- Content-Encoding: gzip
- This indicated a successful HTTP response.
- The response body was compressed.

**4. HTTP TCP Stream**

- Follow TCP Stream was used to inspect the communication.
- HTTP request and response headers were readable.
- This demonstrated that HTTP communication can expose information in readable form.

### B. HTTPS Traffic Analysis

Website used during the investigation: `https://example.com`

The following TLS observations were made in the captured traffic:

**1. TLS Client Hello**

- The Client Hello packet was identified.
- It contained information exchanged during the TLS handshake.
- A Server Name Indication (SNI) value was visible in the captured Client Hello.

**2. TLS Encrypted Application Data**

- TLS Application Data packets were observed.
- The application data appeared encrypted.
- The actual HTTP content could not be read directly from the captured encrypted payload.

## 5. Wireshark Display Filters Used

| Filter | Purpose |
|---|---|
| `http` | Display HTTP packets |
| `http.request` | Display HTTP requests |
| `http.response` | Display HTTP responses |
| `http.response.code == 301` | Find HTTP 301 responses |
| `http.response.code == 200` | Find HTTP 200 responses |
| `tls` | Display TLS packets |
| `dns` | Display DNS packets |

## 6. Key Findings

1. HTTP requests and response headers were visible in readable form.
2. The server returned a 301 redirect response.
3. The server later returned a 200 OK response.
4. The TLS Client Hello packet was visible during HTTPS communication.
5. TLS Application Data appeared encrypted.
6. HTTPS protects application data from being directly read by someone capturing the traffic.
7. Wireshark can help analyse network communication and understand protocol behaviour.

## 7. HTTP vs HTTPS

| HTTP | HTTPS |
|---|---|
| Communication is not encrypted. | Communication is encrypted using TLS. |
| Data may be readable in a packet capture. | Application data is generally unreadable without the necessary decryption keys. |
| Uses no TLS encryption. | Uses TLS encryption. |
| Less secure for sensitive information. | Provides better protection for sensitive information. |

## 8. Conclusion

This project helped me understand how HTTP and HTTPS traffic work through practical packet analysis using Wireshark.

I learned how to capture network traffic, identify HTTP requests and responses, analyse status codes, inspect TLS handshake packets and recognise encrypted application data.

This practical exercise improved my understanding of network protocols and basic cybersecurity concepts.

## 9. Project Structure

- `Captures/` – Contains the saved Wireshark packet capture.
- `Screenshots/` – Contains screenshots of the investigation.
- `README.md` – Contains the project documentation.

---

**Project Type:** Beginner Cybersecurity / Network Traffic Analysis  
**Tool:** Wireshark  
**Focus:** HTTP, HTTPS and TLS Traffic Analysis
