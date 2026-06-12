---
title: "rsync problem with 500Gb USB fat32 drive"
date: 2007-01-27
forum: General Help
---

### Post by andy gee on 2007-01-27
I have just bought a 500Gb external hard drive, using USB 2.0, to back up my internal hard drives. It came partitioned as fat32. I had copied a directory over to it already, but I wanted to set up a local rsync cronjob instead to save time.

I tried to use the gui Grsync first, just to see what happened before I messed with cronjob scripts. When it came to the first big file (a knoppix dvd iso) it spat the dummy and gave the following error message:

rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: write failed on "/media/sda1/200g_drive_backup/storage/Linux_isos/ix86/KNOPPIX_V5.1.0DVD-2006-12-30-EN.iso": File too large (27)
rsync error: error in file IO (code 11) at receiver.c(252) [receiver=2.6.8]
rsync: connection unexpectedly closed (2335 bytes received so far) [generator]
rsync error: error in rsync protocol data stream (code 12) at io.c(463) [generator=2.6.8]
rsync: connection unexpectedly closed (312 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(463) [sender=2.6.8]

I tried again using command line rsync: 
rsync -vr /mnt/hdd1/storage/Linux_isos/ media/sda1/200g_drive_backup/storage/Linux_isos/

and got the same problem:
andy@andy-desktop:~$ rsync -vr /mnt/hdd1/storage/Linux_isos/ /media/sda1/200g_drive_backup/storage/Linux_isos/
building file list ... done
extras/
extras/FrugalHowto.pdf
extras/MyDSLhowto.pdf
extras/Packages 2
extras/Packages 3
extras/bogofilter-sqlite_1.1.3-1ubuntu1_i386.deb
extras/gxine_0.5.7-1ubuntu4~dapper1_i386.deb
extras/gxineplugin_0.5.7-1ubuntu6_i386.deb
extras/vum_manual_html.tar.bz2
ix86/
ix86/1.0.13_freespire.iso
ix86/CentOS-4.4-i386-LiveCD.iso
ix86/CentOS-4.4-i386-binDVD.torrent
ix86/KNOPPIX_V5.1.0CD-2006-12-30-EN.iso
ix86/KNOPPIX_V5.1.0CD-2006-12-30-EN.iso.md5
ix86/KNOPPIX_V5.1.0DVD-2006-12-30-EN.iso
rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: write failed on "/media/sda1/200g_drive_backup/storage/Linux_isos/ix86/KNOPPIX_V5.1.0DVD-2006-12-30-EN.iso": File too large (27)
rsync error: error in file IO (code 11) at receiver.c(252) [receiver=2.6.8]
rsync: connection unexpectedly closed (2335 bytes received so far) [generator]
rsync error: error in rsync protocol data stream (code 12) at io.c(463) [generator=2.6.8]
rsync: connection unexpectedly closed (328 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(463) [sender=2.6.8]

I know I can force rsync to ignore IO errors with the '-ignore errors' option, but I still need the files backed up and '-ignore errors' will ignore the files causing io errors.

Any ideas, anyone?

---

### Post by WW on 2007-01-27
How big is the Knoppix DVD ISO file?  The maximum file size supported by FAT32 is 4gig.

---

### Post by andy gee on 2007-01-27
:redface: Ooooops! Do I feel like a dummy! An RTFM case if ever there was one. Thanks very much for taking the time to answer. Now if I can just get the fat32 formatted to ext2 - guess I'd better ask someone: [http://ubuntuforums.org/showthread.php?t=347402](http://ubuntuforums.org/showthread.php?t=347402)

Thanks again,

andy gee.

---

