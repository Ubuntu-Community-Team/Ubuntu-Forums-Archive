---
title: "Samba Issues: file already open in another program"
date: 2014-08-14
forum: General Help
---

### Post by chris193 on 2014-08-14
Hello, I've got a Ubuntu Server running Samba and BitTorrent Sync, btsync seems to work fine however samba keeps messing up with permissions, I think. If I copy and paste a document in to the samba share (from windows), it immediately becomes un-deletable and unmovable because "...the file is open in another program". It's a real pain in the ass and I'm not sure what I've done to cause it. All the 'storage' files are under /files /files/Resources is the samba share, the rest are btsync

in Samba.conf
```

[**Resources**]comment = Resources
path = /files/Resources
browsable = yes
writeable = yes
guest ok = yes

```

ls -al /files
```
total 48
drwxrwsr-x  9 root     users   4096 Aug 11 15:21 .
drwxr-xr-x 22 root     root    4096 Aug 14 12:26 ..
drwxrwsr-x  5 user1 btsync  4096 Aug 12 11:14 Accounts
drwxrwsr-x  8 user1 btsync  4096 Jul 30 10:12 Clients
drwxrwsr-x  7 user1 btsync  4096 Jul 29 12:12 Destinations
drwxrwxrwx  2 root     root   16384 Jul 10 10:10 lost+found
drwxrwsr-x  6 user1 btsync  4096 Aug  4 09:54 Public
drwxrwsr-x  7 root     btsync  4096 Aug 11 15:21 **Resources**
drwxrwsr-x  6 user1 btsync  4096 Jul 28 16:16 Staff

```

I can't see anything it could be open in on Windows and I'm on the verge of tearing my hear out, greatly appreciate any help!

I've also just noticed the $~ temporary files aren't deleting once close? And the files that I copy in are read only..

(sorry for any ignorance and/or stupidity. I'm still a complete novice)

---

### Post by bab1 on 2014-08-14
> **chris193 said:**
> Hello, I've got a Ubuntu Server running Samba and BitTorrent Sync, btsync seems to work fine however samba keeps messing up with permissions, I think. If I copy and paste a document in to the samba share (from windows), it immediately becomes un-deletable and unmovable because "...the file is open in another program". It's a real pain in the ass and I'm not sure what I've done to cause it. All the 'storage' files are under /files /files/Resources is the samba share, the rest are btsync

in Samba.conf
```

[**Resources**]comment = Resources
path = /files/Resources
browsable = yes
writeable = yes
guest ok = yes

```

ls -al /files
```
total 48
drwxrwsr-x  9 root     users   4096 Aug 11 15:21 .
drwxr-xr-x 22 root     root    4096 Aug 14 12:26 ..
drwxrwsr-x  5 user1 btsync  4096 Aug 12 11:14 Accounts
drwxrwsr-x  8 user1 btsync  4096 Jul 30 10:12 Clients
drwxrwsr-x  7 user1 btsync  4096 Jul 29 12:12 Destinations
drwxrwxrwx  2 root     root   16384 Jul 10 10:10 lost+found
drwxrwsr-x  6 user1 btsync  4096 Aug  4 09:54 Public
drwxrwsr-x  7 root     btsync  4096 Aug 11 15:21 **Resources**
drwxrwsr-x  6 user1 btsync  4096 Jul 28 16:16 Staff

```

I can't see anything it could be open in on Windows and I'm on the verge of tearing my hear out, greatly appreciate any help!

I've also just noticed the $~ temporary files aren't deleting once close? And the files that I copy in are read only..

(sorry for any ignorance and/or stupidity. I'm still a complete novice)
This problem is usually due to mount options used (or not used) when the remote share is mounted (mapped) to the local client's file system.  How do you mount (map) the share?

---

### Post by chris193 on 2014-08-14
bab1, I see you're back to rescue me [again]("http://ubuntuforums.org/showthread.php?t=2226402&p=13037214#post13037214")! I still refer to your last answer frequently (so thanks again!) This is where I'm afraid I may say something stupid, but /files is mounted onto a secondary 3TB HDD sdb1? (sorry if that's not what you meant)

```
UUID=c7535844-7948-4974-b202-bdb68c752b75 /files ext4 rw,auto,user,exec,
```

---

### Post by bab1 on 2014-08-14
> **chris193 said:**
> bab1, I see you're back to rescue me [again]("http://ubuntuforums.org/showthread.php?t=2226402&p=13037214#post13037214")! I still refer to your last answer frequently (so thanks again!) This is where I'm afraid I may say something stupid, but /files is mounted onto a secondary 3TB HDD sdb1? (sorry if that's not what you meant)

```
UUID=c7535844-7948-4974-b202-bdb68c752b75 /files ext4 rw,auto,user,exec,
```
I'm here to spread the gospel.  :-)

I'm referring to how the client mounts the share.  There is a incompatibility between Windows and Samba in the *byte record lock *.  This can cause problems.  The Samba option is called ***nobrl*** for no byte record lock.  I'm not really sure what to do with a Windows client.  I will try and look up some information later in the day.  I'm just about to leave for a few hours.

We are talking about a Windows client mapping this share; correct?

---

