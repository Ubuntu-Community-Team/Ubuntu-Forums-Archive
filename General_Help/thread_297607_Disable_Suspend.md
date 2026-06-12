---
title: "Disable Suspend?"
date: 2006-11-11
forum: General Help
---

### Post by xopher on 2006-11-11
Im using Ubuntu Edgy Eft AMD64. My keyboard is a Logitech Internet Navigator.

Now to my problem. When returning from suspend, my system just freezes. And when I reboot, especially my /home gets corrupted.

Now, I really dont need suspend. So how can I disable it once and for all?

And another question, Ive been using my keyboards sleep key to lock my screen. I have everything bound like it has been before, when it worked. Ok, it still works - with a 'minor' twitch. It also suspends my computer.

Is there a way to disable this 'feature' ? I want to be able to bind my sleep key as I have before.

Thanks!

---

### Post by xopher on 2006-11-13
*bump* ](*,)

---

### Post by patonw on 2006-12-05
1. open up gconf-editor (via the alt-f2 run dialog)
2. go to /apps/gnome-power-manager
3. edit the key 'action_button_suspend' to say 'nothing'

if you want to set the button to lock the screen instead you can open up the System Preferences menu on your desktop and run Keyboard Shortcuts.

---

