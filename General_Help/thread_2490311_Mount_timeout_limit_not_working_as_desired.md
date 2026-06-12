---
title: "Mount timeout limit not working as desired"
date: 2023-08-29
forum: General Help
---

### Post by paulrb on 2023-08-29
I have a self-built "headless" server running Ubuntu 22.04. I have recently fitted a trayless 5.25"-to-3.5" HDD adapter to allow me to hot-swap HDDs/SSDs as needed for backups and so on.

I want to automatically mount a certain disk, when inserted into the adapter, to a certain location. I set this up in /etc/fstab:
```

/dev/disk/by-uuid/075d3dfb-e96e-42a0-bd52-b89c56a0c0f6 /media/sue1 ext4 defaults 0 2

```
and it works well, except...

If, on boot-up, that particular disk is not inserted, the whole boot-up process takes 1m 30s longer because it is waiting for that disk to be ready so that it can be mounted. This is a pain, so I amended /etc/fstab:
```

/dev/disk/by-uuid/075d3dfb-e96e-42a0-bd52-b89c56a0c0f6 /media/sue1 ext4 defaults,x-systemd.mount-timeout=5s 0 2

```
hoping that it would only wait 5 seconds for the disk to be ready, otherwise forget it and continue booting.

But even with the above, it is still waiting 1m 30s for the disk during boot.

What did I get wrong?

Thanks,

Paul

---

### Post by TheFu on 2023-08-30
The fstab is the wrong place to accomplish your goals.  The systemd-automount tool never umounts storage once it is mounted.

Instead, use autofs.  There's a how-to guide - search "autofs ubuntu" and pick the help.ubuntu.com link.

autofs only attempts to mount storage when it is requested.  And it automatically umounts it a few minutes after the last file on it is closed.
BTW, rather than using UUIDs to mount, use the LABEL= instead.  Much easier for in autofs and in the fstab file for humans.  Just set the LABEL on the file system and that will be used.

I have this issue with really long paths that don't actually improve readability.
/dev/disk/by-uuid/075d3dfb-e96e-42a0-bd52-b89c56a0c0f6 
vs
UUID=075d3dfb-e96e-42a0-bd52-b89c56a0c0f6
vs
LABEL=Backup01
Which conveys more useful information to a human?

---

### Post by Morbius1 on 2023-08-30
Just some random thoughts:

Is there a reason you are using **x-systemd.mount-timeout** rather than **x-systemd.device-timeout**.

In the former the mount process has already begun and in the latter the mount process won't start at all if the device is not present.

And you might want to add the **nofail** option to the list.

In the context of systemd nofail is slightly more nuanced than the usual mount meaning. It makes the mount "wanted" not "required" so booting isn't stalled if the mount is not successful or there are errors.

---

### Post by paulrb on 2023-08-31
Hi @TheFu

I've been reading up on autofs, and it looks useful, but I don't think it will solve my problem, and I think that's because I didn't explain the problem very well.

I want to mount drives inserted into the server's hot-swap caddy so they are available to NFS/SAMBA shares. Its the server boot that is delayed by 1m 30s when the drive is not inserted but is listed in fstab.

Looks like autofs runs on client PC/laptops and avoids delaying their bootup by mounting the remote share only when the user attempts to access it.

Good idea about using drive labels, though. It would be great if any drive I put into the caddy could be automartically mounted into a shared directory using a name based on it's label.

---

### Post by paulrb on 2023-08-31
Thanks @Morbius1,

I will try x-systemd.device-timeout and nofail options!

---

### Post by TheFu on 2023-08-31
> **paulrb said:**
> Hi @TheFu

I've been reading up on autofs, and it looks useful, but I don't think it will solve my problem, and I think that's because I didn't explain the problem very well.

Or I misinterpreted your needs. All good. I thought this was for backup disks?  Oh well.

> **paulrb said:**
> 
I want to mount drives inserted into the server's hot-swap caddy so they are available to NFS/SAMBA shares. Its the server boot that is delayed by 1m 30s when the drive is not inserted but is listed in fstab.
noauto option?  Backup disks really shouldn't be available using any file sharing protocols. That's a good way to have all the backups corrupted by malware/crypto-ware.  Use a client/server architecture and have the backup server "pull" the backup data from each client.  Malware and cryptoware know all about network shares and NFS.


> **paulrb said:**
> 
Looks like autofs runs on client PC/laptops and avoids delaying their bootup by mounting the remote share only when the user attempts to access it.
I use autofs for any temporary storage, especially for network storage and USB storage.  For disks in my hot-swap drive cages, I just umount and mount as needed. Decades ago, I'd do that as part of my backup scripts, before I setup "pulled" backups. We all have to figure out the best backup method for our needs and skill. 

> **paulrb said:**
> Good idea about using drive labels, though. It would be great if any drive I put into the caddy could be automartically mounted into a shared directory using a name based on it's label.
File system labels are one of those things that seem to be ignored.  Don't confuse Drive Labels and file system labels, regardless of the lies from MSFT.  They've been using file system letters since partitioning was created and we had HDDs.  They were just too lazy to call it by the correct name.  THERE ARE NO DRIVE LETERS in MS-Windows, unless you use a floppy disk.

Anyway, just a little more knowledge to get you closer to the solution you need/pick.  Everyone evolves their backups over time.

---

### Post by emavow on 2023-09-18
Consider using 'x-systemd.device-timeout' instead of 'x[-]("https://apkwa.net/an-whatsapp/")systemd.mount-timeout' for different mount initiation behaviors based on device availability. 
Also, think about adding the 'nofail' option, which, in systemd, changes the mount from "required" to "wanted," preventing boot delays due to failed mounts or errors.

---

### Post by MAFoElffen on 2023-09-18
@emavow -- Welcome to Ubuntu Forums. Please read all the posts in a thread. If you had, you might have noticed that Morbius1 had suggested that same "of both" in Post #3. That would have changed your suggestion to a +1 as an agreement on his suggestions(?)

---

