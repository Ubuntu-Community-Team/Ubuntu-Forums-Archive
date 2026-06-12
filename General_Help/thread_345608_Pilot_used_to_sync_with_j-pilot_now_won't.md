---
title: "Pilot used to sync with j-pilot now won't"
date: 2007-01-24
forum: General Help
---

### Post by pennygov on 2007-01-24
:mad: Sorry to start out mad but I've been fooling with this since yesterday afternoon and trying, after reading everything about syncing with no luck (and it looks like maybe luck plays a part!) Anyway ...

Some time since January 5 when I last synced my clie SJ22 with j-pilot something happened because I can't now. I am using kernel 2.6.15-27-386. I booted with my old kernel 2.6.15-23-386 and it didn't work with it either. I am using the KDE environment although have tried making the connection in gnome also.

My symlink rules make a symlink "Pilot" from ttyUSB* (I tried ttyUSB[02468] also). I've also set jpilot to look for the palm on ttyUSB0 and ...1, etc. Used to work with "/dev/pilot. No luck.
Here are the messages I get when I hit "sync" on the palm:

Syslog:

Jan 24 12:21:53 localhost kernel: [17180768.964000] usb 3-1: new full speed USB device using uhci_hcd and address 6
Jan 24 12:21:53 localhost kernel: [17180769.104000] usb 3-1: palm_os_4_probe - error -32 getting connection info
Jan 24 12:21:53 localhost kernel: [17180769.104000] visor 3-1:1.0: Handspring Visor / Palm OS converter detected
Jan 24 12:21:53 localhost kernel: [17180769.104000] usb 3-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jan 24 12:21:53 localhost kernel: [17180769.104000] usb 3-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
Jan 24 12:22:17 localhost kernel: [17180793.420000] usb 3-1: USB disconnect, address 6
Jan 24 12:22:17 localhost kernel: [17180793.420000] visor 3-1:1.0: device disconnected
Jan 24 12:22:17 localhost kernel: [17180793.436000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jan 24 12:22:17 localhost kernel: [17180793.436000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1

*****************************************8
messages:

Jan 24 12:18:01 localhost kernel: [17180536.632000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
Jan 24 12:21:53 localhost kernel: [17180768.964000] usb 3-1: new full speed USB device using uhci_hcd and address 6
Jan 24 12:21:53 localhost kernel: [17180769.104000] visor 3-1:1.0: Handspring Visor / Palm OS converter detected
Jan 24 12:21:53 localhost kernel: [17180769.104000] usb 3-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jan 24 12:21:53 localhost kernel: [17180769.104000] usb 3-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
Jan 24 12:22:17 localhost kernel: [17180793.420000] usb 3-1: USB disconnect, address 6
Jan 24 12:22:17 localhost kernel: [17180793.420000] visor 3-1:1.0: device disconnected
Jan 24 12:22:17 localhost kernel: [17180793.436000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jan 24 12:22:17 localhost kernel: [17180793.436000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1

*****

There seems to be a problem with the connection to jpilot (and kpilot and evolution - I've tried them all). I've make sure gpilot isn't working, tried with it working - same with kpilot. 

The above line: palm_os_4_probe - error -32 getting connection info looks suspicious but I don't know what that means.

Maybe I need a newer kernel?

HELP or it's back to M$  The info on my palm is really important to me, both on the computer and on the palm.

Thanks!!!

---

### Post by pennygov on 2007-01-24
:D :o  Oh my intelligent designer!!!!!! I tried the suggestion at
[http://www.ubuntuforums.org/showthread.php?t=202552&page=4&highlight=pilot](http://www.ubuntuforums.org/showthread.php?t=202552&page=4&highlight=pilot)
page 4 by fdimling who said to:
"I created a file 10-visor.rules in /etc/udev/rules.d containing only the line

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", MODE="666", SYMLINK="pilot", RUN="/bin/su - fd -c '/usr/bin/jpilot -s'"

You have to replace the fd in the RUN=... entry by your own user id!!!"

It really worked!!!! I didn't even have to hit the icon in jpilot - just the PDA. I'm so happy now.

I think that Linux users love their linux machines because they suffer so much getting things to work and when they do it feels soooo good.

---

