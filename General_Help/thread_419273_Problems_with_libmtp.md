---
title: "Problems with libmtp"
date: 2007-04-22
forum: General Help
---

### Post by Chumsley on 2007-04-22
So, here's the deal.  I have a Creative Zen Vision:M 30 GB mp3 player.  It worked with Edgy, after I compiled the then-most-recent versions of Amarok and libmtp from source.  I was happy and content with my Ubuntu - it did everything I wanted it to, and I felt a sense of accomplishment in learning about compiling and all that.

I update to Feisty, and that's pretty much the end of paradise.

Lsusb says the player is there, when I plug it in.  mtp-detect gives me this:
> jordan@jordan-desktop:~$ lsusb
Bus 004 Device 008: ID 041e:413e Creative Technology, Ltd 
Bus 004 Device 003: ID 1058:0404 Western Digital Technologies, Inc. 
Bus 004 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
**jordan@jordan-desktop:~$ mtp-detect**
Autodetected device "Creative Zen Vision:M" (VID=041e,PID=413e) is known.
PTP: Opening session
PTP ERROR IO: Trying again after resetting USB
PTP: Opening session
Could not open session! (Return code 767)
  Try to reset the device.
PTP: request code 0x0000 sending req wrote only 12 bytes instead of 0
Could not get device info!
Connection error.
No devices.


lsusb then no longer lists the player until I either restart it or unplug it and plug it back in.

I don't know what the problem is.  I've tried reinstalling libmtp, even compiling from source and installing that.  I've followed every how-to related to this on these forums, and even some others.  I've changed the usb port the player is plugged into.  I've restarted the computer.  I've disabled and re-enabled usb 2.0, which someone said would fix my problem.  I shouldn't even HAVE a problem, according to most of what I've read.  Amarok, gnomad2, and libmtp are all supposed to work 'out of the box' from the Feisty repositories.

I'm at wit's end, here, folks.  Please, somebody help me, before I take drastic measures.
Like re-installing Windows.
](*,)

---

### Post by Chumsley on 2007-04-30
Nothing?

---

### Post by Donshyoku on 2007-05-02
Try running **mtp-detect** from the command line and post your results.  I have the same player and I am running the libmtp and libusb from the Fiesty repositories with no problem.

---

### Post by Chumsley on 2007-05-03
I did, it's the second half of what I quoted.  I just tried it again, with identical results.

That's why I'm so confused - I'm using the repository versions of the files/programs in question, and I seem to be the only one with this problem.

---

