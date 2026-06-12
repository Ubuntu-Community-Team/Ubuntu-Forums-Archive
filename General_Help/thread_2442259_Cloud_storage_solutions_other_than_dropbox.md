---
title: "Cloud storage solutions other than dropbox"
date: 2020-05-01
forum: General Help
---

### Post by Tom_Carr on 2020-05-01
I use  dropbox to sync files between a desktop and two laptops.  Dropbox works fine, and I think it also covers my backup needs.  However the free version of dropbox will only let me sync 3 computers and gives me only 2GB free storage.

Is there  something better than drop box which will run on linux?  Or something as good as dropbox with  more free storage and allows more computers synced?

Is it a good idea to have additional back instead of just  dropbox?

---

### Post by ActionParsnip on 2020-05-01
owncloud is one way

---

### Post by TheFu on 2020-05-01
Some thoughts ... 

Dropbox isn't a backup. It is a mirror.  Corruption from one machine that appears as "new data" will overwrite the data on all the others.

If you want an automatic sync and would self-host it, check out seafile, nextcloud, owncloud, or just use rsync every few hours to push and pull from systems you control.  Nextcloud has a snap or docker install, so we don't need to know all that much to have it working on our LAN.

But for backups, we really need:
* automatic
* daily
* versioned
* encrypted
* "pulled" by a server, not "pushed" from the client
solutions.  The versioning is absolutely key to address corruption and malware.  Daily means we have specific points in time when a backup version is taken.

A mix of nextcloud and versioned backups for the nextcloud data could be sufficient for many setups. Just depends if whether ALL the data on the clients is maintained through the nextcloud sync or not. 

IMHO, putting unencrypted backup data on the internet is foolish. There is likely to be some data that gets included by accident which would be considered sensitive.  And I wouldn't trust any encryption written and provided by the same company doing the backups.  They are looking to check a box on a list of features.  Pre-encrypt the data before it gets placed into the backups for your own safety.  Nextcloud has a per-userid data encryption method. I've not used it.  I have used their 2-factor authentication logins with a yubikey. That worked well and was REALLY easy to configure.

Of course, there are backup services too.  Pushing data over the internet can be fine, assuming you highly restrict the data to just the absolute minimal, perhaps documents and top 10 wedding photos. SpiderOak comes to mind.  Some friends use it and like it.  They pre-encrypt everything.  

OTOH, when you want to push media for backups and have 3 systems, perhaps a different solution would be better?  An 8TB USB3 HDD is about $120 these days. Get two of those and swap the one you have at home and work in the locked desk every week. Be certain to LUKS encrypt those portable drives. That is pretty much the best of everything. You have backups, they are versioned, encrypted, onsite and offsite, while still being under your control.

If I was pushing backups to storage and computers owned by someone else, I'd use Duplicity.  Duplicity (a real backup tool) can use many different cloud storage platforms - S3, FTP, ssh, rsync, and a few others. Best of all, duplicity encrypts the backups and chunks them into manageable file sizes.  The bad parts of duplicity include the old 1970s style backup techniques based on monthly full backups with daily incrementals.  If you do a full backup every month, then to restore from a crash on the 29th, you'd need to restore the full, then 28 incremental sets of backups.  

Other tools, like rdiff-backup work the opposite way. The most recent backup always looks like a mirror and if you want to restore the full set from 29 days ago, you'd do a **sudo rdiff-backup -r 29D root@IP-of-Server::/path/to/backup   /local/target/to/get/files**. Alas, rdiff-backup doesn't encrypt within the tool, so that has to be handled by the remote file system.  For me, having the last backup as a mirror on LUKS encrypted storage does what I need. Perhaps I'm more hands-on than most?

---

### Post by CelticWarrior on 2020-05-01
[MEGA]("https://mega.nz/") is objectively better. Please note this isn't an endorsement. Just like with Dropbox, use it at your own risk.

---

### Post by TheFu on 2020-05-05
Why "pull" backups are necessary, never "pushed" 
[https://www.theregister.co.uk/2020/05/05/godaddy_ssh_login_details_compromised/](https://www.theregister.co.uk/2020/05/05/godaddy_ssh_login_details_compromised/)

---

