---
title: "how do I get ubuntu off my hdd? I cant install image writer so I can replace ubunu"
date: 2016-02-12
forum: General Help
---

### Post by Leon8200 on 2016-02-12
I keep trying to find something to write my debian linux iso to my flashdrive so I can get this ubuntu garbage off my pc and go back to debian, but "image writer" wont download using apt-url,I tried  using unetbootin to burn it to my flash drive but when booting from flashdrive it say's "no operating system found" and boots ubuntu from my hdd!!!, so i have no way of writing my iso to my flashdrive to replace ubuntu, please someone help me I HATE UBUNTU AND WANT IT OFF MY PC!!!

---

### Post by Tadaen_Sylvermane on 2016-02-12
you want to go back to debian but only use gui programs?

```
man dd
```

X being the drive letter of your flash drive. don't screw this up or you wipe out your hard drive / ssd contents.

```
sudo dd if=/path/to/iso of=/dev/sdX oflag=direct bs=4M
```

No such thing as apt-url that I know of.

---

### Post by buzzingrobot on 2016-02-12
And do a "sync" after the prompts returns from dd. Or, just add it at the end with "&& sync".  dd buffers data to memory and the prompt very often returns before that buffer is written to the USB stick.  That's one sure way of getting an unbootable  USB stick. Sync ensures the buffer is flushed.

Also, checking the results of "lsblk" before using dd will ensure you get the right mount point for the USB stick.  dd will happily write data all over whatever you point it at, including the drive you boot from.

There is no "imagewriter" package in the Ubuntu repos. [Edit:  I'll correct that. There is one package for 12.04.]

---

### Post by pqwoerituytrueiwoq on 2016-02-12
i found another tool (there is a ubuntu version there)
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)
you could set it up to boot the iso file like i did
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)
that guide is a bit dated, i just skip to III step 2 and change the directly to /media/$USER/mydrive
here is my grub.cfg from my flash drive [http://pastebin.com/ew98DJNw]("http://pastebin.com/ew98DJNw")

you may want to try a different flavor of ubuntu, say xubuntu (xfce), ubuntu mate (mate), ubuntu gnome (gnome), kubuntu (kde), or lubuntu (lxde)

---

### Post by Leon8200 on 2016-02-12
I tried yumi and tried "startup disk creator" from the menu, nothing I do in ubuntu MATE will allow me to successfully make a bootable usb, it has to be the ubuntu operating system to be at fault, it's unstable and I have to hard kill it now and then I dont know what to do, there was a software included in lubuntu and peppermint that I once used to write an iso to my slave HDD, if someone knows what that software is maybe you can link me to it? I think that may work

---

### Post by QIII on 2016-02-12
Given that so many here use Ubuntu without such issues, I find it an unlikely assumption that "Ubuntu" is at fault or unstable.  It is certainly possible that you have issues with your installation.

You would do well to avoid putting off those who would help you.  If this thread continues as your personal anti-Ubuntu rant, you risk finding yourself with no privileges to post here.

Keep it civil and respectful.

---

### Post by tyler91 on 2016-02-12
Why not just wipe the disk, boot a Live CD and then install it from there? Its how I actually got Ubuntu as an operating system in the first place.

I used tails:

0) Make sure you save the ISO onto a drive or something separate from the computer first!
1) Wipe drive of anything (Use Dban very effective, I would recommend a small wipe option with minimal overwrite)
2) Boot Live CD (Tails)
3) Go into disk menu and find your flash drive
4) format it 
5) click the gear and hit restore image then choose your ISO and wait!

6) Now youre ready to start your new operating system up!

---

### Post by Leon8200 on 2016-02-12
> **Tadaen_Sylvermane said:**
> you want to go back to debian but only use gui programs?

```
man dd
```

X being the drive letter of your flash drive. don't screw this up or you wipe out your hard drive / ssd contents.

```
sudo dd if=/path/to/iso of=/dev/sdX oflag=direct bs=4M
```

No such thing as apt-url that I know of.

thanx for the reply but I don't understand that so I can't take that chance

> **pqwoerituytrueiwoq said:**
> i found another tool (there is a ubuntu version there)
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)
you could set it up to boot the iso file like i did
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)
that guide is a bit dated, i just skip to III step 2 and change the directly to /media/$USER/mydrive
here is my grub.cfg from my flash drive [http://pastebin.com/ew98DJNw](http://pastebin.com/ew98DJNw)

you may want to try a different flavor of ubuntu, say xubuntu (xfce),  ubuntu mate (mate), ubuntu gnome (gnome), kubuntu (kde), or lubuntu  (lxde)

my pc won't  remain stable long enough for me to try to make sense of the guide 

> **QIII said:**
> Given that so many here use Ubuntu without such issues, I find it an unlikely assumption that "Ubuntu" is at fault or unstable.  It is certainly possible that you have issues with your installation.

You would do well to avoid putting off those who would help you.  If this thread continues as your personal anti-Ubuntu rant, you risk finding yourself with no privileges to post here.

Keep it civil and respectful.

sorry I'm not trying to put anybody off, my only PC is running ubuntu MATE with serious issues, my screen keeps becoming corrupt and I dont have any bootable linux flash drives on hand so I cant get out of this situation, I keep having to hard kill my pc and boot it back up again I tried to reply a few times and my screen went blank or corrupt in the proccess

> **tyler91 said:**
> Why not just wipe the disk, boot a Live CD and  then install it from there? Its how I actually got Ubuntu as an  operating system in the first place.

I used tails:

0) Make sure you save the ISO onto a drive or something separate from the computer first!
1) Wipe drive of anything (Use Dban very effective, I would recommend a small wipe option with minimal overwrite)
2) Boot Live CD (Tails)
3) Go into disk menu and find your flash drive
4) format it 
5) click the gear and hit restore image then choose your ISO and wait!

6) Now youre ready to start your new operating system up!

I don't have any live cd's/usb's to boot, I only have isos on my HDD  and I'm unable to burn them to my flash drive, that's the issue, I only  have one pc

---

### Post by buzzingrobot on 2016-02-12
You're first post said you need to "write my debian linux iso to my flashdrive".

Using dd as described in this thread works.  dd is a standard component of the Linux tool set..

I use dd exclusively to burn iso images to USB sticks. This is how I do it; I'll assume the USB is /dev/sdd:


> sudo dd if=<path-to-iso-image>  of=/dev/sdd bs=4M && sync

So, if I had a Debian image to install, and a USB stick as /dev/sdd, I'd change to the directory containing the iso image and execute "sudo dd if=debian.iso of=/dev/sdd bs=4M && sync".

(If you tell a PC BIOS to boot from a USB stick or DVD and the BIOS founds no bootable OS there, the BIOS will move on and boot normally. The problem you reported in your first post had nothing to do with Ubuntu.  It happened because the USB was not bootable.  And that happened either because the flash drive was faulty, the image you burned was faulty, or because it was burned incorrectly.)

---

### Post by oldfred on 2016-02-13
Hard reboots is one of the quickest ways to corrupt a Linux system, whether Ubuntu, Debian or any other.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by maglin2 on 2016-02-13
I am loathe to correct oldfred, because he is a superstar who has saved my system in the past, but - neither of those mnemonics really seems to work! Perhaps:
Raising-Elephants-Is-So-Utterly-Boring

---

### Post by oldfred on 2016-02-13
Oldfred is not always right. And he appreciates any help offered (then he updates notes so hopefully he learns. )

But I have seen various versions of REISUB. And I think the order is not critical as long as you start with R and end with B.

 R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

