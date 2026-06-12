---
title: "After reboot sound needs to be re-enabled"
date: 2007-03-06
forum: General Help
---

### Post by tptbz on 2007-03-06
Hi,

I am using Ubuntu version 6.10 on a DELL OptiPlex GX1 with a 40 GB hard drive, 256MB RAM and Pentium II.  After logging in I can manually enable sound.  But after rebooting I need to manually enable sound again.

To enable sound I run:
ubuntu@ubuntu:~$ sudo modprobe snd-cs4236
Password:
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CS4236B [CS4236B], device 0: CS4231 [CS4236B]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@ubuntu:~$ 

At this point Sound works.  The Volume Control still has the red slash through it though.

To see if there are any problems I ran,
/var/log$ cat syslog | less,
Mar  6 12:58:46 ubuntu kernel: [   42.703189] isapnp: Scanning for PnP cards...
Mar  6 12:58:46 ubuntu kernel: [   42.806569] isapnp: Card 'CS4236B'
Mar  6 12:58:46 ubuntu kernel: [   42.806583] isapnp: 1 Plug & Play card detected total

So, my question is:
- How come I have to run enable sound manually each time I reboot?

Thank you and have a great day!

~Brian

---

