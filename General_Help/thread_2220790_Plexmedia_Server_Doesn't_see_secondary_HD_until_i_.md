---
title: "Plexmedia Server Doesn't see secondary HD until i click it via GUI"
date: 2014-04-29
forum: General Help
---

### Post by romeov007 on 2014-04-29
Hello,

If this is posted else where then I apologize as I was not able to locate it.  My problem is I have a plex media server, when the linux box needs to be rebooted I have to remote in via VNC and actually open the secondary HD from the file manager before the plex media server will see it.  I also noticed that I cannot see it from the SSH terminal either until it's clicked from the GUI.  The Drive options are set to auto mount and it has no problem from the gui.  Ideally I would like it to boot up and be ready to go.

Any idea as to where I'm going wrong with this?  

Thank you. 


Using Ubuntu 12.10 Desktop Edition.

---

### Post by Groodles on 2014-04-30
Are you using the automount function in the desktop environment or is it specifically mounted via /etc/fstab ?

If you're mounting from the desktop, then the behaviour is normal.  The OS will mount a volume on demand, this is more usual for temporary drives (USB Sticks, Cameras which behave like detachable storage and things like that).

If you mount from /etc/fstab then it mounts the drive at boot, regardless of any user mount requests.  This is more useful for a permanently attached drive (inside the case) or a USB drive which can be considered as a permanent connection.

---

### Post by romeov007 on 2014-04-30
Oh! That makes a lot of sense..  I will go ahead and create the appropriate fstab entries.   Thank you :) 

Last question.  if i put an external HD into the Fstab entry. and for whatever reason that external HD is not plugged in, would that cause an error or halt in the boot up?

---

