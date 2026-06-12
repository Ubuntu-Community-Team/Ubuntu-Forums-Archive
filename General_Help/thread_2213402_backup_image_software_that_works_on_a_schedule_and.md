---
title: "backup image software that works on a schedule and sends mail?"
date: 2014-03-26
forum: General Help
---

### Post by casper4 on 2014-03-26
Hi all,

I user both ubuntu for desktop and server 12.04 for server stuff.. 

For my Windows servers i use r-drive which is a cheap one buy product that creates and entire image of my servers drives on a schedule and sends me a mail if it went ok or not.. 

I can't seem to find this for linux?

I have looked at like 12 different and commond image backup software for linux and yes they all do image backup but none of them have the capabilities of doing it on a schedule or sent a mail when its done.. maybe im wrong in this i haven't installed them all and looked but i was hoping someone here had a quick answer.. 

Thanks

Casper

PS: I have thought of using DD with Cron and some timestamps but i haven't figured out how to send the mail with it.. and besides I would like something with some support... I like the idea of being able to boot a cd on a crashed server and restore and entire image or maybe boot an entire server from a CD with a image from some time ago..

---

### Post by TheFu on 2014-03-26
Linux is NOT Windows. There is a different philosophy in our OS. Looking for identical solutions will leave you frustrated. Embrace the UNIX-ness of Linux. [http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

In Linux, backups do not need to be images.  Sure, you can make an image, but that needs to be performed from single-user mode (or booted from a USB drive) to prevent file corruption.  Pretty much any backup tool can make a restore-able backup much more efficiently than the image-based solutions. After the restore is complete, just run a grub-install xyz.

The image-based tool that I use is **partimage**, when I need that. It doesn't send emails because it needs to be booted. Sorry.  **fsarchive** can be used similarly, but this doesn't make an image, it makes a file system archive.

Lots of people use **dd** for this too. It is handy when the desire is to mirror 1 HDD onto another, byte of byte. Lots of how-tos exist for that.

For normal backups, I use cron and rdiff-backup. Because it is using cron, an email is produced. The script that is used to run the backup can check the return code from rdiff-backup (or any other backup tool) and print "success" or "failure" as needed. IF there is a failure, the backup will be rolled back during the next attempt.  After all the system backups have finished, another script can be run to check that they all worked easily.

Cron is how things are scheduled on UNIX-like systems - you can schedule almost anything for any time.

Email is sent using the local MTA - if the MTA is installed and properly configured, you can send an email for almost any reason.

Small tools are used, so that the administrator can decide what is used and what is not necessary. It keeps the servers lite - able to run in 100MB of RAM if that is desired. Chain those small tools together to build the total solution desired. It is very powerful.

---

