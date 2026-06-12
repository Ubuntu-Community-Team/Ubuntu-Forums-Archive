---
title: "Making script run at boot/resume"
date: 2007-06-13
forum: General Help
---

### Post by jazzgossen on 2007-06-13
I have looked around, but I haven't found a working way to get a script to run at boot or resume. 

Specifically, I want to make sure that hdparm sets the spin-down time on my hard drives. Whatever I put in hdparm.conf doesn't have any effect, so I thought I'd try to make a script with the required hdparm commands in it. I put the script at /etc/acpi/resume.d/95-hdparm.sh and made it executable. But it still doesn't run when I resume from hibernation. It works as it should if I run the script manually, though.

How can I make a script that runs at every boot and resume?

---

### Post by dominator22 on 2007-06-13
To run a script at boot time, place it in /etc/rc.local and make the file executable.  rc.local will be run as the last script.  If you want to run the script earlier, place it in /etc/init.d/ and add a symlink to it in  /etc/rc2.d/

---

### Post by jazzgossen on 2007-06-20
I have put the stuff that I want to run at startup in /etc/rc.local, but it still doesn't get executed when I resume from hibernation. 

Anything else I could try? How does /etc/acpi/resume.d work? What mechanism controls which of those scripts that are executed? Shouldn't it be enough to put an executable shell script in that directory? Where can I find more info on this?

---

### Post by dominator22 on 2007-06-20
/etc/acpi/resume.d/ is a directory containing scripts to be run on resume.  The numbers at the beginning of the script file name denote the order the script should be run in.  

One good way of getting what you want done is create a script in /etc/acpi/resume.d/ to run it on resume, then also run it from within /etc/rc.local

To run a script that's in a separate file from rc.local just place the /full/path/to/script on a separate line.  
Example: 
```
/etc/acpi/resume.d/myscript
```

Make sure you set the executable bit on the script and rc.local.  

sudo chmod +x /path/to/script

If you don't want to place your script in /etc/acpi/resume.d/ place it somewhere else and create a symlink to it.  
An alternate location is /etc/init.d/ then create symlinks to the script in /etc/rc#.d/ (AND any anywhere else you want, including /etc/acpi/resume.d/)

---

### Post by jazzgossen on 2007-06-28
In fact, it seems that none of the scripts in /etc/acpi/resume.d are executed. Not the one I put in, nor the one that were already in there. I edited some of them to echo something to a file in my home directory when they are executed. The stuff in /etc/rc.local works when I reboot, but not on resume. Hmm...

---

