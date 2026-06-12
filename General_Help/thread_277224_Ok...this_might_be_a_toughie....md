---
title: "Ok...this might be a toughie..."
date: 2006-10-14
forum: General Help
---

### Post by CornMaster on 2006-10-14
I have two computers (cyclops and biclops) now running Ubuntu in the home.  Both are very similar hardware wise.  One depends on the other for wireless internet, so one is always on.

I want to do one of the following:
1) Change the mounting of my home partition from cyclops local 40GB home partition to the biclops 40GB home partition if communication with biclops is available.

In order to do that, I would need to run a script (probably bash) on startup that would unmount and mount the partition if communication was successful. (I think)  But I am wondering if it is even viable.  I may be logged into both computers at once, and  sharing a home directory like that could be dangerous if I try to use an app that modifies the same files?  Does that make sense?  I could probably limit my double logins to try and eliminate that possibility if it would be a big problem.

2) Mirror biclops home partition to cyclops home on bootup.  This would solve the running off the other computer problem...like if byclops died or was rebooted while I was using cyclops.  And if biclops wasn't available, then the local home is still a decent mirror with most of the settings.

This would seem to me to be much slower.  I have a 10mb link between the two, but if I ever get close to filling the 40gb it might take a long time to boot.  I guess I could write a script that checked the modified dates and only moved files that had changed, that would cut down on copying.

Anyway...what do people think of these plans?  And which one do you think is the better option?  Or am I missing something totally simple here?

I also need to figure out how to share directories and partitions....but I'll check that out elsewhere.

---

### Post by K.Mandla on 2006-10-14
It doesn't sound impossible, just unusual.

You'll need some way of sensing the always-on machine. After that, you can mount a shared directory either through fstab or via a scripted mount command. (I don't know if I would set it as "the" home directory ... why not a symbolic link in home to a shared partition? It might save you if you ever had a data loss problem.)

You could set up one (or both) machines to automatically log in, so even if you just build a severely restricted dummy account, that's not too much of a problem.

You could set rsync to run on startup, and mirror the partitions like you describe. Rsync is usually smart enough to tell if a file needs mirrored or not, which would save you transfer time. 

I think it could be done. Like I said, it's a little unorthodox, but doable. At least on paper. 

If these are both Linux machines, look in the Howto forum for the NFS client/server thread. Otherwise you'll need Samba.

You know, these sound more and more like thin clients. That might be something you could look into as well.

Have fun! Let me know how it goes! :mrgreen:

---

### Post by CornMaster on 2006-10-15
I don't want to go fully thin client just for my home setup....but maybe in the future.  May be setting up a small lab, and that would be an ideal situation.

I think I'll try the syncing.  Might take a bit longer, but seems less risky then remote mounting of partitions.

I've installed both NFS and Samba but don't have much time play around with it.  I suspect I have to make changes to my firewall before if will work properly, and I don't have time to fiddle.  Maybe next weekend.

I'll let you know how it works...and maybe even write a how to incase someone (for some reason) wants to do this in the future.

---

