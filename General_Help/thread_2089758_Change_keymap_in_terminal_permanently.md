---
title: "Change keymap in terminal permanently"
date: 2012-11-30
forum: General Help
---

### Post by sojakob on 2012-11-30
I am encountering a problem with my keymap settings.
I have two keyboards connected to my machine, one over infra-red the other in an USB port.

The one that is connected to the USB port have default keyboard layout set as Danish (which i prefer). The infra-red keyboard has default layout set as English.
I can change the layout of the infra-red keyboard to Danish by using the command:
```
setxkbmap dk
```as suggested in [[this thread]("http://ubuntuforums.org/showthread.php?t=1786314")]. But this is only a temporary fix and default keymap is reloaded after reboot.

Here's the question: How can i sustain a change in keymap settings between reboots?

... and more in for the sake of understanding of the problem: What is the difference between **loadkeys** and **setxkbmap**?

Best wishes.

---

### Post by sojakob on 2012-12-01
bump :-)

---

### Post by JimS on 2012-12-01
Here is how I was able to create a dual language (EN & DK) keyboard.
I change languages by pressing ctrl and shift together
with my left pinky finger.  EZ PZ.

Go to etc/default/keyboard
XKBMODEL="pc105"
XKBLAYOUT="us,dk"
XKBVARIANT=""
XKBOPTIONS="grp:ctrl_shift_toggle"

Sorry, but I don't know how to put a country icon
in panel in a xfce desktop.  Gnome should be easy.

mvh
JimS

---

### Post by sojakob on 2012-12-01
Thanks for answering :-)

I'm not trying to make a dual language keyboard. I suppose that i am trying to set the same language for two keyboards. Sorry for being unclear.

Anyway thanks for guiding me to the /default/keyboard file. Mine looks like this:

```
XKBMODEL="pc105"
XKBLAYOUT="dk"
XKBVARIANT=""
XKBOPTIONS=""
```

And I suppose that is how I want it to look like, as I am trying to load Danish as default for both keyboards...

---

### Post by sojakob on 2012-12-03
... however, one keyboard is switched to English after every reboot. It is starting to annoy me a bit.
A hint to some documentation on **xkb** other than the man pages would also be of great help :-)

---

### Post by sojakob on 2013-02-24
any body have experience with having two keyboards defined in xkb?

---

