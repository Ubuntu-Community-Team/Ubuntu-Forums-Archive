---
title: "Lubuntu 17.04 Dual Monitor Icon Duplication"
date: 2017-10-04
forum: General Help
---

### Post by electrosteam on 2017-10-04
My Dell laptop has a VGA external monitor with the mouse nicely moving between the two screens.
The taskbar is on the external and all the icons are duplicated, except the Documents folder is only on the external.

Where/how can I find the configuration files that determine what is on each screen ?

John

---

### Post by slickymaster on 2017-10-04
Thread moved to **General Help** for a better fit

---

### Post by RobGoss on 2017-10-04
Have you tried looking in the display settings that's were you can choose what display is your primary and so on

---

### Post by electrosteam on 2017-10-05
Rob,
The display settings relate to monitor resolution, external On/Off, and external Left/Right/Above/Below.
There is a tick box to make both screens the same, but removing the tick results in other non-acceptable combinations.
John

---

### Post by RobGoss on 2017-10-05
Do you have double icons on both screens?

---

### Post by electrosteam on 2017-10-06
Rob,
The same 7 icons are shown on the LH screen and the RH screen, either copy can be selected to launch the target.
Icons: Firefox, Thunderbird, KiCad, LibreCad, LXTerminal Rubbish Bin, KiCad drawing.

The LH screen has additionally: Task Bar, Documents icon.

All four desktops are the same.
Folders can be dragged between screens.

John.

---

### Post by RobGoss on 2017-10-07
That's really strange I've only encountered something like this when my resolution was not correct, but still this should not happen. I was reading in another thread that some users were having this same issue while having **nemo** file manger installed once they uninstalled it the issue when away

---

### Post by electrosteam on 2017-10-07
Rob,
Thanks for taking the time to comment.
Synaptic lists nemo as available, but not installed.

Both screens seem entirely normal for resolution.
John

---

### Post by dragonfly41 on 2017-10-07
I'm not sure if this helps you or is relevant to your situation. Our common factor is we are using Dell laptop with VGA second monitor.

When my Dell Inspiron 1720 laptop display failed I added an external VGA monitor (as you have done) so that I could continue working.   On booting up I had to use the <Super-key>+<p> key sequence to toggle to the external monitor.

There is some discussion on this key sequence here.

[https://askubuntu.com/questions/68463/how-to-disable-global-super-p-shortcut/585204](https://askubuntu.com/questions/68463/how-to-disable-global-super-p-shortcut/585204)

In particular install dconf-tools and follow advice in that discussion, using dconf-editor.

Also run command xrandr.

I am now in the process of migrating from laptop to Dell 3268 Tower PC.

---

