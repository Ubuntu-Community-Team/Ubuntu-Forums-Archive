---
title: "poweroff started giving system halted"
date: 2013-04-01
forum: General Help
---

### Post by libertyspike138 on 2013-04-01
So I have a fresh install of the lubuntu core off of the 12.04 64 bit mini cd. This is on a dell poweredge server. I have spent about a week trying to get everything setup to my liking and at some point in the past couple days something changed. Now when I try to power off the machine it goes to system halted so I have to manually hold the power button in to shut it down. I do not have any special drivers for video or anything like that and it was working at first.
This happens if I try from the shutdown menu or if I issue "shutdown -P now" / "shutdown -h now" from the terminal. I have removed the splash quiet parameters so that I could see that it is going to system halted.
If from the terminal I issue "poweroff" it has the same result. Reboot is still working fine everywhere.
If I go run the executable file /usr/lib/klibc/bin/poweroff it instantly shuts off but without unmounting anything etc....
I have inspected /etc/default/halt and it reads "HALT=poweroff" just like my other pc that is working fine.
I have also compared /etc/init.d/halt to make sure it is the same as the other pc.
I have even used synaptic to reinstall the acpi / apm files.

It is hard to say what exactly changed it as I have already invested so much time in installing different programs and setting things up.
Any thoughts would be much appreciated.

---

### Post by Jay_E on 2013-04-01
Hi,
is it this bug?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1002429](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1002429)
 more if google   bug ubuntu shutdown

if not how ,about syslog?

hope this helps,
jay

---

### Post by libertyspike138 on 2013-04-01
Hello Jay,
Thanks for responding. I don't believe it is that bug considering reset works just fine. I added the reboot=pci line to my grub anyway to see if there was any change and no. Exactly what part of the syslog would you like to see?

So I exited X and used shutdown -P now and this is what gets printed.

The system is going down for power off NOW!
... waiting . * Stopping web server apache2
Checking for running unattended-upgrades:
 * Stopping VirtualBox kernel modules
 * Stopping the Winbind daemon winbind
 * Clearing ebtables rulesets
Stopping UPS power management: apcupsd[1736]: apcupsd exiting, signal 15
apcupsd.
waiting for pid 1525 to die
apcupsd[1736]: apcupsd shutdown succeeded
 * Stopping domain name service... bind9
 * Asking all remaining processes to terminate...
 * All processes ended within 1 seconds....
 * Deconfiguring network interfaces...
 * Deactivating swap...
 * Unmounting local filesystems...
 * Will now halt
[  886.866943] System halted.

I then removed apcupsd to make sure that it was not interfering and I still get the same thing.

---

