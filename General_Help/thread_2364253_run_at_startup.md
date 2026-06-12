---
title: "run at startup"
date: 2017-06-20
forum: General Help
---

### Post by bjlockie on 2017-06-20
I'm trying to set the profile of my video card on bootup.
The command is:

```
echo 0f >/sys/kernel/debug/dri/0/pstate
```

I tried adding it to /etc/rc.local:

```
# ls -l /etc/rc.local 
-rwxr-xr-x 1 root root 363 Jun 20 19:23 /etc/rc.local

```
I also tried making /etc/X11/Xsession.d/100_video_card:

```
# ls -l /etc/X11/Xsession.d/100_video_card
-rwxr-xr-x 1 root root 41 Jun 20 19:41 /etc/X11/Xsession.d/100_video_card
```

---

