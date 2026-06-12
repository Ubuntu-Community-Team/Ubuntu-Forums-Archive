---
title: "Bluetooth Mouse"
date: 2007-04-11
forum: General Help
---

### Post by RelativelyQuantum on 2007-04-11
Hello all.

I'm trying to configure my Targus bluetooth mouse to communicate with my computer,  a Sony Vaio VGN-TX750P running Ubuntu 6.10. When I enter the command

"hidd --search"

and my comupter detects my mouse, I get this message: 

"HID create error 13 (Permission denied)"

I'm not certain where to go from here. The mouse usually requires the input of a pairing key, but I don't see where I can enter that.

If anyone can help me out, I would greatly appreciate it.

---

### Post by nahham on 2007-04-20
As for "Permission Denied" you should run the hidd command as root.  Try sudo hidd --search.  When I connect my bluetooth mouse I first scan for it while it is in discoverable mode (you know holding the ridicously small button for a while) and then using 

> hcitool scan

I then find out the MAC address of the mouse and then issue the command

> sudo hidd --connect 00:00:00:00:00

My mouse does not need a pairing key but you should find some useful information at this post [http://ubuntuforums.org/showthread.php?t=75978](http://ubuntuforums.org/showthread.php?t=75978)

I hope this helps,

nahham..

EDIT: found a HOWTO here [http://ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+mouse](http://ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+mouse)

---

