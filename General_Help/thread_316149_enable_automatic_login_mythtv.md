---
title: "enable automatic login mythtv"
date: 2006-12-10
forum: General Help
---

### Post by dancro on 2006-12-10
Hi,

I am building a mythtv box using 0.20 on edgy.  How can I have the mythtv machine do automatic login for the mythtv user?

When I go to /System/Administration/Login Window and click automatic login user list, mythtv is not listed, although I can login with that user name.  I tried typing the name mythtv into the box, but it doesn't remember and next time I power on, it is as if I had never done it.

Thanks in advance for any assistance.
Dan

---

### Post by Titus A Duxass on 2006-12-10
Are you following a particular HowTo or are you just doing it?
If you follow this Howto: > [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

There is a detailed paragraph about Auto Login.

---

### Post by AcidTripp on 2006-12-18
Hello,
It's been almost a week since you posted your problem and maybe you fixed it already, but for everyone else (and hopefully you!) here's the solution.

For some reason, the gdm GUI configuration program won't let you autologin with mythtv. This is stupid and there's no reason for it. Period. Luckily there's always the command line to your rescue!

```
sudo nano /etc/gdm/gdm.conf-custom

```
Change

```
[daemon]
AutomaticLoginEnable=WHATEVER
AutomaticLogin=WHATEVER
TimedLoginEnable=WHATEVER
TimedLogin=WHATEVER
TimedLoginDelay=WHATEVER
```

to

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=mythtv
TimedLoginEnable=true
TimedLogin=mythtv
TimedLoginDelay=5
```

Also, following the instructions for setting up a MythTV session using openbox is advisable. Just follow most of the instructions from [here]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend") (the previous word is a link if it doesn't look that way) to do that. Don't listen to their stuff about setting up mythtv with your regular user, though. I couldn't get that to work for the life of me. Once again this is stupid. Period. Just change your gdm.conf-custom file as noted above. You WILL have to select mythtv as your default Session, though. I'll leave the specifics of that as an exercise to the reader.

Have fun with your mythTV setup!

---

### Post by gosh on 2006-12-20
> **AcidTripp said:**
> Hello,
It's been almost a week since you posted your problem and maybe you fixed it already, but for everyone else (and hopefully you!) here's the solution.

For some reason, the gdm GUI configuration program won't let you autologin with mythtv. This is stupid and there's no reason for it. Period. Luckily there's always the command line to your rescue!

```
sudo nano /etc/gdm/gdm.conf-custom

```Change

```
[daemon]
AutomaticLoginEnable=WHATEVER
AutomaticLogin=WHATEVER
TimedLoginEnable=WHATEVER
TimedLogin=WHATEVER
TimedLoginDelay=WHATEVER
```to

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=mythtv
TimedLoginEnable=true
TimedLogin=mythtv
TimedLoginDelay=5
```Also, following the instructions for setting up a MythTV session using openbox is advisable. Just follow most of the instructions from [here]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend") (the previous word is a link if it doesn't look that way) to do that. Don't listen to their stuff about setting up mythtv with your regular user, though. I couldn't get that to work for the life of me. Once again this is stupid. Period. Just change your gdm.conf-custom file as noted above. You WILL have to select mythtv as your default Session, though. I'll leave the specifics of that as an exercise to the reader.

Have fun with your mythTV setup!

This works but gives:

```
INTERNAL ERROR
failed to initialize HAL!
```

---

