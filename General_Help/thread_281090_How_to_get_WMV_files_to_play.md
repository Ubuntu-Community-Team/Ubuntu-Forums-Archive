---
title: "How to get WMV files to play"
date: 2006-10-20
forum: General Help
---

### Post by jbu311 on 2006-10-20
Hi all,
I can't get WMV files to play in any of my players.  I THINK i have installed the codecs properly, as I have followed the instructions in the ubuntu faq pages ([http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)).  I'll open up a file and it'll play the sound of the video but not the video itself.  Does anyone know if these instructions are universal?  Maybe it's a graphics card problem?  I'm using ubuntu 64, with a nvidia geforce 6200 card.  Please help me out.

Thanks in advance,
jbu

---

### Post by TheRingmaster on 2006-10-20
make sure you have the "w32codecs" installed. Check this by going to synaptic package manager.

---

### Post by jbu311 on 2006-10-20
Well I have an AMD64 processor and I'm on ubuntu's 64 bit version.  Would it matter if I have the w32codecs?  Also, I went to the synaptic package manager and searched for w32codecs and it didnt produce matching results.  I am sure I've added all the repositories because I followed the ubuntu faq directions ([http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)).  I don't know what's wrong.  Thanks for your quick reply.

jbu

---

### Post by Ufo on 2006-10-21
For me WMV files play without sound in Totem and VLC, but ok with sound and picture in GXine. I'm not using 64 bit version though.

I found some threads about AMD64 and wmv which might be helpful:
[http://ubuntuforums.org/showthread.php?t=188974](http://ubuntuforums.org/showthread.php?t=188974)
[http://ubuntuforums.org/showthread.php?t=140565](http://ubuntuforums.org/showthread.php?t=140565)

Then there was this article about 64bit Kubuntu:
[http://polishlinux.org/linux/ubuntu/kubuntu-606-on-athlon-64/](http://polishlinux.org/linux/ubuntu/kubuntu-606-on-athlon-64/)

Maybe some of these will be helpful...

---

### Post by elettronicha on 2006-10-21
> **jbu311 said:**
> Well I have an AMD64 processor and I'm on ubuntu's 64 bit version.  Would it matter if I have the w32codecs?
I think those codecs are unusable on your processor since they are compiled for 32-bit CPU. I haven't a 64-bit machine so I'm not able to help, try to read that Ufo's links.

> Also, I went to the synaptic package manager and searched for w32codecs and it didn't produce matching results.
There is no w32codecs package in the Ubuntu official repos, since they contain restricted formats, so if you didn't add any unofficial repo it's normal you can't see w32codecs.

---

### Post by ser1alsn1per on 2006-10-22
try downloading automatix it might have them in there + u can download the players to

---

