---
title: "rdiff-backup to dvd"
date: 2018-10-29
forum: General Help
---

### Post by mlnease on 2018-10-29
Hello,

I'm trying to adapt to the loss of sbackup and could use some CLI help.  Could anyone please show me how to use rdiff-backup to backup to a dvd? Thanks in advance.

---

### Post by TheFu on 2018-10-29
I don't know that it is a good idea.  rdiff-backup needs to modify files inside the target storage with every new backup version.  That wouldn't be possible with write-once media.

Suppose you could backup to normal storage, then use DVD writing tools to push that to optical media. I'm not certain if restoring from an ISSO9660 file system would work.  I always backup to ext4 file systems using a network connection.  A $50 USB3 HDD can certainly store hundreds of versioned backups for most home needs, assuming any large media is handled separately.

I've been using rdiff-backup here for about 20 systems since around 2010. There have been 2-3 corruption issues in all that time, but that hasn't happened in a very long time - maybe 6 yrs.  rdiff-backup complains loudly if something isn't right. I've never had silent corruption.  For my needs, it is the best backup solution. Efficient, fast, built-in versioning.  The only thing it lacks, which can be handled outside the tool, is supporting encryption.  I should setup a LUKS encrypted LV for my backups.  Hummmm.
Prior to 2010, I used all sorts of backup tools and sometimes for migrating systems I'll use one of those to make life easier.  I've had to restore from the rdiff-backups a few times over the years too.  Takes me about 30-45 min to have the system backup doing what it was.  This was almost always due to a HDD failure, though I did something really stupid on a corporate email server once and broke the entire system during a major upgrade process.  rdiff-backup saved me.  The hardest part was just deciding that fixing the issue was going to be harder than wiping the box and restoring from backup and loosing 4 hrs of emails (2am-6am). Nobody ever complained.

---

### Post by mlnease on 2018-10-29
Thanks a million for the quick reply and the sound advice, TheFu.  I'm living on a pension so looking for a cheap solution and also a bit senile (no kidding!) so every day the command line's a little more challenging.  I guess I'll just have to bite the bullet and buy a new external hard drive--but thanks again for heading me off a bad idea.

---

### Post by TheFu on 2018-10-29
I'm not far behind you, probably. Used DVDs to backup some things for about 5 yrs before finally deciding that the hassle wasn't worth the effort and costs.

If you don't have too much data, I found a "refurbished" 250G WD-Blue for $10 at microcenter last spring.  I just needed something to replace multiple flash memory that was failing due to too much use for some video recording. It was packaged like a new disk from WD.  ZERO issues with nearly constant use all this time.  

If your system doesn't support USB3, adding a PCIe USB3 card is probably a good idea too. If you do, be certain to check for kernel-level Linux compatibility.  The one I bought took a few years before the Linux support became solid, but that was long ago.

But hopefully, you'll be as happy with rdiff-backup as I've been all these years.  --exclude-special-files is a very useful option.  I have it in all my backup scripts.

---

### Post by mlnease on 2018-10-29
Thanks again for the additional advice.  I'll certainly keep --exclude-special-files in mind and report back here if ever I get over the hump.

---

