---
title: "Green rectangles appear, system is immediately unresponsive and then reboots"
date: 2013-03-02
forum: General Help
---

### Post by Palu on 2013-03-02
I just completed a new build and think I did comprehensive hardware research for Linux incompatibility issues, but after a silky smooth installation I logged in and got  green lines / rectangles after about a minute. It doesn't seem to be based upon particular actions. It happens even if I wait on the login screen. Before it happens I can connect to internet, load the software center, etc. Afterwards the system doesn't respond to mouse or keyboard. Google has plenty of ideas for Windows problems, but nothing that seems to apply to me. I don't know if this is a driver or a bad processor, etc.

OS: Ubuntu 12.10, 64-bit
Processor and Graphics: i5 3570k intel HD 4000
HD: Samsung 840 Pro Series, 256 GB SATA 6GB/s SSD (MZ-7PD256BW)
MB: Gigabyte Mini-ITX (GA-Z77N-WIFI) LGA 1155
RAM: Corsair Vengeance 16GB (2x8GB) DDR3 1600 MHz

Troubleshooting so far:
1. Swapped HDMI in for the DVI I started with before realizing the system was unresponsive too.
2. I thought I should try booting from a USB (for instance, the one I installed Ubuntu from) which I cannot seem to do because the computer doesn't seem to have a bios screen that stays on long enough for me to change boot order. It is instantly at GRUB. I guess that's the speed I get with and SSD... I feel like this would be a good test, so any tips are appreciated. Can I add a USB to the GRUB menu or select it somehow? I don't see an obvious option.

[ATTACH=CONFIG]239664[/ATTACH]

---

### Post by matt_symes on 2013-03-02
Hi

No idea what could be causing that.

The first place to look would be the logs though.

I suspect it's the only way to get a handle on what is happening.

When the system freezes can you get to a console (ALT + F1) and restart lightdm ?

```
sudo service lightdm restart
```

Does the magic key combination reboot gracefully ?

alt + sysReq (keep depressed then hit the next 6 keys, one after another, with a 3 second gap between) r e i s u b

I.E. Is it X or the kernel hanging ?

Post 

```

/var/log/xorg.0.log
/var/log/dmesg
/var/log/syslog
```

Zip then up and add them as attachments in your next post.

Obviously make sure you get the correct version of the logs. i.e. get the xorg log file for when the system was actually playing up.

As for the BIOS screen, start tapping the BIOS key before starting the PC and hammer it hard :)

Kind regards

---

### Post by Palu on 2013-03-02
I just booted from the USB I installed from and went into the "try Ubuntu" mode. Same results, so I think that rules out the SSD. I tried your key combo too. The first attempt it restarted before I'd typed it all. The second time, nothing seemed to happen. Since the mouse and keyboard don't respond, I cannot get into a console, but I'm looking through my usb now from this computer to see if I can access logs from the USB. If it looks like the logs are empty, I'll put the machine's SSD in an HD dock and find them on there.

---

### Post by matt_symes on 2013-03-02
Hi

If the magic key combination is not working then that would point to the kernel locking up.

One thing i would suggest is to practice the magic key combination when the computer has not locked up. 

It can be a little bit difficult to get right and, if you try when the computer has not locked up, you will be able to see if you have got the combination correct.

> Since the mouse and keyboard don't respond

What you should see is the computer reboot.

The distinction between the kernel crash and X hanging is quite large and it is important to find out which one is happening.

The keybaord does not have to look like it's responding to do the magic  key combination. As long as the kernel has not locked up it should work.

Obviously, as you pointed out, this is not the same when trying to get to the console.

Kind regards

---

### Post by Palu on 2013-03-02
I think I'm doing the magic key correctly because I did it 4 times now pre-crash but post crash it only worked once, so I think that was a fluke of that simply being the arbitrary time at which the system would have reboot anyway.

Just now (pre-crash) I hit CTRL ALT F1 to switch to the console, and I don't have a crash yet. It's been a minute or two longer than the normal time till crashing. I'm looking up how to find the log files and zip them up now. (I'm not very good with terminal, but I'm eager enough.) Will that still help to get the log file pre-crash, or do they get wiped on reboots?

---

### Post by Palu on 2013-03-02
Ok, so... I used ls, cd, zip and ftp to get the file to myself on another computer. See attachments. I included more than just the logs you asked for... [ATTACH]239655[/ATTACH] If the attachment doesn't work, it's also on my ftp site: [http://www.danwolf.net/mylogs.zip]("http://www.danwolf.net/mylogs.zip")

---

### Post by matt_symes on 2013-03-02
Hi

It does sound like a kernel crash !

I see many of these in kern.log

```
Mar  2 09:33:34 dan-box kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
Mar  2 09:33:34 dan-box kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
Mar  2 09:33:34 dan-box kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M

<snip>

Mar  2 09:33:34 dan-box kernel: [    0.000000] mtrr_cleanup: can not find optimal value
Mar  2 09:33:34 dan-box kernel: [    0.000000] please specify mtrr_gran_size/mtrr_chunk_size

```

I'll keep looking.

Kind regards

---

### Post by Palu on 2013-03-02
Do you recommend I install all current available updates, or would that potentially make troubleshooting more complicated? I could do this from the command line since it seems stable there, and as a new install, there could be a few.

---

### Post by matt_symes on 2013-03-02
Hi

There is also this in your log file
```

.980514] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
Mar  2 09:28:14 dan-box kernel: [    6.980518] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Mar  2 09:28:14 dan-box kernel: [    6.980519] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Mar  2 09:28:14 dan-box kernel: [    6.980521] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
Mar  2 09:28:14 dan-box kernel: [    6.980523] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Mar  2 09:28:14 dan-box kernel: [    6.980525] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \LED_ 1 (20120320/utaddress-251)
Mar  2 09:28:14 dan-box kernel: [    6.980526] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20120320/utaddress-251)
Mar  2 09:28:14 dan-box kernel: [    6.980528] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Mar  2 09:28:14 dan-box kernel: [    6.980528] lpc_ich: Resource conflict(s) found affecting gpio_ich
```

I'll keep looking at the logs.

As an initial test, can you remove everything from your box bar the motherboard, memory (take out all but one stick), graphics card, ssd drive and keyboard. connect to a monitor.

Boot with that. Does it still freeze ?

Kind regards

---

### Post by matt_symes on 2013-03-02
Hi

I don't doubt the machine is totally locking up.

The thing i don't understand about this is there is no kernel panic call stack at all.

It's almost like the hardware itself is locking up (hardware, BIOS, ACPI).

Double check every single BIOS setting you have. Strip the PC down to bare bones and boot it to a LiveCD/USB, incrementally adding hardware.

You said the PC still froze from a LiveCD/USB ? Then you need to do this.

I'm wondering if those mtrr problems are the root cause of the issue.

Kind regards

---

### Post by matt_symes on 2013-03-02
Hi

Hmm. You said that when you switched to the console it did not crash after a couple of minutes extra; enough time to get the logs.

Does it crash if you leave it in the console for a long period of time ?

I'm just trying to find some pattern here.

Kind regards

---

### Post by Palu on 2013-03-02
While wandering around menus, I ran some sort of rescue console and took a picture because I saw a complaint about ACPI. I don't know what it means, but I'll post it here and do the bare bones strip you mentioned.

[http://www.danwolf.net/images/IMG_0074.JPG]("http://www.danwolf.net/images/IMG_0074.JPG")

---

### Post by Palu on 2013-03-02
Also, it looks like it'll never crash in the console.

---

### Post by matt_symes on 2013-03-02
Hi

> Also, it looks like it'll never crash in the console.

Interesting.

Just another simple test to perform.

When it locks up, if you press the caps lock key, does the caps lock led change ?

Kind regards

---

### Post by Palu on 2013-03-02
I started to open my computer and realized that there is really nothing to disconnect in your instructions besides the mouse and one memory stick. The wifi and bluetooth are built in to the motherboard. There are no card readers, CD drives, secondary HDs, or other devices plugged in. The graphics (HD 4000) is integrated from the processor too. That said, I'm at 7 minutes since startup without a crash. Usual time to crash is 30 seconds to 4 minutes, I'd say, so... maybe the stick of RAM I removed was bad. Does that explain not crashing in the console with bad RAM though?

---

### Post by Palu on 2013-03-02
Another thought: Looking up ACPI, I saw that it's about power management, and I remembered that my tiny case has a 300 watt power supply. Since I have no CD drive, an SSD, and a third gen i5, I figured that would be enough, but is it possible that the memory stick I removed is fine but it pushes my machine just over the edge in terms of power? How would I test that?

---

### Post by matt_symes on 2013-03-02
Hi

As far as i can see we have a problem with the mtrr registers and the memory addresses they hold.

We also have resource conflicts as highlighted in your last photo and one of my previous posts.

I am really beginning to think this is due to the mtrr registers but that is a guess. 

This really does look like some kind of memory addressing issue.

We can set values for that using kernel boot parameters and i think we should look at doing that and see where that takes us.

I'm still looking and thinking. This is not an issue i have come across before.

EDIT:

> I figured that would be enough, but is it possible that the memory stick  I removed is fine but it pushes my machine just over the edge in terms  of power? How would I test that?

Try it without that stick for a while but memory is not a power hog.

Kind regards

---

### Post by Palu on 2013-03-02
3 hours stable... if I have to use 8 GB, it's a shame, but really that's plenty. I'm not a gamer but a programmer, so I think most my strength will be from having my first SSD. I'll peek back periodically to see if you have anything else you'd like to check.

---

### Post by matt_symes on 2013-03-03
Hi

@palu.

Are you still getting the mtrr problems with half the ram ? Check your logs and post back.

If they are still there i would suspect power supply and power to drive the exra dimm. 

If they are not there i would suspect those mtrr problems.

Kind regards

---

### Post by Palu on 2013-03-03
My computer ran fine all night and into today. Looked at the hours since I noted stability, and kern.log showed no more "mtrr_cleanup: can not find optimal value" or the memory error it was listing yesterday morning and afternoon (well, I suppose it was your evening).

---

