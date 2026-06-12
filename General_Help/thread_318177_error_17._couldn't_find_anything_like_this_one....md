---
title: "error 17. couldn't find anything like this one..."
date: 2006-12-13
forum: General Help
---

### Post by James_Madrox on 2006-12-13
Okay, so I installed Ubuntu 6.10 onto my hardrive. I partitioned it to run my Windows XP Professional alongside just in case my family wanted to get on my computer. Well, I rebooted my computer, took out my disk. It started up and came to a screen, saying this: 

Grub Loading stage1.5



Grub loading, please wait . . .
Error 17


And that's all it said. Didn't do a thing afterwards, I have to boot off of the Ubuntu CD just do anything with my computer at all. I was hoping someone might be able to help me out?     ](*,) ](*,) ](*,)

---

### Post by daller on 2006-12-13
Well, my browser acted weird, and posted twice... sorry!

---

### Post by daller on 2006-12-13
Hmm... did you do this today?

There seems to be a general error with installation/upgrading today... (The computer had internet-access, right?)

See this:

[http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206)

---

### Post by James_Madrox on 2006-12-19
Hmmm. Okay. I went through that thread, looked at it all, did everything it said there to try. And I ended up having to completely redo my system. So I decided to try again, well, grub error 17 once again. Nothing has worked at all. I've checked up at another thread, and tried something there...but I have no grub in /boot...at all. It is non-existent. I'm at a complete loss of what to do.

When I type in Sudo fdisk -l, I get this. Remember, I have this on a dual partition (single harddrive) with Windows XP Pro.

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5737    46082421    7  HPFS/NTFS
/dev/hda2   *        5738        9563    30732345   83  Linux
/dev/hda3            9564        9729     1333395    5  Extended
/dev/hda5            9564        9729     1333363+  82  Linux swap / Solaris
```

Everything seems to be in order to me, considering when it installed, it showed hda5 as a device it was using, and no 4 anywhere to be seen. If there is anything at all anyone can think of to help, it'll be much appreciated.

---

### Post by bodhi.zazen on 2006-12-19
Can you post /boot/grub/menu.lst

it looks like you may need to boot to the live CD to access this file .....

---

### Post by James_Madrox on 2006-12-19
Well, I put that in and this is what comes up, I'm currently running off of the livedisk, can't use my computer at all otherwise...

```
bash: /boot/grub/menu.lst: No such file or directory
```

---

### Post by bodhi.zazen on 2006-12-19
> **James_Madrox said:**
> Well, I put that in and this is what comes up, I'm currently running off of the livedisk, can't use my computer at all otherwise...

```
bash: /boot/grub/menu.lst: No such file or directory
```

LOL :lol:

Sorry, you need to list this from the Ubuntu partition....

```
sudo mkdir /media/ubuntu
sudo mount /dev/hda2 /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

---

### Post by James_Madrox on 2006-12-19
haha. yeah. I probably should of made a mention of the fact that I'm extremely new to the linux experience..In that I don't know how to do much of anything, but all of this is helping me learn lol! Anyways, here's what I got, just down to the kopt...

```
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cbd8942b-f8f5-48ee-a186-9cc443d60ce1 ro
# kopt_2_6=root=/dev/hda2 ro
```

If i need to post something different, sorry, just let me know. I'll be up trying to get this fixed for a little bit longer.

---

### Post by bodhi.zazen on 2006-12-19
That does not look like what I was expecting to see. Is that the entire file ?

If so, re-install grub:

```
sudo grub
```

This will give a grub prompt:

grub >

At the grub prompt type:

```
root (hd0,1)
setup (hd0)
quit
```

Re-boot

---

### Post by James_Madrox on 2006-12-19
well, no, that's not the full thing. The entire thing is about 151 lines...mostly seems like explanations of how to edit the file though...Should I post all of it up?

---

### Post by bodhi.zazen on 2006-12-19
You can skip any line that starts with a #

Or post the whole thing and I will skim to the relevant parts :)

Or you may draw the attention of Bulldog, he is the resident expert :)

---

### Post by bulldog on 2006-12-19
Have no fear,Bulldog is here :D 

Hi Bodhi and James_Madrox everything well?

I think you can manage,bodhi,you're much more experienced than I am.

---

### Post by CroEragon on 2006-12-19
I'm by no means Ubuntu expert, i'm newbie as you but while having similar problem as you i found out some good things.
If problem is connected to this new problem recently appeared i cannot help you. But i, same as you, avoid messing around with menu.lst and MBR (Master Boot Record) so i found tool called Super Grub. It is basically beginner-friendly version of grub on liveCD and does most of things automatically. If nothing, it will help you boot your Ubuntu from hard-disk without live cd. i suggest you to give it a go. This is direct download link.
[This is direct download link (.iso CD image). ]("http://forjamari.linex.org/frs/download.php/458/sgd_0.9534_EN.iso")
Try rewriting MBR or something similar.
If rest of guys find deeper problem or or say not to use it  listen to them, im no expert.
Hope it helps.

---

### Post by James_Madrox on 2006-12-20
Hmm. Well, I decided to just drop Windows all together on my desktop, since I'm getting a laptop for christmas as it is. Well, I just reinstalled Ubuntu exclusively to the hard drive. Didn't get the error 17...however I did get error 18 this time. I'm gonna pull up the menu.lst in a sec and post it up to see if it won't tell anyone something, but for now. I'm off to take out the trash...*sighs*

---

### Post by James_Madrox on 2006-12-20
Okay, here's the menu.lst. I'm only posting what doesn't show up with a # in the beginning, which isn't much...

```

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot
```

---

### Post by bodhi.zazen on 2006-12-20
And where is our ubuntu root partition ? hda2?

If that is the case, you need to change (hd0,0) to (hd0,1) 

and /dev/hda1 to /dev/hda2 in your kernel line

in your grub enteries.



If you do not know, ```
sudo fsdisk -l
``` to list your partitions

---

### Post by James_Madrox on 2006-12-20
Hmm, I'm at work right now, so I'm not too positive on this, and I won't be home till after 11p.m. Central time, but I believe my root is on hda1, ext on hda2, swap on hda3. Like I said, I'm not totally sure on it, and I'll be double checking and posting it up when I get home. Just thought I'd put up what I was thinking, maybe someone will have an idea before I get home...I have no idea why it isn't working properly, I've used linux on a much older PC before. Thanks for all your help in trying to get this going.

---

### Post by James_Madrox on 2006-12-21
Okay. Here's my fdisk -l.

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

```

---

### Post by James_Madrox on 2006-12-22
Hmm. I spoke with a friend of mine who runs ubuntu on his system, and he explained to me that it's possible that Ubuntu just won't work with my system, as he attempted another distro and it didn't work for him. Maybe that's the problem?

---

