---
title: "Kubuntu 6.10- Cannot Install"
date: 2006-10-27
forum: General Help
---

### Post by tumler on 2006-10-27
Hey,
I tried installing Kubuntu from the torrent iso. But it always hangs at 55% 'Copying Files' I have tried with both an internet connection present and one without.

BTW Computer Specs
-Laptop 2.7Ghz Celeron
- 256 mb Ram
- 40G HD

Anyone know anything about this?

---

### Post by badguyanil on 2006-10-27
the source CD/DVD may be corrupt! try getting another copy of the OS.

---

### Post by JAwuku on 2006-10-28
Have you checked the md5 sums for kubuntu 6.10?

If you type ```
md5sum <name of kubuntu image>.iso
```

You should see one of the following numbers from

[http://releases.ubuntu.com/kubuntu/edgy/MD5SUMS](http://releases.ubuntu.com/kubuntu/edgy/MD5SUMS)

**4f5a12059e1a7f729c396601081ba7f1**  kubuntu-6.10-alternate-amd64.iso

**23347e2e519f0f638cf0161ae65f17f8**  kubuntu-6.10-alternate-i386.iso

**e7f605ca5134dcdbcbb56e7fc0ceffee** kubuntu-6.10-alternate-powerpc.iso

**0b5b707fda9a7cda9868447df497f36d**  kubuntu-6.10-desktop-amd64.iso

**1f9baed847eff89b03c754fcaea8070e**  kubuntu-6.10-desktop-i386.iso

**f2ce77ef53e85c7bf281ee71f3ec8414**  kubuntu-6.10-desktop-powerpc.iso

If there is a dirrerent md5sum result than above, then the torrent .iso has been corrupted.

Hope that helps

---

