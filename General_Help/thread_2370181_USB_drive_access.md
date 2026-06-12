---
title: "USB drive access"
date: 2017-08-31
forum: General Help
---

### Post by csdgbas on 2017-08-31
No, this is not the normal question, and I'm pretty sure that what I want doesn't exist (because I am a weirdo, and what I want to do isn't something that any sane, normal person would want to).

Is there any way of accessing files on a USB drive... *when the USB drive isn't physically available?*  (See? I told you I was a weirdo!)

What I'm thinking of is some kind of "shadow" USB drive / mount that is just a (read-only) copy of what was on the USB drive the last time it was mounted.  I suppose it's effectively a backup, but I want to be able to access the files as normal (again, I stress, only read-only) using normal tools.  Obviously, to be available, the files should be copied to somewhere on the hard disc as and when the USB drive is actually physically available (i.e. mounted).

Does any of that make sense?  I know I could effectively do it manually - every time I mount the USB drive I could copy the files on it to the local HD, but that's prone to human error, so I was hoping that someone else out there is as weird as me and has already automated the process :smile:

---

### Post by TheFu on 2017-08-31
Anything is possible with sufficient time, effort, money.

You can have the computer perform tasks when a specific device is connected.  Look into **udev** for that.
Or you can have the system check every  minute if a file exists somewhere ... like where it was on the USB drive ... then have that kick off anything you want to script ... like an **rsync**.  I would have the start of the rsync script remove the file to prevent it from being run multiple times if the rsync takes a few minutes.  The hard part would be to get the file back on the external disk BEFORE the drive is removed, but not so soon as to cause constant running of the rsync task every minute.

If you knew the disk would be connected for at least 1 hour, then you could schedule it for specific times.  It would be easiest if you had a longer period of time - like every 12 hours or every day. That's how backups work, BTW.

If your goal is really to have a backup, then don't use rsync. Use something like rdiff-backup, so you get versioned files. This is very important if you are trying to protect against file corruption or those Windows viruses that encrypt everything.  A single "mirror" copy is not sufficient to protect against those problems.

---

### Post by csdgbas on 2017-08-31
Thanks for the reply, I'll look into udev (although from first look it looks like udev relates to all users, not on a per user basis).  I did suspect there wouldn't be an OOTB solution, but didn't want to reinvent the wheel either.

No, it's not a backup I'm after, it's really just that I'm sick of swapping my USB key between computers, when I am generally not actually changing anything on it, only referring to documents that are on it.  In my ideal solution, the files on the USB key are the "master" copies, any "shadow copies" which might be on the computer I happen to be using at the time are just for convenience (and might be out of date etc., there's nothing I can do about that).

---

### Post by ajgreeny on 2017-08-31
Just thinking out the box, can you attach the USB to your router if you have one; the files on it should then be available to all connected computers, a bit like a NFS

---

### Post by TheFu on 2017-08-31
Best to never mix storage and routers.  Everyone I've seen has been hacked.  Do you want all the connected storage available over the internet?

If all you want is a mirror across devices, Nextcloud. Don't allow it on the internet directly, but over a VPN remote access is fine.

I think trusting a flash memory device is a mistake.  They fail with very little warning.

So ... my encrypted password manager DB is sorta like your USB flash drive.  Every night at 1am, it is copied from the primary system of record (my desktop), out to 6 other locations/devices.  I only make changes on it from the desktop. All the other locations are "read-only" in my mind.  If I do make a change on another system, then I just need to push that update to the desktop before 1am.  Simple, effective.  Set it up about 8 yrs ago and never worry about it again - other than when I change tablet or phones.

---

