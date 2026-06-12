---
title: "Unable to log in"
date: 2014-02-09
forum: General Help
---

### Post by marco26 on 2014-02-09
Hello, I'm faily new to linux/ubuntu in general and I'm in process of learning stuff.
I tried to look around to fix my problem, but I couldn't find any info related to my issue. I guess I failed at searching for this issue.

The problem is at log in stage: after I type in my password it feels like the desktop starts to load up (the screens flashes black) then it brings me RIGHE BACK to the login screen.

Things I tried to do:
-I tried to put in a wrong password, and it correctly just showed up the "wrong password" message
-I auccesfully changed my password: same result, it takes me back to the login screen.
-I tried to login via ssh from my other pc with my user just to check, it worked. Of course it works as well if I try to login the console via alt+shift+F2.
-I tried to login as guest, it worked. The desktop loads just fine.
-i tried to login as my user as both Ubuntu and Ubuntu2D. Nope!
-I installed gnome, nop!

I'm really lost, suggestions? Is there maybe a log file I can check?

---

### Post by Impavidus on 2014-02-09
You problem is that the GUI is unable to start because something is wrong in your home directory.

Go to the console and login. Then check for any files in your home directory not owned by you. Specifically, this is usually about .Xauthority or .ICEauthority (both hidden files) that may be root-owned as a result of incorrect usage of sudo (running GUI applications with sudo instead of gksu). Both must be owned by you and have permissions 600. Fix them if necessery with chown.

---

### Post by marco26 on 2014-02-09
Thankyou very much ;)

---

