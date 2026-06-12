---
title: "File Sharing - nfs-kernel-server - Service Won't Start"
date: 2021-03-29
forum: General Help
---

### Post by Alan5127 on 2021-03-29
Hi All,

I have an Ubuntu Server (20.04.2 LTS) that is sharing one of its drives on my network.

It was all working fine, but after a reboot, I could not connect from a remote machine.

I checked the server, and specifically, I found this:

```
$ sudo systemctl restart nfs-kernel-server

A dependency job for nfs-server.service failed. See 'journalctl -xe' for details.
```

```
$ systemctl list-dependencies nfs-kernel-server

nfs-kernel-server.service    

[color=green]&#9679;[/color] &#9500;&#9472;-.mount  
&#9679; &#9500;&#9472;auth-rpcgss-module.service  
[color=red]&#9679;[/color] &#9500;&#9472;media-D_Data.mount 
&#9679; &#9500;&#9472;nfs-config.service 
&#9679; &#9500;&#9472;nfs-idmapd.service 
&#9679; &#9500;&#9472;nfs-mountd.service 
[color=green]&#9679;[/color] &#9500;&#9472;proc-fs-nfsd.mount 
&#9679; &#9500;&#9472;rpc-svcgssd.service 
[color=green]&#9679;[/color] &#9500;&#9472;rpcbind.socket 
[color=green]&#9679;[/color] &#9500;&#9472;system.slice 
[color=green]&#9679;[/color] &#9492;&#9472;network.target 
```

Maybe difficult to tell from that, but this line:

media-D_Data.mount

has a red dot next to it.  

The ones that are shown above with a green dot, have a green dot, and the ones above with a black dot, are shown on my screen as white dots (since the terminal background is black).

/media/D_Data is the drive that is being shared.  

However, I can read that drive (from the server console) no problem with, for example:  

ls -la /media/D_Data 

Using the serve console, I can also 'touch' a new file there fine.   

Not sure how to proceed to work out what the issue is?  

Thanks,  

Alan.

---

### Post by HermanAB on 2021-03-30
Usually, the issue is that the network is still down when nfsd tries to start.  If you can start it manually when the system is up and running, that kind of proves it and then you could move the nfsd startup to rc.local to ensure that it is the last thing in the startup list.

---

### Post by Alan5127 on 2021-03-30
Hi HermanAB,

> **HermanAB said:**
> Usually, the issue is that the network is still down when nfsd tries to start.  If you can start it manually when the system is up and running, that kind of proves it and then you could move the nfsd startup to rc.local to ensure that it is the last thing in the startup list.

That was actually my first thought too, but even after waiting for hours (literally!) it still fails to start:

```
$ sudo systemctl restart nfs-kernel-server

A dependency job for nfs-server.service failed. See 'journalctl -xe' for details.
```

The network is definitely up and running for the server - I ran the above command from my desktop machine over SSH :-)


Alan.

---

### Post by HermanAB on 2021-03-30
So what does 'journalctl -xe' say?

[https://wiki.archlinux.org/index.php/NFS/Troubleshooting](https://wiki.archlinux.org/index.php/NFS/Troubleshooting)

---

### Post by TheFu on 2021-03-30
How is /media/D_Data mounted?  fstab?
Which file system does it have?

I've had the problem when the nfs helper daemons got started in the wrong order.  shut them all down, then start them in the correct order, /usr/sbin/rpc.idmapd first, then rpcbind and finally the nfs stuff.

Seems that systemd dependencies aren't quite correct, but are close enough that the timing problem seldom happens .

---

### Post by Alan5127 on 2021-03-30
Hi HermanAB,

> **HermanAB said:**
> So what does 'journalctl -xe' say?

This is everything output from 'journalctl -xe' from the point of entering the 'systemctl restart nfs-kernel-server' command:

```
Mar 31 08:27:03 servername sudo[6657]: pam_unix(sudo:auth): Couldn't open /etc/securetty: No such file or directory
Mar 31 08:27:06 servername sudo[6657]: pam_unix(sudo:auth): Couldn't open /etc/securetty: No such file or directory
Mar 31 08:27:06 servername sudo[6657]: alan : TTY=pts/0 ; PWD=/home/alan ; USER=root ; COMMAND=/usr/bin/systemctl restart nfs-kernel-server
Mar 31 08:27:06 servername sudo[6657]: pam_unix(sudo:session): session opened for user root by alan(uid=0)
Mar 31 08:27:06 servername systemd[1]: Condition check resulted in Kernel Module supporting RPCSEC_GSS being skipped.
-- Subject: A start job for unit auth-rpcgss-module.service has finished successfully
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit auth-rpcgss-module.service has finished successfully.
-- 
-- The job identifier is 4938.
Mar 31 08:27:06 servername systemd[1]: media-D_Data.mount: Directory /media/D_Data to mount over is not empty, mounting anyway.
-- Subject: Mount point is not empty
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The directory /media/D_Data is specified as the mount point (second field in
-- /etc/fstab or Where= field in systemd unit file) and is not empty.
-- This does not interfere with mounting, but the pre-exisiting files in
-- this directory become inaccessible. To see those over-mounted files,
-- please manually mount the underlying file system to a secondary
-- location.
Mar 31 08:27:06 servername systemd[1]: Mounting /media/D_Data...
-- Subject: A start job for unit media-D_Data.mount has begun execution
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit media-D_Data.mount has begun execution.
-- 
-- The job identifier is 4829.
Mar 31 08:27:06 servername systemd[1]: Starting Preprocess NFS configuration...
-- Subject: A start job for unit nfs-config.service has begun execution
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit nfs-config.service has begun execution.
-- 
-- The job identifier is 4934.
Mar 31 08:27:06 servername mount[6670]: Mount is denied because the NTFS volume is already exclusively opened.
Mar 31 08:27:06 servername mount[6670]: The volume may be already mounted, or another software may use it which
Mar 31 08:27:06 servername mount[6670]: could be identified for example by the help of the 'fuser' command.
Mar 31 08:27:06 servername sudo[6657]: pam_unix(sudo:session): session closed for user root
Mar 31 08:27:06 servername systemd[1]: media-D_Data.mount: Mount process exited, code=exited, status=16/n/a
-- Subject: Unit process exited
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- An n/a= process belonging to unit media-D_Data.mount has exited.
-- 
-- The process' exit code is 'exited' and its exit status is 16.
Mar 31 08:27:06 servername systemd[1]: media-D_Data.mount: Failed with result 'exit-code'.
-- Subject: Unit failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The unit media-D_Data.mount has entered the 'failed' state with result 'exit-code'.
Mar 31 08:27:06 servername systemd[1]: Failed to mount /media/D_Data.
-- Subject: A start job for unit media-D_Data.mount has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit media-D_Data.mount has finished with a failure.
-- 
-- The job identifier is 4829 and the job result is failed.
Mar 31 08:27:06 servername systemd[1]: Dependency failed for NFS server and services.
-- Subject: A start job for unit nfs-server.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit nfs-server.service has finished with a failure.
-- 
-- The job identifier is 4825 and the job result is dependency.
Mar 31 08:27:06 servername systemd[1]: Dependency failed for NFS Mount Daemon.
-- Subject: A start job for unit nfs-mountd.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit nfs-mountd.service has finished with a failure.
-- 
-- The job identifier is 4931 and the job result is dependency.
Mar 31 08:27:06 servername systemd[1]: nfs-mountd.service: Job nfs-mountd.service/start failed with result 'dependency'.
Mar 31 08:27:06 servername systemd[1]: Dependency failed for NFSv4 ID-name mapping service.
-- Subject: A start job for unit nfs-idmapd.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit nfs-idmapd.service has finished with a failure.
-- 
-- The job identifier is 4936 and the job result is dependency.
Mar 31 08:27:06 servername systemd[1]: nfs-idmapd.service: Job nfs-idmapd.service/start failed with result 'dependency'.
Mar 31 08:27:06 servername systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
Mar 31 08:27:06 servername systemd[1]: nfs-config.service: Succeeded.
-- Subject: Unit succeeded
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The unit nfs-config.service has successfully entered the 'dead' state.
Mar 31 08:27:06 servername systemd[1]: Finished Preprocess NFS configuration.
-- Subject: A start job for unit nfs-config.service has finished successfully
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit nfs-config.service has finished successfully.
-- 
-- The job identifier is 4934.
Mar 31 08:27:06 servername systemd[1]: Condition check resulted in RPC security service for NFS client and server being skipped.
-- Subject: A start job for unit rpc-gssd.service has finished successfully
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit rpc-gssd.service has finished successfully.
-- 
-- The job identifier is 4939.
Mar 31 08:27:06 servername systemd[1]: Condition check resulted in RPC security service for NFS server being skipped.
-- Subject: A start job for unit rpc-svcgssd.service has finished successfully
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit rpc-svcgssd.service has finished successfully.
-- 
-- The job identifier is 4940.


```

I am guessing that the mounting 'errors' are due to the fact that the share is already mounted, but that was always the case, so nothing has changed there.


> **HermanAB said:**
> [https://wiki.archlinux.org/index.php/NFS/Troubleshooting](https://wiki.archlinux.org/index.php/NFS/Troubleshooting)

The very first line says to remove spaces from /etc/exports.  I forgot, but I did actually make a change to that a few days ago, prior to the reboot, but I just checked and there does not *appear* to be any extraneous spaces in there.  This is what /etc/exports contains:

```
$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/media/D_Data     172.25.25.0/24(rw,sync,no_subtree_check)
$
```

There were five spaces between 'D_Data' and '172' so I removed all five, and replaced with one new space (just in case of a weird character or something).  I then ran:

[code]sudo exportfs -ra  &&  sudo systemctl restart nfs-kernel-server.service]/code]

but I still got the same 'dependency' error as before.

Is there any way to 'validate' /etc/exports?

If that is not the issue, I'm going to work through that exhaustively, but nothing 'appears' to be hitting the symptoms?  This is, I am guessing, a server-side issue (since the service won't start), and none of the server-side on that page seem to relate on the face of it?




Thanks,

Alan.

---

### Post by Alan5127 on 2021-03-30
Hi TheFu,

> **TheFu said:**
> How is /media/D_Data mounted?  fstab?

Yes - this is the line in fstab:

```
UUID=65060ef6-115f-4551-b8b2-721766358216	/media/D_Data		ntfs-3g		defaults          		0       0
```


> **TheFu said:**
> Which file system does it have?

NTFS - this wasn't causing an problems up until now.

> **TheFu said:**
> I've had the problem when the nfs helper daemons got started in the wrong order.  shut them all down, then start them in the correct order, /usr/sbin/rpc.idmapd first, then rpcbind and finally the nfs stuff.

Seems that systemd dependencies aren't quite correct, but are close enough that the timing problem seldom happens .

Okay - how should I do that?

Would this be correct:

```


systemctl stop *nfs*
systemctl stop rpcbind
systemctl stop rpc.idmapd

systemctl start rpc.idmapd
systemctl start rpcbind
systemctl start *nfs*


```


I was checking the names / ways to access the services to post the above, and found this:

```


$ systemctl status rpc.idmapd

Unit rpc.idmapd.service could not be found.


```

Is that a (or the) problem, or is that expected?


Thanks,

Alan.

---

### Post by TheFu on 2021-03-30
ntfs changes everything. I've never used it with nfs. To me, that would completely defeat the reasons to use nfs.
*no_root_squash* seems to be necessary for ntfs exports.  Found that suggestion in these forums. Something about ntfs lacking posix support.

---

### Post by Alan5127 on 2021-03-30
Hi TheFu,

> **TheFu said:**
> ntfs changes everything. I've never used it with nfs. To me, that would completely defeat the reasons to use nfs.
*no_root_squash* sees to be necessary for ntfs exports.  Found that suggestion in these forums. Something about ntfs lacking posix support.

I didn't set it up originally myself (maybe there is some strangeness going on somewhere that I am not aware of), and I've actually been meaning to get rid of that NTFS drive, and replace it with a standard Ext4 one for a while now - maybe this is the kick up the rear that I've needed!

I think what I'll do is:

Attach a new drive and format it to Ext4
Rsync everything over - that whole drive is just static data that is backed up many times anyway, and permissions are a bit of a non-issue for it
Remove the old NTFS drive
Once the new Ext4 drive is working okay for a month (or whatever), I'll wipe the NTFS drive and it can become a spare

I can start that (rsync) right now - performance won't be an issue, and have it done in a couple of hours I suspect.


Alan.

---

### Post by SeijiSensei on 2021-04-28
> -- The directory /media/D_Data is specified as the mount point (second field in
-- /etc/fstab or Where= field in systemd unit file) and is not empty.

This error is pretty clear. The directory /media/D_Data has files in it before the mount is attempted. Delete anything in the directory then try the mount again.

---

