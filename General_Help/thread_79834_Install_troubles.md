---
title: "Install troubles"
date: 2005-10-20
forum: General Help
---

### Post by mustafu on 2005-10-20
Hello everyone,

I'm currently attempting to install Kubuntu on a empty 3 GB disk in my machine.
I have 3 HDs - WinXP on my pri. master, the empty one as my pri. slave, and another drive for data as a sec. slave.

During the install, I wanted to custom partition using XFS.  I then manually
created partitions and created a 3GB one (XFS) as /.   I then created a 200+meg partition for swap on the same drive.  The installer had some options that I did not understand, so I more or less guessed on the correct values.  
I set the 'bootable' flag to on and went on with the install.  

The installer then wanted to install LILO.  There was 3 options: install in the mbr, install on the Kubuntu partition, or manually select location.  The first time I tried to install, I chose to install in the mbr.  In the reboot following the installation, it just still just the WinXP bootloader there, no LILO.

So, I tried again to install using the same partitioning scheme and, on this attempt, I installed LILO to /dev/hda (my WinXP drive, I assumed), and on the reboot following that installation, LILO was there, and seemed like it was going to boot, but I got dropped to a command line and the install didn't finish.

I then reinstalled the WinXP bootloader and haven't attempted to install since.

Is there any way I could get this to work properly?  Am I missing something, or...?  Any help would be much appreciated.

My system is a Pentium-2 400 with 384 MB RAM with the hard disk setup described above.

Thanks,

Chris

---

