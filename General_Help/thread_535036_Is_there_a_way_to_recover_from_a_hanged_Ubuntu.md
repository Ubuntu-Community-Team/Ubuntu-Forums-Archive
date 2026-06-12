---
title: "Is there a way to recover from a hanged Ubuntu?"
date: 2007-08-26
forum: General Help
---

### Post by ekravche on 2007-08-26
Ubuntu seems to hang for me for native games. I'm actually shoked to see that Ubuntu can hang and crash, just like older versions of windows. I don't think XP ever hanged for me like this. Anyway, I'm just wondering if there is a way to recover from this, without having to push the off button on the power supply? Seems like it's a kernel issue, because the entire OS becomes unresponsive...

---

### Post by gletob on 2007-08-26
alt + Print Screen + O

---

### Post by mridkash on 2007-08-26
ctrl-alt-backspace

it'll restart desktop, not the computer. Fast and easy!

---

### Post by merlinus on 2007-08-26
Of course, if the keyboard is frozen as well as the mouse, only a hard power-off will do!

Fortunately I have never had problems with restarting, unlike doing this with windows.

-merlin

---

### Post by southernman on 2007-08-26
One word... rseiub. Don't understand? Can't read between the lines? ;) No worries!

Have a look at this page and print it off. It's much better than a hard reset or power down... providing the keyboard isn't hung as well:

[http://en.wikipedia.org/wiki/Magic_SysRq_key#Emergency_Reboot_-_Raising_Elephants_Is_So_Utterly_Boring]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Emergency_Reboot_-_Raising_Elephants_Is_So_Utterly_Boring")

---

### Post by astralsin on 2007-08-26
i think the more important issue here is figuring out why you're hanging in the first place.  what kind of video card do you have and what driver are you using for it?  i've had the same problem on my onboard nvidia 6600 and the nv drivers in the past.  get to a command line do ctrl-alt-F4 and log in there.  then install the proper video card drivers for whatever card you've got (i'm assuming its ati or nvidia) and see if that stops the freezing... you might have to edit xorg.conf too to use the newly downloaded driver

---

### Post by Lord Illidan on 2007-08-26
Same here..find out what is causing the problem first, before complaining. Could it be video drivers?

---

