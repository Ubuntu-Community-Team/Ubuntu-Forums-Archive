---
title: "unable to login"
date: 2017-03-24
forum: General Help
---

### Post by HappyAsHellas on 2017-03-24
Ubuntu 16.04
Intel processor and sandybridge mobile graphics
8 gig ram

I recently ran a security upgrade and after rebooting I can no longer login as the screen just keeps looping to the login screen. I can use a guest session so I'm guessing it's not a graphics issue. What is really puzzling is that I can log in to my account if I use Ctrl + Alt + F1, but then I'm left with a blank screen and no idea how to get into the desktop.  I have tried running sudo lightdm but then have no input. I am at a loss as to how to solve this and understand it is not a new problem. Any help would be greatly appreciated, and is there a way to stop this happening in the future or should I view any update with trepidation?

---

### Post by Impavidus on 2017-03-24
This means the graphical session fails to start. The most common reason is that one of the files .ICEauthority or .Xauthority has become owned by root or had its permissions messed up. This may result from improper use of sudo. Use ctrl-alt-F1 and log in to the command line, then use```
sudo chown your_username:your_username .Xauthority
sudo chown your_username:your_username .ICEauthority
chmod 600 .Xauthority
chmod 600 .ICEauthority
```Substitude your username (or group name after the colon, but that should normally be the same). If that doesn't work, we have to dig deeper.

You may want to update your forum profile. It still shows you run Ubuntu 14.04.

---

### Post by HappyAsHellas on 2017-03-24
It says file directory doesn't exist or not found?

---

