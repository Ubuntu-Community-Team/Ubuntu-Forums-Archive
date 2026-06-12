---
title: "fstab and many external drives"
date: 2024-07-18
forum: General Help
---

### Post by babag on 2024-07-18
I'm on Ubuntu 22.04 and using it for a lot of video/audio projects. That's resulted in, over time, the accumulation of a lot of drives. Since I often have dormant projects mixed with active as well as archived ones, my drives are not always plugged in. Until now I've just used my Dolphin file manager to mount a drive by simply clicking it. With a bunch of drives, though, it can get to be a nuisance.

What I'd like is to have the system, when booting, auto-mount whatever drives are plugged in (and ignore any not plugged in). I'm assuming this might be accomplished by listing the drives in fstab and that it may be time to start entering all of them but have a question(s).

Is fstab a good way to handle a situation like this?
The listing of drives in fstab could get quite long, not industrial-scale long, but long. Is that bad?
Could someone post an example of current syntax for this kind of listing? (Searching turned up some confusion for me about a 'nofail' option and reference to a newer way to list options.Some of the answers I found went back a couple of decades.)

I notice that, when I use Dolphin to mount a drive, a directory is automatically created for it in </media/user/directory> and, on ejecting the drive, it is removed. Is /media a good place to put directories for these mounts or, being that they are not being handled automatically by the system any more, should I make my own place for them? 
Is there a way to mimic the system's behavior of creating the directory at mount time and removing it on ejection?

Obviously, if there's a wholly different way to deal with this, I'd love to hear about it.

thanks,
BabaG

---

### Post by TheFu on 2024-07-19
**autofs** is what you want.  No reboot needed.
Also, full control over where the storage is mounted AND which options are used works.  The file systems are mounted on-demand. If they are unused for a few minutes (no open files), then the file systems are automatically umounted cleanly.  

Use the --ghost option to have the mount points listed even when the disks aren't connected. This is important for GUI file manager users. Otherwise, there's nothing go click on with the GUI to cause the mount.

I also use autofs for all NFS mounted/network storage.  autofs has been stable and working since the 1990s, so it isn't undocumented or flaky.  It is one of those things that "just works". No surprises.

---

### Post by babag on 2024-07-20
Thanks, TheFu.

Been looking into various things regarding this issue, including your suggestion about autofs. Looks good. I'm far from expert on anything like this so there are things that confuse me still. 

One point of confusion, minor, is that almost all of the info turning up seems to be about network shares rather than external or even internal drives. That makes it hard for me to find things like the mount settings appropriate for my various drives. The drives I use are nvme, sata ssd, and sata hdd.

I also tested some fstab settings and found that the default system behavior differs from what I got using fstab to auto mount a drive. I like the simplicity of the way the system handles things, showing me the drives that are plugged in as unmounted in Dolphin and keeping the /media/user/ directory empty but creating and removing the directory for each drive when it is mounted and unmounted.

When I put the test drive into fstab I had to create a directory for it in /media/user/ (or anywhere I wanted to mount it) but that directory seems permanent. Not only did I have to manually create it but it did not remove itself when the drive was unmounted. That seems like the best way for this process to work as I don't think it would be good to have the process going around deleting directories without knowing more about what I'm doing.

It looks like using a setting in autofs for timeout=0 will keep a drive mounted, even when not accessed for a long time. That's good for my way of working.

I also appreciate the suggestion that using --ghost as an option will help in displaying available drives in Dolphin. I have a question about that, though. Since I have a lot of drives, will this autofs option show them all, even if they are listed but not plugged in? or does it only show drives that are plugged in? If it takes its info from the list of drives, that could lead to a very cluttered file manager pane. If it only displays plugged in drives, that would be great.

Lastly, from what I've read, I should make a file for each drive with its info as the contents. If it's actually necessary to make separate files, that could be cumbersome, not to mention adding to clutter. For me, it would be better to be able, like fstab, to be able to make a listing of all of the drives in a single file, or maybe a couple of files, like one for hdd, one for sdd, one for nvme. If they have to be separate files, I suppose it's probably possible to make a directory just for them. Is that true?

[update]
I used fstab to mount the three types of drives in /media/user/ and it does mount them. I used 'LABEL' rather than the uuid for each drive and, if not directory is present for the drive at boot time, it is created. The down side in terms of mimicing the system's behavior is that, on unmounting the drive, the directory remains present and is not removed.

Thanks again,
BabaG

---

### Post by TheFu on 2024-07-20
That's a bunch of questions that 10 minutes of use will answer AND you'll **know** the answer.

I use different auto-files for NFS and USB mounts.  For storage directly connected via eSATA, SATA, NVMe, Infiniband, I just use the fstab and mount.

I also use the partition LABEL= method for mounting, unless I'm using LVM. With LVM, the /dev/{vg-name}/{lv-name} is more useful than a label, IMHO.  To each their own.

Remember, you aren't mounting drives. You are mounting file systems.

You can easily find some autofs how-to guides around the internet.  autofs works the same regardless of Linux version, so don't worry about different OSes having different settings. Settings are tied to the file system type, but if you are using ext4, then it really is easy.

Don't confuse creating and removing an empty directory when the file system isn't mounted any longer, if that's the way you set it up.  It won't delete data.  In my use of it since the mid-1990s, I've never seen autofs delete files.

However, I think it is a terrible idea, for a number of reasons that should be obvious, to mount storage under /media/ and definitely not under /media/{username}/. But it is your system and everyone should learn their own lessons, hopefully, not the hard way like I did years ago.  Let's just say, having two different daemons trying to manage the same mount areas is asking for problems and I have very little confidence in that the GUI developers behind Qt and GTK do with gio/gvfs managing mounts.  Additionally, the performance of those tools seems to be significantly worse than what a normal mount does, which is how autofs works.  Any tool that doesn't correctly maintain the /etc/mtab is useless to me and should be avoided.  Since the real mount command is used by autofs, you gain access to all the options it provides, if you need them.  If you stick with normal file systems, and not volume managers or foreign file systems like NTFS/exFAT/FAT32 (ewww, I feel dirty just listing those), then the mount options are pretty simple and the same that you'd use from the fstab.

But it is your system.

One hint that may or may not be useful.  in the auto.master file, the top level directory that all other sub-mounts for the config file that follows on the same line is listed.  If you put something like this 
```
/Data /etc/auto.Data --timeout=60 --ghost
/-      /etc/auto.nfs --timeout=60 --ghost
```
to have two different files included (auto.Data and auto.nfs), then the first one with /Data at the start will place all the directories listed in auto.Data under /Data as the top level directory.  I find this confusing, so I prefer the 2nd line with "/-" which says, use the top directory and have all mounted locations referenced inside auto.nfs start from /.  Of course, you probably don't want all those mounts to happen in the top, /, directory, so you'll want to specify something like:
```
/d/D1 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D1
/d/D2 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D2
/d/D3 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D3
```

Which is exactly what my auto.nfs file contains.  I use a bunch of NFS here.  Not so much USB connected external storage.  Rather, I have external storage, it is in an array using either eSATA or Infiniband (don't ask. it was a deal!).  To make internal storage easier, I added 4-disk enclosures with fans to my cases that take (3) 5.25" drive slots, but hold 4 drives. These are hot-swap capable, though I seldom use them that way.

I tested the automount option that systemd provides and found it didn't meet my needs, because it only mounts, doesn't umount when the file system becomes inactive.  There are many reasons to prefer this, but until you are burned like I've been, you'll keep doing the other way.

Good luck.

If others want to jump in an answer the specific questions asked, please do.  A little trial will answer them, however.  Shouldn't take more than 10 minutes following a guide.

---

### Post by babag on 2024-07-20
Wow. Thanks again, TheFu.

Sorry for all the questions. You mentioned not trusting some things which is why I asked so many questions. I feel like the classic dangerous guy armed with a little knowledge.

Much of what you suggest is beyond me but I'm pretty decent at following formats when someone posts examples, as you've done here. I'll probably install and try autofs once I can steel myself for the process.

Very much appreciate the suggestion to avoid using /media for mounts along with the explanation. I'll think about that and what I want to use as an alternative.

Thanks again and would love to hear from others as well, as you suggest, though, this thread seems to be getting very few views. Makes me appreciate your time all the more!

BabaG

---

