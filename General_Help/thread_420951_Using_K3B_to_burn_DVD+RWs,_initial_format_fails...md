---
title: "Using K3B to burn DVD+RWs, initial format fails.."
date: 2007-04-24
forum: General Help
---

### Post by billdotson on 2007-04-24
Ok so this is a clean install of Feisty.. my SATA Lite-On SH-16A7S burner's fstab entry is:
```

/dev/scd0      /media/cdrom0            udf, iso9660 user, noauto          0             0

```

When I insert a blank DVD+RW into the drive it mounts on the desktop and hsows a blank DVD+RW, then I open K3B (version one from repositores using synaptic)
and tell it to burn some data. 
a dialog box comes up and says "pre-formatting", and then shortly after it says "erase failed".
Then the disc tray comes out and a dialog box comes up that says "Found media: no medium present, please insert empty media   Lite-On DVDRW SH-16A7S (/dev/sdc0)"

It has four options Load, Force, cancle and another one I cannot remember.  I chose cancel on a couple and now when I insert those discs they won't automount anymore.  Then I tried another DVDRW and when it got to the dialog box with the 4 options I told it to load.  Then the disc tray went back in and K3B started burning the DVDRW.  It is currently burning right now and I have it set to verify the data after it is done writing.  Hopefully it will work.  

What is going on?  When it tries to pre-format is it not unmounting the DVD?  Should I manuall umount in the terminal before telling K3B to burn?  Please help.. I have pretty much waste $15 on DVD+RWs because of errors like this.. I have gotten 2 good burns out of ~12 DVD+RW.  You would think K3B would automatically umount the drive before formatting the media dn then mount it when it is time to burn..

Anyway thanks! I hope I can get burning to work in Linux.. one less thing I have to use Windows for.

---

### Post by billdotson on 2007-04-24
well that burn I started last night finished but the verify failed.  Maybe I need to unmount the media (not eject) before I tell a project to start..

---

