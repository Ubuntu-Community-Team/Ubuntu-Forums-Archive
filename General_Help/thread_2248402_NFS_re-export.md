---
title: "NFS re-export"
date: 2014-10-14
forum: General Help
---

### Post by kevin117 on 2014-10-14
I need help enabling re-export for my server which is acting as a NFS server and a client

nano /etc/exports:
/mnt/virtual   x.x.x.x/255.255.255.0(insecure,no_root_squash,rw)

nano /etc/fstab:
x.x.x.x:/Share2 /mnt/share02 nfs rw,hard,intr 0 0
x.x.x.x:/SHARE1 /mnt/share01 nfs rw,hard,intr 0 0


when i try to connect to it i get this in syslog
Oct 14 14:23:57 ubuntu14 rpc.mountd[1198]: authenticated mount request from x.x.x.x:908 for /mnt/virtual (/mnt/virtual)
Oct 14 14:23:57 ubuntu14 rpc.mountd[1198]: qword_eol: fflush failed: errno 22 (Invalid argument)
Oct 14 14:23:57 ubuntu14 rpc.mountd[1198]: Cannot export /mnt/virtual, possibly unsupported filesystem or fsid= required
Oct 14 14:26:01 ubuntu14 rpc.mountd[1198]: authenticated mount request from x.x.x.x:906 for /mnt/virtual (/mnt/virtual)
Oct 14 14:26:01 ubuntu14 rpc.mountd[1198]: qword_eol: fflush failed: errno 22 (Invalid argument)
Oct 14 14:26:01 ubuntu14 rpc.mountd[1198]: Cannot export /mnt/virtual, possibly unsupported filesystem or fsid= required
Oct 14 14:27:25 ubuntu14 rpc.mountd[1198]: authenticated mount request from x.x.x.x:904 for /mnt/virtual (/mnt/virtual)
Oct 14 14:27:25 ubuntu14 rpc.mountd[1198]: qword_eol: fflush failed: errno 22 (Invalid argument)
Oct 14 14:27:25 ubuntu14 rpc.mountd[1198]: Cannot export /mnt/virtual, possibly unsupported filesystem or fsid= required

---

### Post by papibe on 2014-10-14
Hi kevin117. Welcome to the forum ):P

For what I can see. you're trying to mount 'x.x.x.x:/Share2', which it is not actually exported. If you don't posted the actual content of your files, it would help a lot if you do.

Please consider that address in these ranges:
```
10.0.0.0/8 (255.0.0.0)
172.16.0.0/12 (255.240.0.0)
192.168.0.0/16 (255.255.0.0)
```
are LAN addresses (no exposed to the Internet), so there's no security risk on posting them. For instance, this is what I have:

/etc/exports on server 192.168.1.1
```
/home/user/media/Iomega 192.168.1.0/24(rw,insecure,async,no_root_squash,no_all_squash,no_subtree_check)
```
/etc/fstab on client 192.168.1.200
```
192.168.1.1:/home/user/media/Iomega /media/Iomega nfs noauto 0 0
```
Regards.

---

### Post by kevin117 on 2014-10-14
> **papibe said:**
> Hi kevin117. Welcome to the forum ):P

For what I can see. you're trying to mount 'x.x.x.x:/Share2', which it is not actually exported. If you don't posted the actual content of your files, it would help a lot if you do.

Please consider that address in these ranges:
```
10.0.0.0/8 (255.0.0.0)
172.16.0.0/12 (255.240.0.0)
192.168.0.0/16 (255.255.0.0)
```
are LAN addresses (no exposed to the Internet), so there's no security risk on posting them. For instance, this is what I have:

/etc/exports on server 192.168.1.1
```
/home/user/media/Iomega 192.168.1.0/24(rw,insecure,async,no_root_squash,no_all_squash,no_subtree_check)
```
/etc/fstab on client 192.168.1.200
```
192.168.1.1:/home/user/media/Iomega /media/Iomega nfs noauto 0 0
```
Regards.


So more background - I have a SAN which has a built in NFS server - but only can do a 15 TB share at a time - but our users would like a huge 20 TB share -- so I have this ubuntu server mounting both the NFS shares from the SAN -- share01 and share02 and then I join them togethr with mhddfs ([https://romanrm.net/mhddfs](https://romanrm.net/mhddfs))

full /etc/export:
172.16.3.200:/Art_Media_Archive02 /mnt/Art_Media_Archive02 nfs rw,hard,intr 0 0
172.16.3.200:/Art_Media_Archive /mnt/Art_Media_Archive01 nfs rw,hard,intr 0 0

df -h
172.16.3.200:/Art_Media_Archive02                         5.0T  608K  5.0T   1% /mnt/Art_Media_Archive02
172.16.3.200:/Art_Media_Archive                            15T   15T  314G  98% /mnt/Art_Media_Archive01
/mnt/Art_Media_Archive01;/root;/mnt/Art_Media_Archive02/   20T   15T  5.3T  74% /mnt/virtual

/etc/exports:
/mnt/virtual   172.16.3.0/255.255.255.0(insecure,no_root_squash,rw)

so /mnt/virtual is what I want to re-export

---

### Post by papibe on 2014-10-14
It could be the case that mhddfs does provide a UUID that nfs cam use as a filesymtem id.

Try setting your own id by using the 'fsid' option. For instance:
/etc/exports:
```
/mnt/virtual 172.16.3.0/255.255.255.0(insecure,no_root_squash,rw,**[COLOR="#FF0000"]fsid=1234[/COLOR]**)
```
1234 is just and example. Any small integer would do.

Let us know if that helps.
Regards.

---

### Post by SeijiSensei on 2014-10-14
Most of the time NFS shares cannot be re-exported because of security concerns.  Your having the rights to mount a share shouldn't enable you to export that share to others who do not have those rights.  SMB has weaker security than NFS so it may work for that protocol, but my recollection is that, as a general rule, NFS re-exports are prohibited by default.  A little browsing on the web confirms this.

---

### Post by kevin117 on 2014-10-15
> **papibe said:**
> It could be the case that mhddfs does provide a UUID that nfs cam use as a filesymtem id.

Try setting your own id by using the 'fsid' option. For instance:
/etc/exports:
```
/mnt/virtual 172.16.3.0/255.255.255.0(insecure,no_root_squash,rw,**[COLOR=#FF0000]fsid=1234[/COLOR]**)
```
1234 is just and example. Any small integer would do.

Let us know if that helps.
Regards.

seems to be working now by changing the fsid to 12

---

