---
title: "Compiz, problem with desktop"
date: 2008-05-15
forum: General Help
---

### Post by silverdulcet on 2008-05-15
Please see the screenshot below. Any idea what I did to make the desktop zoom  out like that? Not sure how to fix it.

---

### Post by sdennie on 2008-05-15
Have you accidentally hit Super-E (The windows key + e).  The screenshot sort of looks like you've gone into Expo mode with a single desktop.

---

### Post by silverdulcet on 2008-05-15
> Have you accidentally hit Super-E (The windows key + e). The screenshot sort of looks like you've gone into Expo mode with a single desktop.

I might have. When I hit Super-E again it goes back to normal for a second and then returns to zoomed out. Is there some config file or configuration setting I can reset? Metacity works fine, but whenever I start up compiz it goes to that zoomed out desktop.

---

### Post by sdennie on 2008-05-15
You could install:

```

sudo apt-get install compizconfig-settings-manager

```

Then, go to System->Preferences->Advanced Desktop Effects Settings.  One thing you could try would be to disable the Expo plugin but, it may be some other setting that will fix it.

---

### Post by silverdulcet on 2008-05-15
> Then, go to System->Preferences->Advanced Desktop Effects Settings. One thing you could try would be to disable the Expo plugin but, it may be some other setting that will fix it.

That did not fix it either. The other strange thing is the mouse behaves as if the window is full screen. Meaning I can interact with the desktop, but my  mouse cursor is actually clicking a couple inches down and to the right of where it is displayed on the screen. I'll keep looking for settings in that menu. 

If anyone else knows of the easiest way to reset everything to default or perhaps what specific setting I need to change let me know!

---

