---
title: "system freezes on user switch (radeon hd2350, ati open source driver)"
date: 2008-06-08
forum: General Help
---

### Post by kc600 on 2008-06-08
When i login as A, switch to B, and switch back to A, the systems hangs.
Things to note (i read about similar issues a lot):
- Switching via the fast-switch applet and via the logout menu produces the same result.
- For both user A and B, screen locking when switching users is disabled.
- Killing X by pressing Ctrl-Alt-Backspace doesn't work, neither does restarting by pressing Ctrl-Alt-Delete
- It's not just a stalled gdm, the entire system freezes. For example, if i'm logged in on the computer via ssh, that session freezes too. Music still playing on one of the users (Amarok) will quit or stall.
- I use the open source ati driver.
- I do not have desktop effects (compiz) enabled. (I can not enable these; why this is is perhaps a related issue. Whenever i try (via preferences > appearance > tab visual effects), it says "desktop effects could not be enabled".)

Does anyone have any ideas i might try out?

---

### Post by milanvora2 on 2008-06-11
same here. although i use the ati restricted drivers.

nothing can be done as this is a bug. the only way to avoid it is to revert to vesa driver till they fix it (or log off the user before logging in as the next one)

i'm pretty bugges that it's taking them so long to fix this

---

### Post by jelofson on 2008-07-17
I seem to have the same issue here with ati restricted driver (9600 mobility radeon). After logging clicking "Log Out" the system hangs right before the new login screen would normally show up. It doesn't happen 100% of the time, but pretty close. Would love to see that fixed. I hate having to restart the whole machine just to do something as SIMPLE as logging off for another user to log back in.

---

### Post by vitorio on 2008-07-17
Hi, folks.

There are actually two different ATI Open Source drivers: "radeon" and "radeonhd". When you say "ati open source driver" which one of them do you mean?

My card is an older one, it's ATI Radeon 9550 Pro, and I had same problem with "fglx" (proprietary) driver.  Then I switched to "radeon" driver and the problem gone.  My system never freeze any more and I can use compiz with it too.

"radeon" is far more mature driver then "radeonhd" today, though both of projects get some sort of support from ATI.

So, if you are having this problem with "radeonhd", give a try to "radeon".  Here you find a good starting point:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

But first see if your card is supported on the project home page. They have quite a long list.

However, be prepared to spend quite a time with the problem, tweaking your card configuration, etc.  

From what I learned digging the subject, it's not just a video card problem but rather combination of your video card, your motherboard, etc. that gives such a poor result.  See what your mobo settings for video are. Try to tweak them too, but only if you know what you are doing. A lot of googling helps.

In my case I believe the problem was rather in my old Asus P4PE mobo then in the video card itself. Though how really knows? :)

---

