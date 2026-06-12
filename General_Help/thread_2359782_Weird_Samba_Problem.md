---
title: "Weird Samba Problem"
date: 2017-04-27
forum: General Help
---

### Post by Andrew_Benjamin on 2017-04-27
I have two servers sitting in my basement. Pretend they are called MAIN and BACKUP.
Each machine is running Ubuntu Server 16.04 and each runs Samba.

Both machines share the same username/password - let's call the user Bob and the password PWord.

I'm trying to share the MAIN machine's Samba share, called TVRecordings, with the BACKUP machine so that it's slave mythtv backend will store recordings in the same location as MAIN.

The Samba section for MAIN reads:

```
[TVRecordings]
path = /media/RAID/Media/TVShows
available = yes
valid users = root Bob mythtv
force user = root
encrypt passwords = true
browseable = yes
security = user
guest ok = no
read only = no
create mask = 0755
writable = yes
write list = server Bob
browsable=yes
force directory mode = 0777
public=yes
```

The RAID array for the TVShows location is owned by root:root

The BACKUP machine's fstab line reads as follows:

```
//192.168.40.28/TVRecordings /media/TVRoot cifs credentials=/etc/samba/user,noexec 0 0
```

/etc/samba/user on the BACKUP machine reads:

```
username=Bob
password=PWord
```

and permissions were set correctly.

So, from the BACKUP machine I can list (ls) the files on MAIN, but I can't write anything.  If I type:
```
cp /etc/fstab .
```

I ge:
```
cp: cannot create regular file './fstab': Permission denied

```

If I preface the command with sudo, I can copy the file.

If I share the same Samba share from a Windows 7 machine using the same username/password (Bob/PWord) it reads and writes without complaint.

I'm clearly missing something simple - the share works as expected from Windows and rejects my permissions from another Ubuntu machine using the same credentials (which are the same credentials the machine expects anyway for itself).

I'm not terribly concerned that I'm using the same username/password - these machines are sitting in my basement behind my firewall (OpenWRT). It's likely easier to gain access to my basement than the machines.

Help?


Andrew

---

