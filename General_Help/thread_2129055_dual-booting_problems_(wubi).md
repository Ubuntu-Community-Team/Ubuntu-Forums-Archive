---
title: "dual-booting problems (wubi)"
date: 2013-03-25
forum: General Help
---

### Post by LinkinMcOwnage on 2013-03-25
Hi there,

I'm pretty much completely new to linux. I've used ophcrack on a CD, *once.* I am having issues getting ubuntu working alongside my windows 7 installation. The first time I booted ubuntu, I got to the ubuntu splash screen, and then it froze. No disk activity and unresponsive keyboard. Four of the five dots were white, with the rightmost one being red, if that matters at all. I couldn't get that to work at all, so I wiped it from windows with wubi and started again.

Then, I got the following message: mount: unable to mount proc/mount - no such file or directory exists

From there it proceeded to boot into the login screen. I entered my name and was entering the password, and it locked up. Subsequent attempts result in the above message and no boot. Holding shift to get into the recovery options doesn't work either, I get the same message.

Additionally, when I made to the ubuntu login screen, my time in windows was set 2 hours earlier after a reboot

If it helps, my specs are below:

Intel 3570K 4.4Ghz
G.Skill 16GB DDR3 2400Mhz
ASRock Z77 Fatal1ty Professional
Galaxy GTX670 2GB
Asus Essence STX
Corsair Force 3 120GB SSD
Western Digital Caviar Black 2TB
Silverstone ST60F-P 600W PSU

---

### Post by Impavidus on 2013-03-25
To get clear how you installed Ubuntu: Is this indeed a wubi install? In that case it's inside a windows partition, not really alongside windows. If it's really alongside you wouldn't be able to uninstall using wubi.

Concerning your clock: this is caused by a mixup of local time and Greenwich time in your hardware clock. Windows defaults to local time, which will cause trouble on every dual boot machine as soon as you change time zone or DST, Linux defaults to Greenwich time. It's easy to fix once you get your Ubuntu running.

---

### Post by LinkinMcOwnage on 2013-03-25
Yes I installed ubuntu via wubi from within windows.

I've fixed my problem - unplugging my DVD drive has gotten ubuntu working. However this a problem - I intend to keep running windows for some things (namely exact audio copy) and I can't use my DVD drive I may as well stick to windows... not that I ever need the drive for anything other than music, all my OS installs are from USB now. But I do need the drive...

---

### Post by oldfred on 2013-03-25
I do not know if it applies to wubi or not, but some have reported this issues with Asrock, particularly the Asmedia ports.

 Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

Full install if you want to install to a separate drive

 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

---

### Post by LinkinMcOwnage on 2013-03-25
Thanks for that. Eventually I probably ditch windows altogether once I get all my data transferred across to the proper disk format.

My SSD & HDD are plugged into the Z77 ports on the board. There are only two of them, the other four ar ASMedia, one of which my optical drive was plugged into.

I've got everything set up as AHCI, I will try that nomsi boot param.

---

### Post by LinkinMcOwnage on 2013-03-25
So I've disabled the asmedia SATA chipset in the UEFI and plugged my optical drive into another port - now working fine. Thanks for the help.

---

