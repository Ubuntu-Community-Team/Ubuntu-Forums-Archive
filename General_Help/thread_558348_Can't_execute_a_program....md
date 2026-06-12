---
title: "Can't execute a program..."
date: 2007-09-23
forum: General Help
---

### Post by zacinaction on 2007-09-23
I just installed emusic's new remote app and I can run it as root, but not as my regular user.  I checked the permissions and it looks like I have read and execute permission... I can't figure it out.

Here's what ls -l emusicremote says:

-rwxrwxr-x 1 root root 28536 2007-09-12 14:35 emusicremote

Anyone know what's up?

Thanks

---

### Post by PanopticChaos on 2007-09-23
Not sure, it works ok for me - did you install it as root?  (I'm wondering if some resource file got locked down)

What error are you getting exactly when you try to run it?

---

### Post by zacinaction on 2007-09-23
I've installed it as root and as a regular user.  Same result in both cases.  Even when I installed it as a regular user in my Home directory, I could run it as sudo but not as my user.  When I try running not as root, nothing happens at the command line.  It just doesn't run.  If i run as sudo, the app comes up just fine.

---

### Post by PanopticChaos on 2007-09-24
Well, I ran a ```
ls -laR
``` from the /emusicremote directory so you can see if any of your permissions are different (loki is my regular user account)

 You may want to try 'ldd'ing the emusicremote executable and checking the permissions on the libraries being used - I'm not sure if that matters.

---

### Post by hanzomon4 on 2007-09-30
Same here, can only run this as root

---

### Post by hanzomon4 on 2007-10-01
I got it:```
sudo chown -R YOURUSERNAME ~/.emusic
```
You have to change the ownership of the ~/.emusic file recursively to your user

---

