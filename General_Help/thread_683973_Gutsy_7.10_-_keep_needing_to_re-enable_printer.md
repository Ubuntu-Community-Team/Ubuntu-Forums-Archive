---
title: "Gutsy 7.10 - keep needing to re-enable printer"
date: 2008-01-31
forum: General Help
---

### Post by kevinatkins on 2008-01-31
Hi All,

I have two systems running Gutsy 7.10. With both systems I am experiencing problems with their printers periodically becoming 'disabled' - the first I know of it is when spooling a print job and nothing happens.

One machine is connected via USB to a Hewlett-Packard DeskJet 5550; the other machine is connected via USB to an HP OfficeJet d145 AIO...

I also connect to a shared HP LaserJet 6L on another cups server - this printer is fine and never seems to suffer the problems (it's connected to a separate printer server machine running Debian Sid, via a good old Centronics cable)

The workaround is to go to System -> Administration -> Printing and re-tick the 'Enabled' check box for the printer in question.

My question is, why is this happening? It's a bit annoying - particularly for other users...

Any help appreciated, or perhaps you're also having the same problem?

Cheers,

Kevin.

---

### Post by eddugo on 2008-02-01
I am having the exact same problem.  HP Business inkjet connected via USB to Gutsy.  I have not figured out any pattern.

---

### Post by mssever on 2008-02-01
I have the same problem. I have an HP DeskJet 5150 connected via USB to my desktop. I think I can print normally from my desktop, but I'm not sure, since I mostly use it as a server.

I connect to my printer via IPP on my laptop. When I print, it'll print the first inch or two of the document, then stop. I have to log in to my desktop and re-enable the printer (I do it from the CUPS website, localhost:631). Then, it prints normally.

Other notes: My printer is configured to automatically turn itself on when it receives a job, and back off after it's been idle for a while. The problem only seems to occur for jobs printed when the printer is off. I haven't uet tried manually turning it on before sending that first job.

This problem only started to occur within the last several weeks. Before that, everything was fine. I can't remember, though, what updates came at that time.

Both my desktop and my laptop are running Gutsy.

---

### Post by staama on 2008-02-02
Hi,

same issue here, also under Ubuntu 7.10 with an HP Deskjet 5150.
When looking through the logs, I found the following lines in syslog, right after the printer was disabled.

> 
Feb  2 17:16:14 homefile kernel: [ 1036.818348] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
Feb  2 17:16:15 homefile kernel: [ 1037.207202] audit(1201968975.215:4):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=9003 profile="/usr/sbin/cupsd"
Feb  2 17:16:15 homefile kernel: [ 1037.339988] audit(1201968975.215:5):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=9006 profile="/usr/sbin/cupsd"
Feb  2 17:16:15 homefile hal_lpadmin: remove
Feb  2 17:16:15 homefile hal_lpadmin: Found configured printer: deskjet_5100
Feb  2 17:16:16 homefile python: hp-info[9010]: error: Device busy: hp:/usb/deskjet_5100?serial=HU36B1Y0K3C3
Feb  2 17:16:16 homefile python: hp-info[9010]: error: Error opening device (Device not found). Exiting.
Feb  2 17:16:16 homefile hal_lpadmin: Disabled printer deskjet_5100, as the corresponding device was unplugged or turned off
Feb  2 17:16:16 homefile NetworkManager: <debug> [1201968976.894368] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_printer_HU36B1Y0K3C3'). 


The Cups error_log contained just a single line.

> E [02/Feb/2008:17:16:16 +0100] Pause-Printer: Unauthorized

Any ideas on why those messages show up and how to solve this problem?

---

### Post by mssever on 2008-02-02
Update: This morning when I went to print something, I remembered to manually turn the printer on. It worked fine. Coincidence, or not? I'll have to do some more testing.

I'm curious about the others who've reported this problem. Are your printers set to automatically turn on and off like mine is? I noticed that staama has the same printer model as I have, so I know such a configuration is possible on his/her printer, but I don't know about the other ones. Also, I'm usint the Foomatic/hpijs driver. What about everyone else?

---

### Post by staama on 2008-02-03
Hi,

after manually turning on the printer before I submitted the print job, it did also work for me.

Looks like the process to automatically turn the printer on, when a job is sent, is part of the  problem. This would also correspond to the syslog extract 

> Feb 2 17:16:16 homefile hal_lpadmin: Disabled printer deskjet_5100, as the corresponding device was unplugged or turned off

Maybe Ubuntu does check the printer availability too early, before it has completed its activation?

Cheers,
Markus

---

### Post by mssever on 2008-02-03
> **staama said:**
> Hi,

after manually turning on the printer before I submitted the print job, it did also work for me.

Looks like the process to automatically turn the printer on, when a job is sent, is part of the  problem. This would also correspond to the syslog extract 



Maybe Ubuntu does check the printer availability too early, before it has completed its activation?

Cheers,
Markus

Maybe. But this is a recent change. I'm just wondering what the change is.

---

### Post by mssever on 2008-02-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/188752](https://bugs.launchpad.net/ubuntu/+bug/188752) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				I just filed bug 188752 on Launchpad. Please include any relevant details there that I missed. Also, please confirm this bug.

---

### Post by staama on 2008-04-06
The bug was fixed with the latest update of hal-cups-utils. For my machine printing works fine now.

Thanks a lot for your help!

---

### Post by mssever on 2008-04-06
> **staama said:**
> The bug was fixed with the latest update of hal-cups-utils. For my machine printing works fine now.
I take it you're running Hardy? I'm still experiencing the bug, but I'm also stil running Gutsy. I'm waiting for the Hardy release before upgrading.

---

### Post by j8a on 2008-04-09
I have CUPS 1.3.5.2 running on Ubuntu Gusty and also have the same problem when printing to a couple of HP laser printers on the network. 
I tried to upgrade hal-cups-utils and system-config-printer but there where no packages available.

---

