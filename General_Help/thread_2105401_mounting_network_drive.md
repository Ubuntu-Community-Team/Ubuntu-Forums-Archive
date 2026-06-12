---
title: "mounting network drive"
date: 2013-01-15
forum: General Help
---

### Post by heiNey on 2013-01-15
i have a question.

i have a hard drive attached to a headless server that is mounted to /mnt/usb1

i want to mount that same folder to my ubuntu computer which has plex installed.  (i'm not installing plex on that headless server because it is actually a pogoplug with arch linux arm on it, and it is very slow and doesn't handle transcoding.)

is it possible to mount it this way?  if yes, how do i go about doing it.  currently, when i browse 'network' on ubuntu, only the windows WORKGROUP shows up, and it's not able to connect even to that.  nothing else shows up and im not sure what i need to modify to make this work.  my windows computer is able to see every computer on the network and connect to them all through samba.

thanks

---

### Post by eenofonn on 2013-01-15
you could do this either with nfs or samba it really depends on what you want to do.  NFS is a better idea IMO

I'm not entirely sure how to setup the NFS stuff on arch but I'm sure if you google NFS server setup with your version of arch you should be able to find a howto.

once that's done then you'd just need to create the mount point on your Ubuntu box and mount it from there

---

### Post by eenofonn on 2013-01-15
so I decided to do the quick google for you 

[Arch Wiki NFS Server]("https://wiki.archlinux.org/index.php/NFS#Server")

once you get that done

[Ubuntu Wiki NFS Client]("https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client")

---

### Post by heiNey on 2013-01-16
> **eenofonn said:**
> so I decided to do the quick google for you 

[Arch Wiki NFS Server]("https://wiki.archlinux.org/index.php/NFS#Server")

once you get that done

[Ubuntu Wiki NFS Client]("https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client")

i think i have it set up, but when i try mounting on the client, it just hangs...doesn't seem to do anything, and i have to ctrl-c in order to get out of it.

```

root@delldesk:~# showmount -e 192.168.0.13
Export list for 192.168.0.13:
/export/usb3 192.168.0.13
/export/usb2 192.168.0.13
/export/usb1 192.168.0.13
/export      192.168.0.13

```

```
root@delldesk:~# mount -t nfs4 192.168.0.13:/usb1 /mnt/media1
^C

```

without -t nfs4 does the same thing

```

root@delldesk:~# mount 192.168.0.13:/usb1 /mnt/media1
^C

```

/etc/exports looks like:

```

# /etc/exports
#
# List of directories exported to NFS clients.  See exports(5).
# Use exportfs -arv to reread.
#
# Example for NFSv2 and NFSv3:
#  /srv/home       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
#  /srv/nfs4       hostname1(rw,sync,fsid=0)
#  /srv/nfs4/home   hostname1(rw,sync,nohide)
# Using Kerberos and integrity checking:
#  /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
#  /srv/nfs4/home   gss/krb5i(rw,sync,nohide)
#
/export 192.168.0.13(rw,fsid=0,no_subtree_check,async,no_root_squash)
/export/usb1    192.168.0.13(rw,no_subtree_check,async,no_root_squash)
/export/usb2    192.168.0.13(rw,no_subtree_check,async,no_root_squash)
/export/usb3    192.168.0.13(rw,no_subtree_check,async,no_root_squash)

```

---

### Post by eenofonn on 2013-01-16
what command are you issuing to mount it?

Also you can run a 
```

showmount -e ip-of-server

```

to give you the mount point if you have that wrong for some reason

---

### Post by heiNey on 2013-01-16
> **eenofonn said:**
> what command are you issuing to mount it?

Also you can run a 
```

showmount -e ip-of-server

```

to give you the mount point if you have that wrong for some reason

i edited my previous reply, but

```

root@delldesk:/# showmount -e 192.168.0.13
Export list for 192.168.0.13:
/export/usb3 192.168.0.13
/export/usb2 192.168.0.13
/export/usb1 192.168.0.13
/export      192.168.0.13

```
```

root@delldesk:/# mount 192.168.0.13:/usb1 /mnt/media1
^C

```

and

```

root@delldesk:/# mount -t nfs4 192.168.0.13:/usb1 /mnt/media1
^C

```

do the same thing.

---

### Post by eenofonn on 2013-01-16
Looks like you've got the mount point wrong, try doing it like this

```

mount -t nfs4 192.168.0.13:/export/usb1 /mnt/media1

```

Also if you didn't create the /mnt/media1 directory then it's not going to want to work

---

### Post by heiNey on 2013-01-16
> **eenofonn said:**
> Looks like you've got the mount point wrong, try doing it like this

```

mount -t nfs4 192.168.0.13:/export/usb1 /mnt/media1

```

Also if you didn't create the /mnt/media1 directory then it's not going to want to work

the folders already exist

```

root@delldesk:/# ls /mnt
media1  media2  media3
root@delldesk:/# mount -t nfs4 192.168.0.13:/export/usb1 /mnt/media1
^C
root@delldesk:/#

```

still same thing...hmm.

---

### Post by eenofonn on 2013-01-16
have you tried configuring it for nfs3 I'm not really familiar with v4

---

### Post by heiNey on 2013-01-16
> **eenofonn said:**
> have you tried configuring it for nfs3 I'm not really familiar with v4

the article you linked to was for nfs4.  this is actually the first time i've used nfs, and i'm not really sure what the difference would be in terms of configuration.

---

### Post by eenofonn on 2013-01-16
Sorry I didn't see that I just saw the comments in the config file for nfs3

also not seeing anything for fsid which I think you need to set up because you're mounting a different file system

edit- Pay not attention to the fsid thing... I had misread that. Idk I'm out of ideas for you here, You could try to do it via samba but you've got a lot of options to consider if you're doing it that way

---

### Post by heiNey on 2013-01-16
thanks for the help anyway.

guess i'll wait to see if anyone else has any ideas.

---

### Post by eenofonn on 2013-01-16
Yeah bummer deal :(

---

### Post by eenofonn on 2013-01-16
Oh I just realized you can change the Title of the Thread so maybe changing it to include something about nfs v4 might attract the right help :)

---

### Post by heiNey on 2013-01-16
what i dont understand is why the arch linux box doesnt show up under 'network'.  shouldn't it at least show up when i try to browse the network?

---

### Post by eenofonn on 2013-01-16
I don't think I've ever seen NFS advertised on a network. Are you talking about on a windows client?

---

### Post by bab1 on 2013-01-16
> **heiNey said:**
> what i dont understand is why the arch linux box doesnt show up under 'network'.  shouldn't it at least show up when i try to browse the network?

NFS does not announce its exports.  Browsing the network is a Windows thing that Samba provides for Unix like OS's.  If you need to browse shares then you need to use Samba.

---

### Post by heiNey on 2013-01-16
> **eenofonn said:**
> I don't think I've ever seen NFS advertised on a network. Are you talking about on a windows client?

> **bab1 said:**
> NFS does not announce its exports.  Browsing the network is a Widows thing that Samba provides for Unix like OS's.  If you need to browse shares then you need to use Samba.

no, i'm talking about browsing 'network' from nautilus.

---

### Post by bab1 on 2013-01-16
> **heiNey said:**
> no, i'm talking about browsing 'network' from nautilus.
And I'm telling you that you can't *browse * NFS exports.  

You can browse Samba shares, but not NFS exports. The ability to browse is a SMB/CIFS (Windows) thing (e.g Network >> Browse in Nautilus).

In fact NFS was designed to be seamless in the file system.  Most enterprise Linux networks use NFS to export the users home directory.  This allows the user to log in on any workstation and have their same working environment.  The Linux way of roaming profiles.  :-)

---

### Post by steeldriver on 2013-01-16
I haven't read the thread thoroughly and I don't have experience with nfs4, but in the past when I have had hangs/timeouts with nfs it has been related to portmapper / rpcbind - either not running or blocked by firewall or hosts.deny - you might want to use rpcinfo to take a look at what rpc services are visible as well as showmount

---

