---
title: "Palm Lifedrive Setup and Synch"
date: 2007-05-18
forum: General Help
---

### Post by jim8433 on 2007-05-18
I have a Lifedrive Palm device and have tried getting to setup and synch'd using gnome-pilot and jpilot.  Unfortunately, I have only been able to get to the three tab gnome-pilot popup twice and now cannot even get to that point.  JPilot has also not permitted me to get setup.  I have looked at the forum links to How to's for Palms, but still have not been able to progress.  On several occassions I have received a prompt indicating that I may need to install visor, but I appear to only have the source code and do not know how to install it.  Bottomline, could anyone please give me a step by step directions for setting up my Lifedrive?  I am at Feisty 7.04.  Thanks in advance.

---

### Post by mbradlcu on 2007-05-19
the link I have for the fix for my palm issue is gone so I'll post my notes, I'm not sure if you're issue is the same is mentioned below,, anyway I hope it helps!

The problem with USB syncing a Palm under Fedore Core 3 is that the device file will not be created until you press the Hotsync button. And when it is created, it is only accessible by root.

This can be fixed by creating /etc/udev/rules.d/10-visor.rules with this content:

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB[13579]", SYMLINK="pilot"

For detailed information on writing udev rules, see Daniel Drake's excellent document. To create the above rule, I pressed the Hotsync button, looked for the newest symlink in /sys/bus/usb/devices, and then examined the product file in the directory to which the symlink pointed. Because the product string had a trailing space on my computer, I added the "*" at the end. The check for the kernel device name "ttyUSB[13579]" is necessary because I use Card Export II, which lets me access the Palm's memory card as a USB drive. Card Export II also identifies itself as a "Palm Handheld" product, but with a different kernel device name. Tim Harper suggested to use "[13579]" in the device name. This is important because udev creates two subsequent, but more or less random ttyUSB devices, and only the one with the odd number works.

A simpler rule would match the kernel device name with KERNEL="ttyUSB1", but that would break if ttyUSB1 is occupied by some other toy when the Palm is connected.

As pointed out in the comments, it is not necessary to create a file in /etc/udev/permissions.d, because the configuration in /etc/security/console.perms takes care of setting the right permissions, once we have created the symlink /dev/pilot.

The rules.d file must have the given name so it is loaded before the default 50-udev.rules. Restarting udevd is not necessary for these changes to take effect.

If you use pilot-xfer to access your Palm, the following script allows you start it before pressing the Hotsync button.

#!/bin/sh

until [ -e /dev/pilot ]; do sleep 1; done
exec /usr/bin/pilot-xfer "$@"

---

### Post by jim8433 on 2007-05-19
Thanks for those tips.  I created the rule and went to the /sys/bus/devices and could not find any smylink to Palm.  I did this after I pressed the Hotsync button.  I do appreciate your help, but I am definitely a novice when it comes to solving this problem.

---

### Post by mbradlcu on 2007-05-20
I wish I could help further but I don't have my palm any longer. Here's a couple things to check that may get you on the right path.. see if /dev/pilot gets created when you press the hotsync button,, and also you may want to install "usbview" and see what it displays when you have your device plugged in. I you have any new findings please post them,, I'm not an expert but occasionally I guess correctly ; )

---

### Post by jim8433 on 2007-05-20
Thanks for the usbview suggestion.  When I plug in my device it shows my PalmOne device with all of its specifications.  However, when I press the hotsynch button and monitor the /dev area, I cannot find any /dev/pilot folder or file being created.  Can you suggest why this might be so?  When I try to do gnome-pilot setting it to tty/USB0 I get a warning that says I do not have the visor module loaded.  Any other tips to get me to the point of creating /dev/pilot would be appreciated.

---

### Post by jim8433 on 2007-05-20
mbradlcu,

Okay, I have finally got my Lifedrive setup and synch'd.  The breakthrough point for me was when I started a terminal window and entered 

sudo modprobe visor

This started up gnome-pilot for me and allowed me to proceed with the setup.  I was able to synch  my calendar, contacts and memos.  

Thanks much for holding my hand

---

### Post by mbunchj8 on 2008-04-20
mbradlcu - 

I have the Palmdrive and I am using Ubuntu Studio 8.04 Hardy.  I am having a ton of challenges with locating the device and getting it to synch.  Will your steps above work on the Hardy 8.04 version?

Being a recent convert from Windows, I am still learning Linux.  So far I am really glad I switched to Studio Ubuntu.  Now if only I could get the Palm Lifedrive to synch.

Any ideas or recommendations.

---

### Post by mbradlcu on 2008-04-20
Hi mbunchj8,
thanks for asking,
I suspect the above steps will work for 8.04. If you have any questions on how to preform the steps mentioned in the above posts, please let me know and we can walk through it together.

thanks
Matt

---

### Post by mbunchj8 on 2008-05-06
mbradlcu -

Thanks for the info.

> **mbradlcu said:**
> Hi mbunchj8,
thanks for asking,
I suspect the above steps will work for 8.04. If you have any questions on how to preform the steps mentioned in the above posts, please let me know and we can walk through it together.

thanks
Matt

Once I complete my current project, I will post my progress with connecting the Palm life Drive.

Thank You -

---

### Post by Melatonin on 2008-07-16
Hi. I'm having a nearly identical problem in Hardy 8.04. I did try "sudo modprobe visor," but for me it does not start the gpilot setup as it did for jim8433, and when I fire that up myself, instead of receiving that error message, my lifedrive resets and gpilot freezes.
Any ideas?

---

### Post by mbradlcu on 2008-07-17
> **Melatonin said:**
> Hi. I'm having a nearly identical problem in Hardy 8.04. I did try "sudo modprobe visor," but for me it does not start the gpilot setup as it did for jim8433, and when I fire that up myself, instead of receiving that error message, my lifedrive resets and gpilot freezes.
Any ideas?

seems the lifedrive is a bit different, you may want to check out this site:
[http://handhelds.org/moin/moin.cgi/PalmLifeDrive]("http://handhelds.org/moin/moin.cgi/PalmLifeDrive")

apparently it does work but from what I see it's not the same as setting up my old palmV

---

