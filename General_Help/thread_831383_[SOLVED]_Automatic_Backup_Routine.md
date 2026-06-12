---
title: "[SOLVED] Automatic Backup Routine?"
date: 2008-06-16
forum: General Help
---

### Post by jlacroix on 2008-06-16
First of all I have three machines running Hardy. My wife and I both have our own desktop and I have a laptop. On each machine we have important files we don't want to lose. All three machines are networked via Samba and can share files between eachother. I have it set up so it's easy to create new shares so that's not an issue.

I'm going to be buying a 500GB external hard drive. I would love it if I was able to have it automatically back up files from all three machines to the external drive.

I was thinking that I'll share three folders on the external drive (each machine having it's own dedicated directory) and whenever someone logs in, something could check the home directory of the machine for any changes and make sure an exact copy is stored on the external drive. Kind of like a script or something.

Going further, I would love for their to be a way to extend this to making sure my hard drive on the laptop and my desktop have the same home directory contents.

I'm not sure if any of this could be done but that would be great if it could.

---

### Post by Vivaldi Gloria on 2008-06-16
I remember seeing a lot of scripts etc. in this forums for backups so search this forum for backups.

Also have a look at

[http://www.linux.com/feature/117236](http://www.linux.com/feature/117236)

and

[http://www.nongnu.org/rdiff-backup/index.html](http://www.nongnu.org/rdiff-backup/index.html)

I remember reading more articles on backups at [www.linux.com](www.linux.com) so also search there.

---

### Post by jlacroix on 2008-06-16
> **Vivaldi Gloria said:**
> I remember seeing a lot of scripts etc. in this forums for backups so search this forum for backups.

Also have a look at

[http://www.linux.com/feature/117236](http://www.linux.com/feature/117236)

and

[http://www.nongnu.org/rdiff-backup/index.html](http://www.nongnu.org/rdiff-backup/index.html)

I remember reading more articles on backups at [www.linux.com](www.linux.com) so also search there.

Thanks, I did do some searching but the tools that are being talked about I'm somewhat of a newbie in.

Rsync seems the best so far from those links, but I was hoping to be able to do this over a Samba share and use Samba paths. Is there a way to do that, or something more beginner friendly?

---

### Post by Vivaldi Gloria on 2008-06-16
jlacroix,

Actually, when i backup, i do it the old way - tar it, gzip it and ssh it. So I don't know much about file synchronization. But I also found this:

[http://ubuntuforums.org/showthread.php?t=815066](http://ubuntuforums.org/showthread.php?t=815066)

There are lots of rsync & unison threads in this forum. Have a look at them.

Hope these help.

---

### Post by rbmorse on 2008-06-16
Look at sbackup. I set it up to performs an incremental backup of /etc, /home and other selected files every four hours to backup drives attached to a Linksys NAS, although attaching the backup drives to any host as shared partitions works too. It also does a fresh base backup once each week and deletes old stores after 30 days (although I'm going to change that to 90 days on my production machine because I have sufficient disk space).   

I mount the NAS share via fstab and the host computers see their shares like any other partation.

---

### Post by jlacroix on 2008-06-16
Thanks guys, I think I'm going to use RSync. I think that it shouldn't be too hard to figure out a way to make it backup to a Samba share. At least I hope its possible. If anyone knows how to do that over Samba that would be great, I did search for Samba rsync but I didn't find anything. I'm going to mark this solved for now but if anyone knows how to make rsync work with Samba that would rock.

You guys really helped, thanks again.

---

