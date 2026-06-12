---
title: "[SOLVED] Dual-Boot setup using dmraid/fakeRAID - Having grub problems"
date: 2007-08-21
forum: General Help
---

### Post by pjman on 2007-08-21
I have two 500 GB SATA drives setup as a mirror using the on-board nvraid. Windows (need it for video editing...) is installed on the first partition, 15 GB. The second partition is for my video, 405 GB. The rest, 80 GB, is for Ubuntu. I've tried following [_this guide_]("http://ubuntuforums.org/showthread.php?t=464758") but I ran into a problem while configuring grub.

I'm not sure if this is the best (or only) route to go. If I should be taking a different approach please let me know :)

Here are commands and outputs after chrooting to /target:

Ubuntu is installed on "nvidia_aieebdef3"
```
root@ubuntu:/# dmraid -ay
RAID set "nvidia_aieebdef" already active
RAID set "nvidia_aieebdef1" already active
RAID set "nvidia_aieebdef2" already active
RAID set "nvidia_aieebdef3" already active
RAID set "nvidia_aieebdef4" already active
```

```
grub> device (hd0) /dev/mapper/nvidia_aieebdef  

grub> root (hd0,2)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub>
```

What would cause grub to give me this error?

Thanks!

---

### Post by fjgaude on 2007-08-22
I've never booted from a raid array but I went and read the link you followed. Did you follow Steps 5, 6 and 7 exactly?

Seems like there is lots of little things to do any of which can cause a problem if not done correctly.

Did you try changing (hd0,2) to another partion, say hd0,1 or 3 ? Will the system boot into Windows anymore?

Many others have this raid1 setup working, booting from it. I think making mistakes are the issues. Have you tried to start all over again?

frank

---

### Post by pjman on 2007-08-22
> Did you follow Steps 5, 6 and 7 exactly?

I'm only getting to step six as "setup (hd0)" causes the error "Error 17: Cannot mount selected partition" within the Grub config tool.

> Did you try changing (hd0,2) to another partion, say hd0,1 or 3 ?

I get the same error with setting root to both (hd0,1) & (hd0,3)...

> Will the system boot into Windows anymore?

Windows still boots fine.

> Many others have this raid1 setup working, booting from it. I think making mistakes are the issues. Have you tried to start all over again?

I agree. With so many intricate steps I can see how something can easily be missed. I'm 95% sure I'm entering everything correctly. I've tried multiple times and I get the same error. 

I've read posts saying the fakeraid support is worse in Feisty than in Edgy yet I don't see any explanation as to why. Does anyone know if this is true and if so what are the differences?

---

### Post by pjman on 2007-08-22
Is there a way to have grub display errors with more detail (verbose..)?

---

### Post by pjman on 2007-08-26
I figured it out :popcorn:

The partition you are trying to modify with grub needs to have the boot flag set either using fdisk or gparted :oops:

---

### Post by fjgaude on 2007-08-26
Great, now you can make the post [SOLVED], using "Thread Tools" Menu at the top of post, so others will see that you did it.

frank

---

### Post by pjman on 2007-08-26
> **fjgaude said:**
> Great, now you can make the post [SOLVED], using "Thread Tools" Menu at the top of post, so others will see that you did it.

frank

Cool - didn't know you could do that :-) thx

---

