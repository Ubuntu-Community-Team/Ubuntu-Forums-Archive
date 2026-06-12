---
title: "Light locker doesn't work"
date: 2014-08-24
forum: General Help
---

### Post by marsdenf on 2014-08-24
Using xubuntu 14.04 on a laptop. When I click on light locker in  settings manager, the window appears for a fraction of a second and then  disappears. Here is the error message when I try the program in a terminal

marsdenf@marsdenf-G75VW:~$ light-locker-settings 
Traceback (most recent call last): 
  File  "/usr/share/light-locker-settings/light-locker-settings/light-locker-settings.py",  line 541, in <module> 
    main = LightLockerSettings() 
  File  "/usr/share/light-locker-settings/light-locker-settings/light-locker-settings.py",  line 97, in __init__ 
    self.init_settings() 
  File  "/usr/share/light-locker-settings/light-locker-settings/light-locker-settings.py",  line 240, in init_settings 
    use_light_locker = settings['light-locker-enabled'] 
TypeError: 'NoneType' object has no attribute '__getitem__' 
marsdenf@marsdenf-G75VW:~$ 



Any suggestions?  (I tried reinstalling light locker, lightdm etc.)

---

### Post by Dennis N on 2014-08-24
Happened to me too when 14.04 was first released. There is a suggested solution in this thread, post #6:
[http://ubuntuforums.org/showthread.php?t=2223143](http://ubuntuforums.org/showthread.php?t=2223143)
My solution was to uninstall light locker and use xscreensaver instead.

---

### Post by marsdenf on 2014-08-25
the solution suggested is to delete the file  ~/ .config/autostart/light-locker.desktop  
I tried searching for this file using catfish and it came up with an abort error.  I know almost nothing about searching for files in linux.  How do I find this file and delete it?

---

### Post by Dennis N on 2014-08-25
> **marsdenf said:**
> the solution suggested is to delete the file  ~/ .config/autostart/light-locker.desktop  
I tried searching for this file using catfish and it came up with an abort error.  I know almost nothing about searching for files in linux.  How do I find this file and delete it?

We don't need to search for it, since we know where it is. Open file manager to view your home folder, then in view menu be sure "show hidden files" is checked. Then open the **.config** folder - you should then see the **autostart** folder. Open that and you should see **light-locker.desktop**

Instead of deleting, you could also just rename it to something else like **light-locker.old** so that you can restore the original if desired. This should work the same as deleting.

---

