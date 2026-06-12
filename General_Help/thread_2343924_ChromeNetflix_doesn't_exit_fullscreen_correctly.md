---
title: "Chrome/Netflix doesn't exit fullscreen correctly"
date: 2016-11-20
forum: General Help
---

### Post by jon-carmicheal on 2016-11-20
Chrome was running fine for me for a long time while I was on Ubuntu 16.04.  Recently I upgraded to 16.10, and now Chrome is not able exit fullscreen properly.  This is especially problematic as I use Chrome for Netflix.  There is another [post]("https://ubuntuforums.org/showthread.php?t=1867020") that reported what seems to be the same issue.  And a solution there helps a little, but only for a short time:

> I ended up replacing this section:
(this is a from a new generated ~/.config/google-chrome/Default/Preferences)

"browser": {
      "window_placement": {
         "bottom": 586,
         "left": 9,
         "maximized": false,
         "right": 1013,
         "top": 29,
         "work_area_bottom": 600,
         "work_area_left": 0,
         "work_area_right": 1024,
         "work_area_top": 23
      }
   },

It seems to work for a while, but the Preferences file gets overwritten by Chrome and loses the customizations.  Then I am unable to correctly exit fullscreen again.  Currently what is happening is Chrome will return its pre-fullscreen size, but the Unity launcher and top bar are missing and I cannot switch to any other applications.  All I can do is Ctrl-Alt-F1 and "sudo service lightdm restart."  

I've tried completely uninstalling Chrome then re-installing it, but the issue persists.

---

### Post by jon-carmicheal on 2016-11-22
Edit: The issue is still present even after what I tried below:

> In case it helps anyone with a similar situation, I think I was able to work around the issue by changing the Chrome theme from "GTK+ Theme" to "Classic Theme."  Do this by opening Chrome and going to Settings -> Appearance -> "Use Classic Theme."  I also selected "Use system title bar and borders," but that by itself didn't seem to resolve the issue.

---

