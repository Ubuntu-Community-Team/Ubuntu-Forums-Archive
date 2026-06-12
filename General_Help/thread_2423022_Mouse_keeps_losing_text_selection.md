---
title: "Mouse keeps losing text selection"
date: 2019-07-16
forum: General Help
---

### Post by honzi97 on 2019-07-16
Hi,
whenever I select text, the mouse keeps losing the selection. This does not happen when I use the touchpad. Apparently, there are quite a few people with this issue, but I couldn't find any solution for it.
The mouse itself works fine.

---

### Post by again? on 2019-07-16
You do know the primary selection is lost when you close the application where you made the selection?

---

### Post by honzi97 on 2019-07-16
Maybe I didn't explain it clearly.
Let's say I'm reading an article and I want to copy the text.
I start at the beginning of the article, and drag the mouse down (keeping the left mouse button clicked)to select the whole article.
When I'm at the middle of the article, the text selection suddenly doesn't start from the beginning anymore, but from the middle.
It's as if I let go of the left mouse button, but I did not.

---

### Post by Impavidus on 2019-07-16
Maybe the mouse button makes poor contact. It should also affect drag-and-drop actions, but rarely other things.

---

### Post by honzi97 on 2019-07-16
The mouse works fine. I tried multiple mice, they all work fine on Windows.
Yes, it does affect drag-and-drop actions, too.

---

### Post by Autodave on 2019-07-16
For long passages, try scrolling from bottom to top.

---

### Post by honzi97 on 2019-07-16
Are you serious?
I can't even select a sentence.

---

### Post by uRock on 2019-07-16
Is the trackpad disabled? Is it clean? Are you trying this on multiple sites or only on one certain site?

---

### Post by honzi97 on 2019-07-17
The trackpad is fine. It's not just the browser, it's everywhere

---

### Post by again? on 2019-07-17
In terminal run
```
xev -event button
```
In the window hold down left mouse and then move the mouse around.
You shouldn't see a release event until you actually release the button.

---

### Post by honzi97 on 2019-07-17
Actually, I do see release events without actually releasing the button

---

### Post by again? on 2019-07-17
Is it a wireless mouse?
Test with xev in a new user account or in a live usb....
or test another mouse with xev.

---

### Post by honzi97 on 2019-07-21
It is a wired mouse. I tested multiple mouses.
This problem does not occur in a new user account.
Any suggestions on how to fix this for my current account?

---

### Post by again? on 2019-07-21
Do you do much customization?
Look at your gnome-shell extensions.

You can reset some user settings with gnome-tweaks by right clicking the panel icon.
```
sudo apt install gnome-tweaks
```
[ATTACH=CONFIG]283655[/ATTACH]

Try these one at a time logging out/in each time and testing with xev.
**1**. Using Tweaks icon menu, reset to defaults.
**2**. Using Tweaks icon menu, disable extensions
**3**. This terminal command is more thorough and will affect customization you may have made to more applications.
[INDENT]It will reset any dconf setting from /org/gnome/ including Gtk theme, icon theme, wallpaper, power settings, 
mouse settings, custom keyboard shortcuts, and more.
```
dconf reset -f /org/gnome/
```[/INDENT]

---

### Post by honzi97 on 2019-07-23
After trying xev in the other user account, the problem seems to be fixed for my user, too. Any ideas on how that might have fixed it?

---

