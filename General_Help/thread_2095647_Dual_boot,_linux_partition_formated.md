---
title: "Dual boot, linux partition formated"
date: 2012-12-17
forum: General Help
---

### Post by haakoan on 2012-12-17
Hi guys, so my roommate was trying to formate an external storage device when he managed to formate the partition that Ubuntu was installed on. Do not ask me how.

So now when I turn the PC on it goes right in to grub rescue>.
From here I am not able to do much, well I don't know what to do, used the ls command to find that every partition was a "unknown formate".

If I put a CD in the drive, tried with grub fix cd, ubuntu cd,win8 and a bootloader fix cd, nothing happens. It just boots in to the rescue menu.

So what can I do? I would say I have an OK understanding of computers in general and of linux, but this I don't know how to fix. Was thinking that I might be able to put the hardrive in to my own PC and somehow fix it that way, but it don't seem like the best way to do it.

It is an ASUS K55V laptop by the way. Came with Win8 and all the trouble that secure boot is.

Any help will be very much appreciated. Googled and tried most of the solutions i found, nothing worked.

---

### Post by sudodus on 2012-12-17
Tough luck :-(

Anyway, welcome to the Ubuntu Forums :-)

I think we can help by asking questions, asking you to give us some information and then suggest what to do.

At first: Was there a fairly recent backup of the
- personal files (documents, pictures ...)
- the Ubuntu system?

What is your primary goal:
- to recover personal files?
- to recover the Ubuntu system with all tweaking?

---

### Post by Debasish Mukherjee on 2012-12-17
I am agree with sudodus
what is your primary goal???
then the proceeding will be according to that..;)

---

### Post by haakoan on 2012-12-17
Hi mates, thanks for the good welcome.

My goal as it stands would be, if possible, to keep the Win8 intact and reinstall kubuntu/ubuntu. I have the kubuntu CD on hand. If Windows has to go we can live with that as well.

No personal files or anything like this, PC is around two weeks old and if he has some files he will just have to accept the loss.

Now as far as I understand things it would be every hard, if not impossible, to recover the system as it was. He did after all formate the ubuntu part of the drive. He did this from Windows by the way.

Ok, goal. Keep Win8 if possible and reinstall Kubuntu. As of now it is essentially a paperweight because the grub recover menu is nice to look at, but limited in its use.

As for backup, nothing at all.

---

### Post by sudodus on 2012-12-17
If you were happy with [K]ubuntu as it was before formating, you can just reinstall into the same partition.

But to play safely, backup your Windows partition before installing (to an external drive or at least make a recovery disk unless you have one already). Editing partitions and installing an OS is risky ...

***Boot from the install CD,*** and start installing. At the page about partitions, select 'something else' which lets you select the previous partition (reuse as /, and reformat it).

If you want to change the partitioning, this is a good time to do it.

You can also reformat from a live session (before starting to install). Then use the GUI tool*** gparted***, if available directly, otherwise you can install it temporarily into the live session with
```
sudo apt-get install gparted
```and then it is there to use.

And when you (or he) is happy, make a backup to an external drive.

---

### Post by haakoan on 2012-12-17
The issue is that when I turn on the computer i get pushed in to the grub recovery thing. It will not boot anything else. It will not boot from a live CD, it just goes in to grub no matter what i put in to it.

Sorry guys, i noobed a bit. As it turns out I just had to push real fast on the del key and i got in to the bios. It boots so damn fast so I was to slow the other times i tried. Fixing it now.

---

### Post by oldfred on 2012-12-17
If you want a gui to help fix, or detailed analysis of you system:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

 Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

