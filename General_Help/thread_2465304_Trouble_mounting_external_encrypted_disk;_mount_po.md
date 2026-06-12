---
title: "Trouble mounting external encrypted disk; mount point doesnt exist and other errors"
date: 2021-07-29
forum: General Help
---

### Post by Ranbunta_Bantubunt on 2021-07-29
Hello... I set up an external drive with an encrypted luks container, but I am having trouble mounting it.

In addition to the passphrase, I made a keyfile for it and added entries to crypttab and fstab. This is what the structure looks like in lsblk:

```
sdb                             8:16   0   7.3T  0 disk  
&#9500;&#9472;sdb1                          8:17   0   256G  0 part  
&#9492;&#9472;sdb2                          8:18   0     7T  0 part  
  &#9492;&#9472;bigdrive                    253:6    0     7T  0 crypt 
    &#9492;&#9472;bigdrive--vg-big_drive 253:7    0   5.6T  0 lvm 

```

When I connect the drive and try to mount it with #mount -a, I get an error "mount:  /media/user/bigdrive: /dev/sdb2 already mounted or mount point busy."

When I remove the mount point directory /media/user/bigdrive, I get the error "Mount point does not exist". 

I notice that there is no mount point listed in lsblk to the right of the lvm for bigdrive--vg-big_drive. Not sure how to assign that, or just mount from the command line.

In contrast, there are mount points listed for the root drive and swap drives:
```
 
&#9492;&#9472;nvme1n1p5 259:11 0 1.8T 0 part
&#9492;&#9472;nvme0n1p5_crypt 253:0 0 1.8T 0 crypt
&#9500;&#9472;ubuntu--vg-swap_1 253:1 0 65G 0 lvm [SWAP]
&#9492;&#9472;ubuntu--vg-root 253:2 0 1.4T 0 lvm /

```

When I try to mount it from nemo, I receive various errors; the above mentioned already mounted error, and also when I removed and reconnected the drive, and it got a new device identifier /sdd rather than /sdb, I got the error "Error unlocking /dev/sdd2: Failed to activate device: File exists".

This is the /etc/crypttab entry:
```
bigdrive--vg-big_drive UUID=[REDACTED] /etc/luks/bigdrive.keyfile luks,discard

```

Sorry if redacting the UUID annoys anyone, in this case that info really isn't needed I think. I kindly ask for the indulgence of my hypervigilence.

This is the /etc/fstab entry:
```
/dev/mapper/bigdrive--vg-big_drive /media/user/bigdrive ext4 defaults 0 2

```

When I try to mount manually, I get this error:
```

/dev/mapper$ sudo mount /dev/mapper/bigdrive--vg-big_drive /media/user/bigdrive
mount: /media/user/bigdrive: wrong fs type, bad option, bad superblock on /dev/mapper/bigdrive--vg-big_drive, missing codepage or helper program, or other error.

```


Anyway so I'm a bit stuck... I dont quite understand how to mount this encrypted volume, either directly with the mount command, or the mount -a command using fstab.

Can someone help me see what I am not understanding about how to do this?
Thank you
Rabu

---

### Post by Ranbunta_Bantubunt on 2021-07-29
In /dev/mapper I see


/dev/mapper$ ls
bigdrive  bigdrive--vg-big_drive

---

### Post by Ranbunta_Bantubunt on 2021-07-29
i tried to post the results of 

```
ls -la /dev/mapper
```

but I am getting vbulletin errors that I cant figure out... including "your post must be at least 1 character" as well as server errors saying not authorized. 

Punting over to the non-  -la version, but just showing the entries are there in /dev/mapper

---

### Post by Ranbunta_Bantubunt on 2021-07-30
Hello... figured it out myself so I'll post the answer for posterity

The part I missed, following the tutorial, was that the ubuntu installer performed the final step of making a file system on the encrypted volume containers. 
I was just following the command line aspects of the tutorial, blowing past the final needed step of creating a file system on the logical volume that was created. 
So, silly me :)

---

