---
title: "need script for touchpad to work on startup"
date: 2021-03-14
forum: General Help
---

### Post by jlh68 on 2021-03-14
I have an Acer Aspire One 725 netbook with 20.04.  On every boot I have to do [Fn]+[F7] to get the touch pad (track pad) to work.  For a netbook the touch pad should work on start up as most will not get a mouse out and operate the mouse on one's lap.  Mouse works on start up, just not the track pad

Does anyone have a script that could be invoked on startup? Or the instructions on how to write and install said script?

Using POP!_OS on System76 LAPTOP not this Netbook

---

### Post by daniewicz on 2021-03-14
From the command line type:

synclient

What do you see?

---

### Post by jlh68 on 2021-03-16
Here is the result:
"Command 'synclient' not found, but can be installed with: sudo apt install xserver-xorg-input-synaptics"

BTW my netbook has a ETPS-2 Elantech Touch Pad not a Synapatic pad.  I also read that Ubuntu removed the synaptic instructions and replaced it with *libinput* in  one of the updates.  I think it was Ubuntu 18.04 or thereabouts.

---

### Post by dunivixs on 2021-03-16
Do you have installed synclient by the command : ```
sudo apt install xserver-xorg-input-synaptics
```

---

### Post by daniewicz on 2021-03-16
Have a look at this thread. Looks like some edits can be made to xorg.conf

[https://forums.linuxmint.com/viewtopic.php?t=279044](https://forums.linuxmint.com/viewtopic.php?t=279044)

---

