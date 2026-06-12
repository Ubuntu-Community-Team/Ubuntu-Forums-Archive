---
title: "Cannot Start Gnome"
date: 2007-10-31
forum: General Help
---

### Post by GingerAlex on 2007-10-31
Hi I am in trouble:

When I start Ubuntu, it fails to load gnome, I can only get to command line. 

I've tried typing 'gdm' and 'startx' at the terminal; neither worked.

I am using an Acer Aspire 5612 Laptop, Intel Graphics 950 card, was using Intel drivers. Ubuntu version 7.10.

_what happened today_ - I did some messing about with the 'screens and displays' utility to see if I could get a projector working, to no avail. At one point I seemed to inadvertently change my main laptop screen resolution, but I thought I'd got back to normal, but possible not..
At the end of play, on some daft impulse I decided to try suspending the laptop again to see if it worked. 
Got home, switched back on, and had intriguing problem where I couldn't see edges of my screen - it was too big!
Tried restarting and then gnome would not start. 

_Some more history_:
-no problems until upgrade from 7.04
-when upgrading I rejected most of the proposed config changes, since my config seemed ok as it was ( i have these in a file at the moment, but no way of sending it!)
-since upgrade a few weeks ago, most things worked however
-- 2 PCI messages - very similar to [URL="http://ubuntuforums.org/showthread.php?t=265132"]
-- terrible problems with hibernate / suspend, always wierd freezes starting up requiring 'hard reboot' to recover; I'd decided I'd just shut down my computer normally instead and wait for a fix to come along
-- occasional gnome error message, just after logging in. It logged in, but without my usual visual settings (differenent colours, plainer windows and no compiz). Re-login and this went away.

Any help desperately recieved!

---

### Post by taurus on 2007-10-31
Did you save a copy of /etc/X11/xorg.conf before you played around with it?

If not, boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
When you are done, reboot your machine and see if X works now.

```
shutdown -r now
```

---

### Post by Thyme on 2007-10-31
What is your /var/log/Xorg.0.log showing? Do you get any messages when typing startx and gdm?

---

### Post by GingerAlex on 2007-10-31
> **taurus said:**
> Did you save a copy of /etc/X11/xorg.conf before you played around with it?

If not, boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
When you are done, reboot your machine and see if X works now.

```
shutdown -r now
```

thank you very much for the quick response, this did the trick, I am now in business again.

---

### Post by GingerAlex on 2007-10-31
> **Thyme said:**
> What is your /var/log/Xorg.0.log showing? Do you get any messages when typing startx and gdm?

cheers Thyme but Taurus just pipped you to the post, thanks all the same.

---

