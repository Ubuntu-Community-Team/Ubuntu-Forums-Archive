---
title: "How to correct errors in the Burnt CD"
date: 2007-07-16
forum: General Help
---

### Post by sastry on 2007-07-16
HI,

I burnt the "downloaded ISO image" of Ubuntu 7.07 using Infra-recorder. I Booted using the CD, after I selected to install the version and the next screen(pink)  appeared in 10sec and it is asking for the "user name" and "Password" though I have NOT chosen any so there is no other option but to restart and quit. **_During the integrity check it showed that there is an error on one File._ **
So I tried to burn the ISO image with very low speeds several times but the same thing is happening. So if there was any error downloading it from the official Ubuntu site then _**How can I correct it without having to download a fresh copy to save a lot of time and finally a similar/new problem could arise.**_ Is it possible to find out which file is defective.

 **Can somebody please help me out ? ?**

---

### Post by confused57 on 2007-07-16
> **sastry said:**
> HI,

I burnt the "downloaded ISO image" of Ubuntu 7.07 using Infra-recorder. I Booted using the CD, after I selected to install the version and the next screen(pink)  appeared in 10sec and it is asking for the "user name" and "Password" though I have NOT chosen any so there is no other option but to restart and quit. **_During the integrity check it showed that there is an error on one File._ **
So I tried to burn the ISO image with very low speeds several times but the same thing is happening. So if there was any error downloading it from the official Ubuntu site then _**How can I correct it without having to download a fresh copy to save a lot of time and finally a similar/new problem could arise.**_ Is it possible to find out which file is defective.

 **Can somebody please help me out ? ?**
You can do a md5sum on the downloaded iso to determine if the iso is corrupted, see this guide:
[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

There should be a md5sum listed from the same site that you downloaded the iso that you can compare with the md5sum results of the iso....if it checks out OK, you shouldn't need to redownload the iso.

---

### Post by sastry on 2007-07-16
[B]Thank u,
[/B]
_I did the md5sum and they did not match_, but when I tried to install the Windows versions of the  programs available through the "flash screen setup" on the burnt CD there was no problem at all. So is there any other option than to re-download the ISO image ?  :-k

---

### Post by confused57 on 2007-07-16
> **sastry said:**
> [B]Thank u,
[/B]
_I did the md5sum and they did not match_, but when I tried to install the Windows versions of the  programs available through the "flash screen setup" on the burnt CD there was no problem at all. So is there any other option than to re-download the ISO image ?  :-k

Not that I'm aware of...if the md5sum didn't match what was listed on the download site, the only thing I could suggest is to download the iso again.   I'm not sure I know what you mean by the "flash screen setup", did you try just pressing "enter" at the login screen  when you booted the live cd.

If you will post the md5sum that you recorded from the download site and the md5sum from the downloaded iso.

---

### Post by merlinus on 2007-07-16
Re; "flash screen" --

IIRC, if you insert the live cd during a windows session, it will offer to install open-source programs such as firefox and thunderbird.

Interesting....  perhaps an ubuntu attempt to be user-friendly, even towards redmond folks.

:)

-merlin

---

### Post by confused57 on 2007-07-16
> **merlinus said:**
> Re; "flash screen" --

IIRC, if you insert the live cd during a windows session, it will offer to install open-source programs such as firefox and thunderbird.

Interesting....  perhaps an ubuntu attempt to be user-friendly, even towards redmond folks.

:)

-merlin
Thanks Merlin...learn something new every day.   I'm sure the MS people are appreciative of Ubuntu making it easier to install open-source programs in Windows.

---

### Post by sastry on 2007-07-17
If this is useful - 
The MD5Sum from the downloaded site is "**e296e3468358789904097fc8df29609a**"
that of my ISO image is "**2a360d5988a2a58dc67a21b9d9d9547e**"

**where can I get a detailed guidelines to do an installation from the ubuntu 7.04 Live CD ??  **

---

### Post by confused57 on 2007-07-17
> **sastry said:**
> If this is useful - 
The MD5Sum from the downloaded site is "**e296e3468358789904097fc8df29609a**"
that of my ISO image is "**2a360d5988a2a58dc67a21b9d9d9547e**"

**where can I get a detailed guidelines to do an installation from the ubuntu 7.04 Live CD ??  **

This is an excellent guide for installing with the Desktop cd:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

You might want to check out this sticky in the Beginner's section:
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

