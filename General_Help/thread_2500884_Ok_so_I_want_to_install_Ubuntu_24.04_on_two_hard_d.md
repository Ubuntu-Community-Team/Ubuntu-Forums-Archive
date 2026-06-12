---
title: "Ok so I want to install Ubuntu 24.04 on two hard drives basically"
date: 2024-09-14
forum: General Help
---

### Post by SpaceManJack on 2024-09-14
[COLOR=#32363A][FONT=-apple-system]So I'm gonna buy a sata 1TB SSD and this will have the OS and home folder and I just want to use an HDD as storage for when I run out of space on the SSD. By the way I won't have any problems transferring files between the two hard drives right, it's just I read somewhere that you can't do that, I mean I can transfer files between the two hard drives as many times as I want right?

[/FONT][/COLOR][COLOR=#32363A][FONT=-apple-system]So here's a tutorial from 2021 [https://healeyj.github.io/2021/02/25/encrypt-ubuntu.html](https://healeyj.github.io/2021/02/25/encrypt-ubuntu.html) that shows you how to do this on Ubuntu 20.04 but my question is, will it still work for Ubuntu 24.04? [/FONT][/COLOR][COLOR=#333D42][FONT=-apple-system]Is it safe, can it be trusted?[/FONT][/COLOR][COLOR=#32363A][FONT=-apple-system] I'm here for second opinions.[/FONT][/COLOR][COLOR=#32363A][FONT=-apple-system]

Also, while researching how to do this I've noticed many people saying they want to transfer the home folder to the HDD but why? I use virtualbox and the virtual machines VMs are stored in the home folder and I'm hoping that by getting an SSD I can improve the speed of whonix (which is a VM). I mean I just simply want the HDD for when I run out of room on the SSD, and then I'll just move files such and music, videos, and pics over to the HDD to make up space on the SSD. I just want to use the HDD as a storage.

[/FONT][/COLOR][COLOR=#32363A][FONT=-apple-system]I'm assuming that by keeping the OS and home folder on the SSD I'll greatly speed things up. Whonix is running slow on my HDD and I think it's cause of the HDD. Whonix which is a VM, is stored in the home folder. Virtualbox stores VMs in the home folder. [/FONT][/COLOR][COLOR=#32363A][FONT=-apple-system]When I simply run out of space on the 1TB SSD I'll just transfer files over to the HDD to make more room on the SSD. [/FONT][/COLOR][COLOR=#32363A][FONT=-apple-system]And I want full disk encryption on both hard drives. And I want both drives to decrypt on startup.

So yeah any tips and pointers before I try and go do this would be great.
[/FONT][/COLOR]

---

### Post by oldfred on 2024-09-15
I do not use VM nor encryption, but to get you started review posts by TheFu and a few others.

A google search like this will give you many threads. 
site:ubuntuforums.org "lvm" "encryption"

LVM &  LUKS2 install 
[https://ubuntuforums.org/showthread.php?t=2461714](https://ubuntuforums.org/showthread.php?t=2461714)
LVM as graphical organization, TheFu
[https://ubuntuforums.org/showthread.php?t=2485286](https://ubuntuforums.org/showthread.php?t=2485286) 
[https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144)

---

### Post by SpaceManJack on 2024-09-17
[COLOR=#32363A][FONT=-apple-system]So yeah any tips and pointers before I try and go do this would be great.[/FONT][/COLOR]

---

### Post by dragonfly41 on 2024-09-17
I dipped into your tutorial but gave up because it is too tiring on my eyes. I can inform you what I do but I do not claim that this is the best way.  I invested in purchasing a Startech dual docking bay, plus caddies for SSD. Old harddrives just plugin without caddies. This gives me the flexibility I want. I plug the exernal docking bay into my tower PC (holding windows and in fact a Ubuntu dual boot installation). But USB 3.0 port is essential.

---

### Post by SpaceManJack on 2024-10-02
So is there anyone here who can help me? I want to install Ubuntu 24.04 on a sata 1TB SSD and then use a 2TB HDD as the storage drive and I want full disk encryption on both of them. I want the storage drive to mount automatically as soon as I log in.

You see that tutorial up above, is that going to work for me? Can I get any tips and pointers on how to do this?

---

### Post by 1fallen on 2024-10-02
> **SpaceManJack said:**
> 
You see that tutorial up above, is that going to work for me? Can I get any tips and pointers on how to do this?

It should still work on 24.04 as well. However if your not sure you can follow that link, then I would wait until you feel you can. (it seems pretty straight forward)

And Your positive you want to use the whole 1TB Drive for your install? {Just for confirmation}

---

