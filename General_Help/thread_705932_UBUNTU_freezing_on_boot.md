---
title: "UBUNTU freezing on boot"
date: 2008-02-23
forum: General Help
---

### Post by linuxhatesme on 2008-02-23
Hello, i am using a hp dv6000, with vista linux dual boot. I got it to install the first time correctly, but it would freeze on bootup, after that i went into recovery mode, which would work, then boot it and i t would work, eventually it just wouldnt boot up no matter what. It will freeze and go into a 'something'box shell after sitting at a frozen loading screen for a while. Now its also doing it in the recovery mode. Heres the screen(its a different language to me) 


[IMG]http://i28.photobucket.com/albums/c244/Croh/DSC_9923.jpg[/IMG]



I already tried reinstall same thing.

I think it maybe my network card ).It also froze at "detecting usb ports, 2 detected"

Thanks for any help

---

### Post by pointone on 2008-02-23
It's saying it can't find your root partition. GRUB is pointing to the wrong place, or the drive isn't working properly.

If you know the parition you installed on (in /dev/sd* /dev/hd* format, as in /dev/sda1) you can go into GRUB during boot and edit the root= boot argument. Right now it says root=UUID=***..., you'll want to change it to root=/dev/sd*.

However, I notice it's also saying "SATA link down". This may be indicative of a bad connection to your hard drive; not sure. However, if the installer found your drives fine, I doubt this is the problem.

---

### Post by linuxhatesme on 2008-02-23
Thank you very very much. It seems to work like new now. Thank you.

I wonder why it got change?

---

### Post by Crafty Kisses on 2008-02-24
> **pointone said:**
> It's saying it can't find your root partition. GRUB is pointing to the wrong place, or the drive isn't working properly.

If you know the parition you installed on (in /dev/sd* /dev/hd* format, as in /dev/sda1) you can go into GRUB during boot and edit the root= boot argument. Right now it says root=UUID=***..., you'll want to change it to root=/dev/sd*.

However, I notice it's also saying "SATA link down". This may be indicative of a bad connection to your hard drive; not sure. However, if the installer found your drives fine, I doubt this is the problem.

Exactly.

---

### Post by percussionhall on 2008-03-01
I am having this same problem, but, forgive me, I do not know what  you are saying to do.  Can you simplify this for me please? (the only  difference is that I have xp not vista, and that I could never run the ubuntu in safe mode or w/e)

---

### Post by pointone on 2008-03-01
When Ubuntu boots, GRUB starts and allows you to choose whether to boot Ubuntu or XP. What you need to do is select the Ubuntu option and hit "e" to edit the commands it passes to Ubuntu during boot. 

After hitting "e", another menu will open with several lines. Select the "kernel" line and hit "e" again. This should take you to a prompt with a chain of commands. One of the commands will be: "root=UUID=########-####-####-####-############". You need to change this to "root=/dev/*d*", where /dev/*d* is your root partition.

To find out what your root partition is, you can run "fdisk -l" from the BusyBox prompt. Post the output of "fdisk -l" here if you are unable to interpret it.

---

### Post by percussionhall on 2008-03-02
how do i get to the busybox prompt, and how do I run fdisk -l from that 

(and is that l an L, 1 or I?)

---

### Post by percussionhall on 2008-03-02
okay, so I used the ubuntu installer cd to check what my root partition is (which I am guessing is the partition that ubuntu is installed on) because I have no clue how to use fdisk, or busybox or anything.  (sorry, I am not a computer person). 

So on the installer, it said that the partition was sda3, which i'm assuming is plugged in at '*d*' at the kernel line place.  So it now says "root=/dev/sda3" rather than root=uuid=...".  (I also tried just sda)

after this i press enter to get back to that menu and then I press 'b' to boot. It still gets stuck at the third little section of the loading bar.  

I also tried to do this booting into recovery mode, and that didnt work.  It went into this crazy thing that I've gotten once before where it keeps flashing by the screen forever, and the numbers on the left are always increasing.  The first time I saw that, I left for a few hours and when I came back it was almost at 20,000 haha.

---

### Post by pointone on 2008-03-02
When you said you were having the same problem, I assumed you meant you were having the same problem and dropping to the BusyBox prompt shown in the OP's screenshot. If you don't see "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)" when your boot fails, then you have a different problem. 

I'd suggest starting a new thread in this case, and providing a more detailed description of your problem, complete with full error messages and all. You can use the "Scroll Lock" to pause the boot process and read the messages it shows if they're going by too quickly. You can also look at /var/log/dmesg on your install drive from the live CD.

---

### Post by percussionhall on 2008-03-02
ok thanks a lot,

I thought my problem was similar

---

