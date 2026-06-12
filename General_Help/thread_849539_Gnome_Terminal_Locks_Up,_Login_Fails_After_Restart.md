---
title: "Gnome Terminal Locks Up, Login Fails After Restarting X, Must Restart System"
date: 2008-07-04
forum: General Help
---

### Post by GenuineXP on 2008-07-04
I'm having quite an annoying problem I think may be linked to the PulseAudio woes introduced in Hardy.

After experiencing media problems (usually due to Pulse) such as Banshee locking up after watching a YouTube video in Firefox, the Gnome Terminal won't launch properly (I usually launch it in an attempt to kill and restart Pulse). It opens, the window remains blank, and the menu bar remains solid gray. In short, it becomes unresponsive. At this point, I know I'm screwed. :-P

Next, I'll try killing X (Ctrl+Alt+Backspace). It works, and GDM presents the login screen. Upon logging in... well, nothing. It takes about two minutes to see the outline of a broken warning dialog, and never gets all the way. I'm forced to kill X again and restart the computer from the login screen.

This has happened on both my desktop and my brother's desktop (both running Hardy). The hardware is very different, so I don't think that's the issue here.

Any ideas? This is almost making our systems unusable (since Pulse seems to act up *a lot*).

Thanks.

---

### Post by GenuineXP on 2008-07-04
Bump.

---

### Post by GenuineXP on 2008-07-05
Bump.

---

### Post by GenuineXP on 2008-07-05
Bump.

---

### Post by GenuineXP on 2008-07-05
Bump.

---

### Post by GenuineXP on 2008-07-06
Bump.

---

### Post by carl_pr on 2008-07-06
> **GenuineXP said:**
> I'm having quite an annoying problem I think may be linked to the PulseAudio woes introduced in Hardy.

After experiencing media problems (usually due to Pulse) such as Banshee locking up after watching a YouTube video in Firefox, the Gnome Terminal won't launch properly (I usually launch it in an attempt to kill and restart Pulse). It opens, the window remains blank, and the menu bar remains solid gray. In short, it becomes unresponsive. At this point, I know I'm screwed. :-P

Next, I'll try killing X (Ctrl+Alt+Backspace). It works, and GDM presents the login screen. Upon logging in... well, nothing. It takes about two minutes to see the outline of a broken warning dialog, and never gets all the way. I'm forced to kill X again and restart the computer from the login screen.

This has happened on both my desktop and my brother's desktop (both running Hardy). The hardware is very different, so I don't think that's the issue here.

Any ideas? This is almost making our systems unusable (since Pulse seems to act up *a lot*).

Thanks.


i had that issue with the audio and i fix it following this 

[http://ubuntuforums.org/showthread.php?t=776739]("http://ubuntuforums.org/showthread.php?t=776739")


[https://wiki.ubuntu.com/PulseAudio]("https://wiki.ubuntu.com/PulseAudio")

it works for me, now ubuntu doesn't freeze anymore, i am no expert or anything you might wanna try.

---

### Post by GenuineXP on 2008-07-06
Thanks! The first guide you posted there worked very well for me!

I really appreciate it; I'm glad to have this patched up. Audio is working much better now.

---

