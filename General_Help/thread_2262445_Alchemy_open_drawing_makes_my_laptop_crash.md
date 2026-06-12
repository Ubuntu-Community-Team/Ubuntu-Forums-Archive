---
title: "Alchemy open drawing makes my laptop crash"
date: 2015-01-24
forum: General Help
---

### Post by nemonoman on 2015-01-24
[COLOR=#333333][FONT=sans-serif]I'm running Lubuntu 14.10 on an Asus eee pc 1215n

I just installed Alchemy ([/FONT][/COLOR]http://al.chemy.org/) but after about 30 seconds of drawing, I get a black screen, then an error message that looks something like this: "[COLOR=#333333][FONT=sans-serif]*[drm:intel_lvds_enable] *ERROR* timed out waiting for panel to power on*" flashes up on the screen, then the log in page comes back and I can log in to my desktop. The error message is only up for a second, so I think that's the right wording, but is there a log I can access to check?

I'm still an Ubuntu noob, so if there's any other info I need to give let me know. I did some googling and it looks like it might be a kernel issue? ([/FONT][/COLOR]http://bbs.archbang.org/viewtopic.php?id=1862)

---

### Post by nemonoman on 2015-01-26
Bump.

Now every time I start up the laptop I get this error message: 

System problem detected
Do you want to report the problem now?

And when I select Report Problem I get:

Sorry, Ubuntu 14.10 has experienced an internal error.

And when I select show details:
[IMG]https://lh3.googleusercontent.com/-Ed_W6oshbjA/VMZHgNPpw5I/AAAAAAAAQIw/ADJK7nSi5rQ/w410-h546-no/IMG_20150126_135605.jpg[/IMG][IMG]https://lh3.googleusercontent.com/-vh3hcWqrARY/VMZHkMZXItI/AAAAAAAAQI8/ZfTta7PvFb4/w410-h546-no/IMG_20150126_135620.jpg[/IMG][IMG]https://lh3.googleusercontent.com/-8RyPv9gS39c/VMZHl_Z-hSI/AAAAAAAAQJI/yCR8dvXNvtA/w410-h546-no/IMG_20150126_135629.jpg[/IMG][IMG]https://lh4.googleusercontent.com/-uu0tDJixNDY/VMZHpSk9VeI/AAAAAAAAQJg/IWhGpqKhMHU/w410-h546-no/IMG_20150126_135643.jpg[/IMG]


Then if I select examine locally, and run gdb session, a terminal window opens up, but it remains blank.

I completely removed Alchemy but I still get this error every start up, so I don't know if they're connected? Or if I failed to remove Alchemy properly? Any help much appreciated.

---

