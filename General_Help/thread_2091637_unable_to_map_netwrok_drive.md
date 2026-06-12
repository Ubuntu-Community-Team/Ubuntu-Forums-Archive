---
title: "unable to map netwrok drive"
date: 2012-12-05
forum: General Help
---

### Post by jessel on 2012-12-05
Hi,

I just got a Synology DS213air and I am having difficulty mapping a network drive. I can move files to the network drive using the web-based interface, so everything is basically set up already, I'm literally just unable to map a network drive, so it is possible for me to browse to the folder also through the network (with nautilis).

So there are a lot of differing instructions that are specific to the operating system and network type. Unfortunately, I have no prior experience with samba, cifs, or nfs. So all the setup is kind of a jumble of protocals, and I've likely installed some unecessary software packages, but thats another story. I am running Ubuntu 12.04.

I've seen these pages:
[http://forum.synology.com/wiki/index.php/Mapping_a_Network_Drive#How_to_map_a_drive_using_a_Linux.2FUnix_Environment](http://forum.synology.com/wiki/index.php/Mapping_a_Network_Drive#How_to_map_a_drive_using_a_Linux.2FUnix_Environment)
[http://askubuntu.com/questions/46183/how-to-map-a-network-drive](http://askubuntu.com/questions/46183/how-to-map-a-network-drive)
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

My objective at this point is to be able to manually mount, once I can do that I'll add the line to my fstab and I'll be happy.

jesse@computer:~$ dmesg | tail
```
[   26.307528] NVRM: drivers including, but not limited to, vesafb, may result in
[   26.307531] NVRM: corruption and stability problems, and is not supported.
[   35.048026] eth0: no IPv6 routers present
[   38.504068] CIFS VFS: Error connecting to socket. Aborting operation
[   38.504154] CIFS VFS: cifs_mount failed w/return code = -115
[   49.164041] CIFS VFS: Error connecting to socket. Aborting operation
[   49.164183] CIFS VFS: cifs_mount failed w/return code = -115
[ 4548.513526] sched: RT throttling activated
[ 4577.308065] NVRM: Xid (0000:01:00): 8, Channel 00000001
[ 4579.308028] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
```jesse@computer:~$ sudo -i

[EMAIL="root@computer:/.music"]root@computer:/.music[/EMAIL]# mount -t cifs //DiskStation/Music/ /.music -o jessePassword: 
```
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```root@computer:~# mount -t cifs //192.168.1.1/Music /.music -o guest
```
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```Thanks!

---

### Post by LewisTM on 2012-12-07
Did you try NFS? It's pretty straightforward to setup, as long as your NAS supports it.
First you need to install the NFS package
```
sudo apt-get install nfs-common
```
Then find out what your NAS shares. You need the NAS IP address.
```
showmount -e <NAS IP>
```
Finally, mount the share to your directory
```
sudo mount <NAS IP>:</share_path> /.music
```
Good luck!

---

### Post by jessel on 2012-12-09
Thanks!

That works.

---

