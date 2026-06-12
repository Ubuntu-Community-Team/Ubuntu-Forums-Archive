---
title: "[SOLVED] Printer port dissapeared"
date: 2008-01-28
forum: General Help
---

### Post by wavetel on 2008-01-28
Ive been messing with Debian based distros for a while now and Ive had this problem happen before under Kanotix. I recently installed Ubuntu 7.10 for the first time and installed a parallel port printer. It was not automatically detected so I directed it to the correct port and loaded the driver Epson Stylus C87. All worked fine. I then installed KDE-desktop . This was also fine. It all seemed to go bad when I started messing about with Printer sharing and trying to print from a Windows machine on the LAN. All printing has stopped now even from Ubuntu. The printer Jobs just sit there and wait so I have to delete the Jobs. Something I did in the sharing setup has caused a real problem now.

I could not make any sense of this so I removed the printer. Lets reinstall the printer. So now I go into the printer setup and the option to install a printer on a direct Parallel or USB port is just no longer available. The printer port just may notbe there anymore. I get options to install all sorts of printers but no longer any direct connected ones. What have I done ? I had the same problem in the end after trying to share a printer in Kanotix recently and that ended up being busted as well. Ive tried looking at it in both Gnome and KDE but it stumps me.

Any ideas anybody ?

---

### Post by cmnorton on 2008-01-28
Stumped other than pouring through your logs to see if something shows up there.

---

### Post by wavetel on 2008-01-29
Ok Charles. Lets see .. Not sure I can post all the logs on here but here are some inteesting findings.

When I go into the Printer setup for CUPS and try to add a printer now. Both the Local Printer (Parallel, serial, usb) and the Serial Fax/Modem Printer options are greyed out and unavailable.

I installed log-analysis and ran that up. Here are some bits of the output.
It seems to spend alot of time on the Parallel port if you ask me. Lots of comments about it throughout the text.
2          kernel: [   65.036509] input: PC Speaker as /class/input/input2
1          kernel: [   65.050673] parport_pc: VIA 686A/8231 detected
1          kernel: [   65.050680] parport_pc: probing current configuration
1          kernel: [   65.050700] parport_pc: Current parallel port base: 0x378
2          kernel: [   65.050786] parport0: PC-style at 0x378 (0x778), irq 7, us
ing FIFO [PCSPP,TRISTATE,COMPAT,ECP]
2          kernel: [   65.111821] parport0: Printer, EPSON Stylus C87
2          kernel: [   65.111847] parport_pc: VIA parallel port: io=0x378, irq=7
2          kernel: [   65.177639] pci_hotplug: PCI Hot Plug PCI Core version: 0.
SNIP>
This doesnt look good at all
2          kernel: [ 1035.280617] audit(1201558091.652:7):  type=1503 operation=
"sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0
/autoprobe" pid=6161 profile="/usr/sbin/cupsd"
1          kernel: [ 1035.288776] ppdev0: registered pardevice
1          kernel: [ 1035.318290] ppdev0: unregistered pardevice
1          kernel: [ 1035.766189] ppdev0: registered pardevice
1          kernel: [ 1035.795985] ppdev0: unregistered pardevice
2          kernel: [ 1114.347549] audit(1201558170.657:8):  type=1503 operation=
"inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=6188 p
rofile="/usr/sbin/cupsd"
2          kernel: [ 1158.205695] audit(1201558214.659:9):  type=1503 operation=
"sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0
/autoprobe" pid=6196 profile="/usr/sbin/cupsd"
2          kernel: [ 1158.218227] audit(1201558214.659:10):  type=1503 operation
="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport
0/autoprobe" pid=6198 profile="/usr/sbin/cupsd"
SNIP>
The above registered then unregistered device just goes on repeating itself at length.

I also found lots of this in the Cups error.log
I [29/Jan/2008:09:36:07 +1030] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6143)

These show up on a lsmod
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc


I [29/Jan/2008:09:36:09 +1030] Started "/usr/lib/cups/daemon/cups-driverd" (pid=6165)
E [29/Jan/2008:09:36:09 +1030] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory

I dont know but somehow this starts to look like a permissions issue going by past experiances but thats only a guess.

Comments anybody ?? Thanks from Tony

---

### Post by wavetel on 2008-01-29
Here is more from the CUPS error Log. which was prior to me removing the Epson printer.

E [29/Jan/2008:08:27:48 +1030] Unknown directive HideImplicitMembers on line 75.
I [29/Jan/2008:08:27:48 +1030] Loaded configuration file "/etc/cups/cupsd.conf"
N [29/Jan/2008:08:27:48 +1030] Group and SystemGroup cannot use the same groups!
I [29/Jan/2008:08:27:48 +1030] Resetting Group to "root"...
I [29/Jan/2008:08:27:48 +1030] Configured for up to 100 clients.
I [29/Jan/2008:08:27:48 +1030] Allowing up to 100 client connections per host.
I [29/Jan/2008:08:27:48 +1030] Using policy "default" as the default!
I [29/Jan/2008:08:27:48 +1030] Full reload is required.
I [29/Jan/2008:08:27:48 +1030] Saving job cache file "/var/cache/cups/job.cache"...
I [29/Jan/2008:08:27:48 +1030] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 36 types, 40 filters...
I [29/Jan/2008:08:27:48 +1030] Loading job cache file "/var/cache/cups/job.cache"...
I [29/Jan/2008:08:27:48 +1030] Full reload complete.
E [29/Jan/2008:08:27:48 +1030] Unable to find IP address for server name "Ubuntu-PRN"!
I [29/Jan/2008:08:27:48 +1030] Listening to :::631 on fd 4...
I [29/Jan/2008:08:27:48 +1030] Listening to 0.0.0.0:631 on fd 5...
I [29/Jan/2008:08:27:48 +1030] Listening to /var/run/cups/cups.sock on fd 6...
I [29/Jan/2008:08:27:48 +1030] Resuming new connection processing...
I [29/Jan/2008:08:32:20 +1030] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6076)
I [29/Jan/2008:08:32:31 +1030] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6078)
I [29/Jan/2008:08:32:31 +1030] [Job 10] Adding start banner page "none".
I [29/Jan/2008:08:32:31 +1030] [Job 10] Adding job file of type application/postscript.
I [29/Jan/2008:08:32:31 +1030] [Job 10] Adding end banner page "none".
I [29/Jan/2008:08:32:31 +1030] [Job 10] Queued on "Stylus_C87" by "guest".
I [29/Jan/2008:08:32:31 +1030] [Job 10] Started filter /usr/lib/cups/filter/pstops (PID 6079)
I [29/Jan/2008:08:32:31 +1030] [Job 10] Started filter /usr/lib/cups/filter/pstoraster (PID 6080)
I [29/Jan/2008:08:32:31 +1030] [Job 10] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 6081)
I [29/Jan/2008:08:32:31 +1030] [Job 10] Started backend /usr/lib/cups/backend/epson (PID 6082)
E [29/Jan/2008:08:32:31 +1030] [Job 10] Unable to open parallel port device file: Permission denied
E [29/Jan/2008:08:32:31 +1030] PID 6082 (/usr/lib/cups/backend/epson) stopped with status 1!
I [29/Jan/2008:08:32:31 +1030] Hint: Try setting the LogLevel to "debug" to find out more.
I [29/Jan/2008:08:32:33 +1030] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6084)
I [29/Jan/2008:08:32:43 +1030] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6085)
I [29/Jan/2008:08:32:55 +1030] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=6086)
I [29/Jan/2008:08:32:55 +1030] [Job 10] Backend returned status 1 (failed)
I [29/Jan/2008:08:33:15 +1030] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=6087)
I [29/Jan/2008:08:33:15 +1030] [Job 10] Canceled by "guest".

AND HERES some more oddities which make me look towards Permissions.

I [29/Jan/2008:09:12:14 +1030] Allowing up to 100 client connections per host.
I [29/Jan/2008:09:12:14 +1030] Using policy "default" as the default!
I [29/Jan/2008:09:12:14 +1030] Partial reload complete.
E [29/Jan/2008:09:12:14 +1030] Unable to find IP address for server name "Ubuntu-PRN"!
I [29/Jan/2008:09:12:14 +1030] Listening to :::631 on fd 2...
I [29/Jan/2008:09:12:14 +1030] Listening to 0.0.0.0:631 on fd 4...
I [29/Jan/2008:09:12:14 +1030] Listening to /var/run/cups/cups.sock on fd 5...
I [29/Jan/2008:09:12:14 +1030] Resuming new connection processing...
E [29/Jan/2008:09:12:15 +1030] cupsdAuthorize: Local authentication certificate not found!
E [29/Jan/2008:09:12:15 +1030] cupsdAuthorize: Local authentication certificate not found!
E [29/Jan/2008:09:12:15 +1030] cupsdAuthorize: Local authentication certificate not found!
I [29/Jan/2008:09:12:17 +1030] Started "/usr/lib/cups/daemon/cups-deviced" (pid=5877)
I [29/Jan/2008:09:12:19 +1030] Started "/usr/lib/cups/daemon/cups-driverd" (pid=5899)
E [29/Jan/2008:09:12:20 +1030] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
I [29/Jan/2008:09:13:42 +1030] Started "/usr/lib/cups/daemon/cups-deviced" (pid=5916)
I [29/Jan/2008:09:13:44 +1030] Started "/usr/lib/cups/daemon/cups-driverd" (pid=5938)
E [29/Jan/2008:09:13:44 +1030] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
I [29/Jan/2008:09:14:14 +1030] Started "/usr/lib/cups/daemon/cups-deviced" (pid=5948)
I [29/Jan/2008:09:14:16 +1030] Started "/usr/lib/cups/daemon/cups-driverd" (pid=5970)
E [29/Jan/2008:09:14:16 +1030] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
I [29/Jan/2008:09:32:50 +1030] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6098)
I [29/Jan/2008:09:32:51 +1030] Started "/usr/lib/cups/daemon/cups-driverd" (pid=6120)
E [29/Jan/2008:09:32:52 +1030] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
I [29/Jan/2008:09:36:07 +1030] Started "/usr/lib/cups/daemon/cups-deviced" (pid=6143)
I [29/Jan/2008:09:36:09 +1030] Started "/usr/lib/cups/daemon/cups-driverd" (pid=6165)
E [29/Jan/2008:09:36:09 +1030] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
I [29/Jan/2008:09:45:38 +1030] Scheduler shutting down normally.

EOF

---

### Post by cmnorton on 2008-01-29
Is cupsd running?

ps -ef | grep cupsd

This is my output

root      4804     1  0 07:57 ?        00:00:55 /usr/sbin/cupsd
cnorton   6608  6524  0 07:59 ?        00:01:55 gnome-cups-icon --sm-client-id default3

---

### Post by wavetel on 2008-02-02
Yep CUPS is running no doubt. If I go into the Printer setup and look at the jobs it says they are Held jobs. The description regards the reason is a permissions issue on lp0

Ive googled this a bit and found numerous instances of issues that seem to go back to the days of Breezy etc. Anyway as soon as I change the permissions on lp0 it all starts to print.
This lasts until I reboot and it seems to reset the permissions back again.

Ive shot myself in the foot in effect as there have been some 160-170 updates waiting since I installed Gutsy. Ive avoided doing the updates because I didnt want to waste the bandwidth considering I only want to keep this install for a short trial. In the updates there are some inclusions for CUPS. So now I stand condemed it seems.

Its just hard to beleive that a fresh install with hardly any changes could be so badly busted in the CUPS area. Something rather odd has certainly happened. The original drivers I had running with this printer seem no longer available so Ive had to revert to using a Guttenprint Epson Stylus C88 driver instead of C87 . The C87 actually did exist as an option until this all went pear shaped.

So for now I will leave off on this and do the updates. It may fix something.

Thanks and lets close this for now.
:KS

---

### Post by Wolf-Ekkehard on 2008-03-12
Is there another label but [SOLVED] for these threads that are really not solved?  Something like [ABANDONED]?

I ran into exactly the same situation (two local printers worked fine until I tried to share them like I successfully had done under Drapper) and hoped to find a solution here.  For now, all I can add is that uninstalling samba doesn't solve the problem either.  cupsd is running and the logs contain nothing suspicious that I could find.

I'd hate to re-install just because of this...

---

### Post by raygj on 2008-07-03
CUPS really doesn't like having "SystemGroup" and "Group" values being the same in the cupsd.conf file.so enter in a konsole
 
"sudo gedit /etc/cups/cupsd.conf" and change the following settings from 

"SystemGroup lpadmin"

"User lp"
"Group lpadmin"

to

"SystemGroup lpadmin"

"User lp"
"Group lp"  

now save the changes   ( back to /etc/cups/cupsd.conf )
then open a Konsole and run "testparm" to make sure you haven't made a typing mistake.
then in konsole run "sudo /etc/init.d/cupsys restart"
now cups can access "/dev/usb/lp0" properly
and now you can print

---

### Post by Wolf-Ekkehard on 2008-07-04
Waw - I didn't hope for a reply to this anymore!  Thanks a lot raygj - now this can be properly archived as "solved".

Since I was really desperate, I re-installed and things worked fine.  Just checked my cupsd.conf though:  It has no entry under "SystemGroup lpadmin" at all - just this heading.  It works fine BTW.  But now that I know where to look, I will experiment with it some more.  I still need to export drivers for the windows machines on the network to be able to print properly.

---

