---
title: "how to use &quot;/nfs/export&quot;?"
date: 2017-08-11
forum: General Help
---

### Post by ronjjjg8885 on 2017-08-11
hi
i'm following this article [http://kodi.wiki/view/NFS#NFS_sharing_from_Linux](http://kodi.wiki/view/NFS#NFS_sharing_from_Linux)

so i should enter this: ```
192.168.1.121(r,all_squash,insecure)
```

but not sure where.

when i nano "/nfs/export" i get an error saying the file does not existed (even after using the sudo command)


what did i do wrong?

---

### Post by TheFu on 2017-08-11
That is incorrect. The export file is /etc/exports and if it doesn't exist, create it.  This is a common question for people new to Unix.  If a config file doesn't exist and you need it, then YOU need to make it.

Here's an example:
```
/D      romulus(rw,async,root_squash)
```

romulus is an approved client and has either a DNS or /etc/hosts file entry. My NFS server and client are GigE connected.  I use the same values for a few raspberry-pi Kodi machines, which are also wired ethernet connected.  I don't do wifi with NFS.

Usually /nfs/ is a location on a client where nfs automounts are made.  I used to see those all the time in the 1990s, but haven't since around 1996.

---

### Post by yancek on 2017-08-11
The file you need to edit is /etc/exports which should already exist so do:  sudo nano /etc/exports and save the file.  You might check first to see if it exists and if not, you would need to install nfs. You would then need to run:  sudo exportfs -ra (the -ra are options and you can do an online search for those and other options to use).  I have an example posted below from an old exports file.  This would allow access from other computers on the 192 subnet to data in /mnt/data on the machine from which I am exporting.  Modify yours to suit what you want to exxport.

> /mnt/data 192.168.0.0/8(no_root_squash,sync,secure,no_subtree_check,rw)

---

### Post by ronjjjg8885 on 2017-08-11
i've entered:
```
/media/ron/5cbb7dfb-765b-4731-9ab2-08cd87bd7f04/Music  192.168.0.0/8(no_root_squash,sync,secure,no_subtree_check,rw)
/media/ron/5cbb7dfb-765b-4731-9ab2-08cd87bd7f04/Videos  192.168.0.0/8(no_root_squash,sync,secure,no_subtree_check,rw)
```

both to [COLOR=#000000]/etc/exports and saved it.

this is after installing nfs.

at the end i did [/COLOR]```
[COLOR=#000000]sudo exportfs -ra[/COLOR]
```[COLOR=#000000]

should it work now if correctly configured on the pi? (ethernet cable- not a wifi)

thank you and please answer if i can procceed with the pi configuration...

edit:

working!!! thanks!!!
what steps can i take to make it more secure?[/COLOR]

---

### Post by TheFu on 2017-08-11
192.168.0.0/8 is crazy!  Use 192.168.1.0/24 to get a normal home subnet.

Which file system is used for each storage device?  If NTFS is used, there will probably be permissions issues.  NFS like Unix compatible file systems - so ext3, 4, jfs, xfs, zfs, ... 

/media/ron/5cbb7dfb-765b-4731-9ab2-08cd87bd7f04/Music can be problematic for remote access due to changing mount decisions.  I would manually mount each and definitely NOT use /media for those mount areas.   

   I'd use something like /D/Music.

There is a file system hierarchy standard which explains what each different top-level mount location should be used to hold - worth a skim to see what /media/ is for (removable media). If this storage is permanent there are better choices.  Things that are automatically handled often ARE NOT the best way.

Whenever modifying config files on the NFS server, I always restart the nfs server - **sudo service nfs-kernel-server restart**. Then restart the nfs client on any client machines, if they are impacted by the change. In theory, having exportfs update the list of exports in the kernel _should_ be enough, but that isn't always true.  The exportfs manpage has some interesting information too.

The more you use Linux, the more comfortable you will be with just trying things.  If you aren't deleting stuff and have automatic, daily, versioned, backups, then what harm can you really do?

---

### Post by ronjjjg8885 on 2017-08-12
i did the change to the ip's.
the hdd is ext4.

> [COLOR=#000000]I'd use something like /D/Music.[/COLOR]
 if i write "[COLOR=#000000]/D/Music" will it be enough? i guess not.

why can't there be a password like in samba?[/COLOR]

---

### Post by TheFu on 2017-08-12
> **ronjjjg8885 said:**
>  why can't there be a password like in samba?[/COLOR]

* Once configured by the systems admin, end-users don't know anything about NFS.  They don't need to know anything about network storage, so it is easier for them.
* NFS is a system-to-system storage sharing protocol, not system-to-user. The NFS client and server have to be configured by the admin to work together.
* Passwords are a complete failure when it comes to security. If you are using passwords, then you've already failed.  Key-based or "ticket-based" security is 1,000,000x more secure (if not more).
* NFS supports Kerberos.
* NFS is faster than CIFS
* NFS supports native Unix permissions and advanced features. The permissions are the same whether the storage is local OR remote. This drives me crazy about CIFS that permissions work different if you are local or remote.

But I can understand that you are frustrated today.  Before we learn how the pieces all fit together, that is common.  Once you see how it all works, CIFS seems like a toy.

That is the only question I saw. Were there other questions?

---

### Post by ronjjjg8885 on 2017-08-13
an update:

after some time that music is playing it stops and the openelec freeze until disconnected from the power and connected again.

is that because my ubuntu machine falls a sleep?

can't i tell my ubuntu to be awake until nfs isn't in use?

i will read your message later because i must to go now

---

