---
title: "Help with ksetisaver (seti screensaver)"
date: 2006-10-29
forum: General Help
---

### Post by kwilliam on 2006-10-29
Hi.  I'd really like to use ksetisaver ([http://www.kde-look.org/content/show.php?content=1055](http://www.kde-look.org/content/show.php?content=1055)) on my Kubuntu desktop. However, ksetisaver depends on an old version of Seti@Home (setiathome) that is no longer supported because the Seti@Home project migrated to the project independent BOINC platform. I've successfully installed boinc-client and boinc-manager and got the Seti@Home project running, but the screensaver can't find the right data to display the project details. Is there a newer version of ksetisaver available, or is there a way I can get ksetisaver to work with the BOINC version of the Seti@Home program?

Yeah... I know this is a kind of bizaire request... I installed Folding@Home on the family's other desktop (An XP box that sits around for hours without being used) and thought I'd support a different cause on my desktop.

---

### Post by autocrosser on 2006-10-29
Well-I can't help with exactly what you want---but, if you goto the Debian Wiki ( [http://wiki.debian.org/BOINC](http://wiki.debian.org/BOINC) )--there is a way to show the Graphic part of the data unit you are working on--I've had this work (but not lately with Edgy--worked in Dapper--I'm looking into why)

From the Wiki:

**Graphics**

  Graphics **are** supported, but they won't show up by default. The X display needs to be accessible to the BOINC graphics processes in order to see the interesting graphics for, e.g., Einstein@Home, and it isn't by default. 
 Your X display can be made accessible to all local UNIX socket connections, including the ones from BOINC, by running  
 xhost +local:
This is generally safe on single-user machines, though not ideal. It is a bad idea on multi-user machines, so don't do it there. 
 Then, the "Show graphics" button in boincmgr, or the --result ... graphics_window option to boinc_cmd, will actually work. Unfortunately, when it doesn't work because of failed X authorization, it does not report the error back to boinc_cmd or boinc_mgr, and the only trace of the error is in some log file in the result directory /var/lib/boinc-client/slots/<whatever>.

I've also talked to the designer of Xscreensaver & he would be very interested in the way to get Xscreensaver to display Boinc data----

---

