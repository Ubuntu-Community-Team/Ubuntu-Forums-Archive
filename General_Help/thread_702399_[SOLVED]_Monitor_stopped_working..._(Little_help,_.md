---
title: "[SOLVED] Monitor stopped working... (Little help, please?)"
date: 2008-02-20
forum: General Help
---

### Post by chazdraves on 2008-02-20
Well, I was just looking at another post in the general help here talking about how they couldn't get 75Hz refresh rate to work with their monitor in Ubuntu even though the monitor supported it. One of the posters said they oughta add "1280x1024@75" to their xorg.conf under the Display section. I've had my monitor (an Acer AL1916W) working great at 1440x900 since Ubuntu installed, but it never let me go to 75Hz.

When I opened xorg.conf, I noticed I didn't even have a "Subsection Modes" under my Display section, so I added it in and entered "1440x900@75". I then wrote the file, exited the terminal, and restarted X. When I came back, I got a low resolution warning and could only choose 8x6 or 640x480. I tried going back to "Plug & Play" for the monitor, but it won't let me. I tried selecting Acer AL1916w from the list and clicking "Widescreen" but the only options are 640x480 @76, 8x6@76, 1024x768@76 and 1920x1200@76... I can't get the bugger back... Heck, I'll take 60Hz again, I just want my 1440x900 back :)

Thanks in advance!
- Chaz

---

### Post by chazdraves on 2008-02-20
Well, I guess I somehow fixed it. Sorry for the bother!

- Chaz

---

