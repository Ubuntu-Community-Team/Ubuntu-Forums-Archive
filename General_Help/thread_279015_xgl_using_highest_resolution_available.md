---
title: "xgl using highest resolution available"
date: 2006-10-17
forum: General Help
---

### Post by Naegling23 on 2006-10-17
It appears that xgl is using the maximum resolution enabled on my system.  Is there any way to tell it to use a different one, other than deleting resolutions in xorg.conf?  In kde, it uses 1080x760, but some insanely high one in xgl.  I have the extra resolutions enabled for some games, but for some reason, xgl ends up using them instead.  Any help?

Im looking for suggestions because yesterday I tried deleting some resolutions, and broke X.  A couple of hours were spent before I booted into windows and replaced my xorg.conf with the backup to fix everything.  Now Im afraid to touch xorg.conf.

---

### Post by davec64 on 2006-10-19
Sorry but I haven't got the answer! I have a similar problem.

But for your information, try this from a terminal before you play with xorg.conf:

Code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

The cp cpmmand is copy, then its the location and name of the file, then its the destination and the name you want to call it.

When X crashes and burns, you'll get the errors come up asking you if you want to read the log file. Once you've read or cancelled out of the log file, you'll be presented with a login. This is the same as working in a terminal to all intense purposes.
Login with your normal user name and password, you'll then get the prompt.

At this point you can now restore your xorg.conf file:

Code:
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

The copy this time will overwrite the duff xorg.conf file.

Believe me, you'll get really good at this after a few goes If your like me and keep playing with your xorg.conf file!!

An alternative to using sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf is sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf. The mv is move, and this moves the backup file to the new location and name. This I think will  efectively change the name of the backup file.

Hope this helps when you need to recover!

I for got to add:

code:
sudo shutdown -r now

this will restart the system!!

---

