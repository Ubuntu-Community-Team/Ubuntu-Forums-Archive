---
title: "Sound not working"
date: 2015-11-15
forum: General Help
---

### Post by radu-stochitoiu on 2015-11-15
After inserting my headphones the sound stopped working and I have tried everything on the internet but I couldn't fix it yet.
If you helped me, I'd be so grateful.

I know there are many other posts related to this, but nothing worked yet.

Thanks

---

### Post by pqwoerituytrueiwoq on 2015-11-15
[FONT=courier new]rm -rf ~/.config/pulse/[/FONT]

logout then login

that should reset your sound config

---

### Post by radu-stochitoiu on 2015-11-16
Still not working. Thanks for trying though.

---

### Post by pqwoerituytrueiwoq on 2015-11-16
try this:
```
kill -9 pulseaudio; start-pulseaudio-x11
```

---

### Post by radu-stochitoiu on 2015-11-16
I used "[COLOR=#000000][FONT=courier new]rm -rf ~/.config/pulse/". [/FONT][/COLOR]It repaired itself after two or three reboots (and switching between Linux and Windows a few times). 
Thanks a lot!

---

### Post by pqwoerituytrueiwoq on 2015-11-16
if it happens again give this a try
[FONT=courier new]kill -9 pulseaudio;rm -rf ~/.config/pulse/[/FONT]
pulse audio should respawn when killed (at least it does here)
i would expect it to take at least enough time as deleting a few files to complete that process

---

