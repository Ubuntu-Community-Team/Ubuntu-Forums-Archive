---
title: "Looks like my system is boned, I don't want to restart!!!  Help!!"
date: 2007-05-06
forum: General Help
---

### Post by murraysw on 2007-05-06
I was installing the Feisty upgrades through the update manager and, like always, VMPlayer ****** up.  It's been a trend with this system, VMWare has never worked and has been ****** up pretty much since I began using Ubuntu (whenever I install something or upgrade anything Vmware player craps out at the end)

But this time VMWare player crapped out the entire Feisty upgrade!!! Should I just backup everything and start from scratch?  I don't even know if my system will recover from a restart after crapping out halfway through that install there...

What's the best course of action here?

---

### Post by fwojciec on 2007-05-06
Can you post what message you get when you try to apt-get remove vmware-player?

---

### Post by murraysw on 2007-05-06
```

Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It can't find the directory because I deleted it long ago.  This app has been f*cked since the day it was installed and I was unable to remove it.  I couldn't uninstall (I tried various methods posted on the forums), so I ended up just deleting the entire directory out of frustration in hopes it would solve something.  Just a different error now that's all....I didn't think this little app would f*ck up a system upgrade for me...

Arg.

---

### Post by fwojciec on 2007-05-06
I had a similar problem once, and this is, more or less, how I fixed it.

1) Clear the directory /etc/vmware (you have to be root to do it) but leave the directory itself.  Now just create an empty directory called "locations" in there (mkdir /etc/vmware/locations) - otherwise later the "apt-get remove" command will complain about not being able to find something at /etc/vmware/locations.  If the directory /etc/vmware is empty just create "locations" inside.

2) Try running the apt-get remove vmware-player again.  If it doesn't work you can also try removing "/etc/init.d/vmware-player" script and restarting the computer (to make sure that vmware is not running) and then trying to remove it again.  

It's a complete hack, but it worked for me.

I helped out with a similar problem once on these forums, and it worked then - [link here]("http://ubuntuforums.org/showthread.php?t=426198&highlight=vmware+player+locations") - maybe it'll be helpful as well.

---

