---
title: "Can't boot after enabling root login!"
date: 2007-09-30
forum: General Help
---

### Post by apple_and _linux on 2007-09-30
So I enabled the root login so that I could create a shared folder in Ubuntu.  After setting the root password in Users and Groups, I went to the Login Window preference window and enabled (under Security tab) "Allow local system administrator login window."  Now Ubuntu won't start up!  It gets to a certain point (somewhere halfway through the initial progress bar), then shows some boot text, and then I get locked up with a blank screen and a spinning cursor (the progress one).  I really want to get back into Linux- I'm going from the Live CD right now.  Any ideas?

---

### Post by bodhi.zazen on 2007-09-30
Well, I assume you changed something additional as root, perhaps unintentionally ?

Was the share your home directory ?

Any other changes, can you give more details ? Error messages ?

Can you boot to recovery mode ? Check the log files for clues.

My only other advices is for you to 

1. Access root with sudo or sudo -i

2. Graphical apps, use gksu (like gksu nautilus)

3. Avoid logging is as root, especially graphically. logging in as root significantly increased the risk you will inadvertently alter system files as you have full access.

---

### Post by apple_and _linux on 2007-10-01
---Well, I assume you changed something additional as root, perhaps unintentionally ?---

No, I never even logged in as root!  All I did was allow the system administrator to log in from the GDM, and when I tried to log out of the regular admin, it did a shut down instead.  After that, I haven't been able to start it up.  If I do the recovery mode, I have the option of using su for maintenance, but it never gets any farther in the boot process.  Just gets locked up with the spinning cursor.

---

### Post by bodhi.zazen on 2007-10-01
Ouch ...

Well what you are describing is obviously not normal behavior.

Can you post any error message or tell me where in booting it hangs ?

Can you check the logs ?

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Any clue ?

---

### Post by apple_and _linux on 2007-10-02
I took some video of what happens when I try to load Ubuntu.
Here's the link: [http://www.4shared.com/dir/4064941/f4caa27a/sharing.html](http://www.4shared.com/dir/4064941/f4caa27a/sharing.html)
and here's the password to get in: ubuntu
The png image is of a screen that was on for about 10 seconds when I pressed the power button (to turn it off) after trying to load in recovery mode.  Ubuntu.mpg is of trying to boot normally, and Ubuntu Safe.mpg is of recovery mode.
Thanks for your help so far, and sorry about the hassle.

---

### Post by apple_and _linux on 2007-10-09
Well, I'm taking a different approach.  I've re-installed the system over another partition.  I can browse the old installation through File Browser, but a lot of the files have permission problems (namely, I'm not allowed to read them).  I've tried using file browser as root (gksudo nautilus), but then I can only browse the home drive.  So now I'm wondering if there's a way I can override the permissions on the old installation so I can copy some of the files.  Any help?

---

