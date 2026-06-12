---
title: "problem burning CDs in Xubuntu"
date: 2007-12-11
forum: General Help
---

### Post by richardy on 2007-12-11
HI,
I am currently running Xubuntu 7.04 on an Asus box and am in the process of migrating to a dell laptop so i want to burn some stuff onto a cd to take across (documents etc). HOwever i keep getting errors when trying to do this (i am using gnomebaker).  Firstly when attempting to burn i get the following error:

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - '&p_error_msg=&p_error_comment=.url=/home/richard/documents/patents/DBSSITEN.Contentp_access_no=&p_error_msg=&p_error_comment=.url'.

I also get an error when trying to access a blank CD in the drive:
"unable to mount volume" even though it has detected what the volume is, and:
"Invalid mount option when attempting to mount the volume."

I also get other errors  such as when trying to eject a CD/DVD:
Failed to eject "/org/freedesktop/Hal/devices/storage_model_HL_DT_ST_CD_RW/DVD_ROM_GCC_4480B".
Given device "/org/freedesktop/Hal/devices/storage_model_HL_DT_ST_CD_RW/DVD_ROM_GCC_4480B" is not a volume or drive.

However i can still access the DVD rom drive and read the contents move files from DVD/CD to hard drive etc

Any help you can give would be much appreciated.

Cheers.

---

### Post by Achetar on 2007-12-11
gnomebaker is most likely your problem. Brasero works wonders with my laptop (XfBurn is OK as well, but Brasero is definately better)

Also, the eject problem is a mystery to me. All I know is that you have to right-click on the CD icon on xfdesktop and click Unmount, then Eject.

---

### Post by richardy on 2007-12-23
Hi,
Thanks for the replay and sorry for not replying sooner.  Your suggestion to use Brasero has fixed the problem i was having, the cdrom itself is still a bit flaky at times but at least i can burn things no problem. So many thanks for your help.

Cheers.

---

