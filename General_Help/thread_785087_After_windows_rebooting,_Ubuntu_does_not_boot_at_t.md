---
title: "After windows rebooting, Ubuntu does not boot at the first time??"
date: 2008-05-07
forum: General Help
---

### Post by lethang on 2008-05-07
I'am using tablet tc4200
I tried Wubi 8.40 et intalled Ubuntu,
Installation was fine in windows,
I rebooted, et selected Ubuntu
et the screen appear:

Booting 'start installer in normal mode'
(hd0,4)
filesystem type is fat, partition type 0xb
[Linux-bzImage, setup=0x2a00, size=0x1ce278]
[Linux-initrd @ 0x1f87300, 0x77c500 bytes]



et nothing happen
Can anyone tell me what is the problem?
What I have to do?

---

### Post by ago on 2008-05-07
Press ESC after selecting Ubuntu and try the other options. In particular ACPI workarounds. The verbose mode should show you why it does not work.

---

### Post by lethang on 2008-05-08
I have tried all 4 options but the result always is the same, I do not know what is the problem?
anyone please tell me?

---

### Post by ago on 2008-05-08
Use verbose mode and see if there is any interesting message
If you get to a command prompt type

cat /casper.log

---

### Post by ago on 2008-05-08
Note, some machines require special parameters to boot, like IRQPOLL. Those have to be added manually. See the WubiGuide.

---

### Post by lethang on 2008-05-08
I've tried all 7 steps from the WubiGuide, 
- adding the argument IRQPOLL,
- Use verbose mode
but the problem is the same, I can not see any log file?? (D:\ubuntu\installation-logs.zip does not exist)
I think the command initrd does not work?? but why? anybody kown? pls!

---

### Post by ago on 2008-05-08
Well in verbose mode do you see any message scroll? Do you end up in a terminal (where you type things) or not? Also try to boot using the live CD.

---

### Post by lethang on 2008-05-09
I can not do anything, just a while splash appear
when I press "c" enter the command 
grup> root (hd0,4)
grup> kernel /ubuntu/install.......
grup> initrd /ubuntu/install/.........

alls 3 command done well
but when I boot
grup> boot
it does not work, just a while splash appear and I can not do anything after

I have one hard disk et divided into 3 partion: C(hd0,NTFS),D(hd4,FAT),E(hd5,FAT) and wubi is installed on D
the problem from wubi? ubuntu? or my tablet?

---

### Post by ago on 2008-05-09
What "splash screen" do you see exactly? Is it brown with a bird or a black screen with ubuntu logo?

---

### Post by lethang on 2008-05-09
My tablet does not have a CD-ROM, I put wubi and ubuntu in the same  folder et install. 
I have tried the verbose mode but the result is the same, just only the while splash _ appear. 
I go in windows and check the log file, but it does not exist.

---

### Post by ago on 2008-05-09
Do you get to a command prompt where you can type commands?

---

### Post by lethang on 2008-05-09
Before entering the boot option, I can enter the command line for editing par press "c". My tablet est exact the picture following

---

### Post by ago on 2008-05-09
Do you know if Ubuntu (without Wubi) is reported to be running ok on your tablet?

---

### Post by lethang on 2008-05-09
Yes, Ubuntu(without Wubi) can work on tablet tc4200.

---

### Post by lethang on 2008-05-10
I use Kubuntu, it work!

---

