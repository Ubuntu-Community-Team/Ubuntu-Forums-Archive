---
title: "NTFS drives drop out a few seconds after boot"
date: 2018-10-30
forum: General Help
---

### Post by vidtek on 2018-10-30
I have been struggling with this for a few days now, after a few days away in beautiful Torquay, this problen arose.

    After booting up and logging in there is a short window in time when the entries in my fstab are valid, then a few seconds later all my ntfs drives just vanish.

    Here is my fstab:
    ```
# /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    # / was on /dev/sda6 during installation
    UUID=6c0ab85c-3f8b-4b7c-8ef1-b0ed9ae4d8ad /               btrfs   defaults,subvol=@ 0       1
    # /boot/efi was on /dev/sda1 during installation
    UUID=B60D-32FF	/boot/efi	vfat	defaults	0	1
    # /home was on /dev/sda8 during installation
    UUID=c68f50bd-e237-4b5b-b12e-ba909f3b1138 /home           btrfs   defaults,subvol=@home 0       2
    # swap was on /dev/sda7 during installation
    UUID=59fa6452-d971-43d3-8dff-dcae4decb78f none            swap    sw              0       0
    UUID=F2E89BB2E89B7397	/media/data	 ntfs-3g	defaults,rw	0	0
    UUID=6E66CE4866CE112F	/media/tv	ntfs-3g		defaults,rw	0	0

```

    
    I use nfs, this is my exports file:
    ```
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


    /media/data 192.168.0.0/24(rw,nohide,insecure,no_subtree_check,async)
    /media/tv 192.168.0.0/24(rw,nohide,insecure,no_subtree_check,async)

```

  
    I am really stumped, why should it work for just a few seconds? It doesn't make sense to me at all.

    Tony 

    Asus Z270 i7 16gb ram 8.25tb GT960 TSB6205 Quad tuner 64-bit Kubuntu 18.04 Bionic & win 10 Be/FE mythtv 0.29
    Laptop Samsung NP R580 i5 nvidia linux ultimate & win 10 Homerun dual netwk tuner 55¨ Samsung ES8000

---

### Post by HermanAB on 2018-10-30
Howdy,

Note that Linux can detect that the NTFS file system has errors and need to be fixed, but it cannot do the fix.  You need to use Windows to run chkdsk.  After that, things should be back to normal again for a while.

---

### Post by vidtek on 2018-10-30
> **HermanAB said:**
> Howdy,

Note that Linux can detect that the NTFS file system has errors and need to be fixed, but it cannot do the fix.  You need to use Windows to run chkdsk.  After that, things should be back to normal again for a while.

Herman, Thanks for the response, I had already done a chkdsk -f in windows and rebooted to windows twice and still no joy.

However, I did notice that my windows10 ntfs partition was always automatically mounted and stays persistently.  I then changed the fstab to mount the ntfs partitions
in the same location; /media/tony/data and /media/tony/tv -- the windows partition was mounted automatically as; /media/tony/w10.

This seems to achieve the result I need (so far).

As a guess, I would say it has a lot to do with folder and file permissions and the recent windows10 update.

I can't figure out why I seem to be the only one who has experienced this, weird.

If it is a permanent work-around I'll mark it as solved (just another of life's little mysteries in linuxland)

Cheers Tony.

Update 31-10-2018 --- Looks like this last is a good work-around for me, I'll mark this as solved.

---

