---
title: "Blank screen after login"
date: 2012-11-06
forum: General Help
---

### Post by ShadowfireXX on 2012-11-06
I ran updates last Thursday.  Since then, my Ubuntu 12.04 has been unable to log in successfully under my existing user sign-on.

I get the sign-on screen appear, I type in my password, then the screen goes black and .....  that's it.  Where the desktop is meant to appear - nothing.  However, the pointer arrow is still there, plus I can do Ctrl-Alt-F2 and drop to the shell, and list my home partition and do stuff there - but no GUI.

I should point out that I can log in successfully as a guest, and also that my login fails whether I log in as Unity 2D, 3D, OpenBox or LXDE (which I have installed as well).  It just doesn't want to know.

Also, I don't use my home directory at /, I have set up a home partition.  If I delete reference to this home partition in fstab, and revert back to the default home directory, it loads fine as well.

So I assume it is a problem with a config file in my existing home partition.

I have looked around various error and log files, and posted help pleas on other forums, but to no avail.

Can anyone suggest any config files stored in one's home directory, that could be either amended or deleted, that might rectify the situation?

Thank you for any help you can give.

---

### Post by bogan on 2012-11-06
Hi!, **ShadowfireXX**,

Try the following, it should show two files with ownership shown as your username.

If they show  "root root" or permissions other than displayed below, that is your problem.

If so, rename or delete the offending file and reboot.```
alan@alan-MS-7616:~$ ls -l /home/alan/.*authority # use your username for 'alan'
-rw------- 1 alan alan 30792 Nov  6 18:06 /home/alan/.ICEauthority
-rw------- 1 alan alan    57 Nov  6 18:06 /home/alan/.Xauthority
alan@alan-MS-7616:~$ 
```Chao!, bogan.

---

### Post by ShadowfireXX on 2012-11-07
Thanks, but it shows that I have read/write authority to both those files.  And, presumably, my whole home partition as well.  So it's not that.

Does anyone have any further suggestions?  My .xsession-errors file has a line that says "gnome-session[1603]: WARNING: Application 'unity-2d-shell.desktop' killed by signal".  Could this be a pointer to the problem?  If Unity was "killed" by something, that would explain its non-appearance... wouldn't it?

---

