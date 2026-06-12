---
title: "Nvidia dual screen behavior lost after logout/login"
date: 2016-05-10
forum: General Help
---

### Post by LazyBoy on 2016-05-10
I have an Nvidia dual screen setup that originally ran on 14.04 with the xorg-edgers ppa. (Unity)

I've been on 15.10 a few months and it's been fine.  I believe the xorg-edgers ppa stopped being relevant with that switch.  

I updated software yesterday, and today when I logged in, my screens were doubled, not side by side.  I use the NVIDIA X Server Settings app to re-configure side-by-side.  But it doesn't survive logout/login.  I've tried writing the config to xorg.conf, but that doesn't help.  (I don't recall if I had an xorg.conf when it worked.)

Any ideas?

Thanks
LB

---

### Post by papibe on 2016-05-10
Hi LazyBoy.

Make sure you have an script on your 'Startup Applications' that load your nvidia settings. It should be something like:
```
sh -c '/usr/bin/nvidia-settings --load-config-only'
```
Also check that your ~/.nvidia-settings-rc is owned by you and readable (in case it change to root where trying the create a xorg.conf):
```
$ ls -l .nvidia-settings-rc 
-rw-rw-r-- 1 user user 2109 Mar 14 11:52 .nvidia-settings-rc

```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by LazyBoy on 2016-05-10
It's there and read/writable.
But it doesn't appear to contain anything related to positioning.

---

### Post by LazyBoy on 2016-05-10
I found it.

In Systems Settings > Displays, there is a "Mirror displays" check box that was checked.

I don't recall seeing this before.  It  might be new, or I might have forgotten.
Also, I read this somewhere: 
> if your using gnome shell it calls xrandr on start and overrides whatever you have in your xorg.conf
I'm not sure if it's true or applies.

Thanks!

---

