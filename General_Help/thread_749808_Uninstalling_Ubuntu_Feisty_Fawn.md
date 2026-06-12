---
title: "Uninstalling Ubuntu Feisty Fawn"
date: 2008-04-08
forum: General Help
---

### Post by Laxrawr on 2008-04-08
I cannot figure out how to do it. I have dual booted it with Windows XP Home Edition. I am next to useless with linux, decent with windows. I decided to install it since I figured that I could dual boot it and everything would work fine once I got internet up and running on linux. WRONG. Installing linux made my internet connection not work on windows, since it wouldn't let me access an IP adress. Another question, uninstalling linux will take away the linux partition, giving me the access to that memory on windows, correct? By the way, I know about QTParted, and it wont install on my computer since "The vendor choose not to support my computer."

Any and all help is appreciated. Thanks in advance.

---

### Post by sekinto on 2008-04-08
You can delete the Linux partition and resize your Windows partition from a live CD using Gparted or whatever other program you want to use.

Although I'm sure we could help you fix your internet connection problems if you told us what they are.

---

### Post by Crushyerbones on 2008-04-08
First of all, I'm no expert but I can't see any reason for Linux to screw your network drivers on windows.

Restoring windows is a simple matter of replacing grub with window's mbr. A quick search of fix mbr will show you, but before you do that you should restore the partition to ntfs (or whatever you'd like)

How did you partition the disk in the first place btw?

---

### Post by Laxrawr on 2008-04-08
Ok, thank you. So I can uninstall via the cd? 


::EDIT:: I partitioned the hard drive using the program Linux uses when it installs. I have no idea what the said program was. I'm making the assumption that linux messed with my internet since it happend soon after I installed Linux. I am not the only one who uses wireless internet in my house, but I am the only one with linux and a broken interweb connection.


This is the problem with my internet btw.

I have WUSB300N (this is for windows btw, I know what I need to do to get linux internet up). When I first log on to windows, the little internet connection wireless thingy says everything is good and normal. Then the little warning sign pops up. (Just for future reference, I open Command Prompt and do the ipconfig deal to get that info) I right click, scroll up to "repair" and click it. The repair window pops up, flys through everything then stops a "Renewing your IP adress". After a little while it says "could not renew your IP adress". So I open up the Linksys icon in the tray at the bottem, go to "edit profiles" and type in the IP adress and gateway info, hit "save changes" and then connect. Now, the little icon in the tray says all is good and clear. I open up Firefox, doesn't connect. I ping my IP adress, lose all the data packets. Lather, Rinse, Repeat. Restarting my computer and my internet router/modem changes nothing.

---

### Post by sekinto on 2008-04-08
Okay, Linux wouldn't mess up networking in Windows. You could try setting a static IP address for your computer, and if there are newer drivers for your wireless card then upgrade.

---

### Post by Crushyerbones on 2008-04-08
Ok, all you need to do is pop your windows cd and do this:
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

I hope you're talking XP because I have no experience with vista :P


if you need your hard drive back and gparted doesn't seem to work, then just do as you would to install linux. When it asks you about partitions select the one which is partitioned as ext3 and reformat it as ntfs.

Someone should also tell you if windows needs a swap because I really can't remember :lolflag:

---

