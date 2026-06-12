---
title: "Cant print in Hardy (thoug I could in Gutsy)"
date: 2008-05-08
forum: General Help
---

### Post by adonet on 2008-05-08
I'm not able to print to my HP Laserjet 4000 printer when I use Ubuntu 8.04 (Hardy). When I use Ubuntu 7.10 (Gutsy) on the same PC (another partition with dual boot) it all works fine. I installed the printer on the same way. Re-installing the printer doesn't help. Removing hplip and CUPS and re-installing these packages does't help.
Even re-installing Hardy doesn't help

When I try to print anything the printopdrachtbeheerder (screen where I see the printing commands) sometimes accepts the printcommand, and sometimes it doesn't. After a while it asks me If the printer is connected or not.

When in a console I give this command: sudo hp-check -r
it gives one error and one warning:

There are no CUPS printer queues found

and

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: taakplanner is actief
Version: 1.3.7
error_log is set to level: warn

I cant find a way to add any CUPS printer Queue and SIP is not in my repositories.


I can ping the printserver. It has a valid IP nr (192.168.2.10) and replies. I can login to the printserver and find all the communication methods are turned on.

I tried: socket://192.168.2.10:9100 as printer port. Does't work (though it works in Gutsy (7.10)
I tried ipp://192.168.2.10/printers/1 Doesn't work
I tried lpd://192.168.2.10 Doesn't work

The printer cannot be browsed for (it couldn't in 7.10 Gutsy too)

I tried tot install hplip 2.8.4 from the HP website without any result. The HP device manager that comes with it doesn't see the connected printer.

What can I do apart from downgrading to Ubuntu 7.10 ?

Any help or suggestions would be very nice.

Jeroen

---

### Post by chrisccoulson on 2008-05-08
Try:
```
sudo aa-complain cupsd
```

This will put Apparmor in to 'complain' mode for the cupsd process. If it works in complain mode, then Apparmor is blocking file access somewhere.

If this is the case, try:
```
sudo logprof
```
...to see what accesses are being blocked

---

### Post by adonet on 2008-05-08
I get this answer:

jeroen@adonet:~$ sudo aa-complain cupsd
[sudo] password for jeroen: 
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
jeroen@adonet:~$ sudo logprof
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.
Use of uninitialized value in string eq at /usr/share/perl5/Immunix/SubDomain.pm line 3377.
Use of uninitialized value in string eq at /usr/share/perl5/Immunix/SubDomain.pm line 3377.

Repository: [http://apparmor.test.opensuse.org/backend/api](http://apparmor.test.opensuse.org/backend/api)

Would you like to enable access to the
profile repository?

(E)nable Repository / (D)isable Repository / Ask Me (L)ater

---

### Post by adonet on 2008-05-08
What could I do now?

---

### Post by chrisccoulson on 2008-05-08
Did printing work after you put Apparmor in to complain mode?

The errors you listed suggest something wrong with the entries in /var/log/messages, which is causing logprof to choke. If printing works with Apparmor disabled, then I'll tell you how to clean your message log and get the relevant data.

---

### Post by adonet on 2008-05-08
Apparmor is in complain mode, but I still cant print. I get messages that the printer probably isn't connected.

How could I disable apparmor?

---

### Post by chrisccoulson on 2008-05-08
> **adonet said:**
> Apparmor is in complain mode, but I still cant print. I get messages that the printer probably isn't connected.

How could I disable apparmor?

No need. Putting the cupsd Apparmor profile in to 'complain' mode is sufficient - and we've already proven that Apparmor isn't to blame. You can put Apparmor back in to 'enforce' mode now:
```
sudo aa-enforce cupsd
```

Is there anything in /var/log/cups/error_log?

---

### Post by adonet on 2008-05-08
/var/log/cups/error.log shows this:

E [07/May/2008:22:57:21 +0200] [Job 30] kan worden hersteld: niet mogelijk om verbinding te maken met printer; nieuwe poging over 30 seconden...
E [07/May/2008:22:57:29 +0200] PID 7415 (/usr/lib/cups/backend/lpd) stopped with status 1!
E [07/May/2008:23:05:44 +0200] [Job 32] kan worden hersteld: niet mogelijk om verbinding te maken met printer; nieuwe poging over 30 seconden...
E [07/May/2008:23:09:23 +0200] [Job 32] kan worden hersteld: niet mogelijk om verbinding te maken met printer; nieuwe poging over 30 seconden...
E [07/May/2008:23:13:02 +0200] [Job 32] kan worden hersteld: niet mogelijk om verbinding te maken met printer; nieuwe poging over 30 seconden...
E [07/May/2008:23:16:41 +0200] [Job 32] kan worden hersteld: niet mogelijk om verbinding te maken met printer; nieuwe poging over 30 seconden...
E [07/May/2008:23:17:17 +0200] PID 7520 (/usr/lib/cups/backend/lpd) stopped with status 1!
E [07/May/2008:23:22:27 +0200] PID 7528 (/usr/lib/cups/backend/lpd) stopped with status 1!
E [07/May/2008:23:27:38 +0200] PID 7533 (/usr/lib/cups/backend/lpd) stopped with status 1!
E [07/May/2008:23:29:20 +0200] Release-Job: Unauthorized
E [07/May/2008:23:29:26 +0200] PID 7563 (/usr/lib/cups/backend/lpd) stopped with status 1!
E [07/May/2008:23:29:26 +0200] [Job 32] Canceling job since it could not be sent after 5 tries.
E [07/May/2008:23:32:49 +0200] Purge-Jobs: Unauthorized
E [07/May/2008:23:32:49 +0200] Purge-Jobs: Unauthorized
E [07/May/2008:23:35:01 +0200] PID 7688 (/usr/lib/cups/backend/lpd) stopped with status 1!
E [09/May/2008:00:07:43 +0200] [Job 35] kan worden hersteld: niet mogelijk om verbinding te maken met printer; nieuwe poging over 30 seconden...

---

### Post by adonet on 2008-05-08
translation:
[Job35] can be repaired: not possible to make a connection with printer; new attempt in 30 seconds....

---

### Post by Fernando Negro on 2008-05-09
Could it be [_this_]("http://ubuntuforums.org/showthread.php?t=661752") problem?

In hardy my HP printer was not detected anymore also, and after I added ",[my username]" in the "scanner:x:105:hplip" line in the /etc/group file it solved the problem.

(scanner:x:105:hplip -> scanner:x:105:hplip**,username**)

(:x = two dots (":") and an "x", not an angry face as it is automatically converted)

---

### Post by adonet on 2008-05-09
Thanks, but no, my username was already in that group. My printer is NOT a USb printer. Its a parallel HP Laserjet 4000 printer connected to a sitecom printserver.  The printserver is connected to my router with a fixed IP address. If I ping this IP nr, I receive nice answers. So the printserver is connected
In Gutsy I use printerpoort

```
socket://192.168.2.10:9100
```

and it works. In Hardy it doesn't.

```
sudo hp-setup
```
doesn't see my printer and I can't print.

Does anyone have another idea?

Thanks

---

### Post by stansford on 2008-05-16
> **adonet said:**
> I'm not able to print to my HP Laserjet 4000 printer when I use Ubuntu 8.04 (Hardy). When I use Ubuntu 7.10 (Gutsy) on the same PC (another partition with dual boot) it all works fine. I installed the printer on the same way. Re-installing the printer doesn't help. Removing hplip and CUPS and re-installing these packages does't help.
Even re-installing Hardy doesn't help

When I try to print anything the printopdrachtbeheerder (screen where I see the printing commands) sometimes accepts the printcommand, and sometimes it doesn't. After a while it asks me If the printer is connected or not.

When in a console I give this command: sudo hp-check -r
it gives one error and one warning:

There are no CUPS printer queues found

and

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: taakplanner is actief
Version: 1.3.7
error_log is set to level: warn

I cant find a way to add any CUPS printer Queue and SIP is not in my repositories.


I can ping the printserver. It has a valid IP nr (192.168.2.10) and replies. I can login to the printserver and find all the communication methods are turned on.

I tried: socket://192.168.2.10:9100 as printer port. Does't work (though it works in Gutsy (7.10)
I tried ipp://192.168.2.10/printers/1 Doesn't work
I tried lpd://192.168.2.10 Doesn't work

The printer cannot be browsed for (it couldn't in 7.10 Gutsy too)

I tried tot install hplip 2.8.4 from the HP website without any result. The HP device manager that comes with it doesn't see the connected printer.

What can I do apart from downgrading to Ubuntu 7.10 ?

Any help or suggestions would be very nice.

Jeroen


As far as I know the lpd command is lpd://192.168.2.10/L1 how about trying that?
Also try the ipp command using: ipp//192.168.2.10/ipp/P1
or ipp//192.168.2.10:631/ipp/P1

I have an epson that used to work under gutsy but doesn't under hardy, printing via a 3com print server. Unfortunately the printserver itself died a day ago, so perhaps that was the main problem for me!

However when it was working I setup a new printer under the GNOME printing screen from the main menus and chose "LPD" as the type of printer. The key entry was the "L1" which isn't intuitive but has to be used and must go in the queue field for the thing to work. It did the trick for me, hope it works for you, otherwise I can't help you more.

---

### Post by esmrg on 2008-05-18
I also lost printing ability after Hardy installed. I send a job to cups, then cups stops it. I checked dmesg and this is what I get:

[16394.427672] audit(1211154077.674:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=23459 profile="/usr/sbin/cupsd" namespace="default"

It is a usb printer and appears to be connected:

[15619.787827] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[15619.787851] usbcore: registered new interface driver usblp

I thought it may be a permission issue, so I tried to print as root. Same thing.

I looked in /var/log/cups/error_log and got this:

E [18/May/2008:16:27:12 -0700] [Job 114] ijsgutenprint: the version of Gutenprint software installed (5.0.2) does not match the PPD file (5.0.1).
E [18/May/2008:16:27:12 -0700] [Job 114] ijsgutenprint: bad key code -4

So I tried reinstalling the printer. Nope.

Any ideas?

---

### Post by adonet on 2008-05-19
Adding yourself to the USB users might help if you've got an USB connected printer. There are threads about that issue. 

This thread is about printing via the router to a printserver connected printer.

---

### Post by adonet on 2008-05-19
The lpd command responds that it is connected to the printer. A print command from yesterday rolls out of the printer, but nothing happens but waiting for half an hour.

---

### Post by adonet on 2008-05-23
Three days later still waiting....

Doesn't anybody have this problem. Doesn't somebody have a solution? I0d like to be able to print. from hardy.

---

### Post by redoscar3 on 2008-05-24
Adonet,

I just found your thread and like you, am having trouble printing via LPD in Hardy.  I've installed Hardy on my Acer 3003LCi laptop.  My printer is a Samsung ML1710 served by a Trendnet ethernet to USB print server.

With Dapper through Gutsy, it has been pretty easy to get printing configured on this machine.  But with Hardy, I still haven't had any luck.  When I try to print a document, the Samsung starts to run, but then enters an error state.  So I have to power off the printer to reset it.  All other printers on the network print without issue.

So you are not alone, but I have not yet solved the problem.  If I find something, I will let you know.

Red

---

### Post by derfinsterling on 2008-05-24
> **chrisccoulson said:**
> Did printing work after you put Apparmor in to complain mode?

The errors you listed suggest something wrong with the entries in /var/log/messages, which is causing logprof to choke. If printing works with Apparmor disabled, then I'll tell you how to clean your message log and get the relevant data.

Putting it in complain mode worked for me... what now?

---

### Post by redoscar3 on 2008-05-25
Hello again,

I was finally able to try putting AppArmor into complain mode and that allowed my Hardy install to print to my Samsung printer.  So what do I need to do from here to re-enable AppArmor but still continue getting printing to work?  Is there a thread that describes the process to reconfigure around offending issues?  This seems to be my last problem with Hardy that I need to get resolved.

Thanks for everyone help so far.

Red

---

### Post by adonet on 2008-05-25
I'm glad you can print at last. Look for an AppArmor specialist who might help you.

AppArmor in complainmode didn't do anything for me. So that isn't the problem for me. 
Is there anybody who didn't make a fresh install of Hardy, but an upgrade from gutsy who has the same problem?

Is booting Hardy with the older Gutsy kernel probably a solution?

---

### Post by musical-hans on 2008-05-26
> 
AppArmor in complainmode didn't do anything for me. So that isn't the problem for me. 
Is there anybody who didn't make a fresh install of Hardy, but an upgrade from gutsy who has the same problem?


I'm having both. A new install on a desktop machine and a update from Gutsy on my notebook. Both are having the same problem:(

Hans - desperately waiting for a solution

---

### Post by adonet on 2008-05-26
Hans,

is it possible to boot your from gutsy updated installation of Hardy with an older Kernel. (normally you can choose the kernel in the GRUB menu from which ubuntu normally starts.) Preferably the old gutsy kernel? 
And if so ,do you then still haven't any printing possibility?

I'm trying to find out if it is a problem in the new linux kernel that is used in Hardy. perhaps that offers a key to a solution.

Jeroen

---

### Post by musical-hans on 2008-05-26
> **adonet said:**
> Hans,

is it possible to boot your from gutsy updated installation of Hardy with an older Kernel. (normally you can choose the kernel in the GRUB menu from which ubuntu normally starts.) Preferably the old gutsy kernel? 
And if so ,do you then still haven't any printing possibility?

I'm trying to find out if it is a problem in the new linux kernel that is used in Hardy. perhaps that offers a key to a solution.


Yeeessss - it's working with the old kernel 2.6.22-14-rt and -generic :):)

Thank you very much for your suggestion!! This really keeps me going till the new kernel is fixed.

Hans

---

### Post by adonet on 2008-05-27
Hans,

I'll try it out this week (first with a copy of ubuntu 7.10) before ruining my working copy)

Anyone any Idea where to post this bug in the hardy kernel?
Jeroen

---

### Post by musical-hans on 2008-05-28
Hi Jeroen,

> **adonet said:**
> Hans,

I'll try it out this week (first with a copy of ubuntu 7.10) before ruining my working copy)

Anyone any Idea where to post this bug in the hardy kernel?
Jeroen

There is a new kernel-version (2.6.24-17) in the recent update. Everything is working fine now :)

Thank you very much for your help.

Hans

---

### Post by musical-hans on 2008-05-28
> **musical-hans said:**
> 
There is a new kernel-version (2.6.24-17) in the recent update. Everything 


I just updated my desktop machine as well and I'm still facing the same problem - Why?? The only difference between the two systems is that the desktop machine has a fresh install with Kubuntu (KDE-Desktop) and my working notebook installation is a update from gutsy with gnome desktop.
The notebook is working with the -rt kernel and the desktop machine is running the -generic kernel. Might this be a issue?

Hans

---

### Post by radagast1155 on 2008-05-28
I would strongly recommend the HP Toolbox app!

---

### Post by Dave Otter on 2008-05-28
System-Administraion-Printing
 Add new printer  
    Choose HP   laserjet 4000 is listaed

---

### Post by adonet on 2008-05-30
I have the updated kernel as well, but still can't print using hardy ande the printserver. I even installed the older gutsy kernel, but that makes the system run in low graphics mode. That's even worse.
I  can only print from Windows or from ubuntu gutsy (7.10) Ubuntu 8.04 with both kernels don't print.

any other Ideas?

---

### Post by musical-hans on 2008-05-31
> **adonet said:**
> I have the updated kernel as well, but still can't print using hardy ande the printserver. I even installed the older gutsy kernel, but that makes the system run in low graphics mode. That's even worse.
I  can only print from Windows or from ubuntu gutsy (7.10) Ubuntu 8.04 with both kernels don't print.


since the new update from yesterday I lost my ability to print again :confused: :confused:
This is really annoying!
hplip and stuff is installed. I'm working with all sorts of Linux for years and never ever had such problems to get a printer running.

Hans

---

### Post by adonet on 2008-05-31
> **musical-hans said:**
> since the new update from yesterday I lost my ability to print again :confused: :confused:
This is really annoying!
hplip and stuff is installed. I'm working with all sorts of Linux for years and never ever had such problems to get a printer running.

Hans
Hans,

I think we should make a bug report of this printing issue. I couldn't make a working updated version of ubuntu 710 to 804. Something went wronso I made a fresh installation of 804 (again) and installed the older 7.10 kernel 2.6.22-14. I can boot with that kernel, but only in low graphics mode. and that's not an option for me. 

I'm still using ubuntu 7.10 and porinting is working fine, but I don't like the fact that I can't update openoffice to version 2.4 , stellarium to version 9.10 and so on and so on.

I know I can print from suse, from PC LinuxOS and from Ubuntu 6.10, 7.04 and 7.10.

A guy from HP couldn't help me in another forum and no-one seems to know the answer.

really disappointing

Jeroen

---

### Post by adonet on 2008-05-31
> **radagast1155 said:**
> I would strongly recommend the HP Toolbox app!
Doesn't work either. We think its a kernel issue.

---

### Post by GiveLove on 2008-06-01
I have the same problem. Unable to print. Printer connected to a parallel port print server through the LAN. See my post:

[http://ubuntuforums.org/showthread.php?t=797508]("http://ubuntuforums.org/showthread.php?t=797508")


The upgrade to kernel 2.6.24-17-generic did not change anything.

---

### Post by adonet on 2008-06-02
I reported a bug in:
[https://bugs.launchpad.net/ubuntu/+bug/235197](https://bugs.launchpad.net/ubuntu/+bug/235197)
please add your bug to this report, so ubuntu starts a repair procedure.

Jeroen

---

### Post by somis on 2008-06-03
My SAMSUNG ML-2015 don't print anything since upgrade from 7.10 to 8.04 too.  I've tryed these things like cups protections and apparmor. don't works now. After searching internet i decided to put it here.
but, am. i still don't know how to change kerner i'm using. any help with this? :)

edit:
ok, downloading a new driver helped. But one interesting thing - there is no driver for ML 2015 in samsung.com, so i used one for ML 2010.

---

### Post by adonet on 2008-06-03
> **somis said:**
> My SAMSUNG ML-2015 don't print anything since upgrade from 7.10 to 8.04 too.  I've tryed these things like cups protections and apparmor. don't works now. After searching internet i decided to put it here.
but, am. i still don't know how to change kerner i'm using. any help with this? :)

edit:
ok, downloading a new driver helped. But one interesting thing - there is no driver for ML 2015 in samsung.com, so i used one for ML 2010.
You've probably got a driver problem. Please start another thread for that. I don't have a driver problem since the printer is working OK from 7.10 but isn't from 8.04 with the same configuration and driver.

---

### Post by GiveLove on 2008-06-04
Hey everyone,

Since there was a new kernel update today that brought it to: 2.6.24-18-generic, I thought I would try printing over the network again. It still does not work, and the symptoms are the same. Anyone else have a different experience?

---

### Post by adonet on 2008-06-04
> **GiveLove said:**
> Hey everyone,

Since there was a new kernel update today that brought it to: 2.6.24-18-generic, I thought I would try printing over the network again. It still does not work, and the symptoms are the same. Anyone else have a different experience?
I tested the print function with the new kernel, but still nothing comes out of the printer. I continue to use ubuntu 7.10. to be able to print.

I don't get any reaction on the ubuntu bug reporting site. It seems as if no-one is reading them.

Perhaps it's wise to make an orientation to another distro?

---

### Post by GiveLove on 2008-06-05
> Perhaps it's wise to make an orientation to another distro?

Agreed adonet. 

I've got my eye on Debian Linux and Arch Linux.
If things don't get fixed around here soon enough I'm gonna have to jump ship. :(

I find it very sad to see a previously solid distribution like Ubuntu sink to the lows of what we have seen in version 8.04 with network printing not working, all the problems with Pulse audio, and the weird graphical glitches I've seen. 

You can't please everyone. So I guess that is why there is so many Linux distributions to choose from. 

In this tug-o-war between stability, and leading edge features, I have to choose stability every time. New features will come in time. But if I cannot use the operating system and it's applications as I need, because things do not work, or are not stable. Then it is useless to me. 

> I don't get any reaction on the ubuntu bug reporting site. It seems as if no-one is reading them.

Let's hope someone takes notice soon.

Take care. :)

---

### Post by adonet on 2008-06-05
Thanx for your understanding. I'll wait for the time being and 'll keep on using ubuntu 7.10 for another half a year or so. Perhaps ubuntu 8.10 will be better. 7.10 is supported for another year.

I reported a bug at [https://bugs.launchpad.net/ubuntu/+bug/237759](https://bugs.launchpad.net/ubuntu/+bug/237759)

I certainly hope that someone of the ubuntu team will take notice soon.

Jeroen

---

### Post by prostar on 2008-06-06
If stability is more important to you than new features, I have to suggest you stop upgrading.  I didn't upgrade my AMD64 until yesterday to hopefully dodge most of these annoying bugs.  If I had waited another month or two, I may not have found any bugs.  I am the worst for violating this rule: "If it ain't broke, don't fix it!"

---

### Post by camateg on 2008-06-07
Adonet, try using the 2.6.22-14-generic kernel version on ubuntu 8.04, I had the same problem but downgrading my kernel version I made my print server works

---

### Post by GiveLove on 2008-06-08
I agree with you prostar. Unfortunately I never upgraded to 7.10. I was on 7.04 last. And I was under the assumption that since it had been a year that support was done for 7.04. So I just did a fresh install of 8.04 when it was released, assuming that everything would just work. As that had been my experience with 6.10 and 7.04. Ah well...

I would have thought that the developers for Linux distributions would want to avoid these same sort of snafu's that Microsoft forces it's users through. Wouldn't it just make more sense, and improve the reputation of Ubuntu and Linux in general, to release the whatever version only when it's done and ready? Rather than stick to deadlines? I mean if you overlook the poor engineering choices in Microsoft Vista, this is exactly what they did. And most informed users know how many problems Vista has.

I would like to see Linux distributions surpass these kind of things. I mean who cares if it comes out a month or two later than expected. It's not like Canonical makes money off of selling the operating system. They make money from selling support as I understand it. And if some users want all the new features and want to live on the "bleeding edge". Let them use a beta version. 

I mean as things stand now with all of the bugs in 8.04... I don't see how I could recommend Ubuntu to friends, colleges, and family. I would look like a complete *** for doing so. And ruin the possibility for people to get away from using Microsoft operating systems. With maybe the exception of Vista, as it wouldn't take much do better than that. LOL

There is always room for improvement. And I believe that Ubuntu has the capability to do this. But if not, other Linux distributions will take it's place. Survival of the fittest. Which is a beautiful thing within the Linux community. Because as we all know Microsoft doesn't compete in this way. 

Peace ):P

---

### Post by adonet on 2008-06-08
> **camateg said:**
> Adonet, try using the 2.6.22-14-generic kernel version on ubuntu 8.04, I had the same problem but downgrading my kernel version I made my print server works

I tried that,but it leaves me with a system that's running in low graphics mode. (640-480 256 colour) Not really an option I'm afraid.

---

### Post by camateg on 2008-06-08
but you were able to print with a 2.6.22-14-generic kernel or not?

---

### Post by rbmorse on 2008-06-08
system > administration > printing

Does you laserjet show up here? 

If not, can you add it from this screen? 

If it is, can you print a test page from this screen? 

If not, can you delete the printer, then add it again?

---

### Post by GiveLove on 2008-06-09
> system > administration > printing

Does you laserjet show up here? 

Only after creating a new printer.

> If it is, can you print a test page from this screen? 

Yes and no. I can click on the "Print Test Page" button. And I can see that something is sent to the print server. And the printers' light starts to blink as if it is receiving information and getting ready to print. And nothing else happens beyond that. 

> If not, can you delete the printer, then add it again?

Yes. But the results are the same. I have added and deleted printers here so many times trying to find a configuration that works. And no luck yet.

---

### Post by cariboo on 2008-06-09
Would this thread be of any help?

[http://www.linuxquestions.org/questions/linux-networking-3/configuring-cups-printing-through-router-w-print-server-158622/](http://www.linuxquestions.org/questions/linux-networking-3/configuring-cups-printing-through-router-w-print-server-158622/)

Jim

---

### Post by rbmorse on 2008-06-09
sounds like the wrong printer driver is loaded. This is an HP LaserJet 4000, correct?

---

### Post by adonet on 2008-06-09
> **camateg said:**
> but you were able to print with a 2.6.22-14-generic kernel or not?

Yes it prints OK with the older kernel 2.6.22-14-generic
but again, using  ubuntu 8.04 with this kernel forces the system to run in low-graphics mode. 

I have no Idea how to get it back to normal again.

---

### Post by adonet on 2008-06-09
> **cariboo907 said:**
> Would this thread be of any help?

[http://www.linuxquestions.org/questions/linux-networking-3/configuring-cups-printing-through-router-w-print-server-158622/](http://www.linuxquestions.org/questions/linux-networking-3/configuring-cups-printing-through-router-w-print-server-158622/)

Jim

No it isn't 
but thanks anyway

---

### Post by camateg on 2008-06-10
> **adonet said:**
> Yes it prints OK with the older kernel 2.6.22-14-generic
but again, using  ubuntu 8.04 with this kernel forces the system to run in low-graphics mode. 

I have no Idea how to get it back to normal again.

We can say that it really is a kernel bug, that's exactly what happens with me, but I have normal resolution with this kernel.

I'll tell it in the [https://bugs.launchpad.net/ubuntu/+bug/237759](https://bugs.launchpad.net/ubuntu/+bug/237759). I think there's nothing to do right now while they don't fix it.

PS: sorry about my english...

---

### Post by redoscar3 on 2008-06-15
Hello again.  I was here about 2 weeks ago, and had similar issues printing to my Samsung printer which is served by a Trendnet print server.  At that time I was able to fix the problem by executing sudo aa-complain cupsd.  However, since that time, one of the package updates has again killed my ability to print, and the aa-complain trick no longer works.  This happened about a week ago.  So now my Hardy laptop has become a non-printing computer.

This has to be a Hardy bug (as you are suggesting) because I can still print to the Samsung just fine from Dapper, Edgy, Feisty, Gutsy, and Debian Sarge.

Hopefully a solution gets here sooner rather than later.

Red

---

### Post by GiveLove on 2008-06-17
As of 2.6.24-19-generic I am finally able to print!!!!

I'm so happy!
I hope this is the case for everyone else.
To bad it took so long to fix.

---

### Post by redoscar3 on 2008-06-17
> **GiveLove said:**
> As of 2.6.24-19-generic I am finally able to print!!!!

I'm so happy!
I hope this is the case for everyone else.
To bad it took so long to fix.

I too have been successful at getting printing to work with the latest kernel upgrade.  I am keeping my fingers crossed that nothing else has broken in the process.  Hardy is looking better all the time.

Red

---

### Post by adonet on 2008-06-17
Well at my system it prints something, but it's not really impressing. I got the first page of a document of three pages and it took half an hour to print. I still get the messages asking whether or not the printer is connected.

So I keep on using Ubuntu Gutsy 7.10 instead of Hardy 8.04

---

### Post by adonet on 2008-06-17
Well at my system it prints something, but it's not really impressing. I got the first page of a document of three pages and it took half an hour to print. I still get the messages asking whether or not the printer is connected.

So I keep on using Ubuntu Gutsy 7.10 instead of Hardy 8.04

---

### Post by pschuel on 2008-06-18
I had the same problem as mentioned above - printing to IP printer doesn't work (or is so slow that it takes days to print 1 page) with Hardy and 2.6.24 kernel (-19-rt here). Printing from a Windows XP virtual machine (virtualbox) on the same machine worked. Downgrade to 2.6.22 kernel from Gutsy repos worked also.

After some further research I found that the bug mentioned further up in this thread is a duplicate of bug #213081 and also occurs in other distros (Debian, Gentoo, ...) with the 2.6.24 kernel.

In the bug report of #213081 there is also a workaround mentioned:
with your favourite editor, add a line with

net.ipv4.tcp_frto = 0

to /etc/sysctl.conf (as usual, back it up before changing). Reboot or 'sudo sysctl -p' and probably also 'sudo /etc/init.d/cupsys restart' and enjoy (but ensure there aren't 20 documents in the queue before trying this ;-))...

I tried this workaround and can finally print with the 2.6.24 kernel :-)

Hope this helps
Patrick

---

### Post by adonet on 2008-06-18
I'm glad for you, but I 'm afraid this doens't help for me. Im using kernem 2.6.24-19 at the moment and still nothing is getting out of the printer. Even after rebooting the entire system it doesn't print.

---

### Post by pschuel on 2008-06-19
> **adonet said:**
> I'm glad for you, but I 'm afraid this doens't help for me. Im using kernem 2.6.24-19 at the moment and still nothing is getting out of the printer. Even after rebooting the entire system it doesn't print.
I'm sorry to hear that it doesn't work for you - I thought it was sort of a general solution to this problem. Maybe there are different versions of the bug :-(

Patrick

---

### Post by Cotopaxi on 2008-06-19
One question:

I have a Brother MFC-5440CN connected via USB and I am also not able to print at all.

Should I open up a new thread or should I post it in here?

Concerning the bug report, should I open a new bug report for USB printing?

---

### Post by adonet on 2008-06-19
There are allready other threads about printing via USB. I suggest you search for them with words like "print usb ubuntu" in google.

---

### Post by adonet on 2008-06-19
> **pschuel said:**
> I'm sorry to hear that it doesn't work for you - I thought it was sort of a general solution to this problem. Maybe there are different versions of the bug :-(

Patrick

What version of the kernel are you using, and what version of hplip and CUPS?

Jeroen

---

### Post by GiveLove on 2008-06-19
A new issue has come up. Initially after updating to the 2.6.24-19-generic kernel, I was suddenly able to print. But as of this morning, I could not print anymore. :(

So I tried the solution that pschuel posted on the previous page, and I can suddenly print again! Yay! :) 

> I had the same problem as mentioned above - printing to IP printer doesn't work (or is so slow that it takes days to print 1 page) with Hardy and 2.6.24 kernel (-19-rt here). Printing from a Windows XP virtual machine (virtualbox) on the same machine worked. Downgrade to 2.6.22 kernel from Gutsy repos worked also.

After some further research I found that the bug mentioned further up in this thread is a duplicate of bug #213081 and also occurs in other distros (Debian, Gentoo, ...) with the 2.6.24 kernel.

In the bug report of #213081 there is also a workaround mentioned:
with your favourite editor, add a line with

net.ipv4.tcp_frto = 0

to /etc/sysctl.conf (as usual, back it up before changing). Reboot or 'sudo sysctl -p' and probably also 'sudo /etc/init.d/cupsys restart' and enjoy (but ensure there aren't 20 documents in the queue before trying this )...

I tried this workaround and can finally print with the 2.6.24 kernel

Hope this helps
Patrick

Thank you for posting this workaround pschuel. :)

Obviously, I am happy that I can print again. But also concerned that it requires a workaround long before it actually gets fixed properly. And also that I will have to continue to keep a close eye on the results of this problem to know when it is really fixed. As I have a secondary computer that I have been waiting to install Ubuntu 8.04 once this network printing problem is solved.

---

### Post by pschuel on 2008-06-19
> **adonet said:**
> What version of the kernel are you using, and what version of hplip and CUPS?

Jeroen
patrick@linuxps:~$ uname -a
Linux linuxps 2.6.24-19-rt #1 SMP PREEMPT RT Wed Jun 4 18:50:11 UTC 2008 i686 GNU/Linux

(I am using the -rt variant because of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234084]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234084"))

patrick@linuxps:~$ cups-config --version
1.3.7

patrick@linuxps:/usr/share/hplip$ sudo apt-cache showpkg hplip
Package: hplip
Versions: 2.8.2-0ubuntu8

---

### Post by adonet on 2008-06-24
I got in another forum this suggestion and after some reboots it works:

I think I have solved my problem - on my system the printserver printing issue appears to be down to permissions on config files stored on /home.

I have /home on a separate partition from my system and when I upgraded i simply reformatted the system partition and reinstalled. When you do this you create a new user, which might be the same username and password as you used on the old install, but as far as the system is concerned is different. Consequently your new login can not access the .XXXXXX configuration files on /home.

Thanks to nelz at linuxformat.co.uk for spotting this. The solution is to run in the terminal:
    sudo chown -R username: ~username

Where username is the username you login with after a restart. You should reboot after doing this.

I got one error message after doing this. Then I rebooted and still couldn't print. I rebooted again in gutsy and lost the print ability there as well. I repeated the chown command in gutsy, rebooted and could print again. I rebooted in hardy and a miracle happened: The printer started printing, from Hardy that is.

Thanks to
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/28](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213081/comments/28)

Jeroen

---

### Post by GiveLove on 2008-06-25
Hiya adonet,

I'm glad you found an answer to your network printing problem. I was starting to wonder if perhaps you had a unique install, or environment.

I just installed Ubuntu 8.04 on my secondary computer. (Arch linux was waaaay to difficult. Debian would not recognize my cheapo D-Link DFE-530TX+ network card. Go figure. :roll: )  Anyways, I had to apply the exact same workaround I used on my primary computer to get network printing to work. Nice to see that the problem and work around is at least consistent. Assuming you are doing a fresh install with all linux partitions and/or entire hard drive(s) wiped clean. 

Cheers!

---

### Post by SimoneB on 2008-07-16
I've tried both the "net.ipv4.tcp_frto = 0" and "sudo chown -R username: ~username" solutions, but none of them work.
I've also tried to set up the printer as IPP or LPD with no luck.
Also tried booting with kernel 2.6.20, but nothing changed (i didn't have an available 2.6.22 kernel).

But, I managed to get it to print using the "Generic PCL 6/PCL XL Printer - CUPS+Gutenprint v5.0.2" driver. Unfortunately, it prints just in black and white.

I have a Sharp MX-2300N network printer

---

### Post by adonet on 2008-07-17
I don't know your printer. My system works fine now since I applied both solutions. the "sudo chown -R username: ~username" I used was both time with the "username" replaced with my actual username. So I typed: "sudo chown -R jeroen: ~jeroen". I', using the normal recomended printerdriver for my HP printer. And I could print from Ubuntu 7.10 and from Windows on more than one machine.
Dit you try to print from an older version of Ubuntu or even from windows? Does that work for you?

Jeroen

---

### Post by SimoneB on 2008-07-18
Thanks for your interest. Of course, i replaced "username" with my actual user name. 
I have two linux machines, one with Ubuntu 8.04 and Windows XP, and the other with just Xubuntu 8.04. I can't print from any of the ubuntu machines with the Sharp driver, though I can with the generic one (in black and white). Also, I can print fine from windows.
I can also print just fine with Ubuntu on another network printer, a Samsung ML-3050 (this one is a black and white only so it wouldn't be a problem anyway to print with a generic driver).
It could be a problem with the Sharp driver, but I tried the foomatic driver, the one on the printer CD, and another one from openprinting.org, and none of them worked.
I tried booting Xubuntu 8.04 with the 2.6.20 kernel, but that didn't help. 
By now, I don't have other ubuntu/kernel versions to try

---

### Post by adonet on 2008-07-18
I afraid thats your printing problem is not the subject of this thread, but a problem of your sharp printer. Dit you try to connect the printer directly to your computer. That is on the USB of parallel port? Does that give the same problem? If that's the case one could think it's a driver problem and not a network printing problem. If your printer works fine when connected locally, you've discovered yet another network printing problem and I suggest you could post a message on the [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) site.

At least the developers will know that your bug excists.

succes

Jeroen

---

### Post by Stan Koper on 2008-07-20
I'm having a similar problem with a Hawking HPSP3 printserver.  I have a Lexmark Optra Rt+ printer attached to it at lpt1.  With Gutsy, I could print fine.  With Hardy, I can find the print server, but when I try printing a test page, sometimes it works, but more often it sends what looks like PS output to what is a PCL 5 printer.  You know, one stepped line of garbage characters per page...And I haven't yet been able to print anything more than an occasional test page.
It seems to me that I ought to be able to set the Lexmark up as an LPD printer:   lpd://192.168.10.250/lp1.  That's how I have it set up on another computer running OpenSuse 10.3  OpenSuse has no problems, and Gutsy had no problems printing to the Optra using lpd.  But for some reason, since I upgraded to Hardy, it's not working.  I have two computers running Hardy, and neither can print properly to this printer.  

I also have an HP 4500 with a jetdirect card installed, and Hardy has no problem with that.  

Has anyone encountered this problem, and found a solution?  I even copied the PPD file from OpenSuse and tried that with one of the Hardy computers.  No difference.  

I'm wondering where Hardy puts the command line lpr etc...  I'm thinking maybe I can track the one down in OpenSuse and compare them, to see if Hardy is doing something that OpenSuse doesn't, or vice versa.

---

### Post by polytropos on 2008-07-21
I've recently upgraded from Gutsy to Hardy 8.04.1 and am having the same printing issues described here.  I've tried all of the solutions proposed here, but none has worked yet.  Help!  

Here is some possibly relevant information about my situation:

Printer: Epson Stylus Color 670

Upgrade: Fresh installation from a live CD.  In Gutsy I did not have a home partition; I made and have one now in Hardy.

Adding printer from the main menu: When the "Select Connection" window opens, my options are:

Gutenprint Parallel Port #1
Print into PDF file
AppSocket/HP JetDirect
Internet Printing Protocol (iip)
LPD/LPR Host or Printer
Windows Printer via SAMBA
Other

When I select the first option, my computer does not automatically recognize the printer as an Epson, so as I go through the menus I choose that as well as the model number.  When I try to print a test page, nothing happens.

Adding printer from CUPS 1.3.7: same deal.  I've done this by typing
[http://127.0.0.1:631](http://127.0.0.1:631) into Firefox.  After getting everything set up, when I try to print a test page, the message at the top of the screen reads "Parallel port busy; will retry in 30 seconds...", and then nothing happens.

The 'chown' solution: When I run it, I get the following message:

grahamhubbs@aja:~$ sudo chown -R grahamhubbs: ~grahamhubbs
chown: cannot access `/home/grahamhubbs/.gvfs': Permission denied

pschuel's editing solution: Did nothing.

Ideas?

---

### Post by reuben on 2008-08-10
Same issue for my. HP Laserjet 4L. No solutions work for me so far. The same problem occurs on two computers, one of which is a fresh install, the other an upgrade.

---

### Post by ricnmar on 2008-08-12
I have had similar trouble - I seem to lose all of my installed printers and when I try to print I get just a 'Print to File' option as my printer.  If I go into the menu 'System > Administration > Services' and uncheck and then recheck the 'Printer service (cupsys)' option, then all of my printers come back, for a while.  

var/log/messages gives a clue, but I don't know yet what this means:

Aug 12 07:42:41 64ubu804 kernel: [83081.085524] cupsd[6818]: segfault at 0 rip 7fc5053fcbb0 rsp 7fff0f140da8 error 4

This is not a fix, but it gets me printing when I need to, at least for the moment.

-ricnmar

---

### Post by alchimist75 on 2008-08-20
Hi all,
I am not sure if I should open a new thread so I post my problem here,   due I think that i have a similar problem.

After a software update I can not print to a network printer in our net.
Everything was fine by then. :confused:

If I change the loglevel to debuig in the cupsd.conf i get the following errot in the error_log

```

D [20/Aug/2008:20:35:46 +0200] [Job 1074] Connected to IPNUMBER:515 (IPv4) (local port 0)...
D [20/Aug/2008:20:35:46 +0200] [Job 1074] lpd_command 02 raw 
D [20/Aug/2008:20:35:46 +0200] [Job 1074] Sending command string (5 bytes)...
D [20/Aug/2008:20:35:46 +0200] [Job 1074] Reading command status...
D [20/Aug/2008:20:35:46 +0200] [Job 1074] lpd_command returning 3
D [20/Aug/2008:20:35:47 +0200] [Job 1074] File 0 is complete.
I [20/Aug/2008:20:35:47 +0200] [Job 1074] Backend returned status 1 (failed)
D [20/Aug/2008:20:37:44 +0200] [Job 1074] Loading from cache...
D [20/Aug/2008:20:37:44 +0200] [Job 1074] Loading attributes...

```

I am pretty sure the error is 
```
I [20/Aug/2008:20:35:47 +0200] [Job 1074] Backend returned status 1 (failed)
```

Any help is appreciated

Maybe this helps
```
uname -a
Linux aerosol 2.6.20-16-generic #2 SMP Tue Dec 18 05:45:12 UTC 2007 i686 GNU/Linux
```

:confused:

---

### Post by adonet on 2008-08-20
Did you also do this:?

with your favourite editor, add a line with

net.ipv4.tcp_frto = 0

to /etc/sysctl.conf (as usual, back it up before changing). Reboot or 'sudo sysctl -p' and probably also 'sudo /etc/init.d/cupsys restart' and enjoy (but ensure there aren't 20 documents in the queue before trying this )...


This is the primary solution to my problem. The chmod command is only required for new installed system with a separate /home partition and the same username as used in another linux installation.

It is enough to get a fresh installed new computer in my network printing to the printserver connected HP Laserjet printer.

I hope this helps....

Jeroen

---

### Post by alchimist75 on 2008-08-21
Yes I already edited /etc/sysctl.conf
net.ipv4.tcp_frto = 0

after sysctl -p

I got this message in the xterm

```

kernel.printk = 4 4 1 7
net.ipv4.tcp_frto = 0

```

The kernel I am using is 
```
uname -a 
Linux aerosol 2.6.20-16-generic #2 SMP Tue Dec 18 05:45:12 UTC 2007 i686 GNU/Linux
```

after restarting cupsd I stil have the error in th error_log
```

I [21/Aug/2008:10:05:21 +0200] [Job 1081] Adding start banner page "none".
I [21/Aug/2008:10:05:21 +0200] [Job 1081] Adding job file of type application/postscript.
I [21/Aug/2008:10:05:21 +0200] [Job 1081] Adding end banner page "none".
I [21/Aug/2008:10:05:21 +0200] [Job 1081] Queued on "lj2200" by "root".
I [21/Aug/2008:10:05:21 +0200] [Job 1081] Started filter /usr/lib/cups/filter/pstops (PID 8333)
I [21/Aug/2008:10:05:21 +0200] [Job 1081] Started filter /usr/lib/cups/filter/pstoraster (PID 8334)
I [21/Aug/2008:10:05:21 +0200] [Job 1081] Started filter /usr/lib/cups/filter/rastertogutenprint.5.0 (PID 8336)
I [21/Aug/2008:10:05:21 +0200] [Job 1081] Started backend /usr/lib/cups/backend/lpd (PID 8337)
E [21/Aug/2008:10:05:25 +0200] PID 8337 (/usr/lib/cups/backend/lpd) stopped with status 1!
I [21/Aug/2008:10:05:25 +0200] Hint: Try setting the LogLevel to "debug" to find out more.
I [21/Aug/2008:10:05:25 +0200] [Job 1081] Backend returned status 1 (failed)
```

any further help
:confused:

---

### Post by adonet on 2008-08-21
Hi Alchimist75

I 'm using the 2.6.24-19-generic kernel. The printing problems We were discussing about only occured with any 2.6.24-XX kernel. The 2.6.22-XX kernel from ubuntu 7.10 didn't have any trouble.

The edited /etc/sysctl.conf
net.ipv4.tcp_frto = 0
solution only applies for users of the 2.6.24-XX kernel, so I'm told.

maybe updating your kernel would help? I think it could be done from synaptic. That is if you're using ubuntu 8.04. 

(Well I'm not a ubuntu guru of any kind, so don't try it on any production machine.)

regards

Jeroen

---

### Post by rem8114 on 2008-09-07
I have had the same issue with a Hawking print server.  With the 2.6.24-19 kernel and using the sysctl.conf edit I got it to print one document, but now it is leaving the printed job in the queue as described in [http://ubuntuforums.org/showthread.php?p=5744583](http://ubuntuforums.org/showthread.php?p=5744583).

Has anyone run into this as well?

Ron

NOTE: Solved this by putting ?waitjob=false after URI.

---

### Post by andyfigueroa on 2008-11-11
> **adonet said:**
> Hi Alchimist75

I 'm using the 2.6.24-19-generic kernel. The printing problems We were discussing about only occured with any 2.6.24-XX kernel. The 2.6.22-XX kernel from ubuntu 7.10 didn't have any trouble.

The edited /etc/sysctl.conf
net.ipv4.tcp_frto = 0
solution only applies for users of the 2.6.24-XX kernel, so I'm told.

maybe updating your kernel would help? I think it could be done from synaptic. That is if you're using ubuntu 8.04. 

(Well I'm not a ubuntu guru of any kind, so don't try it on any production machine.)

regards

Jeroen

That was it!  I'm using Mint (Hardy 8.04) with Kernel 2.6.24-21 (in order to get the ath5k kernel driver for a newer Atheros wireless card) and have been fighting this bug all day.  Upon making the edit as described above and commanding "sysctl -p" all cups errors went away and printing has been easy.  The printer that was causing me trouble was a Brother Fax-4100 w/ hl730 Foomatic driver.  My postcript  and foo2zjsrinters were never affected.

BTW, this is a new installation on the new eMachine $299 (Best Buy) D620 notebook, a particularly Linux compatible collection of hardware.

Jeroen - you are an Ubuntu guru for me!

---

### Post by lisaviolin on 2008-11-26
This is true for me as well.  I have no idea where to find apparmor to put it in "complain" mode.  where is it?  I'm running Hardy with a Brother MFC440CN printer that worked with Gutsy.

Is there someone with an answer?

---

### Post by adonet on 2008-12-01
> **lisaviolin said:**
> This is true for me as well.  I have no idea where to find apparmor to put it in "complain" mode.  where is it?  I'm running Hardy with a Brother MFC440CN printer that worked with Gutsy.

Is there someone with an answer?

Did you try the solutions that were mentioned earlier in this thread? Esp in #77?

---

