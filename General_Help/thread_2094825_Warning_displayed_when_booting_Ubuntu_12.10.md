---
title: "Warning displayed when booting Ubuntu 12.10?"
date: 2012-12-14
forum: General Help
---

### Post by felkar on 2012-12-14
I have started to experience difficulties when booting my (recently-installed) Ubuntu 12.10.

A "normal" boot fails to go to completion.

An "advanced boot - recovery mode" works but displays the following warning during the "boot":

[COLOR="red"]ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    5.843903] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.843966] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    5.844018] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    5.844165] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.844227] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[    5.844376] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.844437] lpc_ich: Resource conflict(s) found affecting gpio_ich[/COLOR]

Does this need fixing?

And if so, what do I do?

All advice will be gratefully received.

felkar

---

### Post by Rexilion on 2012-12-15
Kernel warnings are not to be worried actually. The kernel is aware of conflicts and knows how to deal with these. It does a mere recommendation.

Paradoxally, you should be worried about the warnings and errors you don't see...

Why will your kernel not boot in a normal way?

---

### Post by felkar on 2012-12-16
> **Rexilion said:**
> Kernel warnings are not to be worried actually. The kernel is aware of conflicts and knows how to deal with these. It does a mere recommendation.

Paradoxally, you should be worried about the warnings and errors you don't see...

Why will your kernel not boot in a normal way?

I was hoping that the (identified and posted) warning was the cause of the observed "boot problem".

It appears that it was a vain hope.

The problem may relate to a previously-received advice to install a "Epson-supplied driver" for my "Epson Scanner".

The download of the driver came with the following caveat:

[COLOR="Red"]Index of [ftp://djam.spb.ru/other/soft/Drivers...330_Photo/2.29](ftp://djam.spb.ru/other/soft/Drivers...330_Photo/2.29)

This type of file can harm your computer.
[/COLOR]

After installing the supplied driver, my Epson Scanner works and there did not appear to be any immediate impact on the performance of the computer.

So the currently-described problem may turn out to be a "self-inflicted wound" - which might ultimately need a re-install of the whole OS.  I hope that I am mistaken.

Thank you for the posted advice.

felkar

---

### Post by Rexilion on 2012-12-17
The link you provided is broken/incomplete. Please provide a properly working link.

What errors do you see when doing a normal boot?

---

### Post by felkar on 2012-12-17
> **Rexilion said:**
> The link you provided is broken/incomplete. Please provide a properly working link.

The link appears to get mauled during the posting.

The full address is:

Part One (the web site):
=========
[ftp://djam.spb.ru/other/soft/Drivers/](ftp://djam.spb.ru/other/soft/Drivers/)

and Part Two (the selected Epson driver):
============

./Scanner_Epson_Perfection_V330_Photo/2.29/iscan_2.29.1-5~usb0.1.ltdl7_i386.deb

> **Rexilion said:**
> What errors do you see when doing a normal boot?

I get an "infinite loop" (?).

From recollection, there is a message posted to the top of the screen that says "battery OK" (not relevant, because I am booting from a desktop) and then all further normal inputs from the keyboard have no effect.

Only the last-ditch remedy, (Alt+ SysReq+B) scores the desired response.

felkar

---

### Post by Rexilion on 2012-12-18
Don't see why that packages could cause an infinite boot loop.

It only adds files and does not delete any system files. Wasn't able to check the scripts though.

Try booting the system in normal mode. Then boot a liveCD to access /var/log/syslog and post it here. I don't know what else to do...

---

### Post by felkar on 2012-12-18
> **Rexilion said:**
> 
Try booting the system in normal mode. Then boot a liveCD to access /var/log/syslog and post it here. I don't know what else to do...

Before reading the above advice, I followed the latest Ubuntu suggestion and installed the updated Linux kernel (3.5.0-19.30).

That appears to have fixed my reported problem.

Ubuntu now boots normally.

Thank you for taking the time to explore my reported observations.

felkar

---

### Post by Rexilion on 2012-12-19
And what about the iscan software?

---

### Post by felkar on 2012-12-20
> **Rexilion said:**
> And what about the iscan software?

The "scanner software" still works perfectly.

But, alas, I crowed too soon.

The originally-notified boot problem has not gone away.  But it has now become "intermittent"!

Total defeat!

Up till now - fortunately - the booting problem has been minor and easily remedied.  

I tried looking at the suggested "syslog" file.  

The following entries in the "syslog file are the only ones that scored a CRITICAL:

[COLOR="red"]Dec 20 18:14:13 felixk-desktop gnome-session[2399]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
Dec 20 18:14:13 felixk-desktop gnome-session[2399]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed[/COLOR]

I hope that this tells you something.

felkar

---

### Post by Rexilion on 2012-12-20
Not much really. When does it reboot?

---

### Post by felkar on 2012-12-21
> **Rexilion said:**
> Not much really. When does it reboot?

I do not have enough data yet to answer this.

My normal practice is to leave the computer running (in suspend mode) all the time.

Once in a while, there is a "network problem" that is solved by "shutting down the computer, switching the power off and then on again and rebooting".  This has always restored the network connection.

On the past 3 reboots, Ubuntu booted normally **twice** and needed the "advanced boot routine" on the third occasion.

Given that the problem is "an irritation" and not "a disaster", I think it can be laid to rest.

Thank you for the continuing interest.

felkar

---

### Post by Rexilion on 2012-12-22
> **felkar said:**
> I do not have enough data yet to answer this.

Yes, that is understandable.

> **felkar said:**
> Once in a while, there is a "network problem" that is solved by "shutting down the computer, switching the power off and then on again and rebooting".  This has always restored the network connection.

Ever tried to just rmmod the network driver and then modprobe it again?

> **felkar said:**
> On the past 3 reboots, Ubuntu booted normally **twice** and needed the "advanced boot routine" on the third occasion.

I do not know what 'advanced boot routine' implies. Maybe forced fsck?

> **felkar said:**
> Given that the problem is "an irritation" and not "a disaster", I think it can be laid to rest.

Good, maybe someday a kernel upgrade will fix it. Happenned to me too once.

> **felkar said:**
> Thank you for the continuing interest.

No problem!

---

