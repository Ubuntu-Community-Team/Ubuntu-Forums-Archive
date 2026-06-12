---
title: "[SOLVED] Adept Manager problem"
date: 2008-06-05
forum: General Help
---

### Post by solidus126 on 2008-06-05
Hello all.  I have been running into a few problems with Adept and package management in general.  Lately, I have tried installing a few different packages, with adept only to hang up on me when it neared completion.  

Something I had tried in the past was to issue the command ```
sudo dpkg --configure -a
``` and it would clear out my problems (heard about it in another thread), but now it runs into problems too.  Any suggestions? I am using kernel 2.6.24-18-generic.  Here is the terminal output from running the command.

```
solidus126@lappy486:~$ sudo dpkg --configure -a
[sudo] password for solidus126:
dpkg: status database area is locked by another process
solidus126@lappy486:~$ sudo dpkg --configure -a
Setting up cupswrapperhl2040 (2.0.1-2) ...
ERROR : Brother LPD filter is not installed.
/usr/local/Brother/cupswrapper/cupswrapperHL2040-2.0.1: 64: cannot create /usr/share/cups/model/HL2040.ppd: Directory nonexistent
chmod: cannot access `/usr/local/Brother/inf/brHL2040rc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ]
cp: cannot stat `/usr/share/cups/model/HL2040.ppd': No such file or directory
dpkg: error processing cupswrapperhl2040 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperhl2040
solidus126@lappy486:~$ lpadmin: No such file or directory

```

Also, I have one more question.  I am going to have to reformat my Windows partition and reinstall XP since a virus recently destroyed it.  My partition table has a really small ~50MB partition, followed by the Windows partition ~20GB, and then by my Kubuntu ~60GB and the swap partition for it.  Currently the 50MB partition is assigned sda1, XP is sda2, and Kubuntu sda3. Is it safe to eliminate the small 50MB partition, and tack it on to the new Windows partition, and Kubuntu would have no problem booting up next time (other than having to edit my GRUB menu)?

Thanks!
-solidus126

---

### Post by solidus126 on 2008-06-06
bump

---

### Post by solidus126 on 2008-06-16
Hello all.

It seems that something went wrong during the installation of my printer, but I do not know what.  Can anyone point me in the right direction?  This problem has been rough, I am having a hard time trying to update any of my packages. X is crashing when Adept gets nearly complete, and even command line install hiccups.

Thanks for looking...

-solidus126

---

### Post by solidus126 on 2008-06-24
Hello all.  I have resolved the issue thanks to #kubuntu on freenode irc.  Here is the conversation that pointed me in the right direction (major kudos to those whom helped!).

```

01[15:00] <solidus> http://ubuntuforums.org/showthread.php?t=819973

01[15:00] <solidus> http://www.linuxforums.org/forum/ubuntu-help/123307-adept-manager-problem.html

[15:04] <BluesKaj> ok solidus , sudo fuser -vki /var/lib/dpkg/lock , then sudo dpkg --configure -a , then sudo apt-get update

01[15:05] <solidus> ok, could you post to one of the forums if you don't mind?  I am on campus and have to use a proxy to get an IRC connection through windows, and I will have to reboot

[15:06] <da1l6> solidus, cupswrapperhl2040 is not an kubuntu package.  i suggest removing it and try the hl2060 driver: http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2040

01[15:08] <solidus> ok all, I am going to reboot and see what I can get done, thanks for your help so far.  Will report back soon


```

I followed their advice, and installed the HL-2040 driver from the Brother driver page (using the .deb package).  After some tinkering and experimentation, it appears that everything is back to normal.

Thanks everyone!

-solidus126

---

