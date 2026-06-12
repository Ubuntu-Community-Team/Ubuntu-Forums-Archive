---
title: "Flash drive won't automagically show on Desktop"
date: 2007-05-14
forum: General Help
---

### Post by overkillm on 2007-05-14
A while back I had a problem getting my USB Flash drive to mount, and with the help of this forum, was able to work it out.

I just have a minor quibble... more of a curiosity thing, really... when I plug my Flash drive in, the icon doesn't automagically show up on my desktop the way a blank CD/DVD will.  It does show up in Nautilus, under Computer, but with a generic drive icon (not the custom one I gave it).  If I double-click on that icon to open it, THEN the custom icon will pop up on my desktop.

It's not a serious problem or anything, as the drive is 100% functional, I just wonder why that icon doesn't pop up on the desktop when the drive is hotplugged?  I'd like to learn more about how hal, pmount, and all that fun stuff works. 

Appreciate any input on this.  :)

---

### Post by pianoboy3333 on 2007-05-14
I just quickly scanned your question, you may want to checkout (in gnome I hope you're using) system -> Preferences -> removable drives and media

---

### Post by overkillm on 2007-05-15
These settings are currently checked in System->Preferences->Removable Drives and Media (Storage tab):

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

The flash drive will mount when inserted, it just doesn't immediately appear on my desktop... I have to actively open a Nautilus window and double-click the drive before anything shows on my desktop, which I find kind of strange.

---

### Post by fragos on 2007-05-15
This can be set with the System Tools-> Configuration Editor-> apps-> Nautilus-> Desktop-> volumes_visable checkbox.  This check box covers a lot of items.  You'll also see CR's, USB memory sticks, SD cards, mounted partitions and etc.  If this makes your desktop too busy you can check home_icon_visable, open it and then select the device from the side menu.  They always show up here regardless of icon visibility.

---

### Post by overkillm on 2007-05-16
> **fragos said:**
> This can be set with the System Tools-> Configuration Editor-> apps-> Nautilus-> Desktop-> volumes_visable checkbox.  This check box covers a lot of items.  You'll also see CR's, USB memory sticks, SD cards, mounted partitions and etc.  If this makes your desktop too busy you can check home_icon_visable, open it and then select the device from the side menu.  They always show up here regardless of icon visibility.

I checked there, and the box was already checked.  Just to be sure, I unchecked it and checked it again... still no icon when I insert a flash drive.  I even tried a different flash drive, plugged into a different USB port.  Same result.  So weird...

---

### Post by fragos on 2007-05-16
This did work at one time.  My card reader even gave me specific icons for each kind of media.  It also didn't used to include mounted parations.  A small thing but perhaps worth a bug report.

---

### Post by strabes on 2007-05-16
Do you have it set to mount somewhere in /media? I believe you must mount it in there for it to show up on the desktop.

---

### Post by overkillm on 2007-05-19
> **strabes said:**
> Do you have it set to mount somewhere in /media? I believe you must mount it in there for it to show up on the desktop.

It doesn't mount there automatically.  When I insert the drive an icon appears in Nautilus, under computer:///
Only when I double-click that icon does the drive get mounted to a folder in /media, and the desktop icon appears.

I also just noticed that in KDE, when I insert the drive I get the dialog box asking me what I want to do with the media, and when I select "open in new window" nothing happens.  It doesn't mount in /media, but when I switch over to Gnome and double-click that icon in Nautilus, I can see it in KDE also (I guess KDE/Konqueror doesn't have something analagous to the "computer:///" in Nautilus?).  Once I could see the drive in KDE, I opened the Properties dialog for it and selected "mount automatically." Then I unmounted and unplugged the drive, plugged it back in, and still nothing.

How would I set it to automatically mount in /media, without having to rely on Nautilus?  I assume I have to edit a config file, but which one?

Thanks again for the help.  :)

---

### Post by overkillm on 2007-05-23
Hmm... same thing happens with my iPod, so I imagine it's the same with any USB storage device... weird that the optical drives work fine, though... put in a disc and the icon appears on my desktop.

Anyone know if there's a config file for USB devices that I need to alter or something?  Something that would instruct Ubuntu to automatically mount the device to /media when plugged in?  It works when I change /etc/fstab, but then I'd have to have the device plugged in at boot time, and plus I've read that pmount won't work for devices in fstab.

Well, there are worse things than having to mount a device manually but if anyone knows how I can get hotplugging going, I'll appreciate the help.

---

### Post by fragos on 2007-05-23
System-> Preferences-> "Removable Drives & Media" gives you the control you want for mounting and which applications are run at that time.

---

### Post by overkillm on 2007-05-23
Weird... all of a sudden it's working.  And I don't think I changed anything.

In System->Preferences->Removable Drives and Media, I already had the "Mount removable drives when hot-plugged," "Mount removable media when inserted," and "Browse removable media when inserted" boxes ticked... The other day I decided to tick "Auto-open files on new drives and media" too but that didn't help any. 

The only possible thing I can think of that I changed recently is that I deleted the directories that I had created in /media/, leaving only those containing the ".created_by_pmount" hidden file.  Maybe that's what it took, but I could have sworn that I tried inserting my flash drives after I first deleted those directories and I still didn't get the icons then.

Anyway, it's working now, even if I'm not positive why.  

Now, if only KDE would display the icons I assigned to my devices on the desktop the way Gnome does... KDE seems to use icons assigned to the device *type* on the desktop, rather than the one assigned (I'm assuming) to the device's UUID.  IOW, I can tell my two flash drives apart just by their desktop icons in Gnome but not KDE.  But that's just nitpicky, I can live with it.

Thanks all for your help!  :D

---

### Post by fragos on 2007-05-23
Glad it worked out for you.  I would like to leave you with a thought.  Command line gives much finer granularity than the GUI does for setting things.  This granularity also allows you do things half way -- translation broken.  I always try to use the GUI before going to the command line because its posible for CLI and GUI to interfere with each other.  A single check box in the GUI might initiate what would have taken many steps on the command line.  The order of the CLI steps may even be criticle.

---

