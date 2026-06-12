---
title: "How to make a program run on startup?"
date: 2007-10-23
forum: General Help
---

### Post by aetherh4cker on 2007-10-23
Alright, right now I'm remotely connected to my machine via ssh, so all the advice would need to be from a command line side.

I just installed noip2 to run in the background and update my DNS with my new IP address whenever it changes.  However, I want this program to run on startup and I don't know how to get it to do that!

Someone said I should just add '/usr/local/bin/noip2' to my rc.local file and it should solve my problem.  I haven't done this yet because:
1.  Do I add it in before the 'exit 0' or after it?  The file has a bunch of comments and an exit 0 at the end, and that's it.
2.  I've heard there are better ways to make programs run on startup, I'm completely open to suggestions.

Thanks for any advice!

---

### Post by ihcnet on 2007-10-23
Try going to System>Preferences>Sessions then to the Startup Programs tab and choose Add. Then enter the information for the program you want to start when you login to gnome.

---

### Post by aetherh4cker on 2007-10-23
As stated in my first post, I need a command line alternative to that.

Also, I'd need it startup when the computer does, and not when I log into gnome.

---

### Post by ihcnet on 2007-10-23
Add the command to the /etc/rc.local script before the exit 0 and it should run it as the last step in the boot process.

---

