---
title: "Recovering Encrypted Files After a Failed Update"
date: 2017-04-06
forum: General Help
---

### Post by abilyk on 2017-04-06
Hi All,

First off, let me start by saying this problem is entirely of my own creation, and is a good example why whiskey and computers don't actually mix. I've learned my lesson about backing up files before attempting an upgrade. Also, I'm a bit of a Linux amateur, so please use small words and speak slowly.

A little while ago, I attempted to ubgrade my Ubuntu dual-boot from 14 to 16. I was living overseas on a temporary work posting, and didn't have an external drive sufficient to back up my files. Eventually, the boredom got to me, and I attempted the upgrade. At that point, Murphy's law kicked in and the upgrade failed. Luckily, my Windows install survived, so I still had a operable laptop. Somehow, in my blind stumbling around trying to fix the problem, my Ubuntu ext4 partition reformatted as Linux Native, and was no longer recognized by either windows (via an ext4 viewer), or by a live version of Ubuntu.

At this point, I started to freak out a bit. After a bit more research, I managed to recover most of the drive using testdisk but, as my home partition was encrypted, they are all encrypt.fs files. I also managed to recover the passphrase files.

My question is, is there any way to decrypt these files? I'd like to know if this is a lost cause or not, before I just give up on the data and start from scratch.

Many thanks in advance for helping out this clueless newb.

Andrew

---

### Post by sevendogs on 2017-04-09
Andrew - sorry to hear but we've all done something like this. At least you can blame the whiskey :rolleyes: Since you pulled files off using a forensics tool (testdisk), I am not sure you can decrypt the files you have. I was thinking about a VM install of Ubuntu them encrypting the /home directory, but that doesn't help with the encrypted files you have because what do you do with them? If you copy them onto the encrypted /home, they will remain unchanged. Not sure there is a way out of this. There are some articles on disk encryption for Ubuntu but I read through them quickly and didn't see anything about your specific situation.

In the interim, I would strongly suggest an external backup disk for your data. If you are worried about privacy, you can encrypt files or passwords using a multitude of tools out there without having to encrypt your whole home directory.

---

### Post by abilyk on 2017-04-13
Thank you for the response, I kind of figured that was the way it would go. I suppose there's no other way to recover the old Ubuntu install either. If there isn't, I'll just go ahead and work on a clean re-install.

Cheers,

Andrew

---

