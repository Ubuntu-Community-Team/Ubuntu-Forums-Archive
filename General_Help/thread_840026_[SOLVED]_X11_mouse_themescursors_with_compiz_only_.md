---
title: "[SOLVED] X11 mouse themes/cursors with compiz only partially works"
date: 2008-06-25
forum: General Help
---

### Post by bigdee973 on 2008-06-25
okay im getting really annoyed with my mouse theme constantly changing on me and only working within firefox's environment.  in firefox, as i hover the mouse around and load stuff off the net the custom theme that i have chosen for it works pretty well but however, once i float over to my desktop the theme is totally different and goes to ubuntus default theme im sick of seeing the same on and off effect of switching from my custom theme to ubuntus default theme.  the only time my customize theme works well is when i totally eliminate compiz and put visual effects to none however when i enable compiz i get the problem.  i've been having this problem since ubuntu 6.10 with Beryl and as of today with ubuntu 8.04 i still have not seen a fix for this on any updates.  whats going on? how do i fix this so that it stays permanently to my customized themes without having to turn off compiz

---

### Post by sanus|art on 2008-06-25
You need to restart X (maybe twice even) for the changes to take effect. Unless you tried it already, always worked for me.

---

### Post by bigdee973 on 2008-06-26
> **sanus|art said:**
> You need to restart X (maybe twice even) for the changes to take effect. Unless you tried it already, always worked for me.

no, this absolutely does not work i restarted X (ctrl+alt+BACKSPACE) and restarted computer many many times. like i said i had this problem since ubuntu 6.10.  do i have to install customize theme as root? if so how do i go about doing that? i know for themes to work properly u have to so a command sudo ln -s <directory> is there something like that for X11 mouse themes?

---

### Post by bigdee973 on 2008-06-26
hey nevermind i find the solution to the problem wow its been years for this and here it is [http://ubuntuforums.org/showthread.php?t=620380](http://ubuntuforums.org/showthread.php?t=620380)
its real simple go to system>administration>advanced Desktop effects settings and click general options and in cursor theme write the mouse cursor you want.  by default its DMZ BLACK or something like that.  go to appearance>customize>pointer to find the name of the mouse cursor theme u want and just type in it the cursor theme in ccsm.  and your good to go.

---

