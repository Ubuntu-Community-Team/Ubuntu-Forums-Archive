---
title: "Broken Ubuntu"
date: 2007-03-02
forum: General Help
---

### Post by Invictious on 2007-03-02
I just tried to boot Ubuntu, and then all of a sudden, I get this black screen with white text, telling me to log in.

So I do, and I cannot type in the password field. Then after a while a blue screen pops up, which is pretty messed up, and then it says X Server failed to start etc etc.


How can i reinstall X Server?
I only have the Live CDs, so alternate install CDs are not an option.

Thanks.

---

### Post by booe on 2007-03-02
Check this thread,

[http://ubuntuforums.org/showthread.php?t=374125](http://ubuntuforums.org/showthread.php?t=374125)

If you use the proprietary NVIDIA drivers.

---

### Post by Naatan on 2007-03-02
or try booting up in terminal mode (im not sure what its called but in the boot screen select the second option) and enter this command:

**sudo dpkg-reconfigure xserver-xorg**

after that reboot.

---

### Post by Invictious on 2007-03-02
As in recovery mode?
Well when asked to log in, I can't type anything into the password field.

---

### Post by igknighted on 2007-03-02
> **Invictious said:**
> As in recovery mode?
Well when asked to log in, I can't type anything into the password field.

You in fact are typing, it just doesn't show up.  If you type your password properly you will log in to a text prompt.  When you type passwords in a terminal/tty nothing shows up on the screen.  This is normal.

EDIT: recovery mode logs you in as root, no password, single user mode so you can make necessary changes.

---

### Post by booe on 2007-03-02
> **Invictious said:**
> As in recovery mode?
Well when asked to log in, I can't type anything into the password field.

Well you should be given a prompt for a username/password after the blue/white screen about a stuffed up display closes (you have to press OK to all the errors).

There shouldn't be a need to load up a recovery console from the Live CD or anything that dramatic (I hope).

Otherwise, follow igknighted's advice if you want to use the recovery console (which is always logged in as 'root' and not your own username, therefore you don't need to use 'sudo')

"sudo" is just a method to let a command run with more privileges than not using "sudo". If you're in the recovery console, it is logged in with enough privileges that the effects of "sudo" are automatically applied to all commands you type.

---

### Post by Invictious on 2007-03-02
Fixed with the recovery mode. Thanks!

---

