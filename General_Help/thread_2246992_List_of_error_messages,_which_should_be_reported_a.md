---
title: "List of error messages, which should be reported a s bug and where?"
date: 2014-10-04
forum: General Help
---

### Post by ineuw on 2014-10-04
I compiled a list of error messages after installing Xubuntu and ask the community for guidance as to what should be done with the following, report it as a bug? and if yes, where? 

 1. After installation and 1st update reboot, whisker menu access was lost and the menu could not be edited. (Whisker menu missing software updates icon).

 2. Ubuntu mirror servers are not synchronized with the main server. Two scenarios:
    When swithching to the main server from the Canadian server, it has additional udates for the installed software.
    I also work on another installation (Ubuntu 12.04 in French) and swithing from the main server to the France server 

 3. Nvidia driver 340.46 message "Distribution provided pre-install script failed." not serious, and the driver works well.

 4. Firefox 32.0.3 does not recognize the installed Adobe Flash Player plugin version 11.2.202.406

 5. Activating Thunar from the terminal generated these errors.
    (Thunar:2279): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion 'GDK_IS_WINDOW (window)' failed
    (Thunar:2328): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion 'GDK_IS_WINDOW (window)' failed

 6. Activating GParted from the terminal geberated the following errors:
    (gpartedbin:2876): GLib-CRITICAL **: Source ID 162 was not found when attempting to remove it
    (gpartedbin:2876): GLib-CRITICAL **: Source ID 161 was not found when attempting to remove it
    (gpartedbin:2876): GLib-CRITICAL **: Source ID 167 was not found when attempting to remove it
    (gpartedbin:2876): GLib-CRITICAL **: Source ID 166 was not found when attempting to remove it
    (gpartedbin:2876): GLib-CRITICAL **: Source ID 170 was not found when attempting to remove it . . . . and this goes on and on

 7. On exit from terminal sudo bleachbit: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0 
     Traceback (most recent call last):
     File "/usr/share/bleachbit/bleachbit/Worker.py", line 83, in execute for ret in cmd.execute(self.really_delete):
     File "/usr/share/bleachbit/bleachbit/Command.py", line 131, in execute for func_ret in self.func():
     File "/usr/share/bleachbit/bleachbit/Memory.py", line 270, in wipe_memory wipe_swap_linux(devices, proc_swaps)
     File "/usr/share/bleachbit/bleachbit/Memory.py", line 248, in wipe_swap_linux raise RuntimeError('swap device %s is larger than expected' % device)

---

### Post by mörgæs on 2014-10-04
In which version of Xubuntu did you find the errors?

---

### Post by ineuw on 2014-10-04
> **mörgæs said:**
> In which version of Xubuntu did you find the errors?

Sorry, Xubuntu 14.04

---

### Post by mc4man on 2014-10-04
#5 - likely irrelevant message
#6 - can't see any reason to open gparted from a terminal but if so should be - 
```
gparted-pkexec
```

---

### Post by ineuw on 2014-10-04
Thanks for the advice. I must assume that anything I open from the terminal will generate an (error?) message. It has happened with other software but didn't write it down. The issue is that items which should be in the menu are not placed there, so I must often use the terminal as I am having a hell of a time with MenuLibre. I did file a bug report about MenuLibre at Ubuntu.

---

### Post by mc4man on 2014-10-04
Not anything but many times opening from terminal produces verbose messages. If the app works then generally can be ignored.
In 14.04 opening gui apps as root tends to produce these type messages, ex. here of your GLib-CRITICAL **: Source ID XXX  was not found when attempting to remove it (post 6 for gparted, notice was opened with sudo
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1264368)

---

### Post by mörgæs on 2014-10-05
Small bugs like these are not going to be corrected in 14.04, but if you find them in 14.10 you could discuss them in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") and see if they need reporting.

---

