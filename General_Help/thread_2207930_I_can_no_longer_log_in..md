---
title: "I can no longer log in."
date: 2014-02-25
forum: General Help
---

### Post by jawknee530 on 2014-02-25
I have new Thinkpad T440s that I have installed xubuntu 13.10 on. I was messing with the 50-synaptics.conf file in etc/x11/xorg.conf.d/ trying to get my touchpad working how I want. I didn't want to restart my machine every time I made a change and saw in a forum to type startx to apply my changes. Well I did that wihch caused my screen to flash and go black. After waiting for my machine to respond to no avail I hit the power button and the machine did a normal shut down. After booting the machine back up I was greeted with a login splash screen which I had not used before (set it to not require pass to login when I installed xubuntu). When i put in my password the screen flashes once or twice then drops me back to the login prompt. When i put in an incorrect password it rejects it and tells me the password is incorrect so I know that's not my problem. I can log into a guest account fine but no luck for my normal user account. So what do i do from here?

---

### Post by jawknee530 on 2014-02-25
I solved the issue. After deleting a .Xauthority file in ~/ my machine booted back into my account like normal.

---

### Post by Iowan on 2014-02-25
[Hint...]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ;)

---

