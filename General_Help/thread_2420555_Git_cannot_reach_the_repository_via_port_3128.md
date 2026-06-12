---
title: "Git cannot reach the repository via port 3128"
date: 2019-06-06
forum: General Help
---

### Post by jtpryan on 2019-06-06
WSL, Ubuntu 18.x.x.  When I do a Git Clone it fails with:

fatal: unable to access 'https://git.forge.lmig.com/scm/uscm-devops/docker-dist-load-test.git/': Failed to connect to localhost port 3128: Connection refused

I have no idea why it wants port 3128.  The repository is on our company network in Bitbucket.

Any pointers appreciated.

Jim

---

### Post by TheFu on 2019-06-06
squid proxy server normally runs on port 3128.  squid normally proxies http traffic, not ssh+git traffic.
No clue about WSL - what's that?

---

### Post by jtpryan on 2019-06-06
Thanks.  Is there anyway to bypass/remove it?  WSL = Windows Subsystem for Linux.  Basically running Ubuntu within Windows 10.

---

### Post by TheFu on 2019-06-07
> **jtpryan said:**
> Thanks.  Is there anyway to bypass/remove it?  WSL = Windows Subsystem for Linux.  Basically running Ubuntu within Windows 10.

I don't know if you are actually using squid or not. You can use netstat to see which program is listening on that port to see.  Squid don't get installed by accident. It would be extremely odd for a desktop to have squid on it at all.  

I know nothing about Win10 or WSL. Nothing.  I've never touched or seen either.  Perhaps the proxy is how WSL handles networking for guests instead of doing it way that every other virtualization too does it?  You are the expert on Win10 and WSL here.

---

