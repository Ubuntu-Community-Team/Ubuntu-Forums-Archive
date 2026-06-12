---
title: "No keyboard at boot, totally stuck"
date: 2014-03-26
forum: General Help
---

### Post by Bucky Ball on 2014-03-26
Hi all,

Major issue here. I have a Toshiba Satellite Pro L510 laptop. Always had this problem, but it has never been much of an issue. This time it's different and rather major. 

I rarely switch off my computer but did last night. I switched on this morning and same as usual. No keyboard at the grub menu. I have a heap of kernels and have been testing 14.04 LTS. Those kernels are at the top of the list. So as usual, I just let it reach the 10 seconds and it boot into 14.04, but unfortunately, the kernel at the top of the list is not working. It appears to be totally broken. I just get a list of errors on a black screen and then it hangs.

If I hit F2 to get into the BIOS at boot it takes me to a black screen with a cursor that is not flashing, just sitting there. If I hit F12 to select the boot device (in an attempt to boot from a System Rescue USB stick) same thing; black screen, solid cursor, not flashing. In both instances I have no keyboard and am stuck there. Only thing to do is hold down the power button, switch off and try again.

One boot did get to the 'Ubuntu 14.04' purple screen, it hung there awhile, then back to the black screen and solid cursor. Stuck.

So, getting a bit desperate. I'm totally locked out of my machine and can only boot to the first, broken 14.04 kernel on the list. 

Any further info, just ask. Any help greatly appreciated and TIA. ;)

---

### Post by ajgreeny on 2014-03-26
If you can get hold of a live DVD of something, and assuming your machine is set up by default, as many are, to boot first to an optical disk if present, can you then use the keyboard to navigate the live DVD menu (syslinux?) that appears?

Have you never been able to get into the BIOS, meaning perhaps it is one of those rare machines where the BIOS is locked down by the laptop manufacturer?  If that is the case, how did you install Linux in the first place?

Curiouser and curioser !

---

### Post by Bucky Ball on 2014-03-26
> **ajgreeny said:**
> Have you never been able to get into the BIOS, meaning perhaps it is one of those rare machines where the BIOS is locked down by the laptop manufacturer?  If that is the case, how did you ionstall Linux in the first place?

Absolutely no issues getting into the BIOS in the past, or the device list with F12 (from memory). Only now. Odd. The machine is set to boot from the hard disk by default. There is no changing that at this point.

I've left it alone, but about to start fiddling with that machine again so will post back if there is any change, but I'm not expecting much ... and yes, I'm puzzled, too ... :-k

---

### Post by Bashing-om on 2014-03-26
Bucky Ball; Hi !

Lap top -> usb keyboard ? .. integrated keyboard ?
a) Maybe reset bios to defaults - pull the battery OR CMOS jumpers -
b) Boot into bios, does the keyboard work reliably within bios ?
c) Are there options for "legacy" mode or such for usb devices in general in the bios settings? ( are we looking at a case of no drivers are available after bios hands off )
d) Does the keyboard work with other boxes ?
e) What results when you spare that keyboard off to a known good keyboard ?
f) Hey, maybe a bad cable - broken wires happen.

But, sounds to me like there just is not a driver available after bios hands off to grub - if you have a working keyboard in bios -  ( grub also has limited keyboard drivers), prior to grub handing off to the operating system.

tis indeed 
[INDENT][INDENT]a puzzlen' thing
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-03-26
From my first post:

> **Bucky Ball said:**
> If I hit F2 to get into the BIOS at boot it takes me to a black screen with a cursor that is not flashing, just sitting there. If I hit F12 to select the boot device (in an attempt to boot from a System Rescue USB stick) same thing; black screen, solid cursor, not flashing. In both instances I have no keyboard and am stuck there. Only thing to do is hold down the power button, switch off and try again.

I can _not_ get into the BIOS or anywhere else. I am totally locked out. The keyboard does work before the grub menu, though, because F2 and F12 take me to a black screen with a solid white cursor, not flashing, rather than the grub list, so it is doing something. Once there, power button off is the only option.

I is a laptop, I have no USB keyboard (except a wireless USB keyboard and mouse, neither of which works either) so not a cable issue. I have thought of pulling the battery and am about to try it. 

I am completely stumped. This machine was working faultlessly and all I did was switch it off. I'm starting to think a hardware problem as I can't get into the BIOS at all, and that is before grub. 

I did manage to get it to restart with ctl+alt+delete ... once ... and this normally gets the keyboard working again so I was full of hope ... for a few seconds. Made no difference which is starting to make me think something is seriously wrong. But perhaps I'm panicing. Am also thinking of reposting with a twist in Ubuntu+1 and seeing if I can identify a bug with 14.04 that may be causing this.

So, can't get in to the thing, going around in circles and this is my main machine so that is very bad news. 

PS: Previously, if I switched the machine on, the kernel that is now not booting and throwing a heap of errors must have been booting fine previously, as I would get to the login in screen and 'restart' so I could then use the keyboard to select the kernel I wanted to use (as I mentioned, keyboard worked fine on a restart, just not a cold boot from off). Eeeeek!

PPS: This is the error that things normally kick off with:

BUG:soft lockup - CPU#1 stuck for 23s! [systemd-udevd:366]

But I also get modprobe and upstart instead of systemd-udevd. I have researched these also, to no avail. Indeed puzzling. I'm gonna pull the battery.

---

### Post by Bucky Ball on 2014-03-26
Solved! Pulled the battery, pulled the power cord, held the power button down for about a minute, plugged the power cord back in (no battery inserted), booted the machine and it kicked straight into the old 12.04 LTS Xubuntu cd I had inserted (aj: BIOS must be set for CD first after all, apologies. ;))

Once the cd got to the 'Try Xubuntu' or 'Install Xubuntu' options, I hit 'Try', got to a desktop, immediately restarted the machine and when back at the grub menu I had my keyboard back, as per normal, selected my workhorse 12.04 mini install with xfce and I am typing from it now. Happy days and thank you both so much for your input. 

All the best and see you in the swim ... ;)

PS: My conclusion, naturally, is dead battery. It is about four years old and honestly, I have never run the battery to below 95% as I pretty much always have this machine plugged in to the wall socket. Apparently, these li-ion batteries need to be run down now and then. Being at almost full capacity for long periods kills them. I think I killed this one, but am yet to throw it in again to confirm. If I'm feeling game and have the time later I might throw the battery in and confirm my suspicions, but dead battery seems fairly obvious at this point. Cheers.

PPS: Last point; I have had the machine plugged into the wall all through this saga, have not been trying to boot with only the battery. Despite this, it still seems to have been getting in the way, demonstrated by the resolution of any and all issues when I took it out. Go figure ... :-k So, I guess one could say this was a hardware issue after all.

---

### Post by Bashing-om on 2014-03-27
Bucky Ball; Outstanding !

See you do good work .

The old adage still applies, huh ? .. When all else fails -> pull the battery !

Now
we can
[INDENT][INDENT]just keep on keep'n on 
[/INDENT][/INDENT]

---

