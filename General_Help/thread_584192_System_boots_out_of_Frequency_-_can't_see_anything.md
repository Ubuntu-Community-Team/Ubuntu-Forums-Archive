---
title: "System boots out of Frequency - can't see anything!"
date: 2007-10-20
forum: General Help
---

### Post by MarksWeb on 2007-10-20
I have no idea why, I've just rebooted after installing the ATi Driver via the 'restricted drivers manager' and now when the system boots it goes out of frequency when it loads the GUI.

I have no idea where to start on this - the only solutions i've found say to login through the command line and run something like 'sax2' but i can't do that if i can't see anything!

PLEASE help me! :D :(

---

### Post by dcstar on 2007-10-20
> **MarksWeb said:**
> I have no idea why, I've just rebooted after installing the ATi Driver via the 'restricted drivers manager' and now when the system boots it goes out of frequency when it loads the GUI.

I have no idea where to start on this - the only solutions i've found say to login through the command line and run something like 'sax2' but i can't do that if i can't see anything!

PLEASE help me! :D :(

CTRL-ALT-F1 when you get the "frequency" message.

---

### Post by MarksWeb on 2007-10-20
I was trying that - maybe i have to wait a little longer...


can you please confirm the command (and process) if i get there please?

---

### Post by dcstar on 2007-10-20
> **MarksWeb said:**
> I was trying that - maybe i have to wait a little longer...


can you please confirm the command (and process) if i get there please?

It should be immediate unless your system has totally locked up - which may be what is happening if the driver install is bad.

Do you have hard drive activity once the screen goes blank?

---

### Post by MarksWeb on 2007-10-20
yeah it just seems to be set to the wrong refresh rate or something...

after booting through grub it runs the usual pre GUI boot then when it'd usually flash up the GUI it goes out of frequency and i've tried getting into F1 through to F5 - none of them worked :(

---

### Post by dcstar on 2007-10-20
> **MarksWeb said:**
> yeah it just seems to be set to the wrong refresh rate or something...

after booting through grub it runs the usual pre GUI boot then when it'd usually flash up the GUI it goes out of frequency and i've tried getting into F1 through to F5 - none of them worked :(

If you boot up into Recovery mode you should be able to get a text login going so you can edit your /etc/X11/xorg.conf file as per all the instructions on how to fix this sort of thing.

---

