---
title: "Dual Boot Problems with Windows 8"
date: 2016-05-14
forum: General Help
---

### Post by matey3 on 2016-05-14
Hi:
I was dual booting with Ubuntu 12.04 and Windows 7 on my Asus Laptop (I hate it bcs they moved the keyboard etc.etc. but has Intel 2.4 GHz core, 3 GB RAM and 400 GB HDD).
What happened I upgraded from win7 to win8 but then while upgrading to Windows 8.1 I had to reboot but then my laptop would not boot neither to Win8 nor to Ubuntu 12x. 
I got this HDD hardware error at boot up and nothing fixed it. I ran chkdsk /whatever to fix errors etc, many times and many months but nothing helped so I left the dumb thing alone for over a year then one day I booted it and ran chkdsk again and bingo it fixed it. I could go to Win8.1 but my Ubuntu was ruined! :( 

My question is how do I get in my Ubuntu or activate its startup boot menu so I could get in as Admin user and fix it? I thought all Ubuntu installations gave you that menu where you could go into diff. modes (eg. such as in safe mode etc.)
I hate to lose my partitionless Ubuntu since I used the (now defunct) Wubi and at the same time I don't want to lose my (now) Windows 10.

Thanks for any ideas...
Best Regards;

---

### Post by oldfred on 2016-05-14
If you installed wubi inside Windows, that may be gone. It is just a file inside Windows.
And last supported version of wubi was 12.04.

       Forums Staff recommendations on WUBI
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]http://ubuntuforums.org/showthread.php?t=2229766
[/URL]
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Normally wubi installed a boot  entry into Windows BCD, that for sure would have been erased as Windows 8 created a new BCD.
And Windows 8 fast start up may interfere with wubi installs also. 

 

    [URL="http://ubuntuforums.org/showthread.php?t=2229766"]
[/URL]

---

### Post by grahammechanical on 2016-05-14
> I thought all Ubuntu installations gave you that menu where you could go into diff. modes (eg. such as in safe mode etc.)

That is true provided the Linux boot loader (Grub) is showing a menu. If the upgrade to Windows 8.1 replaces the Grub boot loader with a Windows boot loader then the Grub menu option to load into recovery mode has also be gone. 

Anyway, wubi is not compatible with Windows 8/10. 

Regards.

---

### Post by matey3 on 2016-05-17
Thanks very much for the reply and the links!


> **oldfred said:**
> If you installed wubi inside Windows, that may be gone. It is just a file inside Windows.
And last supported version of wubi was 12.04.

       Forums Staff recommendations on WUBI
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]http://ubuntuforums.org/showthread.php?t=2229766
[/URL]
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Normally wubi installed a boot  entry into Windows BCD, that for sure would have been erased as Windows 8 created a new BCD.
And Windows 8 fast start up may interfere with wubi installs also. 

 

    [URL="http://ubuntuforums.org/showthread.php?t=2229766"]
[/URL]


And thank you also for your reply!
I know I had a lot of problems with windows 8 and later learned from MS own site that upon upgrading to 8, it wiped out all the backup files of previous version and made a big mess. So I am not sure if I really had a hard drive problem like it said...
but everything is all right with win10 and I am going to reinstall Ubuntu again. 
Thanks to you guys for your help!
> **grahammechanical said:**
> That is true provided the Linux boot loader (Grub) is showing a menu. If the upgrade to Windows 8.1 replaces the Grub boot loader with a Windows boot loader then the Grub menu option to load into recovery mode has also be gone. 

Anyway, wubi is not compatible with Windows 8/10. 

Regards.

---

