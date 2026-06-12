---
title: "Is X frozen, in that case ?"
date: 2013-03-10
forum: General Help
---

### Post by GameX2 on 2013-03-10
Hi,


I encoutered a weird freeze, on my laptop.  This rarely ever occur, especially on Ubuntu!
I am converting a 30GB VDI file to VMDK.  The conversion took about 5 hours, and is apparently at 40%...  That's long..

Well, randomly, Ubuntu frozed.  I can still move the mouse, but nothing respond.
So I've opened up a virtual terminal, and tried to kill different processes, such as Firefox, to make it respond again, no luck.  Heck, the conversion took 5 hours, I am not stopping it! Oo

I can't manage to un-freeze the system, I don't know if it's possible at this point.  I could return to LightDM, but that would stop the conversion.  I was able to check the progress of the conversion, by doing a ls in the ouput folder.  I can see that the size of the resulting VMDK file is growing.  The conversion still work, at least.  I've put it at high priority.

Is there a way I could make the system respond again, without stopping the conversion?  I'm going to sleep, and I let that conversion run, for now.  I'm also curious about *what* exactly froze Ubuntu like this.  I only had Firefox opened, with a few tabs, not memory excessive..  Did X froze completely?
Interestingly, the hour still update, in the GUI.  That's weird!

If updating Ubuntu to MIR will make these freeze even rarer, that sound interesting.

Thanks for the info.  If anyone can help to un-freeze the system, that would be appreciated (If a night isn't enough to make Ubuntu un-freeze by itself!).

---

### Post by ManamiVixen on 2013-03-10
What do you mean "high priority" did you set a value on the process on how much time and resources are used for the conversion?

---

### Post by GameX2 on 2013-03-11
> **ManamiVixen said:**
> What do you mean "high priority" did you set a value on the process on how much time and resources are used for the conversion?

I've assigned an higher priority to the conversion service (VBoxManage) by doing this:
```
sudo renice -20 -p 22256
```

I should mention that I've done this when the system was already locked up, because the conversion process is horribly long, and I would love to use my laptop again.  5 hours later, the GUI is still frozen.
I have 8GB of RAM, and the RAM never goes above 20% of use, unless I do virtualization, this can't be a RAM problem, for sure.

Here's what the command "top" display about VBoxManage:

```
PID         user        PR        NI        VIRT        RES        SHR        S        %CPU        %MEM        TIME+        command
22256        gamex        0        -20        261m        7060        5188        S        0        0.1        1:56.9        VBoxManage
```

In the GUI, I can see that the hour still update, for some reason.  Guake-Terminal is also opened, and update as well.  Yesterday, the conversion was at 40%, and this morning, Guake display it's at 50% (So Guake output is shown, even though the system is completely locked up).
From what I remember, it locked up when I've mounted a ISO file with FuriusISOMount, and tried to run an older game with Wine (It's a 2001 game, nothing ressource hungry.  The game work fine).

Is there a way I could return to LightDM without stopping the necessary processes (VBoxManage, VBoxXPCOMIPCD, VBoxSVC...) ?
It's just.. horribly long. :P


Thank you!

---

### Post by GameX2 on 2013-03-11
Well, I restarted LightDM. :/
I was at 60% after more than 12 hours, that's ridiculous.

I've tried killing different known processes, but no luck.  The panel at the top was apparently still working (The hour, and even mail check worked.  Altought mouse clicks and keyboard would not respond).

I'll find another way to do this..
Still, I would be interested to know why this freeze happened (Randomly?) !

Thanks.

---

### Post by GameX2 on 2013-03-12
Sorry for the triple post; the exact freeze happened again, today, I was working with Word in Wine (Work perfectly)..  Glad I managed to restore my document (Word is set to save every minute just in case!).
What was opened?

Firefox, with FaceBook; Clementine music player (The music was still playing when the freeze occured.  I've succesful killed Clementine later on); Word throught Wine.
When I tried to delete a 30GB VDI file from a NTFS partition, the deletion popup didn't even appeared.  The system just frozed (You know, the whole GUI except the top panel fade to black).  The panel at the top was still working (Clementine icon was updating fine), but nothing was responding to the mouse clicks.  Virtual terminal still work, and lauch instantly.

I would really love to know what exactly is freezing.  With 8GB of RAM, my memory never go above 20% (Unless I use VMware.  This was not the case, now).
What frozed?  Nautilus?  Unity?  Ubuntu-Desktop? Compiz ??

Thank you very much for the help!

---

