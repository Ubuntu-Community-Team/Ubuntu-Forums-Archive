---
title: "Problem validating Verisign certificates."
date: 2012-12-12
forum: General Help
---

### Post by Featalene on 2012-12-12
I am having issues with a set of sites that work fine from a browser on my Windows 7 box but not from my up-to-date Ubuntu 12.04 server. Some use a Verisign Class 3 Extended Verification SSL certificate as an intermediate certificate others use a Verisign Class 3 International certificate. OpenSSL, curl, firefox and chrome fail. I have an example below. I've tried various TLS parameters all produce errors. I suspect that I need to add the intermediate certs to my certificates but why and how?

root@ctsms2:/etc/ssl/certs# openssl s_client  -connect anthemnhequote.insurix.com:443
CONNECTED(00000003)
3077994120:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:177:
---
no peer certificate available
---
No client certificate CA names sent
---
SSL handshake has read 0 bytes and written 226 bytes
---
New, (NONE), Cipher is (NONE)
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
---

---

### Post by Habitual on 2012-12-12
Test basic connectivity to the remote host?
terminal >```

telnet anthemnhequote.insurix.com 443
```gives you a 'basic' connectivity test.

offers this output:
Trying 66.179.61.13...
Connected to anthemnhequote.insurix.com.
Escape character is '^]'.

Another easy test:
```
telnet 66.179.61.13 443
```offers this output:
Trying 66.179.61.13...
Connected to 66.179.61.13.
Escape character is '^]'.

I ran your command and got this output:
```
CONNECTED(00000003)
depth=2 C = US, O = "VeriSign, Inc.", OU = VeriSign Trust Network, OU = "(c) 2006 VeriSign, Inc. - For authorized use only", CN = VeriSign Class 3 Public Primary Certification Authority - G5
verify error:num=20:unable to get local issuer certificate
verify return:0
---
Certificate chain
 0 s:/C=US/ST=Connecticut/L=Farmington/O=Corporate Information Technologies/OU=Insurix/OU=Terms of use at www.verisign.com/rpa (c)05/CN=anthemnhequote.insurix.com
   i:/C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=Terms of use at https://www.verisign.com/rpa (c)10/CN=VeriSign Class 3 International Server CA - G3
 1 s:/C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=Terms of use at https://www.verisign.com/rpa (c)10/CN=VeriSign Class 3 International Server CA - G3
   i:/C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=(c) 2006 VeriSign, Inc. - For authorized use only/CN=VeriSign Class 3 Public Primary Certification Authority - G5
 2 s:/C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=(c) 2006 VeriSign, Inc. - For authorized use only/CN=VeriSign Class 3 Public Primary Certification Authority - G5
   i:/C=US/O=VeriSign, Inc./OU=Class 3 Public Primary Certification Authority
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFVjCCBD6gAwIBAgIQQJroSC8kyGhGV/39vyUNFTANBgkqhkiG9w0BAQUFADCB
vDELMAkGA1UEBhMCVVMxFzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMR8wHQYDVQQL
ExZWZXJpU2lnbiBUcnVzdCBOZXR3b3JrMTswOQYDVQQLEzJUZXJtcyBvZiB1c2Ug
YXQgaHR0cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYSAoYykxMDE2MDQGA1UEAxMt
VmVyaVNpZ24gQ2xhc3MgMyBJbnRlcm5hdGlvbmFsIFNlcnZlciBDQSAtIEczMB4X
DTEyMDIxMDAwMDAwMFoXDTEzMDMxMjIzNTk1OVowgdExCzAJBgNVBAYTAlVTMRQw
EgYDVQQIEwtDb25uZWN0aWN1dDETMBEGA1UEBxQKRmFybWluZ3RvbjErMCkGA1UE
ChQiQ29ycG9yYXRlIEluZm9ybWF0aW9uIFRlY2hub2xvZ2llczEQMA4GA1UECxQH
SW5zdXJpeDEzMDEGA1UECxQqVGVybXMgb2YgdXNlIGF0IHd3dy52ZXJpc2lnbi5j
b20vcnBhIChjKTA1MSMwIQYDVQQDFBphbnRoZW1uaGVxdW90ZS5pbnN1cml4LmNv
bTCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEAzwkGXkiMdZF+yxfvdrMK8XBV
+Soxfm6jNgmPq8da1C/bRu9A/THivrpL2PNW1ndLAJvK2NEPFbZ/pBcEfH2oXcVW
E8D7ozs91xtREuGteuqnTLkfcGL0EKBxO7rCiZtwSJ3L73q8N9Wkihv8dhYD/nXa
b5eFBC3vltAGMC+m06UCAwEAAaOCAb8wggG7MAkGA1UdEwQCMAAwCwYDVR0PBAQD
AgWgMEQGA1UdIAQ9MDswOQYLYIZIAYb4RQEHFwMwKjAoBggrBgEFBQcCARYcaHR0
cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYTBBBgNVHR8EOjA4MDagNKAyhjBodHRw
Oi8vU1ZSSW50bC1HMy1jcmwudmVyaXNpZ24uY29tL1NWUkludGxHMy5jcmwwNAYD
VR0lBC0wKwYIKwYBBQUHAwEGCCsGAQUFBwMCBglghkgBhvhCBAEGCisGAQQBgjcK
AwMwcgYIKwYBBQUHAQEEZjBkMCQGCCsGAQUFBzABhhhodHRwOi8vb2NzcC52ZXJp
c2lnbi5jb20wPAYIKwYBBQUHMAKGMGh0dHA6Ly9TVlJJbnRsLUczLWFpYS52ZXJp
c2lnbi5jb20vU1ZSSW50bEczLmNlcjBuBggrBgEFBQcBDARiMGChXqBcMFowWDBW
FglpbWFnZS9naWYwITAfMAcGBSsOAwIaBBRLa7kolgYMu9BSOJsprEsHiyEFGDAm
FiRodHRwOi8vbG9nby52ZXJpc2lnbi5jb20vdnNsb2dvMS5naWYwDQYJKoZIhvcN
AQEFBQADggEBAEl+FMiWJUyOFx9l8T2rpMh9A6zU+W0QaVOu4kfO9L5xbAYIwCXW
lnftQ4MpAot1JteGdy/hiQ9tcCzjTzzRF+WrrkkTt2T8LJpCvjZAR0V679RPSe7C
/4rFj+I4M73l6GjM9lKcsbHbgIF5nVVhez/U5ZcySzFE+g0ohIkuj00PLCXRDBUa
3JmbYjmnPKdhFVoLIwovsZ9M2/L6wvZhkfeJAh8XMJpG6Nk4VXA5D7e/Cm32AQit
aUOK3TLsnkA6ogyY4sCrPt364E8lysa0PtM/WzpurYBf6ErQr5YdKYNIfFOZI+95
49z/CwF5gY1MonucPFk7hkAmjcZ5ljthHdc=
-----END CERTIFICATE-----
subject=/C=US/ST=Connecticut/L=Farmington/O=Corporate Information Technologies/OU=Insurix/OU=Terms of use at www.verisign.com/rpa (c)05/CN=anthemnhequote.insurix.com
issuer=/C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=Terms of use at https://www.verisign.com/rpa (c)10/CN=VeriSign Class 3 International Server CA - G3
---
No client certificate CA names sent
---
SSL handshake has read 4327 bytes and written 509 bytes
---
New, TLSv1/SSLv3, Cipher is DES-CBC3-SHA
Server public key is 1024 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : DES-CBC3-SHA
    Session-ID: 871B0000828F4D9D718897177C92F757C58DA627A9B45553448A64B06D808284
    Session-ID-ctx: 
    Master-Key: 1620F9EC0C60169D02BE750956C74A4602ABDBF22E1EBB3426D8923537B4F44D9E63CC2E5D1B3ED3A0272BF57B214A54
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1355357609
    Timeout   : 300 (sec)
    Verify return code: 20 (unable to get local issuer certificate)
---



```

Please let us know...

---

### Post by Featalene on 2012-12-12
Thank you for your help but even before your test I knew the TCP connection was working and that it is a valid certificate. I assume your command output was from a Ubuntu system if so I am even more perplexed as to what to do to fix mine. This machine has been through several release upgrades. I tried reinstalling the certificate package and that did not help. 

To clarify what I don't know is what I need to do to my Ubuntu 12.04 system so that applications can validate the sites. I am assuming I need to add an intermediate CA certificate but after that I don't know where I get that nor am I sure the correct method to install it.

---

### Post by Habitual on 2012-12-13
If your task is to verify Verisign Certificate **dates**, this will echo the valid dates for the certificate:

```
echo | openssl s_client -connect anthemnhequote.insurix.com:443 2>/dev/null |openssl x509 -dates -noout
```notBefore=Feb 10 00:00:00 2012 GMT
notAfter=Mar 12 23:59:59 2013 GMT

These may help your quest:
[http://www.cyberciti.biz/faq/test-ssl-certificates-diagnosis-ssl-certificate](http://www.cyberciti.biz/faq/test-ssl-certificates-diagnosis-ssl-certificate)
[http://gagravarr.org/writing/openssl-certs/index.shtml](http://gagravarr.org/writing/openssl-certs/index.shtml)
[http://www.sslshopper.com/article-most-common-openssl-commands.html](http://www.sslshopper.com/article-most-common-openssl-commands.html)

---

### Post by Featalene on 2012-12-13
This may be confusing some people the openssl command is a diagnostic not what I want to run. I am running Zabbix to monitor our websites. Zabbix uses the curl library which in turn uses the openssl library. The curl library emits an error about these sites. As I debugged the problem I found that it is indeed a certificate issue using openssl. Now I need to find and fix the issue. I suspect it is an intermediate certificate I need to make the openssl library and thereby making curl library happy.

---

### Post by cconstantine on 2013-03-08
Did you ever find a solution for this?

> 
-----END CERTIFICATE-----
subject=/C=US/ST=Connecticut/L=Farmington/O=Corporate Information Technologies/OU=Insurix/OU=Terms of use at [www.verisign.com/rpa](www.verisign.com/rpa) (c)05/CN=anthemnhequote.insurix.com
issuer=/C=US/O=VeriSign, Inc./OU=VeriSign Trust Network/OU=Terms of use at [https://www.verisign.com/rpa](https://www.verisign.com/rpa) (c)10/CN=VeriSign Class 3 International Server CA - G3
---


I see you're encountering a certificate signed by the VeriSign G3 International CA cert. I've encountered this same problem ... although I'm verifying in the context of STARTTLS for mail servers.

So I'm currently trying to figure out how to install this (the VS G3 int CA cert). I can see it is NOT present in Ubuntu's /etc/ssl/certs directory.

---

### Post by cconstantine on 2013-03-08
I was able to resolve the problem by adding the VeriSign CA certificate to my server:

Here's the contents of the certificate file I created. The first line mentions the URL where I obtained this certificate

```
https://knowledge.verisign.com/support/ssl-certificates-support/index?page=content&id=SO14649&actp=search&viewlocale=en_US&searchid=1311962639768
VeriSign Class 3 International Server CA - G3
Intermediate CA for the following products:
 Secure Site Pro
 Managed PKI for SSL Premium
 Managed PKI for SSL Premium Intranet
Issued to: VeriSign Class 3 International Server CA - G3
Issued by: VeriSign Class 3 Public Primary Certification Authority - G5
Valid from: 2/7/2010 to 2/7/2020
Serial Number: 64 1b e8 20 ce 02 08 13 f3 2d 4d 2d 95 d6 7e 67
-----BEGIN CERTIFICATE-----
MIIGKTCCBRGgAwIBAgIQZBvoIM4CCBPzLU0tldZ+ZzANBgkqhkiG9w0BAQUFADCB
yjELMAkGA1UEBhMCVVMxFzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMR8wHQYDVQQL
ExZWZXJpU2lnbiBUcnVzdCBOZXR3b3JrMTowOAYDVQQLEzEoYykgMjAwNiBWZXJp
U2lnbiwgSW5jLiAtIEZvciBhdXRob3JpemVkIHVzZSBvbmx5MUUwQwYDVQQDEzxW
ZXJpU2lnbiBDbGFzcyAzIFB1YmxpYyBQcmltYXJ5IENlcnRpZmljYXRpb24gQXV0
aG9yaXR5IC0gRzUwHhcNMTAwMjA4MDAwMDAwWhcNMjAwMjA3MjM1OTU5WjCBvDEL
MAkGA1UEBhMCVVMxFzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMR8wHQYDVQQLExZW
ZXJpU2lnbiBUcnVzdCBOZXR3b3JrMTswOQYDVQQLEzJUZXJtcyBvZiB1c2UgYXQg
aHR0cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYSAoYykxMDE2MDQGA1UEAxMtVmVy
aVNpZ24gQ2xhc3MgMyBJbnRlcm5hdGlvbmFsIFNlcnZlciBDQSAtIEczMIIBIjAN
BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAmdacYvAV9IGaQQhZjxOdF8mfUdza
sVLv/+NB3eDfxCjG4615HycQmLi7IJfBKERBD+qpqFLPTU4bi7u1xHbZzFYG7rNV
ICreFY1xy1TIbxfNiQDk3P/hwB9ocenHKS5+vDv85burJlSLZpDN9pK5MSSAvJ5s
1fx+0uFLjNxC+kRLX/gYtS4w9D0SmNNiBXNUppyiHb5SgzoHRsQ7AlYhv/JRT9Cm
mTnprqU/iZucff5NYAclIPe712mDK4KTQzfZg0EbawurSmaET0qO3n40mY5o1so5
BptMs5pITRNGtFghBMT7oE2sLktiEuP7TfbJUQABH/weaoEqOOC5T9YtRQIDAQAB
o4ICFTCCAhEwEgYDVR0TAQH/BAgwBgEB/wIBADBwBgNVHSAEaTBnMGUGC2CGSAGG
+EUBBxcDMFYwKAYIKwYBBQUHAgEWHGh0dHBzOi8vd3d3LnZlcmlzaWduLmNvbS9j
cHMwKgYIKwYBBQUHAgIwHhocaHR0cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYTAO
BgNVHQ8BAf8EBAMCAQYwbQYIKwYBBQUHAQwEYTBfoV2gWzBZMFcwVRYJaW1hZ2Uv
Z2lmMCEwHzAHBgUrDgMCGgQUj+XTGoasjY5rw8+AatRIGCx7GS4wJRYjaHR0cDov
L2xvZ28udmVyaXNpZ24uY29tL3ZzbG9nby5naWYwNAYDVR0lBC0wKwYIKwYBBQUH
AwEGCCsGAQUFBwMCBglghkgBhvhCBAEGCmCGSAGG+EUBCAEwNAYIKwYBBQUHAQEE
KDAmMCQGCCsGAQUFBzABhhhodHRwOi8vb2NzcC52ZXJpc2lnbi5jb20wNAYDVR0f
BC0wKzApoCegJYYjaHR0cDovL2NybC52ZXJpc2lnbi5jb20vcGNhMy1nNS5jcmww
KAYDVR0RBCEwH6QdMBsxGTAXBgNVBAMTEFZlcmlTaWduTVBLSS0yLTcwHQYDVR0O
BBYEFNebfNgioBX33a1fzimbWMO8RgC1MB8GA1UdIwQYMBaAFH/TZafC3ey78DAJ
80M5+gKvMzEzMA0GCSqGSIb3DQEBBQUAA4IBAQBxtX1zUkrd1000Ky6vlEalSVAC
T/gvF3DyE9wfIYaqwk98NzzURniuXXhv0bpavBCrWDbFjGIVRWAXIeLVQqh3oVXY
QwRR9m66SOZdTLdE0z6k1dYzmp8N5tdOlkSVWmzWoxZTDphDzqS4w2Z6BVxiEOgb
Ett9LnZQ/9/XaxvMisxx+rNAVnwzeneUW/ULU/sOX7xo+68q7jA3eRaTJX9NEP9X
+79uOzMh3nnchhdZLUNkt6Zmh+q8lkYZGoaLb9e3SQBb26O/KZru99MzrqP0nkzK
XmnUG623kHdq2FlveasB+lXwiiFm5WVu/XzT3x7rfj8GkPsZC9MGAht4Q5mo
-----END CERTIFICATE-----
```

I placed that into a file named:
```
/usr/local/share/ca-certificates/VeriSign_Class_3_International_Server_-_G3.crt
```

Then I created a sym-link in /etc/ssl/certs:
```
VeriSign_Class_3_International_Server_-_G3.crt -> /usr/local/share/ca-certificates/VeriSign_Class_3_International_Server_-_G3.crt
```

Next I used the "c_rehash" command on /etc/ssl/certs and it built the hashed symlink:
```
876bdba8.0 -> VeriSign_Class_3_International_Server_-_G3.crt
```

Finally, I specified the certs directory on the command line for openssl:
```
$ openssl s_client -CApath /etc/ssl/certs -connect elided.example.com:25 -starttls smtp
```

And I now get a successful indication from that openssl command:
```
{{ much output snipped }}
SSL handshake has read 1771 bytes and written 354 bytes
---
New, TLSv1/SSLv3, Cipher is AES256-SHA
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1
    Cipher    : AES256-SHA
    Session-ID: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    Session-ID-ctx:
    Master-Key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    Key-Arg   : None
    Start Time: 1362770385
    Timeout   : 300 (sec)
    [COLOR=red]Verify return code: 0 (ok)[/COLOR]
---
250 8BITMIME
QUIT
DONE
```

HTH

---

