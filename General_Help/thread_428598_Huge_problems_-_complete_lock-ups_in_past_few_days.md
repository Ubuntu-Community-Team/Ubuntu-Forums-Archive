---
title: "Huge problems - complete lock-ups in past few days"
date: 2007-04-30
forum: General Help
---

### Post by bootsbradford on 2007-04-30
I've been running Feisty Fawn since it came out and it's been running fine.

In the past few days, though, there have been very regular crashes - not just of programs but of the entire system. Everything freezes and only the cursor moves, but nothing can be done except to hold down the power button and power off.

This always seems to happen with Firefox, particularly when Firefox and Skype are running together. I've seen others post about this. 

However, even when I'm doing nothing, my CPU Meter Screelet has seemed very, very high recently. Often it will peak to 99% when I'm not pressing anything nor running an application. I checked in the System Monitor application and it seemed that Amarok was consuming up to 50% CPU while sleeping! Not quite sure how this can be.

What confuses me is that I'm doing nothing different in the past few days, yet I'm getting freezes and lock-ups like never before. If this continues, Ubuntu will be unusable which is a huge shame cos I've loved it and found it greatly preferable to Microsoft. 

I thought Linux wasn't meant to lock-up like Microsoft does?!! 

HELP, PLEASE!!!

---

### Post by bootsbradford on 2007-04-30
This is getting ridiculous!!

Just got rid of Skype and Amarok, hoping that would stop the crashes. Just had the second freeze of the evening so far.

This is definitely a new problem for me. Never had in with Edgy and haven't had it till the past few days with Feisty.

WHAT IS GOING ON??!!

Can see me returning to Windows at this rate.

---

### Post by lukew on 2007-04-30
> **bootsbradford said:**
> This is getting ridiculous!!

Just got rid of Skype and Amarok, hoping that would stop the crashes. Just had the second freeze of the evening so far.

This is definitely a new problem for me. Never had in with Edgy and haven't had it till the past few days with Feisty.

WHAT IS GOING ON??!!

Can see me returning to Windows at this rate.

Are you using wifi? I had this in dapper with a usb wifi. I changed to a pci and everything was ok. In edgy and feisty my rt61 (d-link) wifi was giving me this all the time. In feisty and the new network manager my wifi is enabled and i had to uncheck it every time i started up (even though i was using a network cable) otherwise it would lock up. 

You can always check your logs; though for me nothing was provided when I got these kernel panics.

This is taken from UDSF and might be of some use.


```

 System requests (What to do if your system is unresponsive)

You can "talk" to the kernel directly via system requests: Press "ALT" + "sysreq-key" + "one of the keys" listed below (The sysreq-key is also known as the 'print screen' key):

(Taken from /usr/src/linux/Documentation/sysrq.txt)

    * 'r' - Turns off keyboard raw mode and sets it to XLATE.
    * 'k' - Secure Access Key (SAK) Kills all programs on the current virtual console.
    * 'b' - Will immediately reboot the system without syncing or unmounting your disks.
    * 'c' - Will perform a kexec reboot in order to take a crashdump.
    * 'o' - Will shut your system off (if configured and supported).
    * 's' - Will attempt to sync all mounted filesystems.
    * 'u' - Will attempt to remount all mounted filesystems read-only.
    * 'p' - Will dump the current registers and flags to your console.
    * 't' - Will dump a list of current tasks and their information to your console.
    * 'm' - Will dump current memory info to your console.
    * 'v' - Dumps Voyager SMP processor info to your console.
    * '0'-'9' - Sets the console log level, controlling which kernel messages will be printed to your console. ('0', for example would make it so that only emergency messages like PANICs or OOPSes would make it to your console.)
    * 'f' - Will call oom_kill to kill a memory hog process
    * 'e' - Send a SIGTERM to all processes, except for init.
    * 'i' - Send a SIGKILL to all processes, except for init.
    * 'l' - Send a SIGKILL to all processes, INCLUDING init. (Your system will be non-functional after this.)
    * 'h' - Will display help ( actually any other key than those listed above will display help. but 'h' is easy to remember :-) 

Note that you may have to enable system requests. Read "/usr/src/linux/Documentation/sysrq.txt" for details. By default it is enabled though. 
```

[HTML]http://ubuntuguide.org/wiki/Ubuntu:Feisty
[/HTML]

---

### Post by bootsbradford on 2007-04-30
Thanks for the reply. No I use a wired connection so it shouldn't be anything to do with that.

What is UDSF?

---

### Post by jamespi on 2007-04-30
i've had 3 freezes since i upgraded to feisty - that's 3 more than i ever had since first installing breezy18 months ago.

i assume only something running in kernel mode can lock up the entire system so i assume it must be a driver. Maybe we have some piece of hardware that has a regression in the latest kernel.

is there some way to run the kernel in a debug mode so that it logs any errors for later inspection?

or is it possible for user mode software to freeze the entire system?

---

### Post by jtholmes on 2007-04-30
Had similar problems. Found a msg on the web said to boot with

noapic  option

cured the problem for me

pc  is toshiba  satelleit  a75-226

no more lockups

---

### Post by Bealer on 2007-05-01
I'm getting the same problem, but the "noapic" solution didn't work for me.

I've got a fresh, minimal install of Feisty. Using a Core 2 Duo, Gigabyte DS3 and ATI X1900. My problems start the second I install the fglrx driver for my ATI card.

---

### Post by kamstrup on 2007-05-01
You can also try using "noapic nolapic" boot options. The ultra strict way is "noapic nolapic acpi=off" - this will fix most common cases of wierd hardware/driver errors. With acpi=off you might have to turn the computer off manually.

---

### Post by lukew on 2007-05-01
> **bootsbradford said:**
> Thanks for the reply. No I use a wired connection so it shouldn't be anything to do with that.

What is UDSF?

Ubuntu Document Storage Facility. Some of the good HOWTOs from this website get stored there.

---

### Post by jamespi on 2007-05-02
i added the following line to my xorg.conf after i upgraded to feisty:
```
 Option         "AddARGBGLXVisuals" "True"
```
this was to fix[ this issue.]("http://ubuntuforums.org/showthread.php?t=419058")

since then i've had stability and performance issues, including these lock-ups. i removed the line again, now my system has been up for 24 hours without locking up and runs really smooth. seems the culprit for the lockups was the nvidia proprietary driver.

i have a geforce 5200 AGP.

---

### Post by bootsbradford on 2007-05-07
I am still getting fairly regular freezes. Having thought it was all about firefox, I've had a few just using nautilus.
Today the screen froze, again with the exception of the cursor, though an mp3 I was playing at the time carried on playing! 

Am I right in assuming now that this is a graphics card issue? I am really confused in terms of this. I have an ATI Radeon X600 card. Desktop Effects are enabled (which may be the problem?) but I haven't enabled the ATI driver in the Restricted Drivers Manager. I tried this once and everything went wild! I don't quite understand which driver I should be using or the difference between them!

There is talk in this thread of the 'noapic option' when booting? What is this? How can I do it? Is it relevant to the issues I am facing?

I would be really grateful for any help people can provide!! :)

---

### Post by lynxus on 2007-05-07
Have you checked that your machine isnt overheating ?

---

### Post by bootsbradford on 2007-05-07
What's the easiest way of doing this on Ubuntu/Linux? (I am a relatively recent convert!)

---

### Post by bootsbradford on 2007-05-08
I am still trying desperately to stop my Computer freezing up (see above posts). I am using gnome-compiz-manager. Desktop effects ran fine on the PC initially but, for whatever reason, the PC now freezes randomly.

I would be really grateful if people could help me with any of the following: 
[LIST=1]
[*]What is the best driver to be running for an ATI Radeon X600 card? Would this explain the freezes?
[*]What is the 'noapic' boot option and how to I do it?
[*]How do I check CPU temperature?
[/LIST]

---

