---
title: "Backup (deja dup) not working in Ubuntu 18.04"
date: 2018-11-23
forum: General Help
---

### Post by jfaberna on 2018-11-23
At first I thought it was because I did a "do-release-upgrade", but then I did a fresh install wiping out all data. I can't get backup to keep running. It ran for a couple of days, but now it's stuck and it will not update anymore files to backup.  Also you can't run it manually because the "ran now" button is grey-ed out. 

Any ideas?

---

### Post by jfaberna on 2018-11-25
I'm pretty sure this is related to using a CIFS/SAMBA server to backup your data.  It worked fine in 16.04, but not in 18.04. The change I made was to create a NFS connection for the same server and directory as CIFS was using. Then it all started working. The permissions all looked good and it could backup the first time, but it could not run the following days using CIFS. 

I have 2 runs successful on NFS, the initial run yesterday and then today.

---

### Post by Tadaen_Sylvermane on 2018-11-25
Might ask what type of server you are backing up to? Backing up over SSH would be preferred. Cifs / Samba & NFS are vulnerable to crypto locker stuff as I understand it. If you can backup another way I would look into it.

---

### Post by jfaberna on 2018-11-25
The server is built on Ubuntu 18.04 Server with 2 sets of RAID mirrors.  I enabled CIFS/SAMBA for compatibility with other PCs in the house. All of this is behind a firewall NAT Router.  The only way into the router is via a VPN (OpenVPN is built into the router/AP) I copy stuff to and from the server from the different PCs. Easy way to share. I'm the only one in the house that actually knows how to do that.

The backup in question is Deja Dup the default on Ubuntu.

no ports are exposed on the router except VPN

---

### Post by jfaberna on 2018-11-27
Well deja dup continues to work automatically everyday and it also does NOT have any grayed buttons so I could run manually if I wanted.  The only change was to backup to a NFS share and not a CIFS share as I did on 16.04.

---

