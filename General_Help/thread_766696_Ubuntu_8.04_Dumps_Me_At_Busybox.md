---
title: "Ubuntu 8.04 Dumps Me At Busybox"
date: 2008-04-25
forum: General Help
---

### Post by avkhatri on 2008-04-25
I upgraded Ubuntu via the Update manager and when it was done I rebooted and there were two kernels there was "2.6.24-16" and "2.6.24-14". I'm not 100% sure if it was 2.6.24-14 but basically it was the 7.10 kernel. I chose the "2.6.24-16" kernel and the orange bar would play ping pong as though there is a live cd in there and then I would get dumped to some screen that says busy box. I didn't know what it was, I rebooted and tried the 7.10 kernel and that worked fine, however in the 7.10 kernel Ubuntu was running really slow. So I decided to install 8.04 from a disk to see if that solves any problems and when I did that I am left with kernel "2.6.24-16" and I just get dumped at busy box. Any help would be great :(

When I get to busybox it shows

initramfs _ 

the underscore being the place where you can type commands

---

### Post by k.pekka on 2008-04-27
I have the same problem. But in my case the 22-14 kernel works but i can't configure my nVidia-card to work correctly. Can't set resolutions or anything.

This is driving me crazy. Can't find help anywhere.

---

### Post by howlingmadhowie on 2008-04-27
is there some error message about mounting not working? can you paste the last few lines before the busybox prompt?

---

### Post by Sef on 2008-04-27
What are your system specs?

---

### Post by Zenkai on 2008-04-28
I'm having the same problem, tried a recovery mode on the 2.6.24-16 kernel and the system hangs at 

```
52.446753 ata1: port is slow to respond, please be patient (Status 0xd0)

57.260076 ata1: SRST failed (error=16)
```

I posted my lshw in another thread - [http://ubuntuforums.org/showpost.php?p=4818199&postcount=7](http://ubuntuforums.org/showpost.php?p=4818199&postcount=7)

Cheers
Zenk

---

### Post by avkhatri on 2008-05-12
I heard from someone that this problem could be an issue with my ATI Video card, could that be a reason for why I'm dumped to the busy box shell?

ugh 8.04 should not be an LTS, quite a few people I know have this issue. Plus this never happened with 7.10

---

### Post by avkhatri on 2008-05-29
bump


I forgot to add that after the download of 8.04 via the update manager had failed, I tried an 8.04 disk and it had booted and worked fine. After I installed from the disk it gave me the same busybox dump when trying to boot from the hard drive. So I tried the Ubuntu 8.04 disk again and NOW the disk wont boot either and I am sent straight to busybox. I can't even install or use the live CD now! I don't get it how does the live disk start giving me the same problem after I install? I rolled back to 7.10 and I still cannot get the 8.04 disk to boot. Is there any new information about this problem and how to fix it? I would really like to use 8.04. Also, is it possible to install 8.04 so that it uses the kernel from 7.10?

---

