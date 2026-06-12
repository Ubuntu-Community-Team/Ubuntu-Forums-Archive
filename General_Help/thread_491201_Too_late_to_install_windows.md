---
title: "Too late to install windows?"
date: 2007-07-03
forum: General Help
---

### Post by HimeNoHogosha on 2007-07-03
I built a new machine last week and decided to switch to using ubuntu for my primary OS, mainly because I didn't want to buy Vista. I worked hard through the weekend getting things to run and am now at a happy place. However, I realized there are some things I cannot do yet, such as play certain games or connect with my iPod (i know there are solutions for this but it's kinda complicated to me). 

So I decided maybe I could install WindowsXP on a separate partition or a separate drive. I've only managed to find tutorials on how to set up dual boot, but most of them assume that the user has windows first, and wants to install ubuntu. Are there instructions on how to install windows if you already have ubuntu? Also, would you guys recommend using partitions or separate HDD?

---

### Post by LaRoza on 2007-07-03
Seperate HD is much easier and safer. 

You can install XP next to Ubuntu but you will need to restore grub.

-edit Get GParted Live CD to make a partition for XP. Research how to restore grub before Installing. (Grub can boot Windows and Linux).

I recall hearing about something for Windows which allows you to boot Linux, but I don't remember it.

---

### Post by HimeNoHogosha on 2007-07-03
So is the following order correct:

Buy a new HD and plug it in.
Pop in windows CD and install to second hard drive.
Find some way to restore grub because windows will overwrite it?

Or am I missing the concept?

---

### Post by Shazaam on 2007-07-03
Save yourself some frustration and install VmWare Server(free) or VmWare Player(free again) or VirtualBox on your Ubuntu drive and run XP in a virtual machine. You will find that after time you won't be running XP much.

---

### Post by HimeNoHogosha on 2007-07-03
Does playing games through a virtual machine cause poorer performance? How robust is VmWare Server or Player? Again this is the first time I'm configuring a linux machine by myself so I don't know how to debug things well.

---

### Post by akshaysrinivasan on 2007-07-03
It'll be quite easy to install Windows on a Linux box.You have setup a separate partition,install Windows , reinstall  GRUB , add the windows menu into menu.lst,and that about it.
I am not sure if you'll be able to play games and stuff on VMPlayer.I'm not even sure it supports DirectX.You might want to try some commercial apps like Cedega which let you play many Windows games.

---

### Post by HimeNoHogosha on 2007-07-03
Is there a guide on how to reinstall GRUB?

---

### Post by Irony on 2007-07-03
To restore grub just boot up into a live CD and type;

[PHP]sudo grub[/PHP]

Then do this;

[PHP]grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit[/PHP]

What this does is first find any stage1 menu's in /boot/grub - thus you can see them here in hda3, hda6  and hda7. I then point grub at hda3 (hd0,2) by installing grub to the MBR (hd0) which is hda.

In your case root (hdX,X) will depend on where Ubuntu is installed. Note with the Live CD you may have to install grub first via synaptic - I can't remember; if its not installed the sudo grub instruction won't do anything.

---

### Post by HimeNoHogosha on 2007-07-03
Thanks you guys for the help so far. 

Somebody mentioned to me that I could unplug my linux HD, plug in a second HD,  install windows, and then plug in my first HD again... or something? Does that sounds like a familiar procedure to anybody?

---

### Post by sci-fi guy on 2007-07-04
Are you trying to use [Wine]("http://www.winehq.org") to run some of your Windows programs?
If not, the procedure is simple:

1. Check if your program/game has been tested [here.]("http://appdb.winehq.org/appbrowse.php")  This should give you a good idea how it will run. If it is not found there, You'll just have to give it a try and pray.

2. Follow the directions [here.]("http://winehq.org/site/download-deb")

3. Go to SyStem>>Administration>>Synaptic Package Manager. Search for wine. Click the check box next to wine and select "Mark for installation" and click apply at the bottom.  Wait for that to finish and close Synaptic (and the terminal, if you haven't already)

4. Now install/run your windows programs. I caution you to make sure that it is running well enough before entering critical data.

---

### Post by t2000kw on 2007-07-04
If you install to a different hard drive, use your BIOS to switch your boot drive, install XP, then switch back and you can then use BIOS to determine which hard drive will boot (and consequently which OS to boot to) or you can refresh GRUB (not sure how to do it but it is possible) when you boot to Linux and it will find XP and add it to the menu. Then you can boot to whichever OS you wish that is on the GRUB menu. 

When you use BIOS to change the boot drive, the system won't care what's on the other drive unless you have a boot menu present. So you could install XP and it won't know about the other drive. That's how I installed Ubuntu, just the opposite of what you want to do but similar in approach.

---

### Post by HimeNoHogosha on 2007-07-05
Yeah I do have wine installed, but it doesn't run Ghost Recon Advanced Warfighter at all. I basically just want to use windows to play games.

What I did was unplug my linux drive, install windows onto my second drive, then replug in my linux drive. Now I just need to figure out a way to make grub display the windows installation on the second disk. I've found this link [http://blog.firetree.net/2005/08/26/duel-boot-windows-with-grub/](http://blog.firetree.net/2005/08/26/duel-boot-windows-with-grub/) but I haven't tried it yet. Has anybody tried this method?

---

### Post by Irony on 2007-07-05
Just add the;

[PHP]title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1[/PHP]

to your menu.lst first and when you next boot up see it works.

---

### Post by strabes on 2007-07-05
[http://ubuntuforums.org/showthread.php?t=358183](http://ubuntuforums.org/showthread.php?t=358183)

---

