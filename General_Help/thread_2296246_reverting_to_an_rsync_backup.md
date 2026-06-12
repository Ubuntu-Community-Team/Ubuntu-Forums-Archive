---
title: "reverting to an rsync backup"
date: 2015-09-24
forum: General Help
---

### Post by allcoms on 2015-09-24
I have used this rsync command to backup my box:

rsync -aAXv  --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"}  /* /path/to/backup/folder

I have successfully restored my backup using a similar command but to a formatted drive. What I want to know is what options would be required to make rsync revert a tree of (partly newer) files to match the source without having to format or delete the destination? 

I'd want rsync to replace any files on the destination that have changed with their OLDER equivalents from the source as well as deleting any files and dirs in the destination that are not present in the source. It seems I can achieve the second part of that by using the --delete switch but I'm not sure rsync lets you replace newer with older files unless you replace everything?

---

### Post by allcoms on 2015-09-24
TLDR - can I force rsync to make the destination match the source when the source has older files?

---

### Post by TheFu on 2015-09-24
Don't think so. I'd have to check the rsync manpage.

However .... you could "touch" all the files you want restored in the backup area and they would be "newer" that way.  "touch" makes files have the current timestamp.  If you pair that with a "find" command - should be possible to touch only the files you want  ... all of this assumes I understand the real desire.

---

### Post by allcoms on 2015-09-24
Hi TheFu

I've already read the man page and, as you say, it looks like rsync isn't capable of doing what I want but I was hoping I might be missing something? I'd like to be able to do this with rsync because its so common and well-tested but it looks like I'll be looking for another tool. Maybe unison can do this?

Touching individual files isn't an option as I'm wanting to use this to restore full Linux (plus X/desktop and apps) backups so I could have to touch hundreds or thousands of files to use your suggestion.

What I'm after here is a simple altenative to the snapshotting features offered by BTRFS, ZFS etc mainly so I can rsync (or unison, or whatever) my drive before I do big updates and then quickly and easily roll back if it goes wrong. I don't want to use ZFS under Linux as its not kernel-based or complete and I don't trust BTRFS. Also, I'm running on an SSD so I don't think taking regular snapshots is healthy for my drive.

---

### Post by TheFu on 2015-09-24
To "touch" every file on a system, use ... 
```
sudo find /backup-area-files -type f -exec touch {} \;
```
Not hard at all. You probably want to touch a backup area files.

BTW - rsync really isn't a complete backup system - check out rdiff-backup.It has a similar command to rsync, but provides much more that a backup tool should have.  

Your information about ZFS is wrong. It is a kernel mode driver these days. You can also use LVM which has snapshots.  

What use is an SSD if you don't treat it like a real HDD?  Most current-gen SSDs solved the wear problem sufficiently enough to have predicted use well beyond (like 2x) any spinning disk.

I don't trust BTRFS either - that's mainly because there are well-known performance issues with BTRFS and KVM.

---

### Post by allcoms on 2015-09-24
Touching every file would cause it to update evey file which is what I wanted to avoid.

I've looked at unison again since my last post and it sounds like it does do what I want. It has a -force option that lets you force the restoration of older files so I can backup with rsync or unison so if I want to do quick restores (eg post dodgy updates) I have to use unison. I'll check out rdiff-backup too and see if it offers any advantages over unison. Would you know why it might be better? Neither rsync nor unison offer any snapshotting without extra scripting of course so that would be nice.

Thanks for pointing out my inaccurate ZFS statement. I thought ZFS was still FUSE-only for Linux but as you say, it seems to be a proper kernel module now. At least that's the impression I get from this FAQ [http://zfsonlinux.org/faq.html.]("http://zfsonlinux.org/faq.html") Shame it's not straightforward to install to ZFS under pretty much every Linux distro at present although I know Debian thus very likely Ubuntu too plan to support it.

I was aware I could use LVM thin provisioning to get snapshots with ext4 or XFS and LVM but I failed to find a good guide on how (best) to partition your drives for use with LVM TP and snapper.

---

### Post by TheFu on 2015-09-24
rdiff-backup won't help other than to provide backup "sets" so you can restore files as they were 3 days ago, or 11 days or 34 days or 93 days ago.  A mirror, as is commonly done with rsync just isn't enough of a backup.

*Thin provisioning* is something else. I think you may want to re-read the LVM snapshotting capabilities. I don't think the file system matters for LVM snapshots - I only use it for ext4, so I'm not positive, but the underlying technology shouldn't care about the file system.

I've never used unisom - looked at it a few times and decided is didn't meet my needs. Seemed to be more for media libraries, which I address in a different way. Be certain to look through all the "bad stuff" that can happen with whatever you finally decide.

For OS backups, rdiff-backup is the best tool that I've found. Wish duplicity worked better and not in the "old school" way with a monthly backup schedule needed.

---

### Post by allcoms on 2015-09-24
I should've explained. I would like a GUI for managing snapshots and snapper is the only one I know of for Linux. If you don't use BTRFS you have to use LVM TP to use snapper (see 'Does snapper support LVM' at [http://snapper.io/faq.html](http://snapper.io/faq.html))  but I've not tried it yet. I've heard regular LVM snapsots are a nightmare to deal with. Is this your experience?

I shall check rdiff-backup out soon.

---

### Post by TheFu on 2015-09-24
No, but I avoid GUIs and have been using LVM for 15 yrs. Cannot imagine **not** having LVM deployed on physical hardware systems. It is THAT good.

Perhaps you'd be happier with an easier to understand backup tool like Back-In-Time? There are some caveats for using it as a system backup, but it uses hardlinks to give the appearance of having all the files for a specific backup-set available.  It has a GUI for setup - be certain to read the running-as-root caveats.  Any GUI program that runs as root is a liability - extreme caution is needed.  Really bad things happen.

---

