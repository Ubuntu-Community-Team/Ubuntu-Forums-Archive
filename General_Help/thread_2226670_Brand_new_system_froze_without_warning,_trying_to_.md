---
title: "Brand new system froze without warning, trying to diagnose [Ubuntu Server 14.04]"
date: 2014-05-28
forum: General Help
---

### Post by gabriel-j-michael on 2014-05-28
I just put together a new mini-ITX home server and installed Ubuntu Server 14.04. I've had it running for about five days, configuring it, etc. It is supposed to remain on 24/7. When I woke up this morning, I could not access it via ssh (it will be used headless). I went to log in on the console via a temporarily attached monitor, and there was no response. The power supply and case fans were still running, the power light was on, but no LAN activity from the LED on the motherboard, and no output to the monitor.

At first I assumed it was dead and that I would have to return the components. But I was able to restart it using the power button, and it booted up normally. I use Cacti to monitor system stats, and all logging stopped a few minutes before midnight last night. I was streaming media from the machine without issue up until about 11:45 PM. Temperature, CPU, load, etc were all normal prior to stopping - no spikes or unusual activity. There is nothing in syslog or kern.log to indicate the problem. The last syslog messages are from 11:49 PM (there is a process that runs every minute and produces log entries, so it appears it stopped at 11:49). I don't think the system actually halted or tried to reboot, since I would see messages about that.

Is there anything else I can do to figure out what happened, or do I just have to wait and see if it happens again?

FWIW, there was a severe thunderstorm last night, with lots of lightning, although it had happened several hours earlier. I suppose there could have been a power flicker, but if that was the case I wouldn't have expected to see the fans still running - the BIOS is set to keep the machine off after a power failure. Any ideas?

CPU is an AMD Athlon 5350 APU, motherboard is an MSI AM1 ITX board, 8 GB Crucial DDR3 RAM.

---

