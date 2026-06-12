---
title: "HELP! i cant see my desktop!"
date: 2008-03-24
forum: General Help
---

### Post by darki3lade on 2008-03-24
i was trying to set my refresh rate higher and I accidentally had it set to the wrong monitor and set the refresh too high!

86.4/85.4 Try another resolution

keeps flashing on my screen, its a KDS X Flat or something

Ive tried restarting and it will boot up normal but just after the ubuntu logo and loading bar go away that message comes up and I cant do anything cuz I cant see my screen!

I just go this computer and I really cant afford to have it broken right now.  Please help me!

---

### Post by bwhite82 on 2008-03-24
Boot into single-user mode or "safe mode" (second option down on the grub boot list). Once you're at a prompt, use the 'nano' text editor to open xorg.conf (i'm assuming you've changed the value there) using this:

> nano /etc/X11/xorg.conf

Scroll down and change back the refresh rate (under 'screens' section). Hit CTRL+x then ENTER to save the file.

Try out your changes with:

> startx

---

### Post by Sam Lars on 2008-03-24
When that appears, press
```
Ctrl+Alt+F1
```
You will get a prompt to log in.  Do that, and then do this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Follow the instructions and it should come back up like you want it.

---

### Post by darki3lade on 2008-03-24
i dont think i messed with the Xorg or anything i was using the system tab and then i cant really remember but i went to switch my monitor from plug and play to what it really was and it gave me the option of a higher refresh rate so i clicked on it then it said i needed to log out, I did and now my monitor says that the frequency is out of its range and that i need to try a different resolution... if i unhook and rehook my monitor back in will that reset it to plug and play?

---

### Post by Sam Lars on 2008-03-24
No, that won't do it, you'll have to do what I or darki3lade suggested.

---

### Post by Patb on 2008-03-24
> **darki3lade said:**
> i dont think i messed with the Xorg or anything...
Darki, although "you" didn't mess with Xorg, your system seems to have done just that when you were resetting your refresh rate.  Have to tried what Sam Lars suggested?  If not, try it but with one small addition: After you press Ctrl-Alt-F1 make a back up copy of your xorg file with:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
```
Then continue as Sam Lars suggests.  

Let us know if that does not work.  

Cheers, Pat.

---

