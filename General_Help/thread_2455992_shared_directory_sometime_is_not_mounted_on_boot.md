---
title: "shared directory sometime is not mounted on boot"
date: 2021-01-01
forum: General Help
---

### Post by alain.roger on 2021-01-01
Hi,

My NAS runs on Linux and i share some directories that i mount on my linux desktop with NFS. From time to time, my shared directories are not mounted at the boot and i do not understand why.
I previously used CIFS and now i moved to NFS. I mount the shared directories in /etc/fstab as following:
```
[FONT=monospace][COLOR=#000000]QNAP:/Homes/alain               /mnt/qnap                               nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0[/COLOR][/FONT]
```

Even if my NAS already runs and i boot my desktop computer, shared directories are not (always) automatically mounted at boot time and in this case i have to open a terminal and type: sudo mount -a
What could be the issue ?
thx

---

### Post by ajgreeny on 2021-01-01
Can you please edit the title of your thread which appears to bear no relation to the content here.

Thunderbird and fatsb have no direct connection that I can think of.

---

### Post by alain.roger on 2021-01-01
I don't know how it's possible as this is not the thread title i wrote :(

---

### Post by ajgreeny on 2021-01-02
Go to your original post and click on Edit Post at the bottom.
Click on the Go Advanced button at the bottom again and you will then see the editable title box at the top. Save the changes and all will be done.

I can not figure out how you got the incorrect title but now you can change it.

---

### Post by TheFu on 2021-01-02
This looks file, but I can't find documentation about the actimeo=1800 option.  Can you please point me to that?

I don't use the fstab for NFS mount. Instead, I use autofs, which delays mounts until the resource is requested, then about 5 minutes after a resource is no longer used, it umounts it automatically.  The systemd-mount has this delayed mount ability, but the timeout/umount has never worked for me, so I stopped using it.
 [https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) has a discussion. Here's an example.

```
romulus:/Data/r2  /S  nfs x-systemd.automount,x-systemd.idle-timeout=600s,proto=tcp,noauto 0 2
```
where:
[LIST]
[*] /S is the local mount point
[*] x-systemd.automount            appears to HAVE TO BE first in the options
[*] x-systemd.idle-timeout=600s    is optional AND doesn't work
[*] proto=tcp                      is a best practice for NFS
[*] noauto              is there to prevent mounting before a request was made
[/LIST]

Run these commands to force systemd-automount to see the changes:
```
sudo systemctl daemon-reload
sudo systemctl start S.automount
```
The *S.automount* directly relates to the mount location, so it will be different for different locations. I'd guess something like **sudo systemctl start mnt-qnap.automount** would be needed for your /mnt/qnap location, but don't remember the separator used for deeper mounts.

Just another few options for consideration.

---

### Post by alain.roger on 2021-01-02
Hi,

TheFlu, I read your post and i must confess I was not successful to make fstab works correctly with your information. On previous versions of ubuntu (<20.04) i had no problem to make auto mount of my shared directories in fstab.
Therefore i decided to check autofs and i must say that it works great even in Dolphin (which is a great pleasure).

The only thing i have to tweak, it's that after a given time, mounted points disappear in dolphin and therefore i have to fix it in order to make them always visible and accessible in dolphin till i do not logout or shutdown computer.

---

### Post by TheFu on 2021-01-02
check out the ghost option for autofs inside the auto.master config. For example:
```
/-      /etc/auto.nfs       --timeout=60 --ghost
```
That will keep the mount points shown.  For deeper levels, perhaps using symlinks?

Inside the auto.nfs:
```
/S     -fstype=nfs,proto=tcp,intr,rw,async,soft  romulus:/Data/r2
```
soft mounts are not good for files that need locking, but will prevent the nfs client from locking up if the nfs server mount disappears.
```
$ df -Th
Filesystem                            Type  Size  Used Avail Use% Mounted on
romulus:/Data/r2                      nfs4  1.3T  1.2T   67G  95% /S

```
It is nice to use NFSv4. That has some security and performance enhancements over earlier versions.

---

### Post by ActionParsnip on 2021-01-02
Just add a line in /etc/rc.local to run your mount -a command. If it's mounted it does nothing. If it's not then it'll mount. I suggest you add
```

mount -a &

```
So you don't hold up the boot

---

### Post by TheFu on 2021-01-02
rc.local was deprecated a few years ago.  

We can re-enable it, but isn't enabled automatically so it will need to be configured. Whatever works. Flexibility is one of the great things about Unix.

---

