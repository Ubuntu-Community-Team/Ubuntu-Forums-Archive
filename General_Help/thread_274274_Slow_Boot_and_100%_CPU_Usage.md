---
title: "Slow Boot and 100% CPU Usage?"
date: 2006-10-09
forum: General Help
---

### Post by Kid G on 2006-10-09
Hi,

For about the past week, whenever I boot with Ubuntu, the process hangs on the message "Loading Hardware Drivers....Failed". When Ubuntu does eventually load the CPU is constantly at 100% usage regardless of what programs are running.

The only thing different about the past week is that my computer was stored away for a few days while I was painting and decorating. I've had the same problem when I try to run the Ubuntu 6.06 disc as a Live CD (which worked perfectly before). My computer seems to run reasonably well under Windows.

I've searched around the forums but couldn't really find a solution. Any ideas?

Thanks

---

### Post by Heliix on 2006-10-09
Hi,
first, try to find out what process is slowing your comp down with command "top" (see the man pages for details)
and try to stop the process/or to kill it.
I've had similar problem when my CD-ROM stopped working correctly and the process hald-addon-storage was consuming all the CPU - trying to mount it (as it was explained to me)
when I killed this process (as root), the CPU usage was normal again.

---

### Post by Kid G on 2006-10-09
The process "modprobe" is using around 70% of my CPU but I am unable to end or kill the process. I am prompted to use the root password but nothing happens once I've entered it.

---

### Post by marianom on 2006-10-09
Try this:

first
sudo top

find there the pid of the process you wanna kill, then press "k" and enter the offending pid, then "enter" a few times and you're done.

---

### Post by Kid G on 2006-10-09
I've tried that and got the following message: 
 
"Kill PID 3131 with signal [15]:"

I pressed Enter but again the process is still running.

:(

---

### Post by marianom on 2006-10-09
I did a "man modprobe" and it seems a very important process. Maybe that's why you cannot kill it. I think there's a problem somewhere else since it's a (and I quote) *"program to add and remove modules from the Linux Kernel"*

---

### Post by Kid G on 2006-10-09
Maybe it is related to the recent problems I have been experiencing when Ubuntu boots up. Is there any way of determining why the hardware drivers will not load?

---

### Post by marianom on 2006-10-09
Check System->Administration->System Activity log (this last might be called different since my ubuntu is in castilian and I'm freely traslating here).

Using Register->Open, you'll find all /var/logs. Investigate them (you can select all modified today) to find what's the problem.

If you find something there, post here the problem. Maybe we can help you with it.

---

### Post by Kid G on 2006-10-09
Thanks for the help but I'm not really sure what in the System Log would indicate the source of my problem? Samples of todays system log below:

Oct 10 01:28:43 localhost kernel: [17179570.776000] ACPI: Looking for DSDT ... not found!

Oct 10 01:28:43 localhost kernel: No module symbols loaded - kernel modules not enabled. 

Oct 10 01:28:44 localhost kernel: [17179596.912000] nvidia: module license 'NVIDIA' taints kernel.

Oct 10 01:29:16 localhost kernel: [17179910.656000] apm: BIOS not found.

Oct 10 01:28:44 localhost kernel: [17179859.352000] ibm_acpi: ec object not found

Oct 10 01:28:44 localhost kernel: [17179779.596000] Intel ISA PCIC probe: not found.

Oct 10 01:28:44 localhost kernel: [17179809.640000] hdc: irq timeout: status=0xd0 { Busy }
Oct 10 01:28:44 localhost kernel: [17179809.640000] ide: failed opcode was: unknown

---

### Post by Kid G on 2006-10-10
Bump

Does anyone know how I can identify what is causing this failure of  the hardware drivers. What should I be looking for in my System logs?

I'd appreciate any help.

Thanks

G

---

### Post by codypumper on 2006-10-13
I've had the identical problem. SOMEONE PLEASE HELP. My ubuntu experience is being ruined...

---

### Post by codypumper on 2006-10-14
bump

---

### Post by codypumper on 2006-10-14
Please....

---

### Post by codypumper on 2006-11-11
After two upgrades I still have the same problem. ](*,)

---

### Post by codypumper on 2007-01-20
Alright I solved this one!
It seemed ubuntu didn't like its usb connection with my dsl modem.
I found this out after a comlete reinstallation! I unplugged all usb drives and pinpointed it.
Now I use a lynksys router, so it doesn't need the usb connection.

---

### Post by sillybunt on 2007-06-30
codypumper, THANKYOU for posting this.

ubuntu (k) was slow to start.. it would pause about two to three minutes to during startup , then complete ok, but... 

once i the wm started, modprobe was using 100% of one of my cores ..

no doubt you knew all this...  just wanted to say thanks and possibly help some one with search terms  ;)

all the best

---

### Post by codypumper on 2007-06-30
No problem ;)
I take it you fixed it?
If so, was it solved the same way that I solved my issues?
Just curious since this is useful information to other Ubuntu-rs.

---

