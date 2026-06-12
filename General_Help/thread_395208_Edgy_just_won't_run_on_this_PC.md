---
title: "Edgy just won't run on this PC"
date: 2007-03-27
forum: General Help
---

### Post by zaphod42 on 2007-03-27
Edgy just won't run on this PC

Symptoms are:
Live 6.10 ubuntu CD boots to a desktop (sometimes), then blinks the screen twice and drops back to login screen within 5 to 10 seconds.
It then logs in atuomatically, blinks twice and drops back again, repeating 3 to 5 times, each time with a window saying " Ive detected a panel running and will now exit"
After that sometimes it'll give a desktop  with three copies of file browser open.
You can't do much at this point as the mouse pointer dissappears after first click.
You can't switch to the console.
If you then shut down you get a blank brown screen and ejects the CD.


I have downloaded the CD a second time, same thing, downloaded Xubuntu and it does the same thing (yes exactly). Yet they all boot OK on other PC's i've tried.
Tried a different CDROM drive, keyboard and mouse in this PC and still same problem.

If I boot while watching the console ( quite and splash removed in boot options),
The only problem I can see is the following repeated about 8 times. 

"
hdc media error (bad sector)=0x34 {Aborted Command LastFailedSense =0x03}
ide: failed opcode was unknown
end=request : I/O error dev hdc , Sector 1430256
Buffer I/O error on device hdc, Logical block 357564
hdc media error (bad sector)=0x51 {DriveReady SeekComplete Error}
"
This occurs with different different hard drives installed or none at all.


PC Hardware:
PC partners/ Elpina M/B
Celeron 1.2ghz
RAM 1 x 256mb PC133 & 1 x 128mb PC133
Chipset Via VT82C686B
Video card Voodoo 3
NIC realtec 8139

This hardware runs Knoppix, 98SE and Xp without a hitch.

Can anyone give a suggestion to regain my sanity?:confused: 

Also Is there any boot option to pipe the boot console txt to a com tty port for indepth diag?
Or creating the bootlog on writable media?
:(

---

### Post by NT4usB on 2007-03-27
I believe the alternate CD gives some more install options... F1 to read the options.
iirc, there's an install command string you can remove the 'quiet' (-q?) switch from so you can see the install progress.
Alt+F1, F2, etc shows some terminals.
I fought this installing Edgy on an old PIII 550 i810 board and 768 of pc100.
Finally, after messing around a whole bunch in the bios, disabling stuff I thought (hoped) it wouldn't need, setting irq's, etc. to auto, and pulling all the cards (it was loaded with tuner/video/nic/modem/etc) cards, it installed.

---

### Post by zaphod42 on 2007-03-28
Further results but still no install or sucessfull boot.

Changed video card to Voodoo Banshee and also a video magic 128 but still no change.

Downloaded Alternate Install CD checked it and started install. This failed (twice) at xresprobe and  rebooted.

If trying to boot from hard drive after failed install "error loading operating system" occures.

I think I might stay with 98se to keep my sanity ( at least it doesn't take more than two days to get a working O/S)

Just as a reminder Knoppix 3.6 runs on all the above hardware that ubuntu won't.

:mad: :confused:

---

### Post by zaphod42 on 2007-04-04
Finally after a lot of stuffing around I managed to get Edgy working on this machine. (all be it without 3d hardware acceleration )

It all hinges around the bug Edgy has with Voodoo video cards. I see a lot of threads with very similar boot and x related problems.
The procedure I worked out was to do an install with the 'alternate' Edgy CD and then boot from the Hard drive in recovery mode.

from the console find xorg.conf in /etc/X11 and edit this adding the following line in the Section "Device"

	Option		"NoAccel" "true"

This then allowed X to boot happily on both my Voodoo 3 3000 and the Voodoo Banshee video cards.
I was initially stuck with screen resolutions 640x480 and 800x 600 however I then edited xorg.conf again and added the folowing to the Section "Monitor"

	HorizSync	28-49
	VertRefresh	43-72

This then allowed 1024 x 768 resolution.

Does any one know the solution to get Voodoo cards working fully with hardware acceleration under Edgy.????????

:grin:

---

