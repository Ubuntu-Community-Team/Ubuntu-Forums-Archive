---
title: "No GUI after change of graphics card"
date: 2008-03-09
forum: General Help
---

### Post by allanco on 2008-03-09
Hi
First post and I am a bit of a noobie, despite playing with Linux over the years.
For a couple of months my pc was running fine with Gutsy Gibbon, then I started to get random freezes.
Because this was happening in Windows too (dual boot) I put it down to hardware and after much swapping over of various bits came to the conclusion that the ATI 9550 graphic card was to blame and swapped it out and tried the onboard graphics. However all I got was a black screen which I soon found out after a CTRL Alt something or other was the command line. I then tried an Nvidia FX5200 and got the same black screen.

Some of the messages I saw included the following

"Kinit: No resume image doing normal boot"

"couldn't find package Ubuntu desktop", i think thats when I tried the following:

Sudo aptitude update&&sudo aptitude install ubuntu desktop"  saw this posted elsewhere.

Both the 5200 and onboard graphic cards work if I run the live disc.
I guess its a driver issue but do not know what to try next.
Any help would be greatly appreciated.

---

### Post by taurus on 2008-03-09
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Peter09 on 2008-03-09
Try installing Envy from here : -

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy can be installed from the Gui or from the command line, it can also be run from the command line.

Note - are you able to run from safe-mode ?

PC

---

### Post by allanco on 2008-03-09
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

Many thanks for such a quick response, that did the trick, I have a lot to learn....:)

---

