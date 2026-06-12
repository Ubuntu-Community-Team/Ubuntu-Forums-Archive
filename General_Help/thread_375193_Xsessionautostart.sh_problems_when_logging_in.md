---
title: "Xsession/autostart.sh problems when logging in"
date: 2007-03-03
forum: General Help
---

### Post by jseiser on 2007-03-03
Im on 6.10
When i log into the openbox autostart session i get the error "xsession unable to launch "/home/justin/.config/openbox/autostart.sh Xsession---"/home/justin/.config/openbox/autostart.sh not found; falling back to default session.  

It does this only when logging into the autostart, i can log into a normal openbox session and then run my autostart or run it from the menu and it works fine.  

here is my autostart

#!/bin/sh
# Auto-mounting drives
gnome-volume-manager &
# GTK themes... this is just one method
gnome-settings-daemon &
# Full paths never fail...
feh --bg-scale /home/justin/hendrix & 
pypanel &
# This prevents the panel from failing if it loads too fast
if pgrep pypanel
then exec openbox
else pypanel && exec openbox
fi


My only other question is what is the command to launch nautilus with no gnome? just the file browser, and do i have to run it as a sudo command? if so can i put the password in the command somewhere? ie sudo password nautilus --no-desktop? or something to that effect?  Thanks all.

---

### Post by jseiser on 2007-03-05
I think it may be a problem with my file permissions, i cant delete a java folder because i don't have permission.  So maybe the permission on that file is wrong also?  How would you change it?

---

### Post by Graduate on 2007-03-06
chmod +x ~/.config/openbox/autostart.sh

I had the same problem you had, and I fixed it by using ~/.xsession, but I can't seem to find the tutorial I followed. But I think the filename doesn't matter, so the permission thing should be the only problem.

---

### Post by jseiser on 2007-03-07
thanks ill try that.  but i think i already tried to do that form the original thread i saw on how to install openbox.

I tried that and it didnt work :(

---

