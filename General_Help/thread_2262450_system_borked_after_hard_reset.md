---
title: "system borked after hard reset"
date: 2015-01-24
forum: General Help
---

### Post by MeanRoy on 2015-01-24
Quite some time ago (last June) I was having problems with my no longer supported version and was advised to do a fresh install, which I did.
I installed 14.04 LTS with Mate.
Yesterday I had (apparently) to much going on at once.
The system froze and did not respond to alt-sysreq- REISUB, so I had to hard reset.

I've checked the file system, tried to fix broken packages, and so on but unfortunately it appears it's REALLY messed up now.
It boots but is quite messed up.

I have pretty much everything backed up and am thinking of trying to do a re-install of the operating system but not format and just 'overwrite' my existing installation.
Any reason this can't be done with the the Ubuntu MATE 14.04.1 .iso image like the regular 14.04?

Roy

---

### Post by ibjsb4 on 2015-01-26
> just 'overwrite' my existing installation.
Any reason this can't be done with the the Ubuntu MATE 14.04.1 .iso image like the regular 14.04?
Yes you can, but I never learned to trust this method.  From time to time someone will wipe the entire drive using this method.  I prefer not to take any chance and instead use gparted to wipe the install, turning it into freespace.  Then when you reinstall, you are given the option to install to the largest free space.

---

### Post by MeanRoy on 2015-01-26
Thanks, not what I wanted to hear but what I was afraid of!

In the meantime I've installed 14.04.1 in a new partition and will be migrating stuff over. (tomboy, Firefox, Thunderbird, etc.)
I'll back everything up with clonezilla to my USB drive next,
After I've done that I'm going to try it and see how it goes.

I'll let you all know.

Roy

---

### Post by MeanRoy on 2015-01-26
I'm afraid I've found that in actuality I may have a hardware problem!

I immediately started to have problems with the fresh installation.

I configured Thunderbird, that went ok.
When I brought up the Software Center and started to install Tomboy the system locked up!

Starting to troubleshoot now, what a pain!

Roy

---

### Post by Bashing-om on 2015-01-26
MeanRoy; UnGood !

@ ibjsb4. Hey old friend, while I am passing by :)

@roy
file system check from the liveDVD ?
SMART status from the 'disk' utility  ?

[INDENT][INDENT]small things
[INDENT][INDENT][INDENT]mean a lot
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MeanRoy on 2015-01-26
> file system check from the liveDVD ?

yeah I did that, seemed ok.
I downloaded the UBCD (Ultimate Boot CD) and am running a memory test.
Looks like it will take a long time.
memory test passed fine.
UBCD also has a CPU stress test I'll try but I think before I do that I'll vacuum out and clean everything.
(Maybe I'll even put the sides back on the case. :rolleyes:)

Whelp, UBCD stress tests are a little weird. Seem to run ok but no outputs.
I'm downloading the Phoronix Test Suite Live and will give it a try.

---

