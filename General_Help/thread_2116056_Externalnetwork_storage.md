---
title: "External/network storage"
date: 2013-02-14
forum: General Help
---

### Post by goonybird on 2013-02-14
Hello

I would like a little advice please.

I have bought a Seagate Expansion 2Tb external HDD for potential home network storage. This is a USB device and I am ultimately hoping to plug it into my BT HomeHub.

My network runs two Windows machines, XP and 7, and three Ubuntu machines running 12.04 Precise Pangolin.

Precise didn't recognize the Seagate at all. Neither did XP. I eventually discovered that the drive was formatted as exFAT and therefore only recognizable by Windows 7. I tried to re-format the drive using Paragon but it wouldn't find it, possibly because it doesn't handle exFAT itself.

I have scrubbed the drive using Killdisk on the XP machine, expecting all formatting to be removed in the process so that I could use Paragon on it as a blank drive. It took a week and didn't work!

Paragon still doesn't see it. Windows Explorer only offers to format as exFAT. Ubuntu doesn't see the drive at all. I am stumped.

I want to format the Seagate as NTFS with four 500Gb partitions so that all machines on the network can read and write to it. 

[LIST]
[*]Have I missed something?
[*]Is what I am trying to do the best way to do it?
[/LIST]
Any thoughts, observations or suggestions would be gratefully received.


Thanks

---

### Post by goonybird on 2013-03-02
Update:

On the PC Advisor forum I found a reference to an app called SeaTools provided by Seagate. I am currently running that but it is taking several days.

More later...

---

### Post by prodigy_ on 2013-03-02
> **goonybird said:**
> I have scrubbed the drive using Killdisk on the XP machine, expecting all formatting to be removed in the process so that I could use Paragon on it as a blank drive. It took a week and didn't work!
You only needed to remove partitioning. In Windows it can be done with Computer Management > Disk Management. Takes less than a minute. Of course you can also create and format partitions from there.

If there's no option to format with NTFS in Disk Management (there should be), you can [do it from command line](http://www.techhack.co.uk/2011/03/31/format-a-hard-drive-with-command-prompt/).

---

### Post by goonybird on 2013-03-03
Hi Prodigy

Thanks for that. Err, ooops.

I'm not familiar at all with command prompt. Just starting to get to grips now that I'm changing to Ubuntu.

Can't do much now till it's finished whatever it's up to. I have bookmarked the link you gave and will report back when I have tried it.

Thanks

---

