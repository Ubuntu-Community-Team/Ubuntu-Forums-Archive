---
title: "One system is NOT asking me to update the Hardware Enablement Stack - Why?"
date: 2016-08-19
forum: General Help
---

### Post by bullwinkle2 on 2016-08-19
[ATTACH=CONFIG]270757[/ATTACH]
The saga continues...

Two of my Ubuntu 14.04 LTS systems gave me the above popup (click the thumbnail to see the larger version) and after some help by members of this forum I finally figured out that if you click "Install" enough times it will eventually install the additional components to bring my systems up to date.  But one system refuses to even show this popup, yet according to this it IS one of the affected systems:

[INDENT]$ hwe-support-status --verbose

WARNING: Security updates for your current Hardware Enablement
Stack ended on 2016-08-04:
 * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)

There is a graphics stack installed on this system. An upgrade to a
configuration supported for the full lifetime of the LTS will become
available on 2016-07-21 and can be installed by running 'update-manager'
in the Dash.
[/INDENT]

Also uname -r shows it is running 3.19.0-66-generic which is one of the affected versions according to the page at [https://wiki.ubuntu.com/1404_HWE_EOL](https://wiki.ubuntu.com/1404_HWE_EOL)

But it will not show that popup when I run update-manager in the Dash.  This is a somewhat older system that is different from the others in two main ways that I'm aware of, first it has the old style bios, not efi, and second it has nVidia graphics and therefore the nVidia driver is installed.

Is it possible that I'm not getting the popup on this machine because installing the update would conflict with the nVidia graphics drivers, or maybe that it could screw up a machine with a bios?  Or is there some other reason it might not appear?

Is there any way to force that popup to appear, or would that be a bad thing to do?   Is there another way to install this update that won't break anything?  I do want to continue to get Linux kernel security updates, so that's why I'm asking.

---

### Post by kansasnoob on 2016-08-20
> **bullwinkle2 said:**
> [ATTACH=CONFIG]270757[/ATTACH]
The saga continues...

Two of my Ubuntu 14.04 LTS systems gave me the above popup (click the thumbnail to see the larger version) and after some help by members of this forum I finally figured out that if you click "Install" enough times it will eventually install the additional components to bring my systems up to date.  But one system refuses to even show this popup, yet according to this it IS one of the affected systems:

[INDENT]$ hwe-support-status --verbose

WARNING: Security updates for your current Hardware Enablement
Stack ended on 2016-08-04:
 * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)

There is a graphics stack installed on this system. An upgrade to a
configuration supported for the full lifetime of the LTS will become
available on 2016-07-21 and can be installed by running 'update-manager'
in the Dash.
[/INDENT]

Also uname -r shows it is running 3.19.0-66-generic which is one of the affected versions according to the page at [https://wiki.ubuntu.com/1404_HWE_EOL](https://wiki.ubuntu.com/1404_HWE_EOL)

But it will not show that popup when I run update-manager in the Dash.  This is a somewhat older system that is different from the others in two main ways that I'm aware of, first it has the old style bios, not efi, and second it has nVidia graphics and therefore the nVidia driver is installed.

Is it possible that I'm not getting the popup on this machine because installing the update would conflict with the nVidia graphics drivers, or maybe that it could screw up a machine with a bios?  Or is there some other reason it might not appear?

Is there any way to force that popup to appear, or would that be a bad thing to do?   Is there another way to install this update that won't break anything?  I do want to continue to get Linux kernel security updates, so that's why I'm asking.

I tested the process with nVidia C61 [GeForce 7025 / nForce 630a] (rev a2) and it worked OK (both with the nvidia and nouveau drivers) but your mileage may differ with a different model nvidia chip.

As to why you aren't getting a notification let's look at a few things. Please post the output of these three commands:

```
sudo apt-get update
```

```
apt-cache policy update-manager
```

```
apt-cache policy update-notifier
```

Sort of off topic, but your comments regarding the process are welcome and actually helpful to me. Please see:

[https://ubuntuforums.org/showthread.php?t=2334371&page=3&p=13533630#post13533630](https://ubuntuforums.org/showthread.php?t=2334371&page=3&p=13533630#post13533630)

The squeakiest wheel gets the most grease ;)

---

### Post by grahammechanical on 2016-08-20
> Is it possible that I'm not getting the popup on this machine because  installing the update would conflict with the nVidia graphics drivers,  or maybe that it could screw up a machine with a bios?  Or is there some  other reason it might not appear?

I doubt if the method is that intelligent. What you are experiencing is caused by "phased updates." This explains it.

[http://discourse.ubuntu.com/t/phasing-of-stable-release-updates-finally/910](http://discourse.ubuntu.com/t/phasing-of-stable-release-updates-finally/910)

I only have one machine but I often have more than one install of Ubuntu on that machine. I see this phased update effect even if I update each install daily.

Regards

---

### Post by bullwinkle2 on 2016-08-20
Just wanted to say that for the moment I have put this problem on hold because it turns out that on one of the other updated systems (a MSI Cubi), although the update appeared to go okay and it rebooted fine, it appears to have totally hosed Kodi, which is really the only software that box is used for.  Until I get that resolved, I don't want to risk trying to upgrade the other system with the nVidia graphics.

---

### Post by brian-murray on 2016-08-26
> **bullwinkle2 said:**
> [ATTACH=CONFIG]270757[/ATTACH]
The saga continues...

Two of my Ubuntu 14.04 LTS systems gave me the above popup (click the thumbnail to see the larger version) and after some help by members of this forum I finally figured out that if you click "Install" enough times it will eventually install the additional components to bring my systems up to date.  But one system refuses to even show this popup, yet according to this it IS one of the affected systems:[INDENT]$ hwe-support-status --verbose

WARNING: Security updates for your current Hardware Enablement
Stack ended on 2016-08-04:
 * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)

There is a graphics stack installed on this system. An upgrade to a
configuration supported for the full lifetime of the LTS will become
available on 2016-07-21 and can be installed by running 'update-manager'
in the Dash.
[/INDENT]

Also uname -r shows it is running 3.19.0-66-generic which is one of the affected versions according to the page at [https://wiki.ubuntu.com/1404_HWE_EOL](https://wiki.ubuntu.com/1404_HWE_EOL)

But it will not show that popup when I run update-manager in the Dash.  This is a somewhat older system that is different from the others in two main ways that I'm aware of, first it has the old style bios, not efi, and second it has nVidia graphics and therefore the nVidia driver is installed.

Is it possible that I'm not getting the popup on this machine because installing the update would conflict with the nVidia graphics drivers, or maybe that it could screw up a machine with a bios?  Or is there some other reason it might not appear?

Is there any way to force that popup to appear, or would that be a bad thing to do?   Is there another way to install this update that won't break anything?  I do want to continue to get Linux kernel security updates, so that's why I'm asking.

The popup uses the information returned from the command "hwe-support-status --show-replacements".  You could use something like "sudo apt-get install $(hwe-support-status --show-replacements)" to perform the same operation that update-manager would.  You can also find out what is unsupported via "hwe-support-status --show-all-unsupported".

---

