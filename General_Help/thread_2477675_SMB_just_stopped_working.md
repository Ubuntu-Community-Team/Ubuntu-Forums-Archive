---
title: "SMB just stopped working"
date: 2022-08-03
forum: General Help
---

### Post by dea27 on 2022-08-03
New to the forum, and not an Ubuntu expert by any stretch.

I have an smb share which I have auto mounted via fstab.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=94e84067-63b9-43d5-b514-bcaa41b20ecc /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A598-62FF  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
#Mounting Network Directory
//Gateway/Share /home/mnt/media cifs rw,_netdev,vers=1.0,user=WORKGROUP/user,password=password,uid=1000,gid=100 0 0

```
Everything has been working fine for the last two years, until the other day when it just stopped mounting.

dmesg output:

```
[ 6281.686382] CIFS: VFS: Use of the less secure dialect vers=1.0 is not recommended unless required for access to very old servers
[ 6281.686397] CIFS: Attempting to mount \\Gateway\Share
[ 6281.704836] CIFS: VFS: \\Gateway failed to connect to IPC (rc=-6)
[ 6281.706721] CIFS: VFS: cifs_mount failed w/return code = -6
user_machine:~$ client_loop: send disconnect: Connection reset
```

I have enabled NT1 in my samba.conf

I have even played around with fstab and different versions of SMB (output below) with some success, but still won't mount and a different error code.

```
[ 1483.205310] CIFS: Attempting to mount \\Gateway\Share
[ 1483.215205] CIFS: VFS: cifs_mount failed w/return code = -112

```

My hdd that I use is connected directly to the router and is used by both Ubuntu and Windows 10 machines. Windows 10 is working fine.

My Router seems to only support SMBv1.

It just stopped working, no updating, playing around, I've let it sit and it just works, so I am absolutely lost, and tried multiple things from forums without success.

I can even manually mount it by connecting via other locations smb://gateway/share and it works fine and I can see all of my files.

Would really appreciate if an ubuntu guru can help.

Thanks

---

### Post by deadflowr on 2022-08-03
*Thread moved to **General Help***

---

### Post by ActionParsnip on 2022-08-03
If you ping Gateway, does it resolve to an IP OK?

Can you telnet to port 445 on the "gateway" box from the client system? Does this work OK?

Do you have a firewall on the "gateway" system? Is it allowing the CIFS traffic? Do you have a configured firewall on the Ubuntu system? Is this allowing the CIFS traffic out as well?

---

### Post by rsteinmetz70112 on 2022-08-03
Have you checked to see if the Windows 10 machine(s) have SMB 1 enabled?

---

### Post by dea27 on 2022-08-03
Yes it does.
ping mygateway
PING mygateway.gateway (IPMasked) 56(84) bytes of data.
64 bytes from mygateway (IPMasked): icmp_seq=1 ttl=64 time=1.64 ms
64 bytes from mygateway (IPMasked): icmp_seq=2 ttl=64 time=0.523 ms
64 bytes from mygateway (IPMasked): icmp_seq=3 ttl=64 time=0.571 ms

I can also telnet to my gateway on 445, and also ran a nmap and can see it's open.
nmap gateway
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2022-08-04 13:07 AEST
Nmap scan report for mygateway (IPMasked)
Host is up (0.00047s latency).
Not shown: 844 closed ports, 148 filtered ports
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
8443/tcp  open  https-alt
9000/tcp  open  cslistener
49153/tcp open  unknown


nmap client-pc (this pc)
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2022-08-04 13:09 AEST
Nmap scan report for client-pc (IPMasked)
Host is up (0.00013s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1137/tcp open  trim

Local pc firewall is inactive.
client-pc:~$ sudo ufw status
Status: inactive



No firewall on the gateway. Just in case it was, I have allowed ports 137,138,139,445 through for testing, and still no good.

Sounding very buggy now, but I am going to upgrade Ubuntu and see if it fixes the problems, but I would be interested on your feedback from the above, really appreciate it.

Thanks

---

### Post by dea27 on 2022-08-03
Yes, they're enabled.
SMB 1.0/CIFS Server wasn't, but I enabled it today, still no good.

I even rolled back updates on the Windows box, nothing. Everything is still working from the windows machine as well.

Ubuntu just won't mount my hdd connected to the router.

Cheers

---

### Post by ActionParsnip on 2022-08-04
With a TTL of 64 are you sure it's Windows? Windows gives something around the 128 mark or are there a lot of network segments between?

---

### Post by dea27 on 2022-08-04
> **ActionParsnip said:**
> With a TTL of 64 are you sure it's Windows? Windows gives something around the 128 mark or are there a lot of network segments between?

No sorry, the hdd is connected directly to my router, Windows isn't at play.
64 seems to be the default inside my network, regardless of what I ping.

---

### Post by ActionParsnip on 2022-08-04
Can you mount the remote file system using sshfs?
```

sudo apt install sshfs
sudo sshfs -o allow_other,default_permissions user@mygateway:~/ /home/mnt/media

```

If you can find out the mount point of the storage on the device then you can mount that instead. The command above just mounts the user's $HOME on the mygateway box

---

### Post by dea27 on 2022-08-04
> **ActionParsnip said:**
> Can you mount the remote file system using sshfs?
```

sudo apt install sshfs
sudo sshfs -o allow_other,default_permissions user@mygateway:~/ /home/mnt/media

```

If you can find out the mount point of the storage on the device then you can mount that instead. The command above just mounts the user's $HOME on the mygateway box


Yeah, that won't work, my home network router doesn't accept sshfs requests.

I'm just completely stumped.

---

### Post by ActionParsnip on 2022-08-04
> **dea27 said:**
> Yeah, that won't work, my home network router doesn't accept sshfs requests.

I'm just completely stumped.

Weird. It's running SSH but I guess the service is configured not to allow SSHFS (not sure if that's possible) but it's software so why not huh :-)

---

### Post by TheFu on 2022-08-04
Looks like a name resolution issue. Use the IP address instead.  You may have edited the posts a little too much, but it appears that the command is using "Gateway", not "mygateway". This would be an error.  Still, servers, especially storage servers need to have static IPs for a number of reasons.

```
//Gateway/Share /home/mnt/media cifs rw,_netdev,vers=1.0,user=WORKGROUP/user,password=password,uid=1000,gid=100 0 0
```
Some of this seem odd.    The gid probably needs to be 1000, not 100, unless you've added your userids to the 'user' unix group.  That isn't the default on Ubuntu ... though I agree that it should be.

When mounting, use the verbose option to see errors.
```
sudo mount    -t cifs     -vvv      -o rw,_netdev,vers=1.0,user={user},password={password},uid=1000,gid=1000        /{IP address}/Share       /home/mnt/media
```
BTW, I think snap packages won't be able to access that location, but I agree that not using /media/ is a good idea. I've been burned when multiple mount tools attempt to share the same mount directory.  Just be certain it isn't under any userid's $HOME directory.  That causes even worse issues, as we've seen in these forums a few times.

However, using a WAN router for storage access has been a bad idea for the last 15 yrs.  Bugs have happened, repeatedly, making the storage available to the world.  Beware.  Google about hacked routers with storage.  The list is long and well-know. Pretty much every regarded brand was hit with the same issue, multiple times, as the attempt to fix it failed.  Just so much easier to NOT use the feature, IMHO.

If you don't have a good reason for using SMB1, please, please, use at least SMB 2.1 (Win7). There are security and performance improvements.
And if Windows isn't involved at all, don't use CIFS/SMB at all. Use NFS, the native network file system for Unix systems, like OSX and Linux.

---

