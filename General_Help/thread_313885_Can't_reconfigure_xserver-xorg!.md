---
title: "Can't reconfigure xserver-xorg!"
date: 2006-12-06
forum: General Help
---

### Post by madcow72 on 2006-12-06
The scroll wheel on my mouse stopped working the other day, and I would desperately love to get it going again.  I've changed out mice to make sure the problem isn't hardware specific.  The easiest way, (I figured), to restore the mouse to its original state was to run:```
sudo dpkg-reconfigure xserver-xorg
```
Unfortunately, I keep getting the following response: 
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061205132258
dexconf: error: cannot generate configuration file; shared/default-x-server not
set.  Aborting.  Reconfigure the X server with "dpkg-reconfigure" to correct
this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
```

Any ideas?

---

### Post by bapoumba on 2006-12-07
Not sure though ...
From dexconf error message :
> cannot generate configuration file; question not set
              An  answer to the indicated question was expected in the debconf database, but none was found.  dexconf cannot write a valid configuration  file  without this information.  This problem can be rectified  by  reconfiguring  the  X  server  package  with  the              dpkg-reconfigure(8) command.

[dexconf manual]("http://kjell.haxx.se/man/man.cgi?page=dexconf&section=1")
May be you missed one answer in **sudo dpkg-reconfigure xserver-xorg** ?

---

### Post by madcow72 on 2006-12-07
Hey Bapoumba!  Thanks for the suggestion, but no, I didn't miss any answers, debconf just quits after the step asking for 24 bit depth and write sync ranges to config file... I'm putting the horizontal and vertical syn ranges in correctly, I'm quite sure of that (Dell E193FP H: 30-82kHz  V: 56-76kHz - Dell Website) but debconf just quits immediately after.  

I did realize that logging out of X and going into the command prompt allowed me to get all the way through the reconfiguration however...So I guess that solves the problem of reconfiguring X!  

Also, I was able to solve my mouse problems by setting up support for multiple buttons using the guide here: 
[http://ubuntuforums.org/showthread.php?t=3828]("http://ubuntuforums.org/showthread.php?t=3828")

I consider my problems solved at this point!

---

### Post by bapoumba on 2006-12-08
@ madcow72 : well, I should have done a little more thinking  ;)
That was a good idea to reconfigure xserver-xorg with no X session running. Some files are locked when used. Thumbs up :)

---

