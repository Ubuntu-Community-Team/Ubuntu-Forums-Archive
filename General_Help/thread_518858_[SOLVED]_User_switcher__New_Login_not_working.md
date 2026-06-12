---
title: "[SOLVED] User switcher / New Login not working"
date: 2007-08-06
forum: General Help
---

### Post by zetetic on 2007-08-06
Hi.

When I try to switch users, on fast-user-switch-applet, nothing happens.
If I click on "applications -> system tools -> New Login", I get this error message:

"Cannot start new display
There were errors trying to start the X server"

I also found this error message on /var/log/syslog :

"gdm_child_action: Aborting display :-1"

It's a mystery to me the reason why it mentions "display -1" !
I checked "system -> administration -> Login Window" configuration and there, on "Security -> Configure X Server", I have confirmed that I'm using a VT 0 Standard Server with the following command: "/usr/bin/X -dpi 96 -audit 0"

So, I'm not able to login as another user without logging out of the current user.

If I log out of the current user, I am presented with the gdm login, where I can log in into the other user without any problems!

I would be very grateful if someone could help, cause I'm completely clueless.

I have this problem on both Ubuntu Feisty and Debian Lenny.

---

### Post by zetetic on 2007-08-15
bump
Sorry, but I really need to solve this issue...

---

### Post by zetetic on 2007-08-26
I have finally found the origin of my problem.

I am using a firewall script made by me. On that script I was blocking localhost loopback on IPv6.

After allowing localhost loopback on IPv6 the problem is gone and now I'm able to switch users without any problems.

Now I just would like to know how can I mark this thread as solved.

---

### Post by Warren Watts on 2007-08-26
To mark the thread as solved:

Bring up the thread

Click on Thread Tools - Choose "Mark this Thread as solved"

---

### Post by zetetic on 2007-08-26
Thank you.

Have a nice day.

---

