---
title: "Any really good hardware diagnostics???"
date: 2007-07-27
forum: General Help
---

### Post by newbun on 2007-07-27
Hi there

Can anyone tell me if there is a GOOD hardware monitoring tool out there?  One that works.
Especially for disk testing that shows up errors and WHERE on the disk.
Also one that tests other parts of the hardware system.

In other words - a comprehensive tool.  I don't think 'im-sensors' cuts it.

Any help would be appreciated.

Thanks

---

### Post by madmetal on 2007-07-28
ultimate boot disk has a lot of good diagnostics tools
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by newbun on 2007-07-29
thanks Madmetal, I'll give 'em a try....

---

### Post by az on 2007-07-29
use badblocks to check your disk.


sudo badblocks -v -s /dev/sda1

---

### Post by newbun on 2007-07-29
thanks, also 'az'

---

### Post by gtstephenson on 2007-07-29
I use smartctl for disk issues. There is even a flavor that will run in windows.

[http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

The tool allows you to run tests using the smart feature of your drive
Will also report what LBA has failed (if there are any failures).
Reports things such as:
Power On Hours
Disk Temperature
Current Pending Sector (failing sector requires reallocation)
# if Reallocated sectors

Suggest you run a -t short (test option) then when the test complete run a -a option

example (must be super user)
smartctl -d ata -t short /dev/hda
sleep 120
smartctl -d ata -a > test.txt
more test.txt

Tom S.

---

### Post by newbun on 2007-07-30
Thanks " gtstephenson" .  I believe I can install 'smartmontools' via synaptic manager?
Is that right, and are you familiar with that method?

My reasons for seeking comprehensive diagnostic tools are that (at the moment) my AMD Athlon 1.15 ghz, 750mb ram, 40gb hard drive, machine is a bit temperamental as to WHEN it freezes.
My main PC is a laptop, but to try out UBUNTU (i'm liking it.....so far) on a machine that was just sitting there wondering whether to go the Vista route, or what.

Sometimes the desktop is up for a couple of hours - no freezes.  Other times - its minutes.  Can't pin down what's causing it.  I've loaded an old copy of Windows xp (home edition), and it does the same with that - so it's not just picking on Ubuntu.

So, what I need is a diagnostic that pins down the reason....so I can fix it, and get on with this alternative to Windows.

I've tried all the suggestions, and am currently using the 'bootcd' diags for clues.....

Thanks again

---

