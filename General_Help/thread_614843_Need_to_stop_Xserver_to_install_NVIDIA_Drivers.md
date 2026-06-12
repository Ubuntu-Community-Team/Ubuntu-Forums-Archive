---
title: "Need to stop Xserver to install NVIDIA Drivers"
date: 2007-11-16
forum: General Help
---

### Post by steph09 on 2007-11-16
I'm trying to install NVIDIA drivers for my T61 running Ubuntu 7.10. When the NVIDIA driver installation begins, I get the following error:

" ERROR: You appear to be running an X server; please exit X before installing. "

I tried "sudo /etc/init.d/gdm stop" and it exits the GUI but seems to be stuck running some script. I can never get to the command line.

I also tried sudo init 3 but the GUI doesn't shut down at all, it just sits there as normal.
I have found many places online that says to hit Ctrl+Alt+Backspace but that simply logs out which does nothing for me.

Any other ideas on exiting the X server?

Thanks

---

### Post by taurus on 2007-11-16
At the GUI log in screen, press <Ctrl><Alt>F2 to get to a console.  Log in and shutdown gdm with

```
sudo /etc/init.d/gdm stop
```
Now, install your nVidia driver and when you are done, restart gdm again with 

```
sudo /etc/init.d/gdm start
```

p.s.  Were you logged into Gnome when you tried to shutdown gdm?

---

### Post by steph09 on 2007-11-16
Yes, I was logged into Gnome while trying to shut down GDM. I guess that was my problem. But thanks for the help, I got the drivers installed.

---

