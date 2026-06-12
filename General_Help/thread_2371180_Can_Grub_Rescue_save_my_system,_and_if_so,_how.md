---
title: "Can Grub Rescue save my system, and if so, how?"
date: 2017-09-12
forum: General Help
---

### Post by orthoducks on 2017-09-12
I have a system that dual-boots Windows 7 and Ubuntu 16.04, using Grub. Last week I accidentally deleted the Windows partition. I was still able to boot Linux, and continued to use it while I obtained software to recover the Windows partition. I noticed that Windows disappeared from Grub's boot menu.

Today I restored the Windows partition. When I rebooted the system it booted to a "Grub Rescue" prompt instead of the Grub menu.

Please tell me if my theory about what happened is correct: when I booted the system after deleting the Windows partition, Grub noticed that Windows was gone and rewrote its configuration files to load Linux from the Linux partition's new partition number. When I restored the Windows partition the Grub file's entry for Linuxno longer pointed to the Linux partition, and Grub dropped to the command line rather than display an invalid menu.

If that is what happened, I should be able to repair my system by fixing Grub's boot data. I have not had much luck figuring out how to do it, though. The Grub documentation I've found is written for people who already understand Grub, so it doesn't make much sense to me. So, can someone please explain how to use the Grub Rescue prompt to repair the system?

---

### Post by ajgreeny on 2017-09-12
There are several possible reasons for your problem but we need to see the info from Boot-Info script.

See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by orthoducks on 2017-09-12
Thank you for your assistance. Unfortunately I wasn't able to install boot-repair completely.

apt-get displayed "Setting up..." messages for gawk, python-gi, glade2script, boot-sav, boot-repair, boot-sav-extra, and paste-init. Then it displayed the message "bootrepair: command not found" and quit.

---

### Post by BenginM on 2017-09-12
# See: search & set in [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

### Post by oldfred on 2017-09-12
Are you  adding Boot-Repair to the Ubuntu 16.04 live installer you used to install Ubuntu?
That should work if you add ppa and run command to run Boot-Repair.
Do you have Internet working from Live installer?

 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by orthoducks on 2017-09-12
I tried again, and this time it worked (at least enough to run boot-info). It uploaded the information to [http://paste2.org](http://paste2.org), which seems like an impossibly generic URL, but that's all it said.

I don't know if this matters, but the last script I ran appears to have hung. The last thing it displayed was:

[FONT=courier new]/usr/bin/glad2script: 4004: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as appindicator
[/FONT]
It did not return to a command prompt after that.

---

### Post by oldfred on 2017-09-12
Please add above info to this bug report. Only if multiple users post issues does bug move up in repair order.
[https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778)

You can manually copy & paste entire report to a pastebin site and then post the link.
Report is too large to post directly here.

---

### Post by orthoducks on 2017-09-14
OK, thank you. I don't have access to this system from Thursday night through Sunday night, so I'll do it early next week.

---

### Post by orthoducks on 2017-09-19
I reran boot-repair Monday morning. This time it uploaded to the pastebin site as it should. I just came back to see what the response to it was, but instead I found that the message I posted yesterday with the pastebin URL has disappeared.

I just tried to run boot-repair a third time to get another pastebin URL, but now I can't get it to install. When I run "sudo apt-get update," I get the message "AppStream cache update failed."

I'll be frank: I'm starting to wonder if this is worth pursuing. When I started this thread I felt that I urgently needed to repair my system, but it's taken so long that I have had to build a new one to use in the interim. The new one is now about 90% complete, and the missing parts are missing only because I haven't needed them yet. It's debatable whether repairing the original system or finishing the new one would be easier. The original system disk is useless to me as it is, but as long as I'm trying to repair it I can't repurpose it. I feel like I'm pouring time into a black hole.

Please excuse the complaint: I do still want to repair the original disk, if only to learn how. The next time I have an opportunity to work on this problem I'll try to install and run boot-repair again, and with luck it will work.

---

### Post by oldfred on 2017-09-20
If Boot-Repair runs it also tries to save a copy of the report usually in /var/log/boot-sav or with UEFI in the ESP - efi system partition which is FAT32. Sometimes those folders are write protected or hidden and then it cannot save the report.

But we need report or can do back to the old days and ask for you to run each of the many commands it is running.

If you have a new build, it will be UEFI. Be sure to review link in my signature.

---

### Post by orthoducks on 2017-09-20
I found my successful build's URL in my browser history -- I was too exhausted to think of that yesterday. It is [http://paste.ubuntu.com/25569459/](http://paste.ubuntu.com/25569459/).

---

### Post by orthoducks on 2017-09-20
The web site is misbehaving. I posted a reply a couple of hours ago and saw it at the end of the message sequence after I submitted it; then I refreshed the page, and it disappeared and never came back. I was using Quick Reply; perhaps the full-dress Reply page will work better.

I found the URL in my browser history -- I was too tired to think of doing that yesterday. It is [http://paste.ubuntu.com/25569459/](http://paste.ubuntu.com/25569459/).

---

### Post by oldfred on 2017-09-20
That is BIOS/MBR for Windows.
Windows only boots with BIOS with MBR partitioned drives. That has been the same for the last 35 years since PCs were released.
Newer systems in last 5 years are UEFI which recommends the newer gpt partitioning. You can boot Ubuntu with BIOS on gpt, but not Windows.

---

### Post by orthoducks on 2017-09-26
I'm having some trouble understanding your answer because I'm not really familiar with UEFI -- I understand the basic difference between UEFI and BIOS, but I don't grasp all of the implications. If you could restate it and make a point of not leaving out the "obvious" parts, that may help.

Are you saying that somewhere in this sequence of events my disk got converted from MBR partitioning to GPT, but the motherboard is still using BIOS and consequently Grub can boot Ubuntu but not Windows?

If so, the most direct solution would seem to be to convert the disk back to MBR partitioning. I've never tried that but I've got a copy of MiniTool Partition Wizard, and that's one of the operations in its menu.

I think I may have misinterpreted your message because my disk still appears to have MBR partitioning. When I select it in Partition Wizard and click the Disk menu, the "Convert MBR disk to GPT disk" command is enabled, but the "Convert GPT disk to MBR disk" command is not. That also raises the question: if the disk *is* now a GPT disk and I need to convert it back to MBR, how can I do it?

---

### Post by oldfred on 2017-09-26
Ignore UEFI, you have BIOS/MBR.

But your Windows main partition is sda5 which is unusual but still should work if that was what is correct.
Windows normally with MBR(msdos) has a 100MB boot partition as sda1 and main install as sda2. Your main install is sda5. But the extended partition is now sda2 and is just a container for logical partitions. 
If your Windows was sda2 before, converting to a logical may have changed its start by 2 sectors. Could be important or not?
But you would need to run chkdsk from Windows on all NTFS partitions.

You also show no Linux partitions. Often dual booting with MBR, the Linux partition is the first logical or sda5 and swap sda6. If you had a separate /home it usually also is a logical and then order of partitions could be anything.

Often using Windows to upgrade or major repairs will "forget" to write any logical Linux partitions back into partition table. It looks like you have lots of space after your last partition which may have been a Linux partition or two? Again parted rescue or testdisk may show that/those partitions.

---

