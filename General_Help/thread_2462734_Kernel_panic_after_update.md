---
title: "Kernel panic after update"
date: 2021-05-26
forum: General Help
---

### Post by giobaxx on 2021-05-26
Helllo to everyone i need your help to understand a strange (at least for me) i'm facing. 

I need to install a system with the old kernel (4.15.xx) and set up software RAID1 for the* /Home *partition. Due to the requirement i have used the Ubuntu Server 18.04.4 ISO and i have installed the system in UEFI mode, without any problems.

The first step was running an *apt update && apt upgrade* which has updated also the kernel. After this kernel update the system didn't reboot because was unable to find the root partition which was in an SSD (out of the RAID).

From what i have understood during the upgrade of the system, grub was not correctly updated:
 
[LIST]
[*]editing  the grub manually and comparing it with the parameter of the old kernel the line *linux * was refering to the root partition with the name *sda( *i dont remember exactely the exact line*)* instead of using the UUID, and was completley missing the line initrd */boot/initrd.img-4.15.0-xxx *and I suppose this made the system unbootable.
[/LIST]

I have edited the grub making the boot possible and the running and then running command [COLOR=#111111][FONT=courier]update-grub   [/FONT][/COLOR]seems to have solved the problem but in reality not quite.   Just for test, i have manually updated the the kernel to the latest vesrion with a*pt install --install-reccomends linux-generic-hwe-18.04 *but also in this case i had to manually run  the command update-grub. Without this  the kernel 5.4.xxx  was not visible in the grub menu.

Has such a thing ever happened to you? What is the problem the ubuntu server ISO or what?


I googled a bit and it is not totally clear fior could you tell me if there is a best practice on removing a specific kernel from a system?    I used:* apt purge linux-herder-4.15.0-143* and  the *apt purge linux-generic-4.15.0-143  *but it didn't worked so well.


Thanks for any help A.

---

### Post by guiverc on 2021-05-26
Earlier form of question exists at [https://askubuntu.com/questions/1340788/kernel-panic-after-apr-upgrade](https://askubuntu.com/questions/1340788/kernel-panic-after-apr-upgrade)

---

### Post by giobaxx on 2021-05-27
sorry i didnt know the two forum where connected...sorry again

---

### Post by coffeecat on 2021-05-27
> **giobaxx said:**
> sorry i didnt know the two forum where connected...sorry again

They are not, and no apologies necessary. Or at least the two sites are administered separately, but both are official sources of support for Ubuntu. Some people prefer the traditional forum format found here, and some prefer Stack Exchange sites. I can only speak for ubuntuforums, but we're happy here for the same question to be asked on both sites. guiverc posted the link so that those helping here can see what has been said on AskUbuntu.

Good luck with finding answers to your questions.

---

### Post by giobaxx on 2021-05-27
thanks a lot! i hope to find an help because, even because what was happend....just an running an update/upgrade if the kernel is involved we break the system.

Now if i boot from the new kernel the system isn't  unable to find the raid1 partition, if i boot from the previous kernel work perfectly.....

:-(

---

