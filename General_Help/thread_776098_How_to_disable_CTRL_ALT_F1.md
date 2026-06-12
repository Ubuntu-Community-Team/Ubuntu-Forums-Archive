---
title: "How to disable CTRL ALT F1"
date: 2008-04-30
forum: General Help
---

### Post by Tsu Dho Nimh on 2008-04-30
I want to prevent the terminal from opening with CRTL ALT F1 because it interferes with some (brane-ded) software that uses the same keys to enable and disable the software GUI.

It would normally be done by commenting out a line in inittab 

I have no inittab ... what do I have to do to the files in /etc/event.d to prevent a terminal from opening when I press CTRL ALT F1

Step by step please.

---

### Post by Tsu Dho Nimh on 2008-05-02
Uh ... no answers?

---

### Post by cumulus007 on 2008-10-19
Hi,

This may be strange, answering to a very old topic, but you have to add this to the xorg.conf file:

```

Section "ServerFlags"
Option "DontVTSwitch" "true"
EndSection

```

---

### Post by nagios on 2009-01-14
That's exactly what it was, the:

Option "DontVTSwitch" "true"

in the xorg.conf disabled this option. Thanks!

---

### Post by mwalimu54 on 2009-11-19
just what I was looking for.  I might note that in Karmic the xorg.conf file doesn't exist (if you haven't created it yet) so you'll have to create a blank file in the proper directory and and the previously mentioned lines.

---

### Post by supreme commander on 2011-07-26
I have found the file xorg.conf but it is read only. what do I do:confused:

---

### Post by vxp2006 on 2011-07-27
hey
 
The xorg.conf is not for regular user to edit and save.
 
1. Copy that file to your home directory  ( cp /etc/X11/xorg.conf /home/user1/.... ) 
2. edit and save in your user directory
3. copy it back to the /etc/x11 directory ( sudo cp /home/user/xorg.conf /etc/x11 ) 
 
done.
 
btw, thanks to the previous post about how to disable ctrl-alt-f1.  I've been looking for it for weeks.

---

