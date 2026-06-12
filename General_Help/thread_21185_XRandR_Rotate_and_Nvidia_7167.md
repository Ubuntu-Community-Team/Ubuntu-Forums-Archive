---
title: "XRandR Rotate and Nvidia 7167"
date: 2005-03-20
forum: General Help
---

### Post by Pyroman[FO] on 2005-03-20
I'm running Ubuntu Hoary and I have installed the nvidia drivers from the instructions [here](http://www.ubuntuforums.org/showthread.php?t=21111).

The problem I'm seeing is that when I try to rotate the display (which is supposed to be supported in this driver release), I get the following message.

```
$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

Has anyone gotten rotate to work with the new drivers?

---

### Post by Pyroman[FO] on 2005-03-20
I obviously didn't read the manual, as you have to set 

```
        Option          "RandRRotation"      "on"
```

under the "Device" section of the xorg.conf file.  It works great now.

---

