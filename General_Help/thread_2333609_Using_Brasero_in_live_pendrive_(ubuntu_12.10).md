---
title: "Using Brasero in live pendrive (ubuntu 12.10)"
date: 2016-08-11
forum: General Help
---

### Post by anon_private on 2016-08-11
Using Ubuntu 12.10 live

I tried to burn some folders in my home directory using Brasero.

All seemed to go well, but at the end I received and error message that some files were corrupted. I have tried to view the DVD RW in a variety of programmes, including Windows Explorer on a Windows machine, but I can see no files, yet according to properties in Windows it is full.

How can I view in Ubuntu 12.10 what is on the disk?

Since I am working using a live pendrive at present, I cannot save files, but I copied the last lines of the Brasero log:

BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom Finished track successfully
BraseroReadom called brasero_job_get_done_tracks
BraseroReadom called brasero_job_get_fd_out
BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroReadom deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) b0de676afc774604c757e94c1f1a5ae6 (458a36938a75e76fb5fd1a4bfa8d78e5 before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
    error        = 27
    message    = "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record brasero-burn.c:2856)

---

### Post by Geoffrey_Arndt on 2016-08-11
Hello Anon . . . . to live up to that glorius hacker name, . . . let's get with the program!

Ubuntu 12.10 is long past EOL (end of life) and the repos are not active any more.    No telling what works and what doesn't.    So, do this"

>   Download Ubuntu 16.04 LTS (Long Term Support) from the official Ubuntu website
>   Create your bootable media (DVD or USB Flash-stick)

**EDIT:**   just noticed your installed system is 14.04 KDE . . so disregard below, but booting from a new version of the Live OS is still the proper place to start.

>   Install 16.04 over 12.10 (after first securing your data - - copy data to another external drive)
>   Re-install 16.04.   This version (Xenial Xerus 16.04.1) is supported until Spring of 2021.

Happy Computing!!!

---

### Post by ajgreeny on 2016-08-11
It looks as if you are still misunderstanding the uses of brasero as you did in a thread which I answered previously, see [https://ubuntuforums.org/showthread.php?t=2332397&p=13525005#post13525005](https://ubuntuforums.org/showthread.php?t=2332397&p=13525005#post13525005)

I repeat this for you once more; brasero is used for burning writeable or re-writeable CDs and DVDs, not to copy or "burn" as you call it, any files or folders to a USB pendrive.

Once again, however, I am not certain what you are trying to do so please tell us and somebody will try to help you.

---

### Post by anon_private on 2016-08-11
> **Geoffrey_Arndt said:**
> Hello Anon . . . . to live up to that glorius hacker name, . . . let's get with the program!

Ubuntu 12.10 is long past EOL (end of life) and the repos are not active any more.    No telling what works and what doesn't.    So, do this"

>   Download Ubuntu 16.04 LTS (Long Term Support) from the official Ubuntu website
>   Create your bootable media (DVD or USB Flash-stick)

**EDIT:**   just noticed your installed system is 14.04 KDE . . so disregard below, but booting from a new version of the Live OS is still the proper place to start.

>   Install 16.04 over 12.10 (after first securing your data - - copy data to another external drive)
>   Re-install 16.04.   This version (Xenial Xerus 16.04.1) is supported until Spring of 2021.

Happy Computing!!!

I am only using 12.10 because I have had a crash and only have the use of 12.10 on a live pendrive. Actually, when I finally install an OS it will be kubuntu 16.04 or 16.04.1

This thread relates to the use of Brasero

> **ajgreeny said:**
> It looks as if you are still misunderstanding the uses of brasero as you did in a thread which I answered previously, see [https://ubuntuforums.org/showthread.php?t=2332397&p=13525005#post13525005](https://ubuntuforums.org/showthread.php?t=2332397&p=13525005#post13525005)

I repeat this for you once more; brasero is used for burning writeable or re-writeable CDs and DVDs, not to copy or "burn" as you call it, any files or folders to a USB pendrive.

Once again, however, I am not certain what you are trying to do so please tell us and somebody will try to help you.

I was trying to burn folders from my home directory to a DVD-RW ( I am usinmg a live pendrive as the OS). However, I received an error notification from Brasero, see the last few lines of the log (above). I cannot see any files on the DVD-RW, but a lot of space has been used. Any suggestion that might help me view the disk.

The link that you have refered to is concerned with the very long boot time that I noticed with version 16 (kubuntu)

---

### Post by howefield on 2016-08-12
I believe that around that time (12.10) Brasero was guilty of producing coasters all too often instead of usable media. It is much better now and although I seldom use CD/DVD these days it has been a few years since Brasero failed on me.

I'd suggest installing xfburn and create your backup with that instead of Brasero. Obviously, unless you have persistence on the Live 12.10 xfburn will be lost on shutdown. 

Preferably, one would create a new pendrive with a more current release on it, but if you cannot do that...

---

### Post by anon_private on 2016-08-12
> **howefield said:**
> I believe that around that time (12.10) Brasero was guilty of producing coasters all too often instead of usable media. It is much better now and although I seldom use CD/DVD these days it has been a few years since Brasero failed on me.

I'd suggest installing xfburn and create your backup with that instead of Brasero. Obviously, unless you have persistence on the Live 12.10 xfburn will be lost on shutdown. 

Preferably, one would create a new pendrive with a more current release on it, but if you cannot do that...

Producing coasters - that I can believe.

I will try you suggestion

Best wishes

---

### Post by kurt18947 on 2016-08-12
Brasero did indeed have 'issues' for a period of time though it seems better on 16.04.X. I also second XFburn, it's a simple unadorned CD/DVD burner. K3B is the most polished and functional burner native to KDE but I've used it on non-KDE installs. It just brings a bunch of KDE dependencies in but I have been unaware of any interference.

---

### Post by anon_private on 2016-08-13
Thank you

---

