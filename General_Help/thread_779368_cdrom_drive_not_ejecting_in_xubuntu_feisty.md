---
title: "cdrom drive not ejecting in xubuntu feisty"
date: 2008-05-02
forum: General Help
---

### Post by rolypolycat on 2008-05-02
Hello!

This isn't anything really serious, just a nuisance. Also, I didn't see any posts similiar, so I thought it might help with this particular problem in xubuntu.
When I load a cd, it runs fine. I can do anything I want; run software, play music, copy files. No problem. But when I push the physical eject button, I get this message:

failed to eject "/org/freedesktop/Hal/devices/ storage_model_DVDRW_LH_16W1P
Given devices "org/freedesktop/Hal/devices/storage_model_DVDRW_LH16W1P is not a volume or a drive

So to eject, I have to click on the icon itself, select "eject", and it nicely pops out for me. But why doesn't it do this automatically? I've used other distros in the past which did.

My second question: I did a minimal install several times from the min cd with xfce as the desktop, but without all the other junk. That wouldn't load or eject a cd unless I installed the panel cd plugin, and clicked "mount/unmount". Why the lengthy workaround? what was I missing then?

Here is my present /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2badc984-79cb-49a6-9c84-f5da07066633 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=e87a90a2-403d-4a6a-bdcc-06905962705e /home           ext3    defaults        0       2
# /dev/sda5
UUID=1dc06b51-34f5-4d96-82d3-dbb80f5618b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

A third mystery: when I added a printer (an hp deskjet 940c) via hplip gui, is would say there was an error, and no signal. Give a few seconds, and it printed! This is also under minimal install. I've gone back to full install of xubuntu, but I'd like to know how to correct that, too.

Last but not least: I wanted to try several window managers, as my computer is 5-6 years old and they're faster. I have the hp printer, so I was able to finally find a workaround. I noticed while searching the forums there were a number of folks using other wm's who couldn't get figure out how to add a printer. Maybe someone could do a wiki or a sticky note helping new folks like us install printers under other window managers when they  don't come with a nice printer gui from ubuntu or hp? (I'd do it myself, but I don't know how).It would really help/

Thanks for any help on the above problems!:)

---

### Post by DorianX on 2009-06-05
I'm having the same issue in mythbuntu 9.04  Running 'eject' from the command line also works to eject the drive, and it appears that if you press the eject button before the disc mounts, it will also eject from the hardware button. 

There is an open bug for exo [https://bugs.launchpad.net/ubuntu/+source/exo/+bug/309230]("https://bugs.launchpad.net/ubuntu/+source/exo/+bug/309230") that seems to cover this, but there hasn't been any movement on it.


It's driving me a little crazy since, this being a mythtv box for me, it's a big hassle to do things like right-clicking or pulling up a terminal window (I went to some trouble to not need anything but a remote control for normal day-to-day operations)

---

### Post by Prem Rajendran on 2009-06-05
I think you could eject the cd drive manually

get a safty pin and poke it through the small home on the front 

of the drive

not a permanant solution though

hope this helps

---

