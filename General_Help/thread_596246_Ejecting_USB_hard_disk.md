---
title: "Ejecting USB hard disk"
date: 2007-10-29
forum: General Help
---

### Post by fede on 2007-10-29
Hello,

I have noticed that Gutsy only gives the option to unount an usb disk (flash or usb HD), whereas -if I'm not mistaken- previous versions allowed to "eject" the device.

I would like to have an option to eject an external hard disk which will signal the device to turn itself off. Windows does this, and I think that previous versions did it too... For example, on windows, choosing this option causes de HD led to turn off (after a couple of seconds), and I can hear the drive spinning down. In Ubuntu, instead, if I simply unmount the drive, the led remains on and the drive is still spinning, an if I unplug it I can hear the sound of the drive going suddenly off, which is different from the "correct" spinning down after telling the drive to remove itself.

Using eject ( "sudo eject /dev/My\ Book" ) and unmount commands doesn't seem to solve the problem.

For the record, this is a WD my book external USB hard disk.

Thanks a lot!

---

### Post by SPr on 2007-10-29
I have the same hard drive (or something very similar anyway) and I had the same problem.

I cured it by adding a custom application to the Gnome Panel.
```

Type: Application
Name: Eject
Command: eject sda
Comment: Safely remove USB HDD

```

eject sda works every time for me :)

---

### Post by fede on 2007-11-03
Hello,

Thanks for your reply; still no luck here: eject does not spin down the drive nor does it turn off its power light.

---

### Post by SPr on 2007-11-03
The drive spins down for me! I do have to manually turn it off though. 
```

eject -s /media/disk

```
Have a look at man eject for more options.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am having USB problems too.
This may be related to a confirmed gparted bug of high importance.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The main bug link

---

### Post by fede on 2007-11-03
SPr: I *think* eject sdb (or was it sudo eject sdb?) worked a couple of days ago. Not sure.

But I am certain it does not spin off the drive now. Nor does adding -s help.

Perhaps this could be filesystem dependant? I had a fat partition some days ago, now I formatted it as ntfs.

suchawato: Thanks for the tip, but I don't see how those bugs could be it... I cannot find the gparted-disable-automount.fdi file anywhere, neither where it should be nor elsewhere.

---

### Post by dasunst3r on 2007-11-03
When I plug in a USB drive, an icon pops up on my desktop.  I can right-click on that and use the "Eject" or "Unmount Volume" option to unmount my disk.  I really don't see a need to create a desktop shortcut for it.

---

### Post by fede on 2007-11-03
dasunst3r: well, eject doesn't show up here. Unmount doesn't spin off the drive (we're talking about an usb hard disk here, not a flash drive).

SPr: I can confirm no combination of eject, sudo eject, -s or not, and using sdb or sdb1 (only partition on disk) works. The only weird one was that issuing sudo eject -s /dev/sdb would make the icon disappear and reappear immediately, with nautilus popping up a window. This is similar to a bug I have seen on launchpad, only it was for feisty and seemed fixed for gutsy

---

### Post by suchawato on 2007-11-04
> **suchawato said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am having USB problems too.
This may be related to a confirmed gparted bug of high importance.
**Update:**
Apparently the gparted bug was related to Fiesty and was fixed in Gutsy so is no longer relevant and is not to this issue.

---

### Post by suchawato on 2007-11-04
> **suchawato said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am having USB problems too.
This may be related to a confirmed gparted bug of high importance.
**[highlight]Update[/highlight]:**
Apparently the gparted bug was related to Fiesty and was fixed in Gutsy so is no longer relevant and is not to this issue.

---

