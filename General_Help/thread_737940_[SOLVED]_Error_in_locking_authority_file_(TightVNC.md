---
title: "[SOLVED] Error in locking authority file (TightVNC)"
date: 2008-03-28
forum: General Help
---

### Post by Skylive on 2008-03-28
Hi, there have been similar issues to this, but I still have not found a solution on the forums. Currently, Tight VNC works fine, except that it starts with the following error:
---------
xauth:  /home/david/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/david/.Xauthority

New 'X' desktop is Ubuntu:1
--------

This seems to affect my VNC session as I cannot access system settings. Access the synaptic manager gives me the error: " failed to run usr/sbin/synaptic as user root. Unable to copy user's authority file."

How may I solve this problem?
Also, how can I make tightvncserver auto start on system startup?

---

### Post by Skylive on 2008-03-31
Would someone please help me out? I really need to get VNC working with full desktop capabilities and not half broken.

---

### Post by JoelOl75 on 2008-06-27
I'm having the same problem... It used to work fine with Dapper, but I upgraded my server to hardy and .... same prob... If I find the answer, I'll post back.  Seems to be that gnome locks the file, and starting a new session (I start it on desktop :2) wont allow it...

---

### Post by JoelOl75 on 2008-06-27
OK, got the solution!!! It's just a simple permission problem.... I don't know if there is any security implications to doing this, but I did it in the safest way I can see.... It seems the .Xauthority file is owned by root and only has rw permissions for root

OK, on the server machine edit the .vnc/xstartup file so gnome loads, and not just an x-terminal (I suppose you already did this....)   

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &



OK, then go back to the /home/user directory (Just type cd...)

cd
sudo chown username:username .Xauthority

And that's it!

and bam! good to go....  I usually keep a script in my home directory to start my vnc up because I want a smaller screen than normal so I don't have to go full screen or scroll around to see the taskbar and whatnot..

#!/bin/bash
vncserver -geometry 1500x970 :2

This fits nice in a 1680x1050 res monitor...

If you make the script make sure to chmod a+x it to make it executable.

---

### Post by Skylive on 2008-06-27
Hi there,

Really appreciate you finding out the solution. Actually I found that out too, but after I moved on to Hardy, everything 'just works', so I totally forgot about this thread of mine....

Thanks to you, I get to refresh my memory on this issue and hopefully this helps those poor souls that are still racking their brains!

---

