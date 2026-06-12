---
title: "openconnect is not working on 13.04"
date: 2013-08-18
forum: General Help
---

### Post by Rishikesh_Darandale on 2013-08-18
Hi all,
Need your help to sort out the issue related to getting connect to vpn on ubuntu 13.04. I am trying to connect to vpn using below command and getting erros has shown at the end.

~$ sudo openconnect -v myofficevpn.com --certificate=~/my.crt.pem --sslkey=~/my.key.pem
Attempting to connect to myofficevpn.com:443
Using certificate file /home/user/my.crt.pem
Using private key file /home/user/my.key.pem
Using client certificate 'MY'
SSL negotiation with myofficevpn.com
Server certificate verify failed: signer not found

Certificate from VPN server "myofficevpn.com" failed verification.
Reason: signer not found
Enter 'yes' to accept, 'no' to abort; anything else to view: yes
Connected to HTTPS on myofficevpn.com
GET [https://myofficevpn.com/](https://myofficevpn.com/)
Got HTTP response: HTTP/1.0 302 Object Moved
Content-Type: text/html; charset=UTF-8
Content-Length: 0
Cache-Control: no-cache
Pragma: no-cache
Connection: Close
Date: Sun, 18 Aug 2013 15:47:09 GMT
Location: /+webvpn+/index.html
Set-Cookie: tg=; expires=Thu, 01 Jan 1970 22:00:00 GMT; path=/; secure
HTTP body length:  (0)
SSL negotiation with myofficevpn.com
Server certificate verify failed: signer not found
Connected to HTTPS on myofficevpn.com
GET [https://myofficevpn.com/+webvpn+/index.html](https://myofficevpn.com/+webvpn+/index.html)
Got HTTP response: HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml
Cache-Control: max-age=0
Set-Cookie: webvpn=; expires=Thu, 01 Jan 1970 22:00:00 GMT; path=/; secure
Set-Cookie: webvpnc=; expires=Thu, 01 Jan 1970 22:00:00 GMT; path=/; secure
Set-Cookie: webvpnlogin=1; secure
X-Transcend-Version: 1
HTTP body chunked (-2)
Fixed options give 
Please enter your username and password.
Certificate Validation Failure
Failed to obtain WebVPN cookie

Can somebody help me on this issue?

Another thing, if i tried to see the VPN index page on Firefox using my certificate, it works fine and doesn't show the client certificate error.

I am using openconnect 4.07 version.

Thanks

---

