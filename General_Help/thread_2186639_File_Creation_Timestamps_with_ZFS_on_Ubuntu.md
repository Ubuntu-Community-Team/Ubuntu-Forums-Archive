---
title: "File Creation Timestamps with ZFS on Ubuntu"
date: 2013-11-08
forum: General Help
---

### Post by australisblue on 2013-11-08
Hello,
I've been playing around with a test install of Ubuntu with ZFS and have it pretty much how I would like it. I'm running 12.04 at the moment. I like it a lot and I seem to be able to max out my gigabit network reading and writing files to it.

ZFS itself supports file creation timestamps. I realise the Linux world hasn't traditionally dealt with creation timestamps (although I believe ext4 supports them) but as I'll be moving all my data from numerous external NTFS drives and Windows machines onto this new box plus providing numerous other Windows users with a network document share, I'd very much like to preserve the creation timestamps. However at the moment it looks as though the layer above ZFS in Ubuntu only wants to play with modification timestamps, so as soon as I change a file, both the creation and modification timestamps get updated to the same thing (I'm viewing these from a Windows box from a samba share I created on the Ubuntu machine).

Is there a way to have both the creation and modification timestamps handled correctly on 12.04 and if not, is there a way on later releases (I'm quite happy to install the latest, I just happened to have 12.04 already and it had proved stable in the past so installed that)?

I am sure that some people (maybe a lot, I'm not sure) don't care about creation timestamps, but my OCD does and I also find it handy being able to see when a file was originally created in some cases ;-) As this machine is my new central store for everything, I really would like it to support this too.

Thanks for any info/help.
David

---

