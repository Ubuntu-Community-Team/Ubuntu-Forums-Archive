---
title: "machine keeps freezing"
date: 2023-08-03
forum: General Help
---

### Post by jgw on 2023-08-03
When I start/re-start my machine, and touch the mouse, my machine freezes.  I know its frozen because I can see my cpu, memory and network usage and they are all frozen as well as my mouse.  I have now restarted at least 3 times and its also consistent.  I have hooked up a keyboard via usb so I can do something which didn't work because the system was FROZEN.  I have no idea what to do. 

I have now moved the computer to a different place and started it again and, this time, it worked just fine.  That means, I think, that something that I am plugging in is not right.  When its running at the original place there are some things getting plugged in that may be causing this.  This machine is also attached to my tv.  The display and is run by my denon avr-s530bt av receiver which controls both the display and the sound.  This has been working for, literally, years and it works just fine (I believe).  When this boots up, before it freezes, the display is dandy, for instance.  I connect with the receiver with an hdmi connector.  I have two things connected which is decided by the denon.  One is just plain old tv and the other is this system.  Computer works fine when it does not deal with the denon and, instead uses the regular hook up to the monitor.  

I just moved the computer back - it didn`t work.   Turned it on, it booted up, showed me the programs running (firefox, ubuntu softwae, transmission, and volumn control.  One thing I should have done is see what happens when it works and NOTHING is on.  I am going to take care of that and see what happens.  

I have also changed from weyland to x10 and nvidia driver (didn't change anything)

Just tried to start it with only one thing on, pia (vpn)   Same old thing.  Boots, and then freezes.  I later tried it without pia (nothing on)  Same problem........

OK, I have 3 hard drives on this system.  I also have a 1tb ssd that handles booting, etc.  I have now taken all my hard drives off line.  So, I have a problem on one of my drives.  I will now take each drive, one at a time, to see which one is screwing things up.  After I figure out which one is the evil one I am going to have to figure out what to do.  

I tried the first drive.  Plugged it in and nothing happened and not frozen!  Then I tried to reboot - failure (the ubuntu thing showed but no reboot).  Not only that but now, regardless of drives are running or not the system is freezing.

I can, however get it to run just fine where I am now, the only difference is video is actually plugged in instead of the hdmi thing.  Which actually works just fine when it doesn't freeze.

It would be nice to be able to paste the stuff that comes up when its booting.  I do, however, have "logs" here is my current log which is in the reply below (this is getting too big, I think)


Hopefully, somebody can help me figure that one out. 

Help!!

---

### Post by jgw on 2023-08-04
system-info report:  [https://paste.ubuntu.com/p/2mWVwgqdM8/](https://paste.ubuntu.com/p/2mWVwgqdM8/)

It would be nice if there was a way to either log or stop and start or slow down what is displayed whilst starting up.  There seems to be a lot of it.

I don't know why some of this stuff is here:
waiting for device /dev/disk/by-label/new-4tb.      There is n /new-4tb but used to be>
don't know about pulseaudio                                I start pulseaudio with a 'pulseaudio' in startup applications
fstab has a bunch of stuff that doesn't exist

That's about it.  The rest are mysteries for me. 

my newest log (from log file "logs")::

[HTML]10:53:41 AM systemd: Timed out waiting for device /dev/disk/by-label/new-4tb.
10:53:41 AM kernel: ata4.00: status: { DRDY }
10:52:45 AM kernel: I/O error, dev sdc, sector 134219776 op 0x0:(READ) flags 0x83700 phys_seg 1 prio class 2
10:52:45 AM kernel: ata5.00: error: { UNC }
10:52:42 AM pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
10:52:24 AM systemd: Failed to start Application launched by gnome-session-binary.
10:52:12 AM kernel: /usr/lib/systemd/system-generators/systemd-fstab-generator failed with exit status 1.
10:52:12 AM kernel: Failed to create unit file /run/systemd/generator/mnt-back.mount, as it already exists. Duplicate entry in /etc/fstab?
10:52:12 AM kernel: I/O error, dev sdc, sector 512 op 0x0:(READ) flags 0x80700 phys_seg 1 prio class 2
10:52:12 AM kernel: ata5.00: status: { DRDY }
10:52:12 AM kernel: ata5: SError: { RecovComm Persist HostInt PHYRdyChg 10B8B }
10:52:12 AM kernel: ata5.00: irq_stat 0x00400000, PHY RDY changed
10:52:12 AM kernel: ata5.00: irq_stat 0x00400000, PHY RDY changed
10:52:12 AM kernel: ata5.00: exception Emask 0x50 SAct 0x4 SErr 0x90a02 action 0xe frozen[/HTML]

---

### Post by jgw on 2023-08-10
I have now fixed my problem.  What I did was take the ssd (where the boot is), took it out of one machine and put it into the other and then turned on the other and it came up and everything was fine.  I then took it out and put it back in the machine that had the problems and that did fine too.  I have now had a functioning machine for a couple of days!  

I also went in and got rid of some stuff I didn't need, etc.  Found out, for instance, that half the stuff I have on my machine(s) is logs for just about everything and they are never cleaned out.  I found logs that were over 5 years old!!  Should probably be some kind of cleaner to take care of that one and suspect they may be one - who knows??

---

