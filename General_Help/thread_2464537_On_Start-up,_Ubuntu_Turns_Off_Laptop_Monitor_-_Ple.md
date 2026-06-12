---
title: "On Start-up, Ubuntu Turns Off Laptop Monitor - Please Help"
date: 2021-07-04
forum: General Help
---

### Post by andrew-apw-white on 2021-07-04
I'm experiencing a baffling problem, as described in the title. Here is more detail:

When I start up my laptop, the monitor turns on, like normal, and displays the HP logo. Usually, after displaying the HP logo the HP logo will be displayed with the Ubuntu logo. However, for the past three days, instead of displaying the Ubuntu logo the laptop screen simply turns off. Note that this is not a blank screen or a blue screen of death; the screen is definitely just turned off.

Fortunately, I am still able to use the computer by connecting a second monitor via HDMI. It is worth noting, however, that when the external monitor is connected Ubuntu is still recognizing the presence of the laptop monitor and still considers that to be the primary display. Consequently, I changed the primary display to the external monitor.

Part of me thinks that this is a hardware problem because it didn't start until this past Thursday, which was a day in which I moved to a new apartment. It is certainly believable that the laptop received an unfortunate knock during the move. But, if it is a hardware problem, why would the display only turn off once Ubuntu started up?

My system details are below. Any thoughts or suggestions you could provide are greatly appreciated. Thank you.

Memory: 15.5 GB
Processor: Intel Core i7-8565U CPU @ 1.80GHz x 8
Graphics: NV118 / Mesa Intel UHD Graphics 620 (WHL GT2)
Disk Capacity: 256.1 GB

OS Name: Ubuntu 20.04.2 LTS
OS Type: 64-bit
GNOME Version: 3.36.8
Windowing System: X11

Computer Model: HP Probook 450 G6
ProdID 5YH15UT#ABA

---

### Post by tea for one on 2021-07-04
> **andrew-apw-white said:**
> Part of me thinks that this is a hardware problem because it didn't start until this past Thursday, which was a day in which I moved to a new apartment. It is certainly believable that the laptop received an unfortunate knock during the move. But, if it is a hardware problem, why would the display only turn off once Ubuntu started up?

Quite possibly, it could be a hardware problem.

Why not boot up your installation disk and see if a live session loads?

---

### Post by andrew-apw-white on 2021-07-04
Well, this is odd.

I turned the computer off, put in the thumb drive I had used to install Ubuntu in the first place, turned the computer on, and it didn't boot from the drive. I did a quick search online to see how to boot from a drive it if doesn't do so automatically and I came up empty.

Instead, I tried to boot it in safe mode. Again, I turned off the computer, then turned it on, held the left shift key, and it did not boot in safe mode; it booted normally.

Next, I tried to enter the GRUB 2 menu by pressed ESC during startup. I got to a command-line-only GRUB interface, but then that was replaced by a screen that was blank (blank, not turned off) except for a single underscore in the top left of the screen (no command line prompt, just an underscore). Actually, I have seen that screen before: that is the screen that I see when I try to restart. If I have ever tried to restart Ubuntu, when it restarts it displays that screen with the single underscore and sits there indefinitely. This time, too, once the GRUB command line was replaced with the underscore, it just sat there as long as I cared to wait for it.

---

### Post by tea for one on 2021-07-05
> **andrew-apw-white said:**
> I did a quick search online to see how to boot from a drive it if doesn't do so automatically and I came up empty.

Therefore, you haven't yet managed to try a live session?

Power on HP Laptop.
Press F9 for Boot device menu.

---

### Post by andrew-apw-white on 2021-07-05
Correct, I have not yet managed to try a live session. I tried pressing F9 during startup and it did not load from the USB drive.

My computer has the Fx keys doubled with other functions; F9 is shared with the keyboard backlight toggle. In principle, I have to press "fn" with F9 to actually have the F9 effect; however, while pressing F9 during startup I end up toggling the keyboard backlight, which suggests to me that something is wrong with the ability to register the correct keyboard command?

---

### Post by tea for one on 2021-07-05
When powering on:-

Try Esc
Try F10

Or have a look at this clever interactive UEFI/BIOS simulator [http://h10032.www1.hp.com/ctg/Manual/c06534544.pdf](http://h10032.www1.hp.com/ctg/Manual/c06534544.pdf)

---

### Post by andrew-apw-white on 2021-07-06
Okay, Esc seems to be what I needed.

I pressed Esc during startup, which got me into the grub command line, then I typed "exit" and that put me into the BIOS, from which I was able to boot from a thumb drive.

BUT, after downloading the updates for the most recent Ubuntu version and restarting, the monitor turned off again! This confirms that the problem is due to a bug in the latest Ubuntu update. I am reinstalling the old version and refusing all updates. Now my laptop is back.

How do I submit this bug to the Ubuntu team?

---

