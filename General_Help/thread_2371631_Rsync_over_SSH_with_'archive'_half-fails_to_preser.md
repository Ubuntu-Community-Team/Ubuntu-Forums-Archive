---
title: "Rsync over SSH with 'archive' half-fails to preserve file permissions"
date: 2017-09-16
forum: General Help
---

### Post by redadept on 2017-09-16
Hello --

I am running a Ubuntu Drupal server that was recently upgraded to the 16.04 LTS.  I have a second Ubuntu server that has been working as a backup -- I usually run an rsync script that daily mirrors the entire Drupal /var/www folder over ssh to a /backup folder located in /home/administrator on the second server.  The backup would then be tar'ed and saved to an offsite storage each evening.  As a bonus, the /backup folder on the second server could be copied over to /var/www in order to act as a fully functional Drupal server in the event the main server failed.

After upgrading from 14 to 16, the backup script failed.  When troubleshooting, I tested by using rsync to transfer one folder with ownership 'www-data / www-data' to the backup server, having used ssh-keygen from root (sudo su) in order to run rsync as a cron job.  Note that the both the backup and main server have 'administrator' as the main user.

For some reason I cannot fathom, each time I successfully transfer the folder using 'rsync -avhe ssh', the files on the backup wind up with ownership changed to 'administrator / www-data'.  If I perform the rsync to another folder on the main server, the ownerships are preserved.  (Note that I do need to run rsync with root privileges in order to 'see' the files in /var/www.)

Before uploading actual server responses, does anyone know of something blindingly obvious that I have missed?

As an aside, does any kind soul know the magic incantation to preserve all ownership and file permissions when using rsync to a Linux (not Windows) cifs network share?  I tried, but got permission errors everywhere.  I can look at an NFS solution, but I believe the Samba share includes better default security.

Thanks in advance.

-- Darrell

---

### Post by HermanAB on 2017-09-16
The sticky bit on the destination directory?

---

### Post by TheFu on 2017-09-17
rsync has used ssh by default for over a decade. No need to specify it.

You probably want to use **sudo -i**, not sudo -s.  I wouldn't use sudo su.

For rsync to retain permissions, owners, groups and ACLs, both sides have to have the same userids, groupids, and ACL capabilities. Also, the root account (or an equiv) has to be used on the target system.  It might be necessary on the source system, I don't know.  I don't do backups like this.

NFSv4 security is far beyond anything Windows has, so CIFS is similarly pretty lacking for security. Really neither of these should be used outside the same physical location, though v4 NFS can use a tunnel, if you must.  I've never done that.  I have used read-only NFS mounts over the internet, but that was 20+ yrs ago - gatekeeper.dec.com.  It was a well-known internet NFS tool archive server.
The best thing about NFS is that native file permissions work remote just like they work remote.  The admins on both systems just have to setup the server to server credentials for kerberos and ensure the userids and groupids, the number, map 1-to-1 on both systems.

If you can post the exact rsync command used, **id** output, and the **ls -l** for the source and targets, that would be helpful.

BTW, I would use rsync, not NFS, but not for backups. Backups need to have versions and versioning with rsync isn't exactly good.

---

### Post by redadept on 2017-09-17
Thank you for the suggestions and information.  Before I go too far down the rabbit hole, do you have a recommendation for how to conduct secure full and incremental backups to a second server?  I've looked at several solutions, but they seem to fail when faced with the task of transferring root-access files with permissions intact across a network.  A pointer on how the target system can be opened to root access by rsync over ssh without compromising security would also be helpful :)

Again, thank you for taking the time to respond.  I do have keyboard access to both the production and backup servers in the same room, and can configure both, so an NFS share might actually be the simplest solution.

-- Darrell

---

### Post by HermanAB on 2017-09-18
Well, the old fashioned tar still works.

---

### Post by TheFu on 2017-09-18
> If you can post the exact rsync command used, id output, and the ls -l for the source and targets, that would be helpful.

Please.

Yes, tar, star, gnutar, all work,  but the if the amount of data is over 500MB, I'd avoid it and use a backup tool that has efficient versioning built-in.

Not sure how "keyboard access" matters.  Linux isn't Windows.  local or remote, the permissions are the permissions.  I haven't used "keyboard access" on 20 of my servers in years.  Only need that at first install, unless something really, really, really, really, bad is happening at boot.  Had a boot disk failure last spring on 1 of them - as I was installing the new OS, I used "keyboard access" for about 15 min, then switched back to my normal ssh method to restore from backup and was done about 45 min later.  Minor inconvenience, not a big deal.

If you have higher availability needs, just setup 2 systems to run the front ends and use a load balancer between those. For the back ends, setup near-real-time DB replication that uses 1 master.  If the master and slave DB servers are in the same campus, it is pretty easy and effectively free.  

For a real DR plan, the systems involved need to be 500 miles apart to avoid natural disasters and other large scale local issues (politics).

But in the end, the best system is the one you can create, use, and that works at 3am after a failure. Be certain to test it, quarterly, and document how to accomplish a restore so someone with "average Linux Admin skills" can follow those instructions and end up with a restored server.  Assume you've been taken to hospital with a head injury and someone else has to figure this stuff out.

---

