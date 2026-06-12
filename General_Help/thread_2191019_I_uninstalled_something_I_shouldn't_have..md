---
title: "I uninstalled something I shouldn't have."
date: 2013-11-30
forum: General Help
---

### Post by Cleveland Rock on 2013-11-30
I was uninstalling things I didn't use from the Software Center last night, and I must have uninstalled something I shouldn't have, because it now freezes on the loading screen at boot. I get to the loading screen immediately after the GRUB menu, and it just stays completely frozen. What can I do to restore whatever it was I removed? Thanks.

---

### Post by heir4c on 2013-11-30
That's difficult to know.
The first thing you must do now is: Boot up with a live-cd/dvd or live-usb and Backup all your personal files, or better: the hole /home folder to a external disk. 

Than you can try to go into your system again via the recovery mode in Grub. And when you're again stuck on the login try Ctrl+Alt+F2 to go to a console. Try to login and type after that the following command:
```
startx
```

---

### Post by heir4c on 2013-11-30
Normally you get a warning when you uninstall packages that there are more and other packages that will be removed.
For removing packages you can better use synaptic (Packages Manager, not anymore default installed on Ubuntu). You get more info and can see what files there are installed for that packages and where they are, and also what the dependencies are.

If you remove packages that come default with a fresh install, then don't remove them, they take not much space on your HD.

And if you want a minimal installation you can better use the mini.iso and build than further the system up.

---

### Post by Cleveland Rock on 2013-11-30
I'll be darned! That did the trick! Thanks a lot. How can I mark this as "solved"?

---

### Post by BlinkinCat on 2013-11-30
> **Cleveland Rock said:**
> I'll be darned! That did the trick! Thanks a lot. How can I mark this as "solved"?

Hi,

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by heir4c on 2013-11-30
I'm glad it worked!

Greetings,
Gerolf

---

