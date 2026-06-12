---
title: "[SOLVED] Please, PLEASE help me to set up my PalmOne Tungsten E2 on Ubuntu..."
date: 2008-05-05
forum: General Help
---

### Post by Timbothecat on 2008-05-05
Hi guys,

I've reached desperation point here. I've given up on trying to set up my PDA to sync using bluetooth. It seems that every thread on the subject (that I could find at least) has fallen on deaf ears.

So I thought that I'd just set it up through the USB cable and sync that way. that should be pretty easy right? 

Doesn't happen though. I get to a step which I can't get past. I'll post some screen shots so that you can see what I'm talking about.

As you will see in the screen shots, the device is set up with my name, on the USB port (using the cable it came with) and the device is dev/ttyUSB0 as told to do by the help file. 

In the next step I selected "no, I've never used sync software with this PDA before". I have used it on my Windoze machine but not on my Linux box. Either way (tried it with yes selected also) it didn't make it past the next step.

"Please put PDA in Tim Inglis (/dev/ttyUSB0) and press Hot Sync button" is where I get confused because as you will see in the 4th screen shot, there is no ttyUSB0 folder (or file, checked for both) in the /dev directory.

Just to make sure I haven't just misunderstood what I'm supposed to do I press the button on the cable to start the sync and it fails (obviously, otherwise I wouldn't be here sooking to you guys. :);):-({|= ).

Please guys, if any of you have had some experience setting up this particular model of PDA any help you can give will be greatly appreciated.

All the best,

Tim.

P.S. Should add that I'm using Hardy Heron.

---

### Post by jimv on 2008-05-05
Might want to try the GnomePilot email list and see if anyone on it can help you with the issue.

[http://mail.gnome.org/mailman/listinfo/gnome-pilot-list](http://mail.gnome.org/mailman/listinfo/gnome-pilot-list)

---

### Post by Timbothecat on 2008-05-05
Thanks Jim, I'll give that a go.

---

### Post by Gabn on 2008-05-07
like kym said on LOGIN mailing list check dmesg 

also make sure your a member of the dialout group 

sudo adduser username dialout

should do the job...

---

### Post by Timbothecat on 2008-05-07
Apparently I'm already in the group Gab. This forum comes up with some great answers though so I'm sure it will turn up eventually. Who knows, I might even have an epiphany and work it out myself. :lolflag:

---

### Post by Timbothecat on 2008-05-08
Wiped...

---

### Post by Timbothecat on 2008-05-08
This issue has been solved. 

I had to use the "usb:" connection and not the "dev/ttyUSB0" as I was trying to do.

My next PDA will hopefully be using Access which is a linux based system. Garnett took over PalmOS and now run a linux OS on their smartphones. Hopefully that will integrate a little better with Ubuntu.

Thanks again to everyone who helped with this task. It is greatly appreciated.

All the best,

Tim.

---

