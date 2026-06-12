---
title: "Boot directly in Vista"
date: 2007-10-26
forum: General Help
---

### Post by Chustar on 2007-10-26
I installed Ubuntu on my laptop, but it boots directly into the Grub 1.5. Then, you have three seconds to choose windows or it boots straight into Ubuntu. Is there a way to reinstall the windows bootloader. the problem is i use windows a lot more than i use linux and i'm thinking about deleting the linux partition. I think if i delete the partition my laptop won't boot at all, so i need to repair the boot. And no, the manufacturer didn't give me the installation disk. thanks in advance. 
Chustar

---

### Post by Havek on 2007-10-26
> **Chustar said:**
> I installed Ubuntu on my laptop, but it boots directly into the Grub 1.5. Then, you have three seconds to choose windows or it boots straight into Ubuntu. Is there a way to reinstall the windows bootloader. the problem is i use windows a lot more than i use linux and i'm thinking about deleting the linux partition. I think if i delete the partition my laptop won't boot at all, so i need to repair the boot. And no, the manufacturer didn't give me the installation disk. thanks in advance. 
Chustar

You can change what grub boots too directly and the time for a descion in the menu.lst file in the grub dir.

---

### Post by Chustar on 2007-10-26
i forgot to mention i'm a total newbie when it comes to linux. TOTAL newbie!

---

### Post by kellemes on 2007-10-26
[Super Grub Disk]("http://supergrub.forjamari.linex.org/") will let you reinstall the Windows bootloader..

Indeed you're correct, system won't boot with a faulty Grub-install, so "fix" bootloader first and afterwards delete Ubuntu.

---

### Post by anotherdisciple on 2007-10-26
If you do completely destroy your MBR... I think you can go in DOS and type FDISK/MBR ... umm... yeah.. i think that's right

---

### Post by anotherdisciple on 2007-10-26
I'd edit your GRUB  and play around with linux a little more though. Look how the community works.. you asked a question... and you got answers. I'm a complete newbie and I've gotten tons of help... and linux if fun anyways... I like the work involved in making it do what you want it to do.. and the ability to customize nearly anything.

---

### Post by Chustar on 2007-10-26
I do like Ubuntu, i'm just too busy for any learning curve. Thanks everyone. I'm about to try the super grub disk. wish me luck!

---

### Post by devliljohn on 2007-10-26
i think your going about this all wrong, don't get rid of ubuntu. just change grub to boot into windows first.

---

### Post by kellemes on 2007-10-26
> **devliljohn said:**
> i think your going about this all wrong, don't get rid of ubuntu. just change grub to boot into windows first.

When he delete's Ubuntu (this is his wish) his system will not boot because he lost his bootpartition/directory, without this.. Grub won't function.

---

### Post by Chustar on 2007-10-26
i tried the super grub disk. now, windows won't boot. it says something like "cannot boot due to recent hardware/software change." this is serious for me. i'm consdiering a complete system restore. i'm that desperate!

---

### Post by kellemes on 2007-10-26
> **Chustar said:**
> i tried the super grub disk. now, windows won't boot. it says something like "cannot boot due to recent hardware/software change." this is serious for me. i'm consdiering a complete system restore. i'm that desperate!

This is a message from Windows itself? Strange, never heard of this before..

---

### Post by larryfroot on 2007-10-26
The way around it is - as has been pointed out - to change the grub settings to a) put windows on top of the boot order and b) to give grub longer than three seconds to do it. Which seems like a bloomin aggressive setting as a default. Bit of a black mark there...I can't remember rightly how you do it - I seem to recall doing it via a gui ages ago on suse, but it really isn't that difficult, even changing a couple of very simple values in the grub configuration is a no-brainer...So perhaps the issue will have the will it or won't it wreck my boot partition will not have to be confronted and the chap can still have ubuntu to poke around in and satisfy his curiosity. And I think it is fdisk / mbr...cor this is a right stagger down memory lane...

---

### Post by Can+~ on 2007-10-26
An easy way to set windows as default:

Open a terminal window (App -> Accesories -> Terminal), copy and paste the following (you can paste using middle mouse, or rightbutton+paste).
> gksudo gedit /boot/grub/menu.lst &

Then look for this line:

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default		0**

default is the first OS that will be highlighted. Change the number to the list element (0-based) that should start first. Example:
> 0. -Ubuntu 7.10
1. -Ubuntu 7.10 safe
2. -Other OS's:
**3. Windows Vista**
4. Blah..

"then I should set default to 3"

Once edited, hit Ctrl+S (save) and it's done.

*edit* whoa, a lot of responses while I was writing.

---

### Post by larryfroot on 2007-10-26
Whoa! In the time it took me to write the above post the smelly stuff has hit the fan...hold on I will have a think...

---

### Post by Can+~ on 2007-10-26
> **kellemes said:**
> This is a message from Windows itself? Strange, never heard of this before..

I had.

It happens when a component on Vista has changed. It happened to a writer of APCMag when he changed his graphics card, Vista booted saying that the system changed and can't boot.

According to microsoft, this is not a bug, it's a feature! They thought that blocking your computer after changing something was a sure way to block anyone trying to steal their OS. *edit*: here's the article: [http://apcmag.com/vista_activation](http://apcmag.com/vista_activation)

---

### Post by larryfroot on 2007-10-26
a boot disk with fdisk on it should be able to rewrite the master boot record...just change directory into the drive with the boot disk on eg a: for a floppy and type fdisk / mbr or fdisk \ mbr. That should put the windows bootloader back into place. In the direst of emergencies and it looks to be more than a bootloader issue - which I doubt - then getting hold of a knoppix 5.1 live cd will enable you to mount your windows partition and save your data onto removeable medium.  If you do have to go down that route, PM me and I will happily send you instructions - lots of mounting and make writables in knoppix, nothing inherently complex, just a very secure system. But whatever - good luck...I'm here if you need knoppix help.

---

### Post by Chustar on 2007-10-26
Thank you all for your help. however, i'm going to restore my computer. During the holidays i'll reinstall ubuntu and give myself at least a week to beat it down to its knees! :) Well, here i go. To infinity...and beyond!

---

### Post by larryfroot on 2007-10-26
Well you have taken it pretty well, I must say. Had it been me I would be chewing the carpet by now. But while I am at it...a word about knoppix. It really is a fully featured OS designed to run in ram. To think of it as being like a live cd ala ubuntu and others is a mistake. I once screwed up royally (all part of growing up and being British) and knoppix saved the day...I was able to boot into knoppix, use K3B to burn my windows data onto a series of CD's - using the joliet switch as well, a nice touch that! - and save the day. It really is head and shoulders above other live cd's I have pottered around in. As long as you right click on the drive icons to first mount them from the right click menu and then a second time to choose to make them writeable if need be, then the rest should be relatively straightforwards. Hope you do get to enjoy ubuntu though. It would only be fair after such a display of equanimity possibly born from the fact of having adequate back ups!

---

### Post by Chustar on 2007-10-26
Oh thank God! I got windows to boot again...no idea how! I'm just gonna ignore Ubuntu and somehow, manage myself until vacation. No, i don't have backups. The most important stuff is my projects which are in my email. Everything else was expendable. My psychiatrist says I supress my emotions, i think he's psycho!
Anyway, thank you all for your support. This is really what puts Linux systems above the rest.

---

### Post by Can+~ on 2007-10-26
> **Chustar said:**
> Oh thank God! I got windows to boot again...no idea how! I'm just gonna ignore Ubuntu and somehow, manage myself until vacation. No, i don't have backups. The most important stuff is my projects which are in my email. Everything else was expendable. My psychiatrist says I supress my emotions, i think he's psycho!
Anyway, thank you all for your support. This is really what puts Linux systems above the rest.

Great! I thought you ended up with a bitter taste with all this trouble (bad thing, since vista has that dumb security protection). 

Also. Did you changed the grub in the end? or wiped ubuntu out?

---

### Post by Chustar on 2007-10-26
No, i still have to choose to boot vista instead of ubuntu at startup. better than nothing i suppose.

---

### Post by larryfroot on 2007-10-27
If only the time grub gave you was longer than three seconds...perhaps a switch in the installation process asking for boot order preferences and time allowed would be a nice touch and save bods a scary situation. And help them to access ubuntu and try it out properly. I honestly (this is going to sound so condescending, but I really do mean it) feel sorry for windows users. God have they been short changed. You don't even purchase the OS when you hand over your money? And it is a secure as camping on a racetrack?

---

### Post by Can+~ on 2007-10-27
> **larryfroot said:**
> If only the time grub gave you was longer than three seconds...perhaps a switch in the installation process asking for boot order preferences and time allowed would be a nice touch and save bods a scary situation. And help them to access ubuntu and try it out properly. I honestly (this is going to sound so condescending, but I really do mean it) feel sorry for windows users. God have they been short changed. You don't even purchase the OS when you hand over your money? And it is a secure as camping on a racetrack?

Again... You can change how Grub works, even the timeout before entering: 

****EDITED!****

**EASIER WAY** I was watching the Add/Remove programs, and there is this app called "Start-Up Manager"

It's far more easier to configure than using the terminal, you should check it out ;D.




[COLOR="Silver"]**** Deprecated method ****

Alt+F2:
> gksudo gedit /boot/grub/menu.lst

> # Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default		0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		3**

It should look like something like this. Default is the first option thats highlighted, and timeout is the wait time before auto-selecting (seconds).[/COLOR]

---

### Post by Chustar on 2007-10-27
Uh, the installation disk is mine by right. if i really needed to, i think i could get fujitsu to mail it to me. anyway, i might have misrepresented part of the problem. when i said it gives me 3 seconds, i meant that i had to press a key within that 3 seconds. if i did, then it would stop counting down and give me all the time to choose an OS.

---

### Post by larryfroot on 2007-10-28
I fully understand the impression that microsoft give their customers that the installation disk is theirs by right, but try an significant hardware upgrade on your machine, or even a newer set of drivers for existing hardware and you might be surprised at what your copy of vista will do in response to such actions. it will enter reduced availability mode - or somesuch description thereof - until you contact Microsoft to let you have your Vista back. If they feel you have come up with a good enough reason for them to unlock your copy of Vista. The only people who don't have to play around with all of this are Mac, Linux and XP users and anyone with a pirated copy of Vista. The last point being so unfair on people who have chosen to do the honourable thing. Or been dropped into it by their PC vendor.

---

### Post by Chustar on 2007-10-28
Has this happened to you or do you know someone it has happened to?

---

