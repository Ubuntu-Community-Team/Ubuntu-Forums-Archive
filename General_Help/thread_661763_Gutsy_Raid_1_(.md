---
title: "Gutsy Raid 1 :("
date: 2008-01-08
forum: General Help
---

### Post by petef0_0 on 2008-01-08
Gutsy Raid 1 - mirroring

I've searched for ages on this one and done about 6 installations, so please bear with me

I have a HP xw4300 machine with 2 x 80Gb harddrives installed, the machine does support hardware raid via it's motherboard. 

First Scenario - Hardware Raid 1
I thought first of all I'll  try the hardware raid on the motherboard as it's the simplest so enabled the RAID in the bios and the controller then did a normal installation on one of the disks this went OK but on reboot after install the machine didn't startup, only way to get it to boot was to remove hdb1 and reboot then would boot ok, then power down reconnect hdb1 and reboot, would boot ok but the disk is permenantly degraded and never syncs again to the other disk.

Second Scenario - Software Raid 1 
After trying hardware raid for a while and doing a lot of searching the net I thought I'd try software using  the alternate install CD, I setup my partitions OK following the below guide. 

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

I got through it but about 3 quarters of the way down it says 

WARNING: There is a serious bug in Ubuntu 7.10 (see this and this for details) which makes the boot fail if one of the physical disks in the RAID1 set is missing.

I went ahead with the installation incase this has been fixed by a patch, after installation I removed the power from the secondary hdb drive to test I could boot to either of the drives but the machine just sticks on the Ubuntu startup screen then times out to BuzyBox initramfs screen. I've tried various commands to try and invoke the other drive booting

mdadm --assemble --scan
mdadm --assemble --run 

but had no luck :(

I know that the guide said this is a bug but is there a work around or another way to get this to work

Any advice very welcome 

Cheers

Pete

---

### Post by fjgaude on 2008-01-08
I use software raid5 without troubles but I don't boot from it, but from a single drive.

I've seen the issue you pose and have not seen a solution, yet. I'm sure a bug report is being worked on and the next release of Ubuntu will likely have it fixed.
 
The hardware raid you have on your MB is really not hardware. Many call it "fakeraid" because it uses the the main CPU to do the XORing, etc.

From a philosophic view I wouldn't consider ever booting from a software raid setup. It's complex and hard to fix if broken. Installing the OS is easy, quick on a single drive if that drive fails.

Use raid1 or 5 to protect data, with the apps and OS on another drive, a non-raid, one that is fast, like the newest Samsungs and Seagates.

Maybe others with give you another view.

---

