---
title: "wget segfaults in 16.04 - libc.so.6 to blame?"
date: 2016-05-20
forum: General Help
---

### Post by elagabalus2 on 2016-05-20
While I was trying to deal with [this bug]("https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712") from yesterday I found that wget had stopped working on two of my 64-bit MATE 16.04 machines, giving a SIGSEGV error in both cases.

Using wget with gdb to try to download an image from the Internet yields the following on both machines, the only difference being the exact memory address:

```

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff6bfa328 in ?? ()
   from /lib/x86_64-linux-gnu/libc.so.6

```

On both of the machines I had tried switching the software download server yesterday when the appstream bug was going on, although I don't know if that's relevant at all. Maybe it's also worth noting that a virtual machine with the same 16.04 MATE installed as the two machines doesn't have this problem with wget; however the VM doesn't seem to have been affected by the bug from yesterday either.

Might anyone have suggestions on where to go from here to fix wget? I don't often download files from command line but I would like to fix this if it turns out to be a serious problem.

Thanks a lot for any and all help!

---

### Post by elagabalus2 on 2016-05-21
I have now tried wget on a third machine and it works fine- a desktop, unlike the original two which are laptops. Two days ago the desktop was also experiencing the same appstream bug as the two laptops, but unlike those cases I did not apply the [manual fix]("https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712/comments/24") mentioned in the Launchpad thread. Overall it seems like nothing out of the ordinary is going on with the desktop for now.

Frustratingly wget still segfaults on the laptops, though.

I'm really puzzled by this. Is there anything I can do to fix this on the laptops? I'm tempted to just reinstall 16.04 rather than deal with the fallout of having wget cease to function...

Edit: I've added an image of a portion of the crash report that runs when I try to run wget on one of the laptops.
[IMG]http://i.imgur.com/Ppgi5YB.png[/IMG]

---

### Post by mc4man on 2016-05-21
try running wget with a -d option (debug), maybe it'll produce something useful as nothing you've posted yet is.

---

### Post by elagabalus2 on 2016-05-21
> **mc4man said:**
> try running wget with a -d option (debug), maybe it'll produce something useful as nothing you've posted yet is.

I thought as much, unfortunately. I'm the first to admit that I'm sort of out of my depth here.

I reinstalled 16.04 on one of the laptops but regrettably the segfault is still happening. Running wget -d on the Google logo for today gives the following:
```

x@y:~/z$ wget -d https://images.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png
DEBUG output created by Wget 1.17.1 on linux-gnu.

Reading HSTS entries from /home/x/.wget-hsts
URI encoding = &#8216;UTF-8&#8217;
--2016-05-21 15:30:19--  https://images.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png
Resolving images.google.com (images.google.com)... 172.217.4.206, 2607:f8b0:4006:80c::200e
Caching images.google.com => 172.217.4.206 2607:f8b0:4006:80c::200e
Connecting to images.google.com (images.google.com)|172.217.4.206|:443... connected.
Created socket 3.
Releasing 0x0000562f0aa3fec0 (new refcount 1).
Initiating SSL handshake.
Handshake successful; connected socket 3 to SSL handle 0x0000562f0aa41380
certificate:
  subject: CN=*.google.com,O=Google Inc,L=Mountain View,ST=California,C=US
  issuer:  CN=Google Internet Authority G2,O=Google Inc,C=US
X509 certificate successfully verified and matches host images.google.com

---request begin---
GET /images/branding/googlelogo/1x/googlelogo_color_272x92dp.png HTTP/1.1
User-Agent: Wget/1.17.1 (linux-gnu)
Accept: */*
Accept-Encoding: identity
Host: images.google.com
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... 
---response begin---
HTTP/1.1 200 OK
Content-Type: image/png
Date: Sat, 21 May 2016 19:30:19 GMT
Expires: Sat, 21 May 2016 19:30:19 GMT
Cache-Control: private, max-age=31536000
Last-Modified: Fri, 04 Sep 2015 22:33:08 GMT
X-Content-Type-Options: nosniff
Server: sffe
Content-Length: 5969
X-XSS-Protection: 1; mode=block
Alternate-Protocol: 443:quic
Alt-Svc: quic=":443"; ma=2592000; v="34,33,32,31,30,29,28,27,26,25"

---response end---
200 OK
Registered socket 3 for persistent reuse.
Length: 5969 (5.8K) [image/png]
Saving to: &#8216;googlelogo_color_272x92dp.png.1&#8217;

Segmentation fault (core dumped)

```

---

