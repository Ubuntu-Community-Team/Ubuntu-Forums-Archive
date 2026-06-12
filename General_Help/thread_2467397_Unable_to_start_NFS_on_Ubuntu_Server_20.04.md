---
title: "Unable to start NFS on Ubuntu Server 20.04"
date: 2021-09-25
forum: General Help
---

### Post by orsty9001 on 2021-09-25
Trying to setup a new file server. This is all a clean install on new hardware. Just installed nfs-server and I'm getting an error when I start it. 

```
Sep 25 13:47:59 kernel: nfsd: unable to allocate nfsd_file_hashtbl
Sep 25 13:47:59 rpc.nfsd[797860]: error starting threads: errno 12 (Cannot allocate memory)
Sep 25 13:47:59 systemd[1]: nfs-server.service: Main process exited, code=exited, status=1/FAILURE
-- Subject: Unit process exited
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- An ExecStart= process belonging to unit nfs-server.service has exited.
-- 
-- The process' exit code is 'exited' and its exit status is 1.
Sep 25 13:47:59 treatbox systemd[1]: nfs-server.service: Failed with result 'exit-code'.
-- Subject: Unit failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support

```

Sytem has 16gb of ram and a new hard drive for the system drive. I've tried purging all the related software and reinstalling everything NFS requires. And just to be sure I rebooted. Nost sure where to go from here. Any help would be appreciated.

---

### Post by TheFu on 2021-09-26
[https://askubuntu.com/questions/1286659/nfs-wont-start-after-upgrade-to-20-04](https://askubuntu.com/questions/1286659/nfs-wont-start-after-upgrade-to-20-04) says:
>  Re-installed all of the nfs packages, rpcbind, etc., rebooted, and the NFS shares are now available.

Is the server on hardware or in a container/VM?
Showing your /etc/exports could help too.


[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04) seems pretty straight forward.
I don't have any 20.04 NFS servers, but I've been using it for decades with prior releases ... going back into the 1990s.

NFSv4 without Kerberos sorta "just works".

---

### Post by orsty9001 on 2021-09-26
It's always just worked for me in the past as well. 

It's on a standalone box. No VM. I just tried reinstall all packages related to NFS again. Also rebooting after that with no luck. I get the same error. 

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
/srv/nfs4/Storage       192.168.1.0/24(rw,sync,no_subtree_check)

---

### Post by TheFu on 2021-09-26
I just spent the last 30 minutes trying to setup a 20.04 nfs-server and failed.  I didn't have the same issue you did, but moved through different 2 failures and solutions. The 3rd failure, I couldn't figure out.  

Sorry.

```
$ systemctl list-dependencies nfs-server.service 
nfs-server.service
&#9679; &#9500;&#9472;auth-rpcgss-module.service
&#9679; &#9500;&#9472;nfs-config.service
&#9679; &#9500;&#9472;nfs-idmapd.service
&#9679; &#9500;&#9472;nfs-mountd.service
[COLOR="#FF0000"]&#9679; &#9500;&#9472;proc-fs-nfsd.mount[/COLOR]
&#9679; &#9500;&#9472;rpc-svcgssd.service
&#9679; &#9500;&#9472;rpcbind.socket
&#9679; &#9500;&#9472;system.slice
&#9679; &#9492;&#9472;network.target

```
proc-fs-nfsd.mount is failing to start and there are apparmor errors.

```
[  217.471423] audit: type=1400 audit(1632714651.443:116): apparmor="DENIED" operation="mount" info="failed type match" error=-13 profile="lxd-back-2004_</var/snap/lxd/common/lxd>" name="/proc/fs/nfsd/" pid=8290 comm="mount" fstype="nfsd" srcname="nfsd"
```
I've already relaxed the mount for nfs and made the container privileged (ouch).

```
$ showmount -e
clnt_create: RPC: Program not registered
```

Anyways, yet another reason I haven't moved to 20.04.  BTW, this machine is an NFS client and that **was** working before I started screwing around to make it an nfs-server tonight. ;)

---

### Post by orsty9001 on 2021-09-28
I figured it out. This system has a raid of standard mechanical drives and an NVME ssd installed on a PCI-E adapter card. Ubuntu is installed on a 2.5&#8221; SATA drive. This motherboard will not boot from an NVME drive. Or at least this NVME drive. It will not show up in the bios. It&#8217;s configured to be the cache drive for the RAID. Honestly I don&#8217;t thing it would need it but it&#8217;s what they wanted. Anyway, the Ubuntu installer placed some of its folders on that NVME drive. Grub was installed on the SATA drive but told to boot from that cache drive. Not sure how that happened or how it booted. Also not sure how it didn&#8217;t break the raid or it&#8217;s ability to boot after it set the raid up they way they wanted. I rebuilt Ubuntu on the SATA ssd. Fixed grub but setting it not to look at that NVME drive to boot and wiped that NVME drive. Rebooted and now NFS works. 

My assumption is this machine has an uncommon setup the Ubuntu server installer couldn&#8217;t make sense of. I honestly didn&#8217;t know that NVME drive was installed until I took the top off this sever.

---

### Post by TheFu on 2021-09-28
Sometimes updating the NVMe firmware will help with boot and other issues.  I've never done it, as I don't have any NVMe installed (have one on my desk waiting for a new system build).

---

