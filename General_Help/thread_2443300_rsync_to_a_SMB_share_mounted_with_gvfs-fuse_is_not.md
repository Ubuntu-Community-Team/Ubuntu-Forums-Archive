---
title: "rsync to a SMB share mounted with gvfs-fuse is not working for me"
date: 2020-05-13
forum: General Help
---

### Post by jzandbergen1 on 2020-05-13
I have the SMB share mounted in /run/user/1000/gvfs/share name here
I have a CRON job to copy a database every night:

44 2 * * * cp /run/user/1000/gvfs/sftp:host=mygceserver/home/jeremy/gdatabase_`date '+\%m-\%d-\%Y'`.sql.gz /storage2/backup/db/

this works PERFECTLY

I am trying to also sync a backup folder on a SSD with a folder on another computer, so a simple copy wont work for me
these commands below dont work for me, rsync wont finish, but it stops using network resources and the CPU load on the second computer drops after a few seconds. It creates the folders, but thats about it.  I've read a lot of threads about this, and I am at a loss.....other people seem to be able to use rsync with a SMB share....
The HDD on the other PC is formatted to EXT4, but i also read that gvfs mounts things as cifs. How do I bypass all that **** and just put the files on the drive
I do not care at all about permissions, or anything else. I just want the data on there!!!!! I hopefully will never need the files also, this is a SECOND copy of backups for just in case.

I've tried these to no avail:
rsync -aAXS --delete /storage2/backup/ /run/user/1000/gvfs/smb-share:server=192.168.50.75,share=backup

rsync -aHAXxv --numeric-ids --chmod=Du+rwx --delete --progress -e "ssh -T -c arcfour -o Compression=no -x" /storage2/backup/ /run/user/1000/gvfs/smb-share:server=192.168.50.75,share=backup

rsync -aHAXxv --numeric-ids --delete --progress -e "ssh -T -c arcfour -o Compression=no -x" /storage2/backup/ /run/user/1000/gvfs/smb-share:server=192.168.50.75,share=backup

rsync -aAXvS -O --delete --no-perms /storage2/backup/ /run/user/1000/gvfs/smb-share:server=192.168.50.75,share=backup

I'll copy the folder over for now so I at least have it saved, but what am I missing?

---

### Post by ActionParsnip on 2020-05-14
Are both sides Linux based? If so, why use SMB?

---

### Post by jzandbergen1 on 2020-05-14
I have Windows PC's on network too, so I've shared the backup folder using SMB.

---

### Post by SeijiSensei on 2020-05-14
Okay, but if the backup folder is on a Linux machine, you should install openssh-server and use rsync.  You don't need anything more than:
```
sudo rsync -av source_folder user@server:/backup_folder
```
I'd create a separate folder for the Linux backups, and one for the Windows backups.

---

### Post by TheFu on 2020-05-14
+1 for rsync over ssh, if you don't want to use a better backup tool.  For mirroring, rsync is great. For backups, there are better, more efficient, options that provide versioned backups for very little extra storage - 30-60 days of versioned backups only needs 10-15% more storage. Those versions are much faster than rsync because the tools store the block checksums from the last backup set, so only half of the checksum needs to be calculated.

---

### Post by jzandbergen1 on 2020-05-15
> **TheFu said:**
> +1 for rsync over ssh, if you don't want to use a better backup tool.  For mirroring, rsync is great. For backups, there are better, more efficient, options that provide versioned backups for very little extra storage - 30-60 days of versioned backups only needs 10-15% more storage. Those versions are much faster than rsync because the tools store the block checksums from the last backup set, so only half of the checksum needs to be calculated.

Hmm This seems like the solution for me! Any recommendations on Software?

Another reason why I like the SMB share is because I have all my Samba shares accessible by my Asus Router, and I have an app that lets me access the routers external USB hard drive, and all my samba shares on my network through SSL and using a certificate from one of those free cert sites. Its my own little 8TB cloud :)
Any of the PC's that do not have samba shares are not readable by this app :(

---

### Post by TheFu on 2020-05-15
How do I say this ... 

Please don't connect storage you don't want shared with the world to your internet router/firewall.  Backups should never be shared with the world.

Most of the backup solutions require a Unix file system be used, not NTFS, not exFAT.  This is so the owner, group, ACLs, xattrs and permissions are retained.  Samba/SMB/CIFS doesn't work with those.  It is fine to use a router-connected storage solution provided the router is NOT connected externally, but that won't allow many backup solutions to work unless there is a backup tool that runs on the 

Using network file share mounts for backups that the client controls is asking for a crypto-malware attack to destroy your backups.  Please use a client/server model that doesn't use standard CIFS/Samba/NFS networking.  rdiff-backup works over ssh with a client and server rdiff-backup running on both sides.  Backups really need to be "pulled" by the backup server, never "pushed" by clients. The backup server shouldn't have direct access to the internet.

SSL for HTTPS is for privacy, not security.  If you want access to your files remotely, then there 2 network encryption tools
[LIST]
[*]ssh (sftp, scp, rsync, sshfs, etc.)
[*]full-VPN (openvpn or wireguard)
[/LIST]

Of course, we all have what we have. The "desired state" is a target.  For me, the upgrade to 20.04 broke my backups because the version of rdiff-backup on my backup server and about 15 other systems is incompatible with the version on 20.04.  I need to find a way to get the correct versions installed that is compatible across all the systems. No good solution at this point.

If you cannot use rdiff-backup or something similar, then duplicity is crazy flexible, but restoring backup sets captured by duplicity (and the family of other tools based on it) is a huge hassle. Duplicity uses the 1970s-style backup schedule with monthly "full backups" and daily incremental.  That means if you make a full backup on the 1st of every month, then need to restore on the 23rd, you'll have to restore 22 incremental backups to get all the data back, after restoring the full-backup.  rdiff-backup stores an rsync mirror in the last backup set, then reverse incrementals going to older backup sets. The tool automatically merges all the incrementals if you need a set, file, from 8 days ago or 46 days ago or 170 days ago.

rdiff-backup works similar to rsync, meaning over ssh.  It supports "pull" or "push" backups. The network packets are encrypted by ssh, but the local storage has to be encrypted outside the tool, by you.  LUKS encryption would be smart for that.

There are lots of threads here about rdiff-backup, some with example scripts.  Alas, you shouldn't use a router for storage.  Something is usually easy because it isn't secure. Access to router connected storage is commonly hacked. Often, the vendor handling the DDNS to make it easy has very poor security.  Just because there aren't any reports, doesn't mean it isn't cracked.  Stuff like this goes for years before being discovered all-the-time.

---

### Post by jzandbergen1 on 2020-05-15
Thanks for your recommendations! I am not currently too worried about people being able to see my data, as long as it isnt deleted from every single source lol.
I know I need to learn more about the security aspects of it all, but sometimes it's easier to get things setup with relaxed security then turn up the security when you know it all works. I suppose I can run the backup server behind another PC on this router so it has access to everything, but nothing has access to it lol. Then I could pull the data to the backup server, and push it back. I like complex networks but I need more experience so I don't scratch my head for so long on each concept :(

---

### Post by TheFu on 2020-05-15
Here's the water,
[LIST]
[*]2014: [https://arstechnica.com/information-technology/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/](https://arstechnica.com/information-technology/2014/02/dear-asus-router-user-youve-been-pwned-thanks-to-easily-exploited-flaw/)
[*]2016: [https://www.techadvisor.co.uk/how-to/network-wifi/how-stop-your-asus-router-being-hacked-3635607/](https://www.techadvisor.co.uk/how-to/network-wifi/how-stop-your-asus-router-being-hacked-3635607/)
[*]2018: [https://rog.asus.com/forum/showthread.php?101004-I-Believed-my-RT-AC88U-hacked-3-times-please-help](https://rog.asus.com/forum/showthread.php?101004-I-Believed-my-RT-AC88U-hacked-3-times-please-help)
[*]2020: [https://www.forbes.com/sites/thomasbrewster/2020/02/28/fbi-warned-of-fraudsters-paradise-up-to-130000-hacked-asus-routers-on-sale-for-a-few-dollars/](https://www.forbes.com/sites/thomasbrewster/2020/02/28/fbi-warned-of-fraudsters-paradise-up-to-130000-hacked-asus-routers-on-sale-for-a-few-dollars/)
[/LIST]
 but we can't get the horse to drink it.

---

