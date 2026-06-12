---
title: "Brother MFC5840CN driver install"
date: 2008-03-17
forum: General Help
---

### Post by Randy Wells on 2008-03-17
Hi Ubuntu gurus.... Randy here...

I just blew off WinXP on my wife's computer.  She doesn't need a lot of stuff and my son recommended Ubuntu.  I have a [COLOR="Blue"]Brother MFC5840CN [/COLOR]on my lan as a network printer.  I've downloaded and ran the installation on the [COLOR="Blue"]lpd[/COLOR] and [COLOR="Blue"]cupwrapper[/COLOR] drivers.  I still can't figure out how to get the darn printer installed!

The drivers are in [COLOR="DarkRed"]/usr/local/Brothe[/COLOR]r.  There are the cupwrapper, inf, and lpd files.  What does it take to get them recognized with the "Add Printer" wizard?  My Unix/Linux is a bit rusty.  It's been 2002 since I've seriously worked with the OS's.  I've forgotten a lot since then.

I went to [COLOR="Blue"]http://localhost:631[/COLOR] to install the printer but didn't get anywhere there either.  It wanted a user name and password for CUPS.  I gave it root and the root password but it didn't like it.  My personal login, which has admin rights, but  doesn't work either.  I checked in "Users and Groups" but the only user close to CUPS was "cupsystem".  That login didn't work.  Maybe I just don't need for her to use the lpr.  It would be nice, though.

Anyhow, any help getting this printer installed would be greatly appreciated....

Thanks!

Randy

---

### Post by DoctorMO on 2008-03-17
If cupwrapper is anything like ndiswrapper then you'll need to register the inf file with cupwrapper.

at a guess:

```
sudo cupwrapper -i brother.inf
```

As for cups, you need to enable network printing from the printing administration in order to be able to get access to cups on port 631; Although these isn't a point in going to 631 unless your using it as a networked printer.

---

