---
title: "Uninstall Ubuntu and Partition?"
date: 2007-04-14
forum: General Help
---

### Post by nwolf on 2007-04-14
Hi,
  I recently installed Ubuntu 6.10, I believe. I have a Dell Inspiron 8500 with Windows XP. I would like to, if possible, remove the Ubuntu OS and give the partition back for Windows XP use. Is this possible? If so, how? I tried this once before and lost all of my data. So...I need help. :) -Nick

---

### Post by holz on 2007-04-14
There are few ways you can do it. For all you must have your original XP installation CD.
You will need to download the Linux rescue cd which contains a program called gparted, and burn the ISO into a CD.
[http://linux.softpedia.com/get/System/Recovery/System-Rescue-CD-188.shtml]("http://linux.softpedia.com/get/System/Recovery/System-Rescue-CD-188.shtml")
Boot from the CD, and select all defaults. type startx to start an X session, close the terminal and right click, select GParted,  and remove the Linux partition. Click apply then 
Expand your XP partition. Click apply and
Boot from the xp cd into repair mode
select console
run fixboot and answer yes
run fixmbr and answer yes
reboot. If everything goes well, fine. If not:
 Again, boot into the XP cd. Enter the in-place repair.
Do NOT select R the first time you have the option, continue as if you are about to run a new install. Setup will identify your partition and ask you if you want to repair, only then you select R, and let it run. Once completed, you will need to aplly many automatic updates which are now gone due o the repair.
Hopefully it helps.

---

### Post by nwolf on 2007-04-14
Worked perfectly! Thank you holz! -Nick :KS

---

### Post by cham44 on 2007-04-22
the original win xp install cd? all i have is what came with my computer which is the recovery disk which will only restore the computer to its initial state.

---

