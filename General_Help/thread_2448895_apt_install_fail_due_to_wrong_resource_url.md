---
title: "apt install fail due to wrong resource url"
date: 2020-08-15
forum: General Help
---

### Post by wlsdx on 2020-08-15
Hello, I was using apt to install aria2. The terminal showed the error: 
[HTML]Wrong :1 http://archive.ubuntu.com/ubuntu disco/universe amd64 aria2 amd64 1.34.0-3 404 Not Found [IP: 91.189.88.142 80]
E: Cannot Download http://archive.ubuntu.com/ubuntu/pool/universe/a/aria2/aria2_1.34.0-3_amd64.deb 404 Not Found [IP: 91.189.88.142 80][/HTML]

I tried using a browser to connect that url. The browser could access [http://archive.ubuntu.com](http://archive.ubuntu.com). But there was no such file 'aria2_1.34.0-3_amd64.deb' as in the error message. The closet one was 'aria2_1.34.0-4_amd64.deb'.

Is it an error of apt that gave a wrong resource url?
If I want to install it manually, what do I need to do other than to download deb file and to run dkpg -i <deb>?

The OS version was lubuntu 19.04. Thanks for any help.

---

### Post by Bashing-om on 2020-08-16
wlsdx; Ouch -

I be that harbinger of ill news:
> 
Ubuntu 19.04 (Disco Dingo) was the 30th release of Ubuntu, support ended January 2020. see !eol and 
               [https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-January/005263.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2020-January/005263.html)


the repository no longer exists.
You are strongly urged to upgrade to a current release.
```

sysop@2004x-c:~$ apt list aria2
Listing... Done
aria2/focal,focal 1.35.0-1build1 amd64
sysop@2004x-c:~$

```

[INDENT][INDENT]all good things must end
[/INDENT][/INDENT]

---

### Post by wlsdx on 2020-08-16
Thanks very much!

---

### Post by ActionParsnip on 2020-08-16
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

It's like looking for Windows updates for Windows 2000. They don't exist.

---

