---
title: "Mirror Eee PC screen to bigger monitor"
date: 2008-04-20
forum: General Help
---

### Post by sebast on 2008-04-20
Hi,

I installed Hardy RC 1 on a friend's Eee PC and I'm trying to set it up so when he plugs his second monitor the screen switches (or mirror) to it and with the right resolution.

At first, I set up Ubuntu while at my place without his other monitor and it wouldn't then mirror to the other monitor at all except on Ubuntu's log in screen (shockingly). Also, when I do a 

```
sudo dpkg-reconfigure xserver-xorg
```

it only asks for keyboard questions, it doesn't set-up the screen.

I then created a new user on the system while the new monitor was plugged and it suddenly worked as needed. What's the possible explanation for such a behavior?

Also, if the big monitor is plugged before the session is opened and we unplug it afterward, I have to change the resolution by hand: it doesn't switch to the small (800x600) resolution automatically.

Also, a bigger problem: if the big screen is not plugged while we open the session and I plug it afterward, there seems to be no way to make the screen mirror to it with the resolution GUI so it wont work at all until I restart the session.

Can anybody help me with those problems?

Thanks in advance

---

