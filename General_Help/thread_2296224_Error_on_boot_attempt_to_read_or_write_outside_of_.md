---
title: "Error on boot: attempt to read or write outside of disk 'hd0'"
date: 2015-09-24
forum: General Help
---

### Post by Sammy_Abukmeil on 2015-09-24
Hi all,

I recently went to reboot my pc and I was faced with this error: attempt to read or write outside of disk 'hd0'

I have tried installing ubuntu on a USB stick and booting into that, then running boot repair. Here is the pastebin I got: [http://paste.ubuntu.com/12540580/](http://paste.ubuntu.com/12540580/)

When I try and reboot after running boot repair I get nothing (not even the initial error).

Haven't recently installed any software or tampered with hardware at all. Not sure what the cause is.

Any help is greatly appreciated.

Thanks.

---

### Post by Sammy_Abukmeil on 2015-09-24
I managed to fix this.

This is what I did:

- booted into a USB copy of ubuntu
- went into Gparted and selected my bootup partition
- [**not sure if this step helped**] changed the size of the partion slightly (and back) as I had a suspicion there was a discrepancy between space available and space used
- Ran a repair on the partition
- Reboot
- Win

---

