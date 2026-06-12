---
title: "Black desktop problems after lockscreen"
date: 2007-11-05
forum: General Help
---

### Post by experience on 2007-11-05
After locking the screen, when I login back, I only got a black desktop with the default upper and lower panels. New applications can run normally, But the documents or windows I left open before the lockscreen action get lost.
Plus: I can't open any items under the "Places" menu. When I clicked on it, nothing happened.

I can repeat the problem. How can I indentity it, or even solve it?

---

### Post by experience on 2007-11-05
Can anybody help, please?

---

### Post by avik on 2007-11-05
Are you using compiz (visual effects)?

---

### Post by experience on 2007-11-05
Yes, I am. But I have tried the lockscreen-and-login-back action when the compiz is turned off.

---

### Post by santiagoward2000 on 2007-11-05
In Xubuntu I had this problem. The thing was that Xfdesktop was disabled. To get it back on, I went to "Desktop Preferences" and checked "Allow Xfce to mahage the desktop", but I don't know how that would be done on Gnome. Sorry.

---

### Post by experience on 2007-11-05
Thank you for your reply. I search in my Ubuntu System Preferences and Administration menus. Unfortunately, I didn't find anything contained similar options.

---

### Post by santiagoward2000 on 2007-11-05
> **experience said:**
> Thank you for your reply. I search in my Ubuntu System Preferences and Administration menus. Unfortunately, I didn't find anything contained similar options.

If you go to System, Settings, isn't there anything like "Desktop Preferences" or similar?

---

### Post by experience on 2007-11-05
No. As far as I know, ubuntu made the system>apperence to handle some preferences about desktop including theme, background, fonts, interface and Visual effects.

---

### Post by experience on 2007-11-05
What log files or other trace information do I have to post helping finding the problem?

---

### Post by santiagoward2000 on 2007-11-05
> **experience said:**
> No. As far as I know, ubuntu made the system>apperence to handle some preferences about desktop including theme, background, fonts, interface and Visual effects.

Hmm, sorry, but I can't help you here, but I'm not used to Gnome. I'm sure there must be a command to get it running, but I can't find it anywhere.

---

### Post by experience on 2007-11-05
> **santiagoward2000 said:**
> Hmm, sorry, but I can't help you here, but I'm not used to Gnome. I'm sure there must be a command to get it running, but I can't find it anywhere.

Thank you, I believe there will be a way to solve the problem.

---

### Post by experience on 2007-11-05
I might be something wrong with the nautilus. when I
```
killall nautilus
```
I got my wallpaper back and the menu items under Places works again, I will look for some further solutions to the problem.

---

### Post by santiagoward2000 on 2007-11-05
> **experience said:**
> I might be something wrong with the nautilus. when I
```
killall nautilus
```
I got my wallpaper back and the menu items under Places works again, I will look for some further solutions to the problem.

Well, I'm glad it's working now! I hope it stays that way...

---

### Post by experience on 2007-11-05
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150471)

The problem is related to the bug above. Anyone reads the post can try the workarounds there, but It is still working on the way, and final solution is not decided yet. You can help!

---

