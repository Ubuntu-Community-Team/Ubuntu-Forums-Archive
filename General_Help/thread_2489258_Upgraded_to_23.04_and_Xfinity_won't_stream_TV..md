---
title: "Upgraded to 23.04 and Xfinity won't stream TV."
date: 2023-07-24
forum: General Help
---

### Post by rmjohnson144 on 2023-07-24
After upgrading to 23.04, I can't seem to watch Xfinity TV with Chrome.

I'm not sure if I even watched it on Ubuntu 22.04.

But Xfinity gives me this message:

Please download the latest browser version.
Before upgrading to the latest browser version, ensure you're on a supported Operating System.
Supported Operating Systems Windows 7+, iOS 11+, Android 7+ Mac OS X 10.14.4+ for Safari Mac OS X 10.7+ for Chrome and Firefox

So, does Xfinity work for Linux at all?

I tried updating through auto updater.  I also used the sudo apt install google-chrome-stable

or am I just missing something?

I have an all AMD Ryzen system. Ryzen 5800 (OEM) and RX 6800 XT

---

### Post by QIII on 2023-07-24
You might try a user agent (which attempts to tell the resource that you are using a different OS), but I'm not sure I ever got that to really work when I had Comcast as my ISP.  I couldn't play Xfinity content as I remember.

Comcast rejects Linux due to DRM concerns ... but I found that their servers were running on Linux at the time.  Go figure.

---

### Post by Autodave on 2023-07-24
I have never been able to stream Xfinity on any version of Linux.

---

### Post by #&amp;thj^% on 2023-07-24
> **QIII said:**
> 
Comcast rejects Linux due to DRM concerns ... but I found that their servers were running on Linux at the time.  Go figure.

Comcast is so afraid of Linux it's scary, so now they just buy Studios and cabled TV broadcasters and alike.
How are they still around? Worst provider I have *ever* used Hands Down. (Rant Over :D )

---

### Post by QIII on 2023-07-24
Hmnmm.  Looks like they are actively snubbing curl queries.  Can't get the server type or OS.

---

### Post by #&amp;thj^% on 2023-07-24
> **QIII said:**
> Hmnmm.  Looks like they are actively snubbing curl queries.  Can't get the server type or OS.

I rest my case...LOL
But you are right they do use a Linux based sever system.
```
; <<>> DiG 9.18.16-1-Debian <<>> https://www.xfinity.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 39104
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;https://www.xfinity.com.	IN	A

;; AUTHORITY SECTION:
xfinity.com.		900	IN	SOA	dns101.comcast.net. dnsadmin.comcast.net. 2015041283 7200 3600 604800 900

;; Query time: 59 msec
;; SERVER: 10.30.162.1#53(10.30.162.1) (UDP)
;; WHEN: Mon Jul 24 13:32:03 MDT 2023
;; MSG SIZE  rcvd: 115


```

---

### Post by rmjohnson144 on 2023-07-24
I rebooted and keep getting this weird error:

Dell_SMBIOS: Unable to run on non-Dell system

Maybe Ubuntu doesn't like Dell?  Maybe that is the case for most people too.  LOL

It seems to do well, except Xfinity tv streaming.

---

