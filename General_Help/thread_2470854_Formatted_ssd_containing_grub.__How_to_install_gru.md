---
title: "Formatted ssd containing grub.  How to install grub on other ssd?"
date: 2022-01-13
forum: General Help
---

### Post by marsdenf on 2022-01-13
Using  a desktop comp with two ssd's, both loaded with Xubuntu 20.04.  I never use the second drive, so I decided to format it using gparted.  Both partitions of the drive to ext4.
The second ssd must have had grub on it, because now when I boot into the main drive, instead of the grub choice menu, I get a message:     "Gnu Grub version 2.04
Minimal bash like line editing is supported..."    If I boot into the formatted drive,  the message :      "Welcome to grub.   error: no such device:  ...
error: unknown file system.   grub rescue>_"      (Using bios to boot to particular drive).   As you can see, I know almost nothing about partitions etc.
How can I get the main drive to boot into xubuntu?

---

### Post by oldfred on 2022-01-13
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I have always said with mulitiple drives or multiple installs, to only use Boot-Repair's advanced mode. It may choose wrong install or wrong drive for boot loader. But Yann is making some changes to improve choices in Boot-Repairs default fixes.

---

### Post by marsdenf on 2022-01-14
So if I understand correctly, you are giving me two options: first: Use Boot-Repair iso advanced mode and pastebin the link to summary report, do not autofix until report is analyzed and second: use ppa version?   Can you be more specific and detailed, I don't know much about these things.

---

### Post by tea for one on 2022-01-14
Two options but one recommendation, which is to use the [COLOR="#0000FF"]ppa version[/COLOR].
The reason is that the ppa will supply the current version (4ppa161)
The boot-repair software is undergoing active development.

Using your installation USB, can you boot into a live session, open the terminal and enter:-
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```
```
sudo apt-get update
```
```
sudo apt-get install -y boot-repair && boot-repair
```
The final command will install the latest boot-repair software and also start the software.
It will generate a report, together with a pastebin link.
Post the pastebin link in this thread.

As mentioned by [COLOR="#0000FF"]oldfred[/COLOR] - [COLOR="#FF0000"]do not run the auto fix till reviewed[/COLOR]
Please allow forum members to study the report and offer advice.

---

### Post by yancek on 2022-01-14
I'm sure you understand now that In situations like this, the standard procedure would be to boot into the OS you want to keep and install Grub to the device the OS is on..  .  With UEFI and Legacy installs, it gets a little more complicated but I would suggest that you follow the advice above and also keep boot repair either on your OS or on a USB as it is a very useful tool.

---

### Post by oldfred on 2022-01-14
Please click on the first link to Boot-Repair.
It shows two options, one a live flash drive based on Lubuntu to be lightweight and the other is a ppa to add Boot-Repair to your current live installer or any working system.
Instructions on ppa are the same as tea for one posted.

Many new users do not understand all the options in the advanced mode, second link, and we need to review your configuration before making suggestions.
Default repair often works, but best to have one of us review configuration first.

---

### Post by marsdenf on 2022-01-14
I also have a laptop with Xubuntu 20.04, which is what I am using to post this thread.  Maybe the best thing would be to download the latest boot-repair iso onto a flash drive and use that on my desktop computer?

---

### Post by oldfred on 2022-01-14
You can use ISO, just not sure if it is as current as ppa.
The ISO is typically not updated as frequently as the ppa.

So suggest using Ubuntu live installer flash drive, that you should always have for current version of installed systems & use that.

---

### Post by marsdenf on 2022-01-14
Okay, I created a bootable usb drive with latest xubuntu 20.04, installed boot-repair via ppa and here is the url for the scan done by boot repair:  [https://paste.ubuntu.com/p/PPGmWYyDRx/](https://paste.ubuntu.com/p/PPGmWYyDRx/)
The drive I want to keep with xubuntu on it is sda.   The drive I formatted and want to keep empty is sdb.   I await your instructions.

---

### Post by marsdenf on 2022-01-14
I inadvertently clicked "apply" on advanced options in boot-repair.  So the repair is done, and everything works fine now.  Will mark this thread as solved.
Here is url for the report on the repair done:  [https://paste.ubuntu.com/p/7MhrSH2xtB/](https://paste.ubuntu.com/p/7MhrSH2xtB/)

---

### Post by oldfred on 2022-01-14
Is grub ok?
This in /etc/default/grub line 313 in final report should be two lines.

> GRUB_SAVEDEFAULT="false"GRUB_DISABLE_OS_PROBER=false


GRUB_SAVEDEFAULT="false"
GRUB_DISABLE_OS_PROBER=false

---

### Post by marsdenf on 2022-01-14
> **oldfred said:**
> Is grub ok?
This in /etc/default/grub line 313 in final report should be two lines.



GRUB_SAVEDEFAULT="false"
GRUB_DISABLE_OS_PROBER=false

         It works okay, but I changed the line into two lines as you suggested, and it still works fine.

---

