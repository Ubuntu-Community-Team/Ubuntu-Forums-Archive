---
title: "Windows 10 Update broke Grub"
date: 2017-06-18
forum: General Help
---

### Post by jeremycollins92 on 2017-06-18
Hello, 

My Win10 just ran an update, and it put Grub into rescue mode. Now I cannot boot into either Win10 or Ubuntu 16.04. I am trying to figure out how to repair this, but I'm not having any luck. 

I am using a Live USB and I ran boot-repair, but it did not fix the issues. From the Grub rescue screen, I checked the drives to try and find the boot partition, but every partition comes back as "Filesystem unknown". 

Here is the output of Boot-Repair: [https://pastebin.com/kQBDbNEb](https://pastebin.com/kQBDbNEb)

What can I do in order to fix this?

---

### Post by Bashing-om on 2017-06-18
jeremycollins92; Hello; Welcome to the forum .

Here are the directions to re-install the boot code:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by oldfred on 2017-06-18
Its not the boot loader but the missing partition.
Windows on major updates in BIOS mode, rewrites partition table, and "forgets" to include a logical Linux partition. We consider it a bug but since same issue since Windows 7 came out and is still in Windows 10, they probably think it is a "feature".

       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by jeremycollins92 on 2017-06-18
Thanks for the help! I was able to add the missing partition and get grub working again. It took a few hours and a few tries, but it seems like everything is back to normal!

---

### Post by ajgreeny on 2017-06-19
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

