---
title: "Ubuntu 14.04 randomly logs out"
date: 2015-10-08
forum: General Help
---

### Post by nmyrick on 2015-10-08
I've just installed Ubuntu 14.04 on a Dell Inspiron 15 5000 series laptop (5558 series to be exact), and I'm having an issue where Ubuntu just randomly logs off. It doesn't matter what program is running. From what I understand, this may be a graphics driver issue, but I don't see any additional drivers available. Also, I could not find any drivers on Intel's website.

My laptop has the following:

Ubuntu 14.04 LTS
Processor: Intel Core i7-5500 CPU @ 2.4GHz x 4
Graphics: Intel HD Graphics 5500 (Broadwell GT2)
OS Type: 64-bit
RAM: 16GB
Window Manager: Compiz with OpenGL

Does anyone know what might cause this issue, and how I can fix it? This happens once or twice a day.

---

### Post by efflandt on 2015-10-09
What do you mean "logs off"? Are programs that were opened still there or gone when you log in again, or is your computer shutting off entirely?

Maybe you are not familiar with screen lock which may lock the screen after a period of inactivity. In that case when you log back in, everything should be just as you left it. The time for that and whether it locks the screen if using default Unity desktop would be under **System Settings** (gear/wrench icon) > **Brightness & Lock**. I am not familiar with "OpenGL" as a window manager, that usually refers to a method of graphics.

Or it is possible that a BIOS setting is putting your laptop into suspend, especially if on battery power.

---

### Post by nmyrick on 2015-10-09
I mean that it freezes up for a second, and then logs off when I'm in the middle of doing things. I could be looking at email or watching a video or browsing the web or anything. It just kills everything that I have running and goes back to the login screen.  When I log back in, nothing that I had open is still open.

Compiz is the window manager that I am using.

I also does this while it is plugged in, and when it is on battery.

Also, thank you very much for responding. I really appreciate it. It would be nice if I could get my computer to stop doing this.

Here is some information about my computer, if this helps.

```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
	Subsystem: Dell Device 06ae
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>


00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 06ae
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915_bpo
```

OK, I've got more information on this. Hopefully someone will be able to help me with this.  I've figured out that every time this has happened is when I am mousing over the bottom of the Unity Toolbar to expand the flattened icons.  However, it doesn't happen every time. It happens only a couple times a day.

So I guess the Unity Desktop is crashing, and it takes me back to the sign in screen and doesn't save anything that I had open.

I just switched my hardware acceleration texture quality all the way to 'Fast' in the Unity Tweak tool, so maybe that will help.

The hardware acceleration texture quality settings options are Best, Good, and Fast, which I'm assuming equates to Slow, Medium, and Fast as far as the acceleration goes. 

It was originally set to Good (Medium), and I tried setting it to Best (Slow), and Unity crashed twice in about 10 minutes time at the Slow setting. So I've set the hardware acceleration to Fast to see if that fixes the issue.

It seems that switching the hardware acceleration to Fast has corrected the issue. It's been a week and I have not had the issue since switching to fast.

---

### Post by David.A.Hannasch on 2016-03-26
> **nmyrick said:**
> It seems that switching the hardware acceleration to Fast has corrected the issue. It's been a week and I have not had the issue since switching to fast.

Thank you for posting this! I'm going to try that and see if it solves my problem.

For anyone else with this problem, the hardware acceleration setting is under Window Manager -> General. You might need to install Unity Tweak.

---

### Post by nagarajtantri on 2016-09-27
All i did was reset to default inside the Unity Tweak. I don't remember which option of animation was causing it. The reset to default is good enough for me! :|

---

