---
title: "Ubuntu 16.04 Desktop won't refresh"
date: 2016-06-02
forum: General Help
---

### Post by r00st3r32 on 2016-06-02
Just did some updates tonight and now only my desktop is broken. It will not refresh at all. Can't see the background just see what I had running. Everything else works as far as graphics. If I open the terminal and restart unity the desktop background goes black but it is still the same problem. I have put in a picture to help explain better.

[http://imgur.com/LjgDJnB](http://imgur.com/LjgDJnB)

Please help, thanks.

---

### Post by Bucky Ball on 2016-06-03
Most unappealling! Have you tried restarting the machine entirely, not just Unity? 

Run these in a terminal and reboot the machine. 

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

After the reboot check in Additional Drivers and see which third-party graphics driver you are using, if any. The update may have taken you to a version that is not compatible with your hardware for some unknown, as yet, reason.

---

### Post by r00st3r32 on 2016-06-03
> **Bucky Ball said:**
> Most unappealling! Have you tried restarting the machine entirely, not just Unity? 

Run these in a terminal and reboot the machine. 

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

After the reboot check in Additional Drivers and see which third-party graphics driver you are using, if any. The update may have taken you to a version that is not compatible with your hardware for some unknown, as yet, reason.

This fixed the issue. Thank you very much for your help. It pulled down some Compiz stuff which Unity uses so I am guessing one of the other updates last night botched Compiz or something.

---

### Post by Bucky Ball on 2016-06-03
Great news and thanks for marking as solved. 

Good luck with Ubuntu and hope you enjoy. :)

---

