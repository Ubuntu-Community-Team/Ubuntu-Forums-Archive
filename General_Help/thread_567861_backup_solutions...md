---
title: "backup solutions.."
date: 2007-10-05
forum: General Help
---

### Post by andytayloruk on 2007-10-05
I'm trying to figure out a decent way for a home backup system that I can put together myself. The system I'm leaning towards at the moment is:

2x 250gb SATA Seagate drives in an enclosure, each drive mirrored (so hold the same content, for redundancy)

Any suggestions on a decent dual-bay enclosure and/or a better hard drive would be much appreciated. Or even a completely different approach  So far I'm relying on one Western Digital external drive which is fast approaching its death I think, so I want to switch pretty fast. And for not too much money (hopefully). 

Also, some help on what programs to use in Linux for a backup. I don't need continuous incremental backups, I just need to transfer everything once in a while. I presume rsync is best? I don't know.

Cheers!

---

### Post by kidders on 2007-10-06
> **andytayloruk said:**
> 2x 250gb SATA Seagate drives in an enclosure, each drive mirrored (so hold the same content, for redundancy)Yikes! Your data must be pretty important if you feel the need to make *two* backups of it.

I've always liked Seagates tbh, so I've no suggestions to make there. At least where I live though, they're always that bit more expensive than many others.

In terms of software, rsync is certainly a smart choice imo. The important things to consider are:[LIST=1]
[*]Whether your choice will protect you against everything you want to be protected from. For example, say you delete something critically important today, but don't notice until after you've made one or two backups.
[*]How well your choice will work in the event you actually need to use your backups. To take a related example, you'd be surprised how many people use RAID to secure their data, but aren't quite sure how to recover an array in the event they actually need to do it.
[/LIST]If the answers are "Yes", then go for it. :-) My preferred methods for making backups probably won't be much use to you, because they're predicated on there being a relatively small amount of data worth backing up. Just for the sake of comparison, I thought I'd mention them anyway...
[LIST]
[*]I often make tarballs of critical data and copy them to another computer, or an external hard disk, where I'm keeping a whole collection of them. I only delete old tarballs when the amount of disk space I've allocated for backups is exhausted. I tend to do that with data I modify very regularly, so I can do more than just roll back to the *last* snapshot.
[*]Other times, I take raw disk dumps. I find this useful because I can take snapshots of multiple filesystems (ie entire on-disk structures), and the operating system I use to restore the data doesn't have to be compatible with the filesystems I'm using. I'd only do this sort of thing with infrequently modified stuff. It's also very easy to verify the quality of the backup.
[/LIST]

Anyhow, you seem to have the whole thing figured out in your mind already, so I'm not sure any of this will be helpful. The one question I do have is whether what you really need is a "good" external hard drive. In your shoes, I'm not entirely sure I wouldn't go with the crappest, cheapest option I could find, and buy six of them instead of two. That way, at any one time, you could have three backups to choose from, all of which were mirrored, and each containing data you had deleted by the time you created the next.

---

### Post by gavinjb on 2007-10-06
If you just want to have the data on your 2 drives in Sync you might want to give FullSync a try it is not in the repository but you can get it from sourceforge.net and it is fairly simple to install and use.

There is a slight bug in the startup script (or maybe Ubuntu as it seems to work with other Distros ok), but if you do try this let me know and I can give you the info on what you need to change to get the script to work.

---

### Post by Freqs on 2007-10-06
A cd to back up is also not a bad idea

---

### Post by por100pre1 on 2007-10-06
I just wanted to add that Grsync is good GUI for rsync, if interested in rsync give it a try.

---

