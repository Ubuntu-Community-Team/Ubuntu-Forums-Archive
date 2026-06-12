---
title: "(SOLVED) Win 10 SSD doesn't show up under linux"
date: 2018-10-30
forum: General Help
---

### Post by luisseyfer on 2018-10-30
Hello,

I used to backup my Windows C drive with ntfsclone.
I just got a new laptop [Lenovo  IdeaPad Y910 512GB SSD, Windows 10 Home.]("https://deref-1und1.de/mail/client/uRgq7GdD5PM/dereferrer/?redirectUrl=https%3A%2F%2Fwww.amazon.de%2Fgp%2Fr.html%3FC%3D3ILR4VQSVD3HI%26K%3D1BGK00Z0DQJ7B%26M%3Durn%3Artn%3Amsg%3A20181025072213524df7a0bf1c4bdb97881ceeb590p0eu%26R%3D15IVG10HE73RV%26T%3DC%26U%3Dhttps%253A%252F%252Fwww.amazon.de%252Fdp%252FB01N4M6VIG%252Fref%253Dpe_3044161_185740101_TE_item%26H%3DYAYWR40FADBJZN13NE6HWFWYFAUA%26ref_%3Dpe_3044161_185740101_TE_item")
Unfortunatly I can't see none of the internal partitions at all. 
For example, in GParted the only Disk I can select to show the partitions and manipulate them is the flashdrive with the Linux I booted from.
Normally I use [Desinfec't]("https://www.heise.de/download/product/desinfect-71642") (a cutomized Ubuntu) for the job, but under Knoppix 8.2 it's the same.

The problem seems similar to this:
[https://ubuntuforums.org/showthread.php?t=2380454](https://ubuntuforums.org/showthread.php?t=2380454)
So, my first attempt was "powercfg –h off" as recommended in the thread, but to no avail.

Any ideas what could cause this are welcome.

---

### Post by oldfred on 2018-10-30
In addition to Windows fast start up off, many systems now use RAID or Intel SRT. You have to change drives to AHCI, but is still booting Windows install the Windows AHCI drivers first.
Also many new systems still need UEFI updates and SSD firmware updates.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Issues often common across multiple models of a brand as same UEFI used, with just minor changes for options. Bigger difference if Intel or AMD.
       
 Lenovo Y700 Ideapad Windows 10 & Ubuntu SSD & HDD
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)
Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)

---

### Post by luisseyfer on 2018-11-06
Thank you oldfred,

this was a pradox situation. Normally creating a backup is the first todo after getting a new mashine for me.
I had to find a backup-tool for windows first. Since I am too lazy to look if it's aloud to give hints about products:
If you're looking for such a backup-tool please, send me a PM.
One has to switch to AHCI anyway in order to get access to the internal disk.

For the the actually change to AHCI I followed this:
[http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)
In paragraph 4 I switched also legacy boot on.

---

### Post by oldfred on 2018-11-06
Not sure if you should have legacy boot on. Some before did need it, but most systems it should be off, so you still boot in UEFI mode.
You do not want to boot in BIOS/CSM/Legacy mode.

My Dell wanted a Dell backup, a Windows backup & I did a full backup with Macrium Reflect.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

