---
title: "Can not log in"
date: 2006-10-17
forum: General Help
---

### Post by cssutto on 2006-10-17
When trying to read mutt email this morning, I got unable to copy messages.

Something to the effect the disk is full.

So I ran df and it reported that /dev/hda3 is full.

/dev/hda3 mounted on /

I poked around and could not find what was making it report full.

I then made a huge mistake.  I thought that like so many problems, this one would go away if I shut down and started up again froma cold start.

So I did the sudo shutdown -h now thing and when I started up Ubuntu will not take my password.

The message is to the effect that I can not sign on either because the disk is full or my home directory can not be accessed.

However, I can dual boot into W2K, which is where I am now.

I did two things late last night which could be at the root, if you will pardon the pun, of this problem.

I updated wine.

I ran a backup to a Maxtor external drive using rsync.  I watched it for a few minutes and it looked like always, that it was going to the Maxtor.

However, when I looked at the command line results, there was something to the effect that the disk was full.

There is plenty of room on the Maxtor confirmed both by df and by system>administrator>...?...devices.

I can boot into recovery mode, but I have no idea what to do when I get there.

I have some important work that must be done in linux and I need to get it up and running as soon as I can.

Help would be appreciated.

CSSJR

---

### Post by cssutto on 2006-10-17
I forgot to mention:

Ubuntu Dapper 6.0

Latest kernal updates.

Dual boot W2K.

Thinkpad A30p 60G drive.

Maxtor is external 200G and should be no factor.

CSSJR

---

### Post by cssutto on 2006-10-17
I found the problem, which I post here because it may save someone else grief.

I ran a backup using rsync which was supposed to go to my external Maxtor drive.

I remembered that I forgot to turn the Maxtor on and had to restart the backup.

Well, it dumped the entire contents of my 60G laptop drive into Ubuntu root.

No wonder it was full.

Of course it also copied some stuff that I am not sure how to sort out from what belongs in / to begin with,  but I have recovered a huge amount of space.

CSSJR

---

