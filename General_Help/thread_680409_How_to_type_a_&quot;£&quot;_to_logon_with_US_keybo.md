---
title: "How to type a &quot;£&quot; to logon with US keyboard layout"
date: 2008-01-27
forum: General Help
---

### Post by MrGutsy on 2008-01-27
HELP! I live in the U.K. During ubuntu install I somehow ended up with US keyboard layout. (thought I selected UK, but maybe not). No problem I thought, and set the layout to UK in the System|Preferences|keyboard. At some point I changed my password to include a "£" (pound). It all worked fine administering stuff while I was logged in, but next time I went to log in, on the login screen,  I can't type a "£" as ubuntu thinks I have a US keyboard until I log in. That is the only account with admin rights, so if I can't type a "£", I'm looking at a complete reinstall and lose all my data!
Might it be possible to log on as another user, with UK keyboard, use sudo to login as my admin account and somehow set the keyboard to UK from there?

---

### Post by danwood76 on 2008-01-28
Restart your PC and at grub press escape and load the ubuntu recover mode.
then once thats loaded up you will be logged in as root.

At this point you have a couple of options, you could change your users password or reconfigure xorg to use the gb layout (best option).

So at the command prompt type:
```
dpkg-reconfigure xserver-xorg
```
this will give you a graphical menu guiding you through the xorg config, when prompted type gb as your keyboard layout and I think its 105 key layout also.

Then once that has saved reboot and your layout should be UK, if it isnt it might be selectable in the bottom right hand corner.

regards,
Danny

---

### Post by MrGutsy on 2008-01-29
That worked! thank you so much! When logged in it prompted me asking whether to keep XSettings or Gnome settings, I chose XSettings and it's fine now. I 'm back in and don't have to reinstall. Cheers!

---

### Post by danwood76 on 2008-01-29
mark the thread as solved if you could (under thread tools) so that if other people have these problems they can find the solution easily.

regards,
Danny

---

