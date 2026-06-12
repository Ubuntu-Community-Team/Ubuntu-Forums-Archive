---
title: "Ubuntu locking 100% load only with open browser."
date: 2019-07-12
forum: General Help
---

### Post by espectro2 on 2019-07-12
Hello
I am using Ubuntu 18.04. however running command uname -a appears that I am using 18.04.1 the fact that I downloaded the iso a little and 18.04 2 is happening a few legs sometimes the machine goes to 100% load only with open browser somebody knows what can be happening hardware should i download another iso? thanks for listening.
Is it possible to know this iso that running on my machine has been corrupted causing these small crashes?

---

### Post by Impavidus on 2019-07-13
I have some difficulty parsing your question. The difference between 18.04.1 and 18.04.2 is mostly relevant for the live disk you used. After installation of Ubuntu and all upgrades they are identical (except for one small detail: 18.04.2 will automatically get you the HWE stack).

Web browsers are among the heaviest applications around. They are pretty much virtual machines running all kinds of code, mostly for ads or sometimes mining cryptocurrencies (which is far more profitable if they use someone else's electricity). What browser do you use and how heavy are the sites you visit?

I managed to reduce the heating of my room and increase browsing speed by disabling flash, installing an adblocker and a scriptblocker (although some websites don't work without those scripts, even though they rarely add anything useful).

Corrupt isos are possible and can cause crashes. You can check the iso before creating the live disk by checking the hash (happens automatically if you use the torrent download). When you boot the live disk, you can check the disk for errors.

---

### Post by TheFu on 2019-07-13
At first boot, every Ubuntu ISO installer should have an option to validate/verify the media.  Run that.

Using the checksums - md5sum, sha1sum, sha256sum on the ISO file before burning and comparing that to the sums file on the site were you got the ISO file(s).
For example:
```
$ sha256sum ubuntu-16.04.6-server-amd64.iso 
16afb1375372c57471ea5e29803a89a5a6bd1f6aabea2e5e34ac1ab7eb9786ac  ubuntu-16.04.6-server-amd64.iso
```
Then look inside```

$ more ubuntu-16.04.6-server-amd64.sha256 
16afb1375372c57471ea5e29803a89a5a6bd1f6aabea2e5e34ac1ab7eb9786ac  ubuntu-16.04.6-server-amd64.iso
```

See how the local sum and txt file result is identical?  That means my download was good.

---

### Post by Autodave on 2019-07-13
If checksums are good, try running uBlock as an extension and see what happens.

---

### Post by espectro2 on 2019-07-23
thanks for the attention possibly adblock would solve the problem I had not thought of this possibility the iso hit md5 sha256sum but I thought that much more fluid version 19.04 of my machine was in doubt if it would be hardware or system suddenly my source causing the crashes. sha256sum -c SHA256SUMS 2> & 1 | grep SUCCESS
ubuntu-18.04.2-desktop-amd64.iso: SUCCESS
Thanks for listening.

---

### Post by TheFu on 2019-07-23
Lockups can happen for many different reasons.  Our of RAM is a common issue if the swap file is too small.  My last 16.04.6 install only created a 1GB swap, which is 4x too small for any desktop install.

Out of RAM equals crash.  No programs handle that situation well.

---

