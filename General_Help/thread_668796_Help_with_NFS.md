---
title: "Help with NFS"
date: 2008-01-15
forum: General Help
---

### Post by cheetaux on 2008-01-15
Hi,

I have two machines running Ubuntu and am trying to get NFS up working.  For the most part, I have everthing working expect that my client does not automatically mount the shares even though I added the shares to the /etc/fstab file on the client.

Here's what I have done so far:

(1) I installed nfs-kernel-server, nfs-common, and portmap on the server

(2) I installed nfs-common and portmap on the client

(3) On the server I added the following to /etc/hosts.deny:
portmap mountd nfsd statd lockd rquotad: ALL

and I added the following to /etc/hosts.allow:
portmap mountd nfsd statd lockd rquotad: XXX.XXX.X.YYY XXX.XXX.X.ZZZ
(where XXX.XXX.X.YYY and XXX.XXX.X.ZZZ are the IP addresses of the client and server)

(4) I created a directory for sharing on the server (/home/tom/Share)

(5) On the server, I added the following to /etc/exports:
/home/tom/Share XXX.XXX.X.ZZZ(rw,sync,no_subtree_check)
(again where XXX.XXX.X.ZZZ is the IP address of the client)

(6) On the client, I exported the shares via "sudo exportfs -a"

(7) On the client, I added the following to /etc/fstab:

XXX.XX.X.XXX:/home/tom/Share /home/tom/Share nfs rw,soft,intr 0 0
(where XXX.XX.X.XXX is the IP address of the server)

However, when I boot the client, the share is not automatically mounted (I thought this would happen automatically since it is specified in the /etc/fstab file).  

If I do a "sudo mount -a", however, the share is mounted.  Why does it not happen automatically?

---

### Post by DirtDawg on 2008-01-15
Not sure if this will help, but the entry in /etc/fstab on my client machine looks like this:
XXXXXXXXX:/shared/folder /local/folder nfs rw,auto

Maybe the 'auto' setting has something to do with it? (obviously, I'm no expert ;))

---

