---
title: "Ubuntu Server GPG error NODATA1 NODATA2"
date: 2013-04-30
forum: General Help
---

### Post by Xuvatilavv on 2013-04-30
Any time I try to run apt-get update it stops at:
```
Get:1 http://us.archive.ubuntu.com quantal Release.gpg
Get:2 http://security.ubuntu.com quantal-security Release.gpg
Get:3 http://us.archive.ubuntu.com quantal-updates Release.gpg
Get:4 http://us.archive.ubuntu.com quantal-backports Release.gpg
Get:5 http://security.ubuntu.com quantal-security Release
Ign http://security.ubuntu.com quantal-security Release
E: GPG error: http://security.ubuntu.com quantal-security Release: The following signatures were invalid: NODATA 1 NODATA 2

```


My problem started with plain errors for about half of the archives, but after trying many suggestions I've found from various Google results I am getting that error instead. No solutions I've tried after that have had any affect.

I definitely have internet connection. The machine is connected via ethernet cable directly to the gateway, I can ssh to it internally, and a friend can ssh externally. I can wget files just fine.

Running apt-get install for any package I get "E: Unable to locate package xxxxx"

This seems to have spontaneously begun while I was working in a Debian VM setting up sshd. Probably unrelated but beginning at the same time, I am also now unable to ping any outside IP (or hostname and the IP will show up correctly). I can ping internal IPs with no issue.

---

### Post by Xuvatilavv on 2013-04-30
Fixed it myself.

 It turns out my router firewall's ill-documented settings led me to (supposedly) block all outgoing port 80 connections and ICMP requests, though no other computers were affected but the server.

Thanks guys.

---

