---
title: "transfering OS's to new HDD"
date: 2005-10-25
forum: General Help
---

### Post by tonysathre on 2005-10-25
my dell dimensions 4550 has a 60 GB HDD with XP on it. i had an old 10 GB HDD lying that i threw in for linux, but now i need more room for linux, i was wondering if it is possible to create 2 partitions on a new bigger HDD and move XP onto one and Linux on the other to give myself 125 GB for each without having to reinstall... any help would be greatly appreciated.

---

### Post by Xentex on 2005-10-25
[QUOTE=tonysathre]my dell dimensions 4550 has a 60 GB HDD with XP on it. i had an old 10 GB HDD lying that i threw in for linux, but now i need more room for linux, i was wondering if it is possible to create 2 partitions on a new bigger HDD and move XP onto one and Linux on the other to give myself 125 GB for each without having to reinstall... any help would be greatly appreciated.[/QUOTE]

If you're in XP, you might be able to use Partition Magic to first resize a drive (i.e. shrink the XP ;-) ), then clone it onto the second drive (primary partition).

Or you might be able to use a LiveCD (Knoppix, Gnoppix, or Ubuntu's LiveCD), and boot up with the new drive installed - and simply to a copy & paste of the XP files onto a new partition?

Ideally, you could back-up the /Documents & Settings/* , and install XP from scratch again?

---

### Post by tonysathre on 2005-10-26
would that work if i have a lot of customizing done on xp, like icons, boot splash, login screen, complete OS X theme

if i copied and pasted everything i would have to reinstall the boot loader right?

also in the ubuntu installer there is an option to copy from another drive or partition, would that work

---

### Post by Xentex on 2005-10-26
Yes, you can use the "copy from anoher partition" option within the Installer.

Remember, you will have to install XP on the primary partition, on the primary disk for it to go smoothly - there are files within XP which remember where it is...
Step #1:  Remove current primary (XP), and install new disk as primary.
Step #2:  Install "old" XP disk - where is not important.
Step #3:  Boot up using K/Ubuntu CD, and define partitions
Step #4:  Use Installer to copy from "old" XP to new primary partition (hda1). 
Step #5:  Carry on installing K/Ubuntu as normal - maybe in hdb? :-)

The installer will pick-up XP when it comes to grub-install, and install it alongside K/Ubuntu.

Anyone else got a suggestion?

---

### Post by tonysathre on 2005-10-26
thanks for the advice, after i get a new HDD ill try it

---

### Post by adrianhensler on 2005-10-27
What about if I'm moving Kubuntu from a ata to a SATA; what's the best way to copy  it from a 30 gb ata to a 160gb sata; and then get grub to see it. It will be going from /dev/hdc1 to /dev/sda1 correct?

The system I am talking about is not a dual boot. Maybe I should make my own thread; but it seems related enough.

ajh

---

### Post by Xentex on 2005-10-27
[QUOTE=adrianhensler]What about if I'm moving Kubuntu from a ata to a SATA; what's the best way to copy  it from a 30 gb ata to a 160gb sata; and then get grub to see it. It will be going from /dev/hdc1 to /dev/sda1 correct?

The system I am talking about is not a dual boot. Maybe I should make my own thread; but it seems related enough.

ajh[/QUOTE]

Correct :-)

The trick with installing linux is simple - plug *everything* in to start with (the *opposite* to Windows..), and let the hardware scanner pick everything up.

Somethings it will install by default, or as part of a package (KPilot, CUPS, Ktv, etc) even if you don't have the hardware installed.

Just create a new partition sda1, and copy across from hda1. 
Alternatively, just back up /etc and /home, and then start from afresh.

---

### Post by adrianhensler on 2005-10-27
My question was really how to get grub updated to reflect the new locations of the mount points (ie; hte new swap location; the /dev/hda1 now being /dev/sda1 etc). I don't know how to do that. I haven't tried it yet; maybe it is all automagic? I'll eat my shorts if it is.

---

### Post by tonysathre on 2005-10-31
reinstall grub with the install cd to update grub...thats what i did after i resized my swap and it worked perfectly

---

### Post by adrianhensler on 2005-11-17
Just to follow up on this thread for anybody who might be in a similar boat; it was a pretty easy operation. And; as suggested; reinstalling grub with the install CD was the way to go. I did have some issues with the grub entries not being correct for some reason; but I think I can safely chalk that up to probably user error. (To get the grub entries to work; I had to delete the first line; I'm not sure what happened; but as I said - the end result was that everything worked).

---

