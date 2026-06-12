---
title: "eSATA drive activity light blinks constantly on 13.04"
date: 2013-06-17
forum: General Help
---

### Post by CelticWhisper on 2013-06-17
I just updated my HTPC to 13.04 from 10.04 and while almost all is well, I'm seeing a new problem (?) that wasn't there before.  I have a 3TB drive in a Mediasonic HF2-SU3S2 eSATA/USB3 enclosure (connected over eSATA) and the activity light on the enclosure is blinking, rhythmically and constantly, as long as the system is running once it's finished booting.  I'd say it blinks about 2x per second, and after every 5th or 6th blink there's a brief (1-second or so) period of more rapid blinking before it returns to its steady 2x/sec cadence.

I ran "Disks" and checked the SMART status of the drive and it's reporting everything OK.  fsck returned an OK status as well.  It looks like permissions are alright, as I was able to create a dummy file called "Hi" on the drive, so I'm not sure that it's a matter of the system trying and failing some background write (though I'm not certain either).  The drive is formatted as ext4.  /etc/fstab entry is as follows:

UUID=194b2968-63d4-4aaa-89b8-71fb1a99c056 /mnt/NOAH1 ext4 defaults,noatime 0 2

Anyone else run into this?  Should I be worried?  The drive sat idle and the light unlit before on 10.04, so this is a change and I don't like unknowns.  I just lost 2TB of media files when one of my drives croaked, and I'd hate to lose another 3 so soon thereafter.

Thanks for any help you can provide.

---

