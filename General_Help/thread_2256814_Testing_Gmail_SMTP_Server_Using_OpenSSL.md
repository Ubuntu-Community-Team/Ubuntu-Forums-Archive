---
title: "Testing Gmail SMTP Server Using OpenSSL"
date: 2014-12-15
forum: General Help
---

### Post by chiques on 2014-12-15
Hello Community,
I've been searching for ways to check to see if my machine can connect to Gmail via SMTP. I see that the Gmail serves require TLS encrypton hence using Openssl instead of telnet.

I've tried these commands but nothing seems to work. Could it be my ISP is blocking this?

```

Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-43-generic i686)

 * Documentation:  https://help.ubuntu.com/

johnnyrico@falcon:~$ openssl s_client -starttls smtp -connect smtp.gmail.com:587 -crlf -ign_eof
connect: Connection timed out
connect:errno=110
johnnyrico@falcon:~$ openssl s_client -connect smtp.gmail.com:465 -crlf

```


```

Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-43-generic i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Sun Dec 14 20:38:40 2014 from johnnyricos-acer.home
johnnyrico@falcon:~$ telnet smtp-relay.gmail.com 25
Trying 74.125.129.28...
Trying 2607:f8b0:400e:c02::1c...
telnet: Unable to connect to remote host: Network is unreachable
johnnyrico@falcon:~$ telnet smtp.gmail.com 25
Trying 74.125.129.108...
Trying 74.125.129.109...
Trying 2607:f8b0:400e:c02::6c...
telnet: Unable to connect to remote host: Network is unreachable
johnnyrico@falcon:~$ openssl s_client -connect smtp.gmail.com:465 -crlf -ign_eof
connect: Connection timed out
connect:errno=110
johnnyrico@falcon:~$ openssl s_client -starttls smtp -crlf -connect smtp.gmail.com:587
connect: Connection timed out
connect:errno=110
johnnyrico@falcon:~$


```


My source is [https://support.google.com/a/answer/2956491](https://support.google.com/a/answer/2956491) . I know it recommends using **smtp-relay.gmail.com** but that also times out.

---

### Post by lisati on 2014-12-15
Port 25 is normally used when one MTA (e.g. email server) wants to connect to another. If you're wanting to replicate what might happen when an email client is trying to connect to an email provider's server, it is likely that you will have to use another port.

---

### Post by chiques on 2014-12-15
> **lisati said:**
> Port 25 is normally used when one MTA (e.g. email server) wants to connect to another. If you're wanting to replicate what might happen when an email client is trying to connect to an email provider's server, it is likely that you will have to use another port.

I tried a couple of ways but they also time out:

```

openssl s_client -starttls smtp -crlf -connect smtp.gmail.com:587

```

```

johnnyrico@falcon:~$ openssl s_client -connect smtp.gmail.com:465 -crlf -ign_eof
connect: Connection timed out
connect:errno=110
johnnyrico@falcon:~$ openssl s_client -starttls smtp -crlf -connect smtp.gmail.com:587
connect: Connection timed out
connect:errno=110
johnnyrico@falcon:~$

```

---

### Post by andrew.46 on 2014-12-15
Hmmmm.... this works here:

```

andrew@ilium~$ **[COLOR="#FF0000"]openssl s_client -CApath /usr/share/ca-certificates/ -starttls smtp -connect smtp.gmail.com:587 -crlf -ign_eof[/COLOR]**
CONNECTED(00000003)
depth=3 C = US, O = Equifax, OU = Equifax Secure Certificate Authority
verify return:1
depth=2 C = US, O = GeoTrust Inc., CN = GeoTrust Global CA
verify return:1
depth=1 C = US, O = Google Inc, CN = Google Internet Authority G2
verify return:1
depth=0 C = US, ST = California, L = Mountain View, O = Google Inc, CN = smtp.gmail.com
verify return:1
---
Certificate chain
 0 s:/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
   i:/C=US/O=Google Inc/CN=Google Internet Authority G2
 1 s:/C=US/O=Google Inc/CN=Google Internet Authority G2
   i:/C=US/O=GeoTrust Inc./CN=GeoTrust Global CA
 2 s:/C=US/O=GeoTrust Inc./CN=GeoTrust Global CA
   i:/C=US/O=Equifax/OU=Equifax Secure Certificate Authority
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIEdjCCA16gAwIBAgIIGcMF7jeVMoAwDQYJKoZIhvcNAQEFBQAwSTELMAkGA1UE
BhMCVVMxEzARBgNVBAoTCkdvb2dsZSBJbmMxJTAjBgNVBAMTHEdvb2dsZSBJbnRl
cm5ldCBBdXRob3JpdHkgRzIwHhcNMTQwNzE1MDg0MDM4WhcNMTUwNDA0MTUxNTU1
WjBoMQswCQYDVQQGEwJVUzETMBEGA1UECAwKQ2FsaWZvcm5pYTEWMBQGA1UEBwwN
TW91bnRhaW4gVmlldzETMBEGA1UECgwKR29vZ2xlIEluYzEXMBUGA1UEAwwOc210
cC5nbWFpbC5jb20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCu4vOr
LgyNsHicxBORgO2OOfXKxEKb830NzNu6elubbf1T45GilB3fHgDQJELRydTRZilo
Efv75Ag7uRQM/M1tk+1h18wDpJZem+zFmJcs30ccBN21CnCvqsIEYJMyY3kcV4vD
x44bx6VvEAmJ9/kiFJ7xRUlCchu5YVOFoVkMaEax3UWb5Fti9pe8VgYdasuk53ae
8ZuIr4pFew9fraxOe/6LXEaPMSw622KSWpyK/GUbaAp07hV11c+LVgjlUDTgA+2k
nDigWrdb+yLL9Hv3WNLWjEAHFWhEce5QwV3SN8JLga3Rbw2N3lq9afkQtOnkJgdM
UG4xkUHGqscggMDJAgMBAAGjggFBMIIBPTAdBgNVHSUEFjAUBggrBgEFBQcDAQYI
KwYBBQUHAwIwGQYDVR0RBBIwEIIOc210cC5nbWFpbC5jb20waAYIKwYBBQUHAQEE
XDBaMCsGCCsGAQUFBzAChh9odHRwOi8vcGtpLmdvb2dsZS5jb20vR0lBRzIuY3J0
MCsGCCsGAQUFBzABhh9odHRwOi8vY2xpZW50czEuZ29vZ2xlLmNvbS9vY3NwMB0G
A1UdDgQWBBSanZBvY+Rnj0HquJmae9AJvwiCzTAMBgNVHRMBAf8EAjAAMB8GA1Ud
IwQYMBaAFErdBhYbvPZotXb1gba7Yhq6WoEvMBcGA1UdIAQQMA4wDAYKKwYBBAHW
eQIFATAwBgNVHR8EKTAnMCWgI6Ahhh9odHRwOi8vcGtpLmdvb2dsZS5jb20vR0lB
RzIuY3JsMA0GCSqGSIb3DQEBBQUAA4IBAQCVoGAOKZoil4sNAYvlb9uxNmWqQqyh
ql0D1bewbLxs3DSVWSe2DhPjjhdMHMTcMpB+jQzAbGxVYiuNLdqLl1Xcde7EUmo1
KJUGzTO046k+11LYVOxEXLBe5s3FF+niFJby7XFgmI3yMt4blHN5tHm/7JijL1Ip
vkcsynOnOwAEHehI1U12N0JEpkcoetM6MA8cGtn74EPTas4Npa+mTNo3seH8iY43
4L4hnsubXMhcQQ9IQMPtKuZYNUXklN/NS0f69Be+3HQRTOljtCxdpm/v/emHPjwg
/Cwu+58fZK+flQ1PQcY24Cgt7EF0R+uqo5Il3CGuCgrd4JxJNMuGcsGS
-----END CERTIFICATE-----
subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
issuer=/C=US/O=Google Inc/CN=Google Internet Authority G2
---
No client certificate CA names sent
---
SSL handshake has read 3990 bytes and written 466 bytes
---
New, TLSv1/SSLv3, Cipher is ECDHE-RSA-AES128-GCM-SHA256
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES128-GCM-SHA256
    Session-ID: 0EEC98CDED40ECEF041DEC2F6A80C2CA1C60650846FB835F34FCBC2DFB3C93CA
    Session-ID-ctx: 
    Master-Key: 5684E3D6CCFA94D5EEE4C14F8229B6A4D548083381D1718CC4934E2FBCC0E12207FCF862E5FE25D967A400FD3320FBE7
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 100800 (seconds)
    TLS session ticket:
    0000 - d7 15 b6 8e 84 c9 af 13-f0 5d 95 16 f3 99 1e b5   .........]......
    0010 - 6c 89 af 82 3e 94 20 3a-de 36 08 e8 93 7a 38 9c   l...>. :.6...z8.
    0020 - 0d 06 07 f1 26 3b da 33-3b d5 f3 89 6c e3 c3 9e   ....&;.3;...l...
    0030 - dd 03 d2 10 69 26 f8 05-b0 fd 06 67 4d f8 ae 9f   ....i&.....gM...
    0040 - f4 c5 8f a0 d6 1f 7c 2b-c2 7f 99 35 b1 3b 9b b0   ......|+...5.;..
    0050 - c5 af 07 df 9a b0 97 57-8f d2 e8 35 ee 50 6c 7b   .......W...5.Pl{
    0060 - cb 12 96 3e bd 28 5b 04-ac 8b c0 75 c0 3c 8e c4   ...>.([....u.<..
    0070 - d4 64 cb b3 f8 47 dd 2c-53 5f 78 a4 bc cb 3e 07   .d...G.,S_x...>.
    0080 - 3f e7 8d 7b 06 7b 23 f2-41 a9 2f 41 3c c9 74 f1   ?..{.{#.A./A<.t.
    0090 - b7 03 14 49 96 fa b9 0f-9b 69 fe bc 41 db 9f 9a   ...I.....i..A...
    00a0 - 4c 7f 67 d1                                       L.g.

    Start Time: 1418632937
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)
---
250 SMTPUTF8


```

You will need to find the path to your certs, which may differ to mine...

---

### Post by chiques on 2014-12-15
> **andrew.46 said:**
> Hmmmm.... this works here:

```

andrew@ilium~$ **[COLOR="#FF0000"]openssl s_client -CApath /usr/share/ca-certificates/ -starttls smtp -connect smtp.gmail.com:587 -crlf -ign_eof[/COLOR]**
CONNECTED(00000003)
depth=3 C = US, O = Equifax, OU = Equifax Secure Certificate Authority
verify return:1
depth=2 C = US, O = GeoTrust Inc., CN = GeoTrust Global CA
verify return:1
depth=1 C = US, O = Google Inc, CN = Google Internet Authority G2
verify return:1
depth=0 C = US, ST = California, L = Mountain View, O = Google Inc, CN = smtp.gmail.com
verify return:1
---
Certificate chain
 0 s:/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
   i:/C=US/O=Google Inc/CN=Google Internet Authority G2
 1 s:/C=US/O=Google Inc/CN=Google Internet Authority G2
   i:/C=US/O=GeoTrust Inc./CN=GeoTrust Global CA
 2 s:/C=US/O=GeoTrust Inc./CN=GeoTrust Global CA
   i:/C=US/O=Equifax/OU=Equifax Secure Certificate Authority
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIEdjCCA16gAwIBAgIIGcMF7jeVMoAwDQYJKoZIhvcNAQEFBQAwSTELMAkGA1UE
BhMCVVMxEzARBgNVBAoTCkdvb2dsZSBJbmMxJTAjBgNVBAMTHEdvb2dsZSBJbnRl
cm5ldCBBdXRob3JpdHkgRzIwHhcNMTQwNzE1MDg0MDM4WhcNMTUwNDA0MTUxNTU1
WjBoMQswCQYDVQQGEwJVUzETMBEGA1UECAwKQ2FsaWZvcm5pYTEWMBQGA1UEBwwN
TW91bnRhaW4gVmlldzETMBEGA1UECgwKR29vZ2xlIEluYzEXMBUGA1UEAwwOc210
cC5nbWFpbC5jb20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCu4vOr
LgyNsHicxBORgO2OOfXKxEKb830NzNu6elubbf1T45GilB3fHgDQJELRydTRZilo
Efv75Ag7uRQM/M1tk+1h18wDpJZem+zFmJcs30ccBN21CnCvqsIEYJMyY3kcV4vD
x44bx6VvEAmJ9/kiFJ7xRUlCchu5YVOFoVkMaEax3UWb5Fti9pe8VgYdasuk53ae
8ZuIr4pFew9fraxOe/6LXEaPMSw622KSWpyK/GUbaAp07hV11c+LVgjlUDTgA+2k
nDigWrdb+yLL9Hv3WNLWjEAHFWhEce5QwV3SN8JLga3Rbw2N3lq9afkQtOnkJgdM
UG4xkUHGqscggMDJAgMBAAGjggFBMIIBPTAdBgNVHSUEFjAUBggrBgEFBQcDAQYI
KwYBBQUHAwIwGQYDVR0RBBIwEIIOc210cC5nbWFpbC5jb20waAYIKwYBBQUHAQEE
XDBaMCsGCCsGAQUFBzAChh9odHRwOi8vcGtpLmdvb2dsZS5jb20vR0lBRzIuY3J0
MCsGCCsGAQUFBzABhh9odHRwOi8vY2xpZW50czEuZ29vZ2xlLmNvbS9vY3NwMB0G
A1UdDgQWBBSanZBvY+Rnj0HquJmae9AJvwiCzTAMBgNVHRMBAf8EAjAAMB8GA1Ud
IwQYMBaAFErdBhYbvPZotXb1gba7Yhq6WoEvMBcGA1UdIAQQMA4wDAYKKwYBBAHW
eQIFATAwBgNVHR8EKTAnMCWgI6Ahhh9odHRwOi8vcGtpLmdvb2dsZS5jb20vR0lB
RzIuY3JsMA0GCSqGSIb3DQEBBQUAA4IBAQCVoGAOKZoil4sNAYvlb9uxNmWqQqyh
ql0D1bewbLxs3DSVWSe2DhPjjhdMHMTcMpB+jQzAbGxVYiuNLdqLl1Xcde7EUmo1
KJUGzTO046k+11LYVOxEXLBe5s3FF+niFJby7XFgmI3yMt4blHN5tHm/7JijL1Ip
vkcsynOnOwAEHehI1U12N0JEpkcoetM6MA8cGtn74EPTas4Npa+mTNo3seH8iY43
4L4hnsubXMhcQQ9IQMPtKuZYNUXklN/NS0f69Be+3HQRTOljtCxdpm/v/emHPjwg
/Cwu+58fZK+flQ1PQcY24Cgt7EF0R+uqo5Il3CGuCgrd4JxJNMuGcsGS
-----END CERTIFICATE-----
subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
issuer=/C=US/O=Google Inc/CN=Google Internet Authority G2
---
No client certificate CA names sent
---
SSL handshake has read 3990 bytes and written 466 bytes
---
New, TLSv1/SSLv3, Cipher is ECDHE-RSA-AES128-GCM-SHA256
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES128-GCM-SHA256
    Session-ID: 0EEC98CDED40ECEF041DEC2F6A80C2CA1C60650846FB835F34FCBC2DFB3C93CA
    Session-ID-ctx: 
    Master-Key: 5684E3D6CCFA94D5EEE4C14F8229B6A4D548083381D1718CC4934E2FBCC0E12207FCF862E5FE25D967A400FD3320FBE7
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 100800 (seconds)
    TLS session ticket:
    0000 - d7 15 b6 8e 84 c9 af 13-f0 5d 95 16 f3 99 1e b5   .........]......
    0010 - 6c 89 af 82 3e 94 20 3a-de 36 08 e8 93 7a 38 9c   l...>. :.6...z8.
    0020 - 0d 06 07 f1 26 3b da 33-3b d5 f3 89 6c e3 c3 9e   ....&;.3;...l...
    0030 - dd 03 d2 10 69 26 f8 05-b0 fd 06 67 4d f8 ae 9f   ....i&.....gM...
    0040 - f4 c5 8f a0 d6 1f 7c 2b-c2 7f 99 35 b1 3b 9b b0   ......|+...5.;..
    0050 - c5 af 07 df 9a b0 97 57-8f d2 e8 35 ee 50 6c 7b   .......W...5.Pl{
    0060 - cb 12 96 3e bd 28 5b 04-ac 8b c0 75 c0 3c 8e c4   ...>.([....u.<..
    0070 - d4 64 cb b3 f8 47 dd 2c-53 5f 78 a4 bc cb 3e 07   .d...G.,S_x...>.
    0080 - 3f e7 8d 7b 06 7b 23 f2-41 a9 2f 41 3c c9 74 f1   ?..{.{#.A./A<.t.
    0090 - b7 03 14 49 96 fa b9 0f-9b 69 fe bc 41 db 9f 9a   ...I.....i..A...
    00a0 - 4c 7f 67 d1                                       L.g.

    Start Time: 1418632937
    Timeout   : 300 (sec)
    Verify return code: 0 (ok)
---
250 SMTPUTF8


```

You will need to find the path to your certs, which may differ to mine...

How do I know if my certificates are in in that path? I checked and the path exists. The command that works for you still times out with the error '110'.

```

Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-43-generic i686)

 * Documentation:  https://help.ubuntu.com/

Last login: Sun Dec 14 22:00:32 2014 from johnnyricos-acer.home
johnnyrico@falcon:~$ cd /usr/share/ca-certificates/
johnnyrico@falcon:/usr/share/ca-certificates$ ls
mozilla  spi-inc.org
johnnyrico@falcon:/usr/share/ca-certificates$ cd ~/
johnnyrico@falcon:~$ openssl s_client -CApath /usr/share/ca-certificates/ -starttls smtp -connect smtp.gmail.com:587 -crlf -ign_eof
connect: Connection timed out
connect:errno=110

```

---

### Post by kpatz on 2014-12-15
Try using port 465 instead of 587.  465 is reserved for SMTP with TLS.  587 is for normal unencrypted SMTP from a client to a server.

Ignore the stuff below if port 465 worked.

Is there a firewall in your location that could be blocking port 587?

Try using telnet (telnet smtp.gmail.com 587).  The connection starts out unencrypted until the certificates are exchanged so you'll get a ESMTP header from the server and you can type "quit" to exit.

```

kpatz@zuul ~ $ telnet smtp.gmail.com 587
Trying 74.125.22.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP k4sm10806763qaf.0 - gsmtp
quit
221 2.0.0 closing connection k4sm10806763qaf.0 - gsmtp
Connection closed by foreign host.
kpatz@zuul ~ $

```

---

### Post by chiques on 2014-12-16
Something must be up with my system. I don't get the same message you do.

```

johnnyrico@falcon:~$ telnet smtp.gmail.com 587
Trying 74.125.129.108...
Trying 74.125.129.109...
Trying 2607:f8b0:400e:c02::6c...
telnet: Unable to connect to remote host: Network is unreachable
johnnyrico@falcon:~$

```

---

### Post by andrew.46 on 2014-12-16
Certainly sounds like it, I can duplicate kpatz's effort:

```

andrew@ilium~$ telnet smtp.gmail.com 587
Trying 74.125.23.109...
Connected to smtp.gmail.com.
Escape character is '^]'.
220 mx.google.com ESMTP pb6sm10913906pbb.13 - gsmtp
quit
221 2.0.0 closing connection pb6sm10913906pbb.13 - gsmtp
Connection closed by foreign host.
andrew@ilium~$ 

```

---

### Post by chiques on 2014-12-16
I think I found the problem. Someone mentioned [here]("http://www.dslreports.com/forum/r24160885-FIOS-blocking-outbound-SMTP") that Verizon FiOS is now blocking these type of connections. I tried using the Verizon server and it worked right away.

```

johnnyrico@falcon:~$ telnet outgoing.verizon.net 25
Trying 206.46.232.12...
Connected to outgoing.verizon.net.
Escape character is '^]'.
220 vms173009pub.verizon.net -- Server ESMTP (Oracle Communications Messaging Server 7.0.5.32.0 64bit (built Jul 16 2014))
421 4.4.2 Timeout while waiting for command.
Connection closed by foreign host.
johnnyrico@falcon:~$

```


Suuuucks! Oh well. At least I can use their server....I think.

Thanks for the help guys!

---

### Post by Bucky Ball on 2014-12-16
Could you please mark the thread as solved, if your happy your original issue is, to help others? This won't close the thread so conversation can continue. Thanks. ;)

---

### Post by chiques on 2014-12-16
> **Bucky Ball said:**
> Could you please mark the thread as solved, if your happy your original issue is, to help others? This won't close the thread so conversation can continue. Thanks. ;)

Already did. Thanks for the heads up though.

---

### Post by Bucky Ball on 2014-12-16
Ah, you must have been doing that when I posted as wasn't there then, there now. Good luck. ;)

---

