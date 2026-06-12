---
title: "Feisty freezes randomly"
date: 2007-09-03
forum: General Help
---

### Post by dborowitz on 2007-09-03
I've been running Feisty pretty happily since its release, with the exception of the fact that once a day or so it locks up completely and I have to hard reboot it. Here's what I know:
-It seems more likely to happen during periods of heavy load, but not always (sometimes e.g. it will freeze at the KDM login screen).
-Can happen even when X is not running.
-Hard reboot is the *only* way to reboot. Not even Alt-SysRq-B works (but it does work when it's not frozen, so I know it's enabled).
-Nothing shows up in any system logs. I added a '*.* /var/log/everything' to my syslog.conf, and the last thing before the freeze is just a dhclient message. But those happen every few minutes anyway, so I doubt it's dhclient.
-memtest86+ runs fine, for 2 passes at least.
-badblocks reports no bad blocks on either of my hard drives.
-I moved my entire installation (a tricky endeavor) to the other HD, no change.
-I first ran across this problem in the Feisty beta, then I switched back to Windows on this machine for a few months, and there were no crashes (other than the normal Windows stuff, of course :). This makes it seem kind of unlikely it's a hardware problem, but as you can see from the above, I haven't ruled it out.
-No kernel panic dumps to the console.
-The cursor on the console continues blinking.

Any ideas? Some things I haven't tried yet:
-Some way of logging the voltages in the PSU to see if it's crapping out on me. Don't know how to do this in Linux.
-Upgrading motherboard BIOS.

Some system details:
Athlon XP 3500+
MSI K8N Neo4 motherboard
GeForce 7800 GTX
2 GB RAM
320 GB WD/400 GB Seagate SATA HDs
Microsoft Natural Ergonomic Keyboard 4000 (USB)

---

### Post by thelocust on 2007-09-03
Double check your voltage settings for the RAM. Just a thought.

---

### Post by Jimmy The Clown on 2007-09-15
I am having almost the exact same sysmptoms. I originally thought it was due to a software raid1 but I have since manually faulted one of the disks and am only running on half the raid.

I occasionally get a lock during simple stuff like browsing or whatever, but it is usaully directly related to high disk access. For instance, running "bonnie++" a disk benchmarking tool will usually cause a hard freeze. Trying to copy a large (>~5GB) directory from my USB hard drive to home will _always_ cause a freeze. Using K9 to create an iso of a dvd will _always_ cause a freeze.

I have a 400 watt psu, 2 sata WD hard drives, and a nvidia 6800. The DVD drive is eSata. The motherboard is a Shuttle SN27P2

If I limit my disk access to only doing tasks that don't cause a heavy load, I am stable for days and days. The minute I do HD intesive stuff I freeze.

So, you aren't alone out there. Hoepfully we can find a fix.

-JTC

---

### Post by Jimmy The Clown on 2007-10-01
Tried a fresh install of Gutsy Beta (after a crashed upgrade took my whole system out). Still no dice. Currently just one hard drive, an external esata dvdrom. As long as I was installing, I ripped the raid system out to see if that fixed things. Nope

Crash is definitely triggered by heavy hard drive loads. Man this sucks.

-JTC

---

### Post by MarkieB on 2007-10-01
> **dborowitz said:**
> 
-Some way of logging the voltages in the PSU to see if it's crapping out on me. Don't know how to do this in Linux.


install the packages

lm-sensors
gkrellm

Although! The voltages don't look right to me, you're supposed to rescale them yourself — how?!
Speedfan in windows reports different voltages

---

