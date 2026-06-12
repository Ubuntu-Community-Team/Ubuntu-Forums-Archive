---
title: "Ubuntu - cannot send mail to smtp.office365.com"
date: 2015-03-20
forum: General Help
---

### Post by andrew-bridget-btinternet on 2015-03-20
Thunderbird 31.5.0
Ubuntu 14.04

I seem to have a problem that thunderbird does not ask or save for the smtp password. this is not a new install but recently upgraded from 12.04. Email was working fine after upgrade for several days so I am sure it is not down to the upgrade. 
I had lost email receiving and sending, I have checked with BT and nothing has changed there, and I have the account working on another pc. I have cleared the account, and re-installed the account. I can now receive emails now but cannot send them. I get the error

An error occurred sending mail: SMTP server xxxx.xxxxxxx.com is unknown. The server may be incorrectly configured. Please verify......

I have checked the passwords but the only passwords that are saved in 'Saved Passwords' are mailbox://, but not SMTP password. I am wondering if I have a issue with a corrupted password file ? I have removed all passwords and re-saved. I have re-installed thunderbird via synaptic but this has made no difference.
Any advise what to try now ?
Thanks.

---

### Post by amanchesterman on 2015-03-20
The answers given here [https://support.mozilla.org/en-US/questions/995190](https://support.mozilla.org/en-US/questions/995190) suggest
a) edit the settings so that TBird prompts you for passwords, and if that fails then
b) create a new user profile.

In my experience (b) solves most problems. However you then have to transfer saved emails, settings etc. from the old profile, so it's more work.  The weblink given above includes instructions on how to do it, but make sure you save your old profile folder: don't just delete it.

As a general hint, if you're having problems with an application it's a good idea to look for help in forums dedicated to that application rather than asking in a general Linux forum first.

---

### Post by buzzingrobot on 2015-03-20
> **andrew-bridget-btinternet said:**
> 
An error occurred sending mail: SMTP server xxxx.xxxxxxx.com is unknown. The server may be incorrectly configured. Please verify......



Check that Thunderbird is using the correct ports, etc. I've noticed the error messages it displays are sometimes off-target.

---

### Post by ajgreeny on 2015-03-20
I wonder if this is anything to do with the newer security requirements of TB as mentioned in some posts in the thread at [http://ubuntuforums.org/showthread.php?t=2264770](http://ubuntuforums.org/showthread.php?t=2264770)

---

### Post by andrew-bridget-btinternet on 2015-03-21
Thanks for your replies, this is nothing to do with passwords as I first thought, it seems that smtp.office365.com will not talk to Ubuntu.
 I have tried pinging the smtp.office365.com from Ubuntu(14.04) but I get a unknown server, but if i ping  smtp.office365.com from a windows pc it gives me the server address of  outlook-emeawest.office365.com if I ping this address from Ubuntu I get a reply, If I enter this address in the smtp address for the outgoing server I can send mail  without problems. The only problem I will get balcklisted for using this  address I have been informed by BT. It would seem windows have changed something to stop linux accessing office365.com mail servers. I can access smtp.office365,com on my MAC !

---

### Post by howefield on 2015-03-21
> **andrew-bridget-btinternet said:**
> Thanks for your replies, this is nothing to do with passwords as I first thought, it seems that smtp.office365.com will not talk to Ubuntu.
 I have tried pinging the smtp.office365.com from Ubuntu(14.04) but I get a unknown server, but if i ping  smtp.office365.com from a windows pc it gives me the server address of  outlook-emeawest.office365.com if I ping this address from Ubuntu I get a reply, If I enter this address in the smtp address for the outgoing server I can send mail  without problems. The only problem I will get balcklisted for using this  address I have been informed by BT. It would seem windows have changed something to stop linux accessing office365.com mail servers. I can access smtp.office365,com on my MAC !

You need to look elsewhere, smtp.office365.com is pingable from Ubuntu. Blacklisted for using smtp.office365.com ? I doubt it.

---

### Post by andrew-bridget-btinternet on 2015-03-21
Thanks I had tried using 'telnet' not 'ping'. You are certainly right you can 'ping' smtp.office365.com. Any pointers to where I would start to look elsewhere ? 

server name : smtp.office365.com - does not work.
server name : **outlook-emeawest.office365.com - works !**


(using - outlook-emeawest.office365.com I would get black listed.)

I can now send mail by using this address:

smtp.outlook.office365.com

After lots searching I an no wiser.


[LIST]
[*]I can ping the server smtp.office365.com, but cannot send mail.
[*]I can send mail via smtp.outlook.office365.com - but [http://community.office365.com](http://community.office365.com) MSFT Support cannot advise me and no documentation available for that address.
[/LIST]
> I have done lots of research and found no official documents saying  that you can send emails by ''smtp.outlook.office365.com''. Since this  address is not supported, we cannot make sure whether  ''smtp.outlook.office365.com'' will work in the future or not.
 If  you use this address and it is blocked by BT, you need to contact BT  support for dedicated assistance. Your understanding is highly  appreciated.

[LIST]
[*]if i nslookup :
[/LIST]
```
nslookup smtp.office365.com
Server:        127.0.1.1
Address:    127.0.1.1#53

Non-authoritative answer:
smtp.office365.com    canonical name = smtp.outlook.office365.com.
smtp.outlook.office365.com    canonical name = outlook.office365.com.
outlook.office365.com    canonical name = lb.geo.office365.com.
lb.geo.office365.com    canonical name = outlook.office365.com.glbdns2.microsoft.com.
outlook.office365.com.glbdns2.microsoft.com    canonical name = outlook-emeawest.office365.com.
Name:    outlook-emeawest.office365.com
Address: 132.245.225.98
Name:    outlook-emeawest.office365.com
Address: 132.245.224.162
Name:    outlook-emeawest.office365.com
Address: 132.245.194.242
Name:    outlook-emeawest.office365.com
Address: 132.245.226.34
Name:    outlook-emeawest.office365.com
Address: 132.245.229.130
Name:    outlook-emeawest.office365.com
Address: 132.245.195.162
Name:    outlook-emeawest.office365.com
Address: 132.245.34.34
Name:    outlook-emeawest.office365.com
Address: 132.245.67.82
Name:    outlook-emeawest.office365.com
Address: 191.234.225.162
Name:    outlook-emeawest.office365.com
Address: 132.245.27.34
Name:    outlook-emeawest.office365.com
Address: 132.245.68.242
Name:    outlook-emeawest.office365.com
Address: 132.245.212.98
```


[LIST]
[*]BT are unhelpful 'As they donot support Linux or Thunderbird', it is not a Thunderbird issue as I have tried other mail clients and my own python scripts. They suggest they have not changed anything in the last 10 days to cause this problem,
[/LIST]

In my very limited understanding of the issue it would seem that the smtp.office365.com will not talk to Linux. With my python script I get this error using smtp.office365.com:
```
[PHP]Traceback (most recent call last):
  File "/home/andrew/sharedfolder/test.py", line 15, in <module>
    smtpObj = smtplib.SMTP('smtp.office365.com',587)
  File "/usr/lib/python2.7/smtplib.py", line 251, in __init__
    (code, msg) = self.connect(host, port)
  File "/usr/lib/python2.7/smtplib.py", line 311, in connect
    self.sock = self._get_socket(host, port, self.timeout)
  File "/usr/lib/python2.7/smtplib.py", line 286, in _get_socket
    return socket.create_connection((host, port), timeout)
  File "/usr/lib/python2.7/socket.py", line 553, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
socket.gaierror: [Errno -2] Name or service not known[/PHP]
```

---

### Post by buzzingrobot on 2015-03-25
FWIW, pings and traceroutes here to both addresses resolve to an identical "outlook-namcentral.office365.com'.  The IP's vary, but I'd expect that for something as large as office65.com.

It might be interesting to compare the full headers of a message sent using the SMTP address that works on Thunderbird with one sent using the other, assuming you have access to a Windows system.

Many customer/tech support staffers work off a script and are directed to avoid giving responses to people using unsupported software, even if you're just asking about the names of their mail servers. Telling them you use Windows or Macs will at least get them to start talking.

---

### Post by andrew-bridget-btinternet on 2015-03-25
As far as I can see from my python script we are not even getting to that stage, the server is not accepting a connection from Linux. So we are not even getting a hand shake to say 'Hello' I am smtp.office365.com, as I get no response from the server. Where as with 'smtp.outlook.office365.com' I get a 250 reply Hello .

[PHP]send: 'ehlo [127.0.1.1]\r\n'
reply: '250-HE1PR08CA0041.outlook.office365.com Hello [81.149.56.108]\r\n'
reply: '250-SIZE 157286400\r\n'
reply: '250-PIPELINING\r\n'
reply: '250-DSN\r\n'
reply: '250-ENHANCEDSTATUSCODES\r\n'
reply: '250-STARTTLS\r\n'
reply: '250-8BITMIME\r\n'
reply: '250-BINARYMIME\r\n'
reply: '250 CHUNKING\r\n'
reply: retcode (250); Msg: HE1PR08CA0041.outlook.office365.com Hello [81.149.56.108][/PHP]

It would appear I can connect via openssl s_cleint ?

[PHP]openssl s_client -starttls smtp -crlf -connect smtp.office365.com:587
CONNECTED(00000003)
depth=1 C = US, ST = Washington, L = Redmond, O = Microsoft Corporation, OU = Microsoft IT, CN = Microsoft IT SSL SHA1
verify error:num=20:unable to get local issuer certificate
verify return:0
---
Certificate chain
 0 s:/C=US/ST=WA/L=Redmond/O=Microsoft Corporation/OU=Microsoft Corporation/CN=outlook.com
   i:/C=US/ST=Washington/L=Redmond/O=Microsoft Corporation/OU=Microsoft IT/CN=Microsoft IT SSL SHA1
 1 s:/C=US/ST=Washington/L=Redmond/O=Microsoft Corporation/OU=Microsoft IT/CN=Microsoft IT SSL SHA1
   i:/C=IE/O=Baltimore/OU=CyberTrust/CN=Baltimore CyberTrust Root
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIGzjCCBbagAwIBAgITGQAADkwY0+oD6i7gSwABAAAOTDANBgkqhkiG9w0BAQUF
ADCBizELMAkGA1UEBhMCVVMxEzARBgNVBAgTCldhc2hpbmd0b24xEDAOBgNVBAcT
B1JlZG1vbmQxHjAcBgNVBAoTFU1pY3Jvc29mdCBDb3Jwb3JhdGlvbjEVMBMGA1UE
CxMMTWljcm9zb2Z0IElUMR4wHAYDVQQDExVNaWNyb3NvZnQgSVQgU1NMIFNIQTEw
HhcNMTUwMjEzMDAzODE1WhcNMTYwMjEzMDAzODE1WjCBgjELMAkGA1UEBhMCVVMx
CzAJBgNVBAgTAldBMRAwDgYDVQQHEwdSZWRtb25kMR4wHAYDVQQKExVNaWNyb3Nv
ZnQgQ29ycG9yYXRpb24xHjAcBgNVBAsTFU1pY3Jvc29mdCBDb3Jwb3JhdGlvbjEU
MBIGA1UEAxMLb3V0bG9vay5jb20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
AoIBAQCx1np0uaQcYd3xAokYkWte3+EH+fuWg0cZKmSvud9O9rlWyTTaMzlo1FR0
dqmyfuzClQxG0kKwPhhl4G6A+yE4hoYCYY/RYokSmVdFddoA7kVPwnE8b/DA+ge3
qGWJCOJoxYmlRF/exQlPfrTZ57mfRD4ajbxqPqhD20MGtKS4Plsr5qiJ7Wt7nV68
58LdG5xm/kCVj6A4Px+tL/wL1HraQYN8FEi8Aq8AovbSfDBFgL1QwMT6ZotjwJ5k
/LpCgbPNcYr1WZ8chUHrchWV5qmsZcmYCeMzn1HQBDRptoQNnQsuXB8VOPRPvW6g
rKDSUqiYGOYfMM/ZNn6iHDp4uby/AgMBAAGjggMwMIIDLDALBgNVHQ8EBAMCBLAw
HQYDVR0lBBYwFAYIKwYBBQUHAwIGCCsGAQUFBwMBMHgGCSqGSIb3DQEJDwRrMGkw
DgYIKoZIhvcNAwICAgCAMA4GCCqGSIb3DQMEAgIAgDALBglghkgBZQMEASowCwYJ
YIZIAWUDBAEtMAsGCWCGSAFlAwQBAjALBglghkgBZQMEAQUwBwYFKw4DAgcwCgYI
KoZIhvcNAwcwHQYDVR0OBBYEFG/I8zShnKgaS1lmD85Fl6GnqcsjMB8GA1UdIwQY
MBaAFNyILdlsTT0AUDPxFbl4+8HmoSSvMH0GA1UdHwR2MHQwcqBwoG6GNmh0dHA6
Ly9tc2NybC5taWNyb3NvZnQuY29tL3BraS9tc2NvcnAvY3JsL21zaXR3d3cxLmNy
bIY0aHR0cDovL2NybC5taWNyb3NvZnQuY29tL3BraS9tc2NvcnAvY3JsL21zaXR3
d3cxLmNybDBwBggrBgEFBQcBAQRkMGIwPAYIKwYBBQUHMAKGMGh0dHA6Ly93d3cu
bWljcm9zb2Z0LmNvbS9wa2kvbXNjb3JwL21zaXR3d3cxLmNydDAiBggrBgEFBQcw
AYYWaHR0cDovL29jc3AubXNvY3NwLmNvbTBOBgNVHSAERzBFMEMGCSsGAQQBgjcq
ATA2MDQGCCsGAQUFBwIBFihodHRwOi8vd3d3Lm1pY3Jvc29mdC5jb20vcGtpL21z
Y29ycC9jcHMAMCcGCSsGAQQBgjcVCgQaMBgwCgYIKwYBBQUHAwIwCgYIKwYBBQUH
AwEwgdkGA1UdEQSB0TCBzoILb3V0bG9vay5jb22CDSoub3V0bG9vay5jb22CDW9m
ZmljZTM2NS5jb22CDyoub2ZmaWNlMzY1LmNvbYIKKi5saXZlLmNvbYIWKi5pbnRl
cm5hbC5vdXRsb29rLmNvbYIXKi5vdXRsb29rLm9mZmljZTM2NS5jb22CEm91dGxv
b2sub2ZmaWNlLmNvbYIdYXR0YWNobWVudC5vdXRsb29rLm9mZmljZS5uZXSCIGF0
dGFjaG1lbnQub3V0bG9vay5vZmZpY2VwcGUubmV0MA0GCSqGSIb3DQEBBQUAA4IB
AQAaG/qZoWu4xncpyyd2dcqqIar8yjq3XrSaS0V0QTm2aJAUEOldvG+Jy0p82ObJ
wk1EOdw1OZNFzzg8TKWFs7nHRNeGeQLLVVwAR0s9VTEyl8KsRlZlKz+tfrRuHDRW
GpqS7oC7wkrJziDn8c1CCiYO4DSJjR708E6TTi5yOGaCvIEKfQ4bHPCRAsBrsTHE
qLD1jfz7nX0wu41vNxlD7yzvYp/NXRYRC63Nxm2f2gGGBWYu9dTM/VF3FJJ6VTu1
499r9KLM4zKU+JJ3eLCbNzU0MTCS8mGCQtr9QG5+tZSMNOv1y9lSbkl08WP5dX3W
YzVLRobM+Gokge2V62lz1T3U
-----END CERTIFICATE-----
subject=/C=US/ST=WA/L=Redmond/O=Microsoft Corporation/OU=Microsoft Corporation/CN=outlook.com
issuer=/C=US/ST=Washington/L=Redmond/O=Microsoft Corporation/OU=Microsoft IT/CN=Microsoft IT SSL SHA1
---
No client certificate CA names sent
---
SSL handshake has read 3844 bytes and written 566 bytes
---
New, TLSv1/SSLv3, Cipher is ECDHE-RSA-AES256-SHA384
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-SHA384
    Session-ID: BB35000072E0F9BC34480EFFE0A3D412B4B4BCC0B8AEBABC77F3A71245F3022C
    Session-ID-ctx: 
    Master-Key: 8F7EF34EA53E0CDCA635D1E885F818A4AC91491258CDF628DB401FCD895D5FE841447DDE3C566D1F3CEEE1C5CBE5F3EA
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    Start Time: 1427283821
    Timeout   : 300 (sec)
    Verify return code: 20 (unable to get local issuer certificate)
---
250 CHUNKING
[/PHP]

[COLOR=#111111][FONT=Ubuntu]This seems to have sorted the problem...

> Try disabling IPv6
[https://support.mozilla.org/en-US/kb/firefox-cant-load-websites-other-browsers-can](https://support.mozilla.org/en-US/kb/firefox-cant-load-websites-other-browsers-can)
set 'network.dns.disableIPv6' to 'true'
(Thunderbird: preferences: advanced: config editor)


[/FONT][/COLOR]

---

### Post by MattBro on 2015-12-18
Yes thanks this worked for me as well some 8 months later.  Should we blame microsoft?

> Try disabling IPv6
[https://support.mozilla.org/en-US/kb...r-browsers-can](https://support.mozilla.org/en-US/kb...r-browsers-can)
set 'network.dns.disableIPv6' to 'true'
(Thunderbird: preferences: advanced: config editor)

---

