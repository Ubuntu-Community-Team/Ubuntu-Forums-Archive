---
title: "Processor keeps running"
date: 2015-04-27
forum: General Help
---

### Post by LeeU on 2015-04-27
I am running Ubuntu 12.04 LTS. A few weeks ago I began to hear my processor running in the background. It's usually continuous but then increased for a bit and then goes back down. Right now my processors are running at 72% and 68% but continuously surging up and down. It doesn't matter whether there is one program or more running. It obviously affects the operation of the system.

I really need to get this fixed. Anyone have any ideas?

---

### Post by grahammechanical on 2015-04-27
I have Psensor installed that gives readouts on the temperature of the CPU, motherboard, graphic adapter and the hard disk, as well as other information.

I think that what you are hearing is fan noise. I do not believe we can hear a CPU working but we can hear the cooling fan for the CPU and any case fan as well as the fan for the power supply. The graphic adapter should also have a fan. You may need to check if the case is getting sufficient ventilation. It may be that a fan is breaking down.

I also have System Load Indicator installed. It gives me readouts on CPU and memory usage and other stuff. I find it useful to see what is happening from indicators in the top panel.

This command will show what processes are running and what percentage CPU and memory are being used.

```
top
```

Regards.

---

### Post by LeeU on 2015-04-29
Thanks for the info. I'll be sured to clean it. Meantime, it seems to have "cured" itself. It's not running like it was recently; just like it was before. Thanks again.

---

### Post by LeeU on 2015-04-30
Well, it started back again after I posted the above. However, I was able to figure it out. Nautilus was running (I use Gnome Commander) and I used this method [post #2] and it stopped it.

[http://forums.fedoraforum.org/showthread.php?t=295193](http://forums.fedoraforum.org/showthread.php?t=295193)

Of course my desktop doesn't display the icons but I can live with that ... and it's much cleaner.

---

### Post by QDR06VV9 on 2015-04-30
Hi LeeU
You could (if you want).
**Disable desktop handling by Nautilus**
Run this command in Terminal:
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```

**Make sure gnome-commander is set to handle desktop**
```
gsettings set org.gnome-commander.desktop show-desktop-icons true
```
I have done this with double-commander(my choice) works well;)
More info on [Double Commander]("http://doublecmd.sourceforge.net/")
to revert the changes and set Nautilus back as the default file manager, firstly let Nautilus draw the desktop icons:
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
Then, set Nautilus as the default file manager:
```
xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
```
Regards

---

