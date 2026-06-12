---
title: "Advisory for firefox: Site ID gives false broken connections for TLS 1.3"
date: 2017-02-03
forum: General Help
---

### Post by bcschmerker on 2017-02-03
I have opened [Bug #1661400](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1661400) at Launchpad&#8482; to give ubuntu® developers, and ideally the Firefox team at Mozilla® as well, specific information on a misbehavior I observed when opening a URL with Transport Layer Security 1.3 (e.g., any Index page [https://*.cloudflare.com/](https://www.cloudflare.com/)).  In Firefox 50-up with the following settings in about:config (security.tls.version.min can be 1 to 3 and Firefox 50+ (actual: 51.0.1) will still reproduce the behavior in the Bug):
```
security.tls.version.fallback_limit                       integer                3
security.tls.version.max                                  integer                4
security.tls.version.min                                  integer                3
```
the Site Identity Button gives a false positive for an insecure connection.  The Gavin Lloyd Extension CipherFox ([https://addons.mozilla.org/en-US/firefox/addon/cipherfox](https://addons.mozilla.org/en-US/firefox/addon/cipherfox)) reports the use of TLS 1.3 as follows:
```
TLS 1.3 - AES 128-bit
TLS_AES_128-GCM_SHA256
Cloudflare, Inc. ECC 256-bit SHA256.
DigiCert Inc: ECC 384-bit SHA384.
DigiCert Inc: RSA 2048-bit SHA1.

```
The Sibi Anthony Extension SSleuth ([https://addons.mozilla.org/en-US-firefox/addon/ssleuth](https://addons.mozilla.org/en-US-firefox/addon/ssleuth)) reports the following for [www.cloudflare.com:]()
```
Cipher Suite
TLS_AES_128_GCM_SHA256_SHA256
Key exchange: Unknown. TLS 1.3
Authentication: Unknown. TLS 1.3
Bulk Cipher: AES GCM 128 bits. AEAD
HMAC: SHA-256.
Perfect Forward Secrecy: Yes
SSL/TLS Version: TLSv1.3
Connection Status: Broken
  This page has either insecure content or a bad certificate.
Certificate
Extended validation: No
Signature SHA-256/ECDSA bits.
Common name: cloudflare.com
Issued to: Cloudflare, Inc.
Issued by: DigiCert Inc
           www.digicert.com
Validity: [Redacted]
Fingerprint: [Redacted]

```
The exact information I'd like relayed to Mozilla describes the bug in Mozilla's terms:
```
User Agent: Mozilla 5.0 (X11; LinUX x86_64; rv:51.0) Gecko/20100101 Firefox/51.0.1
Build ID: 20170125172221

Steps to reproduce:

Opened HTML page https://www.cloudflare.com/; Opened Site Identity Button

Reproducible: Always

Actual Results:
www.cloudflare.com
Connection is Not Secure
! This page uses weak encryption.
->
  Your connection to this website uses weak encryption and is not private.
  ! Other people can view your information or modify the website's behavior.

Expected Results:
www.cloudflare.com
  Secure Connection
->
  Verified by: DigiCert, Inc.

```As the required fix entails new code, I'm recommending Triage as soon as enough Users are confirmed affected.

---

### Post by bcschmerker on 2017-03-14
All systems go for Firefox 52.0.  Considering the issue RESOLVED FIXED.

```
User Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0
Build ID: 20170303012758

```

---

