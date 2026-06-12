---
title: "MD5 sum is incorrect"
date: 2007-01-22
forum: General Help
---

### Post by jones172 on 2007-01-22
Under Edgy Eft 6.10, I computed an MD5 checksum on the downloaded file, or tried to. It came out:

b950a4d7cf3151e5f213843e2ad77fe3

Then there was an error message:

MD5 sums don't match.

I presume there was an MD5 sum in the downloaded file. Is there  an easy way to find out what the MD5 sum SHOULD have been? The file may have been corrupted during download.

The file is given as ubuntu-6.10-desktop-i386.iso

I have a 32 bit Dell Dimension 2400 desktop with an Intel Celeron CPU. I burned the CD-ROM, but it wouldn't boot up.

Tom Jones

---

### Post by taurus on 2007-01-22
```

283158c7da8c0ada74502794fa8745eb  ubuntu-6.10-alternate-amd64.iso
549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso
5717dd795bfd74edc2e9e81d37394349  ubuntu-6.10-alternate-powerpc.iso
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso
2f44a48a9f5b4f1dff36b63fc2115f40  ubuntu-6.10-server-amd64.iso
cd6c09ff8f9c72a19d0c3dced4b31b3a  ubuntu-6.10-server-i386.iso
6f165f915c356264ecf56232c2abb7b5  ubuntu-6.10-server-powerpc.iso
4971edddbfc667e0effbc0f6b4f7e7e0  ubuntu-6.10-server-sparc.iso

```

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by jones172 on 2007-01-23
Note added: Apparently the MD5 sum was correct (incorrect error message).

---

