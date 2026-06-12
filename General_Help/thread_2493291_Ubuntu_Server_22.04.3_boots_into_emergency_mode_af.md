---
title: "Ubuntu Server 22.04.3 boots into emergency mode after modifying /etc/fstab"
date: 2023-12-09
forum: General Help
---

### Post by madscientist032 on 2023-12-09
Hello friends, I am back with another server support case.

Today I modified my /etc/fstab file so that my server would mount discs using best practices. (Prior to this, I was using the root crontab with a @reboot mount <dev> <mount dir> command which is sloppy & I regret setting it up like that to begin with.)

After saving the fstab and rebooting I get this screen which tells me it's in emergency mode. Is it safe to assume that all I have to do is go in and revert/fix  /etc/fstab then reboot & I should be fine? Or is there more to this mystery? 

Furthermore, what I am asking the community is, what is the fstab entry supposed to look like? Below is my original /etc/fstab entry, the modified version, as well as the BLKID output.

[B]Original /etc/fstab:

[/B]```
madsci@bossvc2ubnnas:/etc$ cat fstab
UUID=bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c / ext4 defaults 0 0
UUID=F20B-6791 /boot/efi vfat defaults 0 0
/swap.img    none    swap    sw    0    0
```

**Updated /etc/fstab**

```
UUID=bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c / ext4 defaults 0 0
UUID=F20B-6791 /boot/efi vfat defaults 0 0
UUID=73801dd5-f2b0-48a9-98bd-80786291c443 /media/SHARE ext4 defaults 0 0
UUID=e9f7b0eb-7ebc-431c-8b25-de22b9715ee5 /media/ARCHIVE ext4 defaults 0 0
UUID=9E20FF6820FF45B5 /media/scratch ext4 defaults 0 0
/swap.img    none    swap    sw    0    0
```

** Here is the BLKID output:**
```
madsci@bossvc2ubnnas:~$ sudo blkid
/dev/nvme0n1p1: UUID="F20B-6791" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="b72aa35c-e592-4c31-baf8-b5f43605e4ab"
/dev/nvme0n1p2: UUID="bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="7f7e3f69-a24e-4242-936f-4de459dbe202"
/dev/sdb1: UUID="e9f7b0eb-7ebc-431c-8b25-de22b9715ee5" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="0b74cf39-d345-4c48-8f36-d561f3eb4243"
/dev/sdc2: LABEL="SEAGATE4TB" BLOCK_SIZE="512" UUID="9E20FF6820FF45B5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9a665ed8-7087-42e0-92d5-c894d5ac58ff"
/dev/sda1: LABEL="share01" UUID="73801dd5-f2b0-48a9-98bd-80786291c443" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="636a3eb9-cf55-4ab5-a709-11deee628f12"

```

Attached photo is what I get from the server, I had to hook up a display to it as I could not SSH into the box. 

[https://cdn.discordapp.com/attachments/750412299533156456/1183156427745935370/PXL_20231209_212025099.jpg?ex=65874f4a&is=6574da4a&hm=82b260d6989c0b393ecf4444632b8964d9e424f7456c4aef7cda4e42fd0be636&](https://cdn.discordapp.com/attachments/750412299533156456/1183156427745935370/PXL_20231209_212025099.jpg?ex=65874f4a&is=6574da4a&hm=82b260d6989c0b393ecf4444632b8964d9e424f7456c4aef7cda4e42fd0be636&)

---

### Post by Tadaen_Sylvermane on 2023-12-09
```
UUID=9E20FF6820FF45B5 /media/scratch _**ext4**_ defaults 0 0
```

```

/dev/sdc2: LABEL="SEAGATE4TB" BLOCK_SIZE="512" UUID="9E20FF6820FF45B5" TYPE="_**ntfs**_" PARTLABEL="Basic data partition" PARTUUID="9a665ed8-7087-42e0-92d5-c894d5ac58ff"
``` 
Your blkid shows this as an ntfs drive. But you are trying to mount it as ext4.

---

### Post by #&amp;thj^% on 2023-12-09
> **Tadaen_Sylvermane said:**
> ```
UUID=9E20FF6820FF45B5 /media/scratch ext4 defaults 0 0
```

Your blkid shows this as an ntfs drive. But you are trying to mount it as ext4.

+1
Good catch

---

### Post by madscientist032 on 2023-12-09
> **Tadaen_Sylvermane said:**
> ```
UUID=9E20FF6820FF45B5 /media/scratch _**ext4**_ defaults 0 0
```

```

/dev/sdc2: LABEL="SEAGATE4TB" BLOCK_SIZE="512" UUID="9E20FF6820FF45B5" TYPE="_**ntfs**_" PARTLABEL="Basic data partition" PARTUUID="9a665ed8-7087-42e0-92d5-c894d5ac58ff"
``` 
Your blkid shows this as an ntfs drive. But you are trying to mount it as ext4.

Thanks for the catch, but I applied the change to /etc/fstab and it's still putting me in emergency state.

I checked if the other drives were mounting and it seems ubuntu's having issues with mounting /media/SHARE (which would be UUID "73801dd5-f2b0-48a9-98bd-80786291c443")

I changed /etc/fstab to omit that entry & rebooted. I am able to remote into the system now. 

I am not sure why Ubuntu is having a fit over trying to mount a drive to /media/SHARE

Here is the below output from /etc/fstab & BLKID commands:

```
###############
nasadm@bossvc2ubnnas:~$ date ; cat /etc/fstab
Sat Dec  9 05:08:45 PM EST 2023
UUID=bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c / ext4 defaults 0 0
UUID=F20B-6791 /boot/efi vfat defaults 0 0
#UUID=73801dd5-f2b0-48a9-98bd-80786291c443 /media/SHARE ext4 defaults 0 0 
UUID=e9f7b0eb-7ebc-431c-8b25-de22b9715ee5 /media/ARCHIVE ext4 defaults 0 0 
UUID=9E20FF6820FF45B5 /media/scratch ntfs defaults 0 0 
/swap.img    none    swap    sw    0    0
nasadm@bossvc2ubnnas:~$ 
nasadm@bossvc2ubnnas:~$ 
nasadm@bossvc2ubnnas:~$ sudo blkid
[sudo] password for nasadm: 
/dev/nvme0n1p1: UUID="F20B-6791" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="b72aa35c-e592-4c31-baf8-b5f43605e4ab"
/dev/nvme0n1p2: UUID="bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="7f7e3f69-a24e-4242-936f-4de459dbe202"
/dev/sda1: UUID="e9f7b0eb-7ebc-431c-8b25-de22b9715ee5" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="0b74cf39-d345-4c48-8f36-d561f3eb4243"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="ecf52b4c-a09a-476a-8f13-036a09dc2864"
/dev/sdb2: LABEL="SEAGATE4TB" BLOCK_SIZE="512" UUID="9E20FF6820FF45B5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9a665ed8-7087-42e0-92d5-c894d5ac58ff"
/dev/sdc1: LABEL="share01" UUID="73801dd5-f2b0-48a9-98bd-80786291c443" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="636a3eb9-cf55-4ab5-a709-11deee628f12"
```

---

### Post by MAFoElffen on 2023-12-09
Please show this
```

du -L 3 /media 
ls -l /dev/disk/by-uid/73801dd5-f2b0-48a9-98bd-80786291c443

```

---

### Post by madscientist032 on 2023-12-09
I am not going to post the contents of that du command as it spans thousands of lines and has PII data of which would be a pain to scrub. 

If it helps, /media contains three main directories: 

ARCHIVE (10 TB single disk)
SHARE (which is really short for "shared media", on a 2TB single disk)
scratch (4tb single disk)

Out of curiosity what were you looking for with du -L 3 /media? 

In the interim, here is the **ls -l dev/disk ouptut: **

```
nasadm@bossvc2ubnnas:~$ date ; ls -l /dev/disk/by-uuid/73801dd5-f2b0-48a9-98bd-80786291c443
Sat Dec  9 06:04:34 PM EST 2023
lrwxrwxrwx 1 root root 10 Dec  9 17:08 /dev/disk/by-uuid/73801dd5-f2b0-48a9-98bd-80786291c443 -> ../../sdc1

```

ALso please note I am able to mount the 2tb media drive just fine with "sudo mount /dev/sdc1 /media/SHARE" command. Just not fstab (yet)

---

### Post by MAFoElffen on 2023-12-09
Remember the quote "show me the money"? <==> "Show me the data..."

Not that I don't believe you, but just trying to verify that the mountpoint exists. If it is mounted, then it would show the next level beyond that. If not, it would show that mountpoint and stop. 

I see that the UUID does exist, and is verified...

At the moment, it doesn't make sense why it is not mounting from the fstab. I am curious why not.

---

### Post by madscientist032 on 2023-12-09
Fair enough, if it helps I can cd into /media/ARCHIVE just fine & same with /media/scratch. Ls works, pwd works, vi, etc. like nothings wrong.  Same goes for accessing these drives via SAMBA on remote workstations. 

I'm going to try and just mount /media/SHARE via /etc/fstab and see where that takes me vs trying to mount all three drives in one go. 

I'll report back with my findings.

---

### Post by madscientist032 on 2023-12-09
Sorry for double post. I have no clue what happened earlier, but the issue is resolved. My guess is that Ubuntu needed an extra reboot or two after modifying the fstab file back when it was discovered I had put down ext4 instead of ntfs for the scratch drive. 

I am happy to report that all three /media dirs are being mounted and are accessible!

```
madsci@bossvc2ubnnas:~$ date ; cat /etc/fstab
Sat Dec  9 06:53:57 PM EST 2023
UUID=bc0e1b91-54e9-11ea-ae6e-a8a15900bd9c / ext4 defaults 0 0
UUID=F20B-6791 /boot/efi vfat defaults 0 0
UUID=73801dd5-f2b0-48a9-98bd-80786291c443 /media/SHARE ext4 defaults 0 0 
UUID=e9f7b0eb-7ebc-431c-8b25-de22b9715ee5 /media/ARCHIVE ext4 defaults 0 0 
UUID=9E20FF6820FF45B5 /media/scratch ntfs defaults 0 0 
/swap.img    none    swap    sw    0    0
madsci@bossvc2ubnnas:~$ 
madsci@bossvc2ubnnas:~$ ls -l /media/SHARE | wc
      4      30     171
madsci@bossvc2ubnnas:~$ ls -l /media/ARCHIVE | wc
     21     182    1267
madsci@bossvc2ubnnas:~$ ls -l /media/scratch | wc
      8      67     465
madsci@bossvc2ubnnas:~$

```

I am going to mark this as SOLVED.

---

