---
title: "PS/2 Keyboard Dies"
date: 2014-05-01
forum: General Help
---

### Post by Zukaro on 2014-05-01
Recently I got a new keyboard and I use a PS/2 connector for it (as this allows me to have N-key rollover as well as turn my computer on by pressing CTRL-ESC (while I don't necessarily NEED those features, I like to have the option; plus it frees up a USB port)).

Once in awhile my keyboard will just completely die under Ubuntu and I don't know why.  I know it's not the keyboard itself, as it works fine under Windows, so I don't know what's going on with it in Ubuntu (I suspect it has to do with the PS/2 port specifically and that using USB would fix the issue, but I'd rather use PS/2 so I was wondering if there's anything I can do to fix it).  It'll be fine for an hour or two, maybe three, and then suddenly give up and I'll have to restart the computer to fix it.  However, when I attempt to play games it seems to just immediately die less than 10 minutes later.

I was wondering if anyone had any ideas as to what may be causing this issue and any ideas on how to fix it.

---

### Post by tgalati4 on 2014-05-01
Look through the log files in /var/log for clues.  Also dmesg.  Open a terminal.

Right after the keyboard freeze:

```
dmesg | tail -50
```

Only post keyboard-related errors, not entire log files.

Check the pins on your keyboard cable.  Slightly bent pins can cause disconnects.  Since the PS/2 port is a serial port with smaller pins, any disruption of the signal can cause the keyboard to go offline.  USB is hotplug.  Serial ports are not.  If you lose the syncronous signal, it goes offline and stays offline until a reboot.  Quite annoying.  USB solved that with an asyncronous polling that enables hot plug capability.  To reset the USB device, simply unplug and plug it back in.

It's a mystery as to why your keyboard is failing.  I would check the capacitors on the motherboard and clean out the machine of dust bunnies.

---

### Post by Zukaro on 2014-05-02
k
(I will be back as soon as my keyboard dies :razz: which surprisingly hasn't happened yet and I've been using it quite awhile today)
Last I checked my motherboard it was fine (which wasn't too long ago);  also cleaned out the dust pretty recently too and upon looking in the  case it doesn't seem to have gotten much more since I last cleaned it.

I somewhat doubt it's the PS/2 port itself though, as it works fine  under Windows.  So I have a feeling there's some software issue here.

I looked in the dmesg log and found this, although I'm not sure it's related or not (also not sure how old this log is :V)

```
[    0.799714] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.799715] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
```

---

### Post by tgalati4 on 2014-05-02
Check your BIOS and see if there is a joystick setting.  Try setting it to "Active".  PnP is Plug-and-Play and your keyboard is trying to identify itself to the computer, but the driver is getting confused.  So either disable PnP using a boot switch or see if there are PnP settings in the BIOS.

---

