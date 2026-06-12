---
title: "PulseAudio suspected to cause freezes"
date: 2008-05-29
forum: General Help
---

### Post by george9233 on 2008-05-29
After my [previous post on the system freezing problem]("http://ubuntuforums.org/showthread.php?t=811492") earlier, I suddenly remembered to checked out the System Log, and found some interesting things:
```

May 29 15:43:11 george-hardy pulseaudio[6222]: alsa-util.c Device hw:1 doesn't support 2 channels, changed to 1.

```

This log message appeared lots and lots of times in the "messages" and the "user.log" part of the System Log, and one or two lines below there is a line indicating 'system restart' in the "messages" part. In the "user.log" part it is immediately followed by a line indicating 'system start up'. I think this has much to do with my freeze problem, but it's not that straight forward.

Can you figure out any clues according to this log message? Thanks a lot.

---

### Post by glenstewart on 2008-08-14
I have also been having freezes, and while disk errors are a candidate, my recent switch to Pulseaudio occurred at a similar time.

This is my messages.log entry:
pulseaudio[8701]: main.c: This program is not intended to be run as root (unless --system is specified).

...and in users.log:
pulseaudio[8710]: module-x11-xsmp.c: X11 session manager not running.
pulseaudio[8710]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.


> **george9233 said:**
> After my [previous post on the system freezing problem]("http://ubuntuforums.org/showthread.php?t=811492") earlier, I suddenly remembered to checked out the System Log, and found some interesting things:
```

May 29 15:43:11 george-hardy pulseaudio[6222]: alsa-util.c Device hw:1 doesn't support 2 channels, changed to 1.

```

This log message appeared lots and lots of times in the "messages" and the "user.log" part of the System Log, and one or two lines below there is a line indicating 'system restart' in the "messages" part. In the "user.log" part it is immediately followed by a line indicating 'system start up'. I think this has much to do with my freeze problem, but it's not that straight forward.

Can you figure out any clues according to this log message? Thanks a lot.

---

### Post by devastian on 2008-11-26
Same around here. I am running Intrepid 64bits and I have Pulseaudio errors just before I restart the PC since gnome freezes completely. I have another  [**_thread_**]("http://ubuntuforums.org/showthread.php?t=993500") open for the same issue and I shared more details there.:(

---

### Post by george9233 on 2008-11-26
I think now its obvious that more work needs to be done on PulseAudio, since the problem still exist in Intrepid.

---

### Post by smdofjmdsfjoiez on 2008-12-25
Same thing 

random freeze with pulse and firefox :(

---

### Post by el_fela on 2009-04-20
Hi folks. I have EXACTLY the same problem on hardy/jaunty amd64 AND i386. I had never checked the user.log before, but now i realized this happens every time the system freezes:

> Apr 20 18:55:03 17-115-191-190 pulseaudio[3161]: alsa-util.c: Device hw:0 doesn't support 2 channels, changed to 10.
Apr 20 18:55:03 17-115-191-190 pulseaudio[3161]: alsa-util.c: Device hw:0 doesn't support sample format s16le, changed to s32le.
Apr 20 18:55:03 17-115-191-190 pulseaudio[3161]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Apr 20 18:55:03 17-115-191-190 pulseaudio[3161]: alsa-util.c: Device hw:0 doesn't support 2 channels, changed to 12.
Apr 20 18:55:03 17-115-191-190 pulseaudio[3161]: alsa-util.c: Device hw:0 doesn't support sample format s16le, changed to s32le.
Apr 20 18:55:03 17-115-191-190 pulseaudio[3161]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.

Im using a PCI M-Audio Delta soundcard. I was thinking about getting rid of pulseaudio completely.

---

### Post by ciaovos on 2009-05-30
I have been getting this log message too:

```
May 30 09:54:14 ciaovos pulseaudio[3445]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
May 30 09:54:14 ciaovos pulseaudio[3445]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.

```Can someone offer a fix or post a link to the fix for this?

---

### Post by Das2009 on 2009-06-12
Video was freezing (vlc). I'm on Ubuntu 8.04 (hardy).
Tried out various possibilities as suggested on various forums/resources. 
Nothing worked.
Uninstalled pulseaudio (and so ubuntu-desktop)
Reinstalled ubuntu-desktop (was prompted for the cd)
Restarted the system. The video no longer freezes.
**Confirm** and try this out.

---

