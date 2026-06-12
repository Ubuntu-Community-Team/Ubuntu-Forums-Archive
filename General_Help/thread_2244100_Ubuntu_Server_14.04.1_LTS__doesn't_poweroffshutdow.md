---
title: "Ubuntu Server 14.04.1 LTS  doesn't poweroff/shutdown but always restarts"
date: 2014-09-13
forum: General Help
---

### Post by fomember on 2014-09-13
I just upgraded my home server from 12.04.1 LTS to 14.04.1 LTS and now I cannot poweroff the system anymore.
If I issue a "poweroff" command the server shuts down and then instantly reboots.
I already tried to set acpi=force in /etc/default/grub but this did not help.

With 12.04 I had no problem with  poweroff   and I used to use  Wake On LAN to wake up my server whenever a client needs it.
Fortunately I had cloned my old system disk before the upgrade so I was able to revert to 12.04 without a fuss.
As expected there is no problem with poweroff in 12.04.
Thus it is not the hardware or BIOS which causes the problem but definetely something in 14.04.

Any clues why the server behaves differently with 14.04?
Is there possibly some major change in ACPI behaviour?

P.S. My Mobo is an ASUS P9D-X with a  Xeon CPU E3-1230L v3

---

### Post by Stormlord on 2014-09-13
By "upgraded" do you mean "upgraded" indeed or did you do a clean install?  Did you try shutting down your system from a 14.04 startup DVD to see if it works?

---

### Post by egeezer on 2014-09-13
I believe there may be a real difference in ACPI behavior between 12.04 and 14.04.  In order to get Suspend working on a recent 14.04 install (from the Minimal Install) I had to use a separate sudo apt-get install acpi-support uswsusp.  You might try a search on the Ubuntu User Documentation:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by fomember on 2014-09-14
I did a do-release-upgrade to upgrade to 14.04 and it went smoothly.
Just the poweroff thing.

On my 12.04 I had "suspend" working after I had installed acpi-support.
I was using it happily for over a year to wake up my server every night to perform unattended updates and backups and then go to sleep again.

As I stated everything was working in 12.04 like it should until the upgrade messed something up.

Of course I can try a clean install but the advantage of a server LTS should be that an upgrade is well supported.
A clean install needs a lot of afterwork which should not be necessary with an upgrade, especially on a server without a GUI.

Today I read a note that tells me that I should update my hardware enablement stack on 12.04 to get support for new kernels.
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL).
With the experience from the 14.04 upgrade I suspect that this will bring the problem to my 12.04 system too.

---

### Post by fomember on 2014-09-15
I found that I needed a BIOS update to my ASUS P9D-X which fixed the reboot issue.
Strange that it worked without problems with 12.04 but obviously Ubuntu 14 uses features which interact differently with the Hardware.
Thus for me the reboot issue is no more now.

---

