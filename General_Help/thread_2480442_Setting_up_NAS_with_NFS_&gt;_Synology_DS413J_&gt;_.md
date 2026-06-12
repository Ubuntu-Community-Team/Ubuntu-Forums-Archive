---
title: "Setting up NAS with NFS &gt; Synology DS413J &gt; Unable to access dirs on NAS from PC &gt;"
date: 2022-10-30
forum: General Help
---

### Post by GeordieJedi on 2022-10-30
Hi there guys.

I was hoping that you could help me with a project please.

**Background / History:**
I have a Synology DS413J NAS device.
It was working well for many years, however a while ago It had a hard drive
failure (was in SHR / RAID-5) so I managed to retrieve my data.

I have very recently decided to set this up again from scratch and bought
some new HDD's (again x3, 4TB drives in SHR / RAID-5)

I am trying to set up the mount points, but I'm struggling.

**Additional Information:**
I use Linux (Ubuntu 20.04 LTS) as my desktop OS
hoth = Synology NAS
corellia = Desktop PC


**Steps already taken:**

01. Set up a static ip (via DHCP reservation) address for my NAS

1.2. Set up a static ip (via DHCP reservation) address for my client PC

1.3. (On the NAS)
Added both the NAS and the client PC to the hosts file
Added both the NAS and the client PC to the hosts.allowed file

1.4. (On the client PC)
Added both the NAS and the client PC to the hosts file
Added both the NAS and the client PC to the hosts.allowed file

1.5. (On the NAS)
Added both the NAS and the client PC to the exports file


02. I have added mount points for the NAS in my fstab file on my client PC
(corellia) (see below):

fstab (on client PC) =

```
#
hoth:/volume1/videos /mnt/video_share/video nfs
nouser,atime,auto,rw,dev,exec,suid 0 0
#
hoth:/volume1/photos /mnt/photo_share/photo nfs
nouser,atime,auto,rw,dev,exec,suid 0 0
#
hoth:/volume1/music /mnt/music_share/music nfs
nouser,atime,auto,rw,dev,exec,suid 0 0
#
```


03. The network shares now show up on my desktop (Dolphin in KDE)
However, when clicking on the dirs to access them.
I recieve the following error messages:

3.1.
```
"Could not enter folder /mnt/photo_share/photo."
```

3.2. Or the new error mesage:
```
"An error occurred while accessing '/volume1/photos on hoth', the system responded: mount: /mnt/photo_share/photo: operation permitted for root only."
```


So this now appears to be a permissions issue (from the NAS side of things)
 

04. Interestingly I tried an experiment -

(On the client PC)
I su'd to a root shell, then cd'd into the dir (on the NAS)
and I was able to access the NAS and its dirs via the shell prompt

4.1. (On the NAS - via DSM / in the NAS GUI) I created a test dir (called test_01)
in volume1/videos/

4.2. (On the client PC) I then re-ran the ls command, and the test dir appeard


05. (On the client PC) I have then run the following command:

```
showmount -e hoth
```

Here are the results:

```
/volume1/music corellia.home
/volume1/photos corellia.home
/volume1/videos corellia.home
```

This looks promising, hoever the .home at the end of the hostname of the
PC (corellia), looks a bit strange to my eyes.


06. (On the NAS) Here are the results of my exports list:

```
/volume1/videos
corellia(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,
anonuid=1025,anongid=100)

/volume1/photos
corellia(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,
anonuid=1025,anongid=100)

/volume1/music
corellia(rw,async,no_wdelay,crossmnt,no_root_squash,insecure_locks,sec=sys,
anonuid=1025,anongid=100)
```

 

07. (On the client PC) I ran:

```
sudo mount -a 
```

Output:
```
mount: 0: mount point does not exist.
mount: 0: mount point does not exist.
mount: 0: mount point does not exist.
```

 

08. The permissions for the dirs are as follows:

8.1. /mnt/photo_share/photo = root
8.2. /mnt/music_share/music = [my username]
8.3. /mnt/video_share/video = root

8.4. Interestingly, for both root and [my username] when I look at the access
permissions, I see the following:

user: no access
group: no access
others: no access

However, when I created the mount points for these dirs
I did perform a sudo chown -R [my username] : [my username] on each of the 3
dirs.


09. (On the client) I ran the following command:
```
ls -l /mnt 
```

Result was:
```
drwxr-xr-x 3 755 [my username] 4096 Oct 23 12:22 music_share
drwxr-xr-x 3 [my username] [my username] 4096 Oct 23 12:22 photo_share
drwxr-xr-x 3 755 [my username] 4096 Oct 23 12:22 video_share
```

 

10. (On the NAS) Running the following command:
```
ps aux | grep nfsd 
```

Gave me this result:

```
root 6578 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd4]
root 6580 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6581 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6583 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6585 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6587 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6589 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6591 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6595 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6599 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6601 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6604 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6605 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6606 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6607 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6608 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 6609 0.0 0.0 0 0 ? S 13:52 0:00 [nfsd]
root 20164 0.0 0.1 4756 952 pts/1 S+ 18:40 0:00 grep nfsd
```


Would that mean the nfs deamon is running correctly on the NAS ?


14. (On the client PC) Running the following command:
```
mount | grep nfs
```

Result:
```
nfsd on /proc/fs/nfsd type nfsd (rw,relatime)
hoth:/volume1/music on /mnt/music_share/music type nfs
(rw,relatime,vers=3,rsize=131072,wsize=131072,namlen=255,hard,proto=tcp,timeo=
600,retrans=2,sec=sys,mountaddr=192.168.1.138,mountvers=3,mountport=892,
mountproto=udp,local_lock=none,addr=192.168.1.138)

hoth:/volume1/photos on /mnt/photo_share/photo type nfs
(rw,relatime,vers=3,rsize=131072,wsize=131072,namlen=255,hard,proto=tcp,timeo=
600,retrans=2,sec=sys,mountaddr=192.168.1.138,mountvers=3,mountport=892,
mountproto=udp,local_lock=none,addr=192.168.1.138)

hoth:/volume1/videos on /mnt/video_share/video type nfs
(rw,relatime,vers=3,rsize=131072,wsize=131072,namlen=255,hard,proto=tcp,timeo=
600,retrans=2,sec=sys,mountaddr=192.168.1.138,mountvers=3,mountport=892,
mountproto=udp,local_lock=none,addr=192.168.1.138)
```

 

**Questions:**

1. How do I create a mount point (on the client PC) to allow it to see / access
the NAS box ?

2. How can I alter the permissions (on the NAS) to allow me to mount
and access the NAS and its files ?

3. What other steps do I need to do, in order to get this to work ?

 

TIA for any help or advice

 

**Useful details:**

NAS: Synology DS413J
NAS OS: DSM 6.2.4-25556

PC details:
OS: Ubuntu 20.04 LTS
OS type: 64-bit
DE: KDE 5.18.8
Kernel: 5.14.0-1051-oem
CPU: 4x Intel Core-2 Q8200 (@2.33 Ghz)
GFX: Intel HD
RAM: 8GB

---

### Post by TheFu on 2022-10-30
Most of the question seems to be on the NAS side.  Follow the instructions for the NAS to export the shares you want.

On the client side, the nfs mounts in the /etc/fstab should be mounted at reboot automatically, or after running 
'sudo mount -a'

There are a few options that I would never use on a NFS device - like dev and suid, but if you have to good reason, go for it.
Don't use a GUI to mount things. That's a completely different sort of mount and won't cause NFS to be used.  Most likely, it will use webdav or CIFS, which should be avoided if you have a real NAS.

On the client, 
$ showmount -e {remote IP}

Will show the exported shares from the NFS server.  The remote IP can be the hostname, if DNS is working or /etc/hosts is setup on the client.

BTW, the post above shows the /etc/fstab mounts using multiple lines. This isn't allowed.  1 line for 1 mount.  Period.

If it were me, I'd use
```
hoth:/volume1/music      /mnt/music     nfs    nconnect=2,proto=tcp,rw,async,nodev,nosuid     0       0
```
These are NFSv4.1 and later options.  proto=tcp should be the default.  Same for rw.  Allosing suid and dev files to be placed on NFS is a security failure.  I do allow getgid, since it is very useful for having multiple accounts working in the same directories.

The client only needs a static IP if you use IPs to limit access.  I think you should and I think all non-portable systems on a network should have static IPs for many reasons.  For desktops/servers, the static IPs should be manually configured on the box.  For portable devices, say laptops and phones/tablets, dhcp reservations is the least evil method that works.

---

### Post by GeordieJedi on 2022-10-31
I've managed to resolve this.

It was a permissions problem (on the NAS)

I had to change the "Squash" settings to: "Map all users to Admin"
This is what allowed my to access the NAS shared folders on the client.

15. Here are the setps I took to fix it:

(On the NAS)
Log into the web interface > Control panel > Shared folder > (Chose the folder you want to
allow access to from a client).
Edit > NFS permissions > Chose host > Edit > Select the option called "Squash" >
Chose - Map all users to Admin > OK > (Wait for this to be saved)

---

