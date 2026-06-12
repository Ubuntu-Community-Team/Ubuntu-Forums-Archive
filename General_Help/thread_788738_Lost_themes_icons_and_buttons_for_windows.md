---
title: "Lost themes icons and buttons for windows"
date: 2008-05-10
forum: General Help
---

### Post by jrekkedal on 2008-05-10
Alright everyone, I have been looking over the boards for hours along with google and have come up empty.  I hope someone out there is able to help me out.


Things were working fine for the first couple of days and then I started to see issues.

I am running Hardy Heron, NVidia GeForce (can't remember specific card this late) with no visual effects in use. Heck, I haven't even gone to that screen since installing 8.04, but I've lost all my icons in the panel drop downs as well as the close "x" and other functional buttons in the right hands of windows.

I cannot select any other themes in the appearance section that make a difference.  I've used aptitude to try and reinstall gdm, and various other parts of gnome to no avail.

Attached are screens of what my screen looks like... please help.:confused:

---

### Post by rubicon on 2008-05-10
Try to install/reinstall gtk2-engines-* (well, not necessary all of them, but just some) and look in theme selection dialog then.

---

### Post by jrekkedal on 2008-05-10
I went though the installs on Synaptics and just for giggles reinstalled the gtk2-engines- and the theme dialog looks the same as always.

I changed the theme to another one available but to no avail.  I am still missing my "X" and minimize/maximize buttons.

Another weird symptom I found is that I cannot play any of the previous media files I once could.  This is to include all movie files and mp3's that were working just the other day.

I swear to god when I say I didn't make any changes previously but I do recall an error just prior to this happening that was only visible for a second.  It say something to effect of an error starting "human clearlooks"?

---

### Post by jrekkedal on 2008-05-10
New symptom to mention now.  I rebooted a few times and have noticed this message has started to appear:

The configuration defaults for GNOME power manager have not been installed correctly. Please contact your computer administrator.

I didn't even TOUCH power manager at any given time.  So far I 'm not very impressed with Hardy :(

---

### Post by rubicon on 2008-05-10
Sorry to hear that...

Try to reinstall gnome-power-manager. Hopefully, this will help.

---

### Post by jrekkedal on 2008-05-11
Ok, the good news is that last fix was able to get the gnome power manager up and running. So thank you rubicon!

If I could get my themes and buttons back I would be a very happy man. Any further ideas?

---

### Post by RJARRRPCGP on 2008-05-11
That's NOT normal! I would check your RAM with Memtest86+ (on the Ubuntu live CD) and HDD for errors.

---

### Post by snatsuoh on 2008-09-03
Hi,

I had the same problem. My Ubuntu cannot work using better visual effects. I have an HP tx2114 (amd turion 64), ubuntu 8.04.

What I did to have my minimize and close buttons? I just chose the Normal Visual effects.

In the Menu, choose System > Preferences > Appearance. Select the Visual Effects tab, then choose Normal. After this my buttons came back.

I am still searching for a fix to have my themes back...

---

