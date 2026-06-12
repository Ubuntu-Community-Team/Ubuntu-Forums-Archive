---
title: "System impossibly slow"
date: 2016-05-15
forum: General Help
---

### Post by ccdavis77 on 2016-05-15
Hello-
I am running Ubuntu Trusty 14.04.3 on my HTPC installed on a 2TB hard drive mounted in the front bay. I use it to run Kodi media center and all of a sudden, it has gotten so slow that it is basically non-operational when trying many functions while it seems ok when accessing others. A prime example of this is Addon Installer. Trying to run the add on installer Leads to the progress wheel spinning for minutes at a time, often causing it to lose connection with my remote and requiring a hard reset.  Tried to delete and re-install, just hangs on "Installing add-on..." Dialog box and nothing happens, again requiring a hard reset.
 
There is no problem accessing local media (located on the same drive, for now...).  I did a check disk, says the disk is OK and my internet connection seems fine. My question is, could this be a problem with the drive despite the check disk function saying it's OK? I'm thinking of replacing it with a SSD but don't want to spend the $ if that's not the problem. Any help would be much appreciated, I'm stumped!!!

---

### Post by Geoffrey_Arndt on 2016-05-15
Did you check if your server connection is still functional . . are updates still coming across?   One way to check is via software & updates in system setting - - check the "download from" and do a search for fastest server.   Another possibility - - is the ubuntu partition running low on disk space?

---

### Post by QIII on 2016-05-15
Is this when you attempt to install Kodi add-ons?

What happens when you do Ubuntu updates?

The question here is whether your difficulty is arising from the OS or an application.

---

### Post by ccdavis77 on 2016-05-16
Thanks. I did check and change the server and it didn't seem to make any difference. Using the "df -Th" command my dev/sda1 is at 65%, all the rest are at 1% or 0%. Don't think it is just Kodi because "sudo apt-get update" used to be very quick, now takes a long time as it hangs up and says "connecting". Does eventually finish though.

---

### Post by ccdavis77 on 2016-05-23
Any ideas as to where I can go from here? Thanks!!

---

