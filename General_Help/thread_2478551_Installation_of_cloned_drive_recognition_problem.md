---
title: "Installation of cloned drive recognition problem"
date: 2022-08-29
forum: General Help
---

### Post by mosscomes on 2022-08-29
```


I am trying to upgrade a 2gb data drive to a cloned 4 gb. It is a samba file share. I am having problems with the system properly recognizing the new drive.
 
 
 Details:
 Linux Server 20.04.5
 Managed by LXQt GUI and Webmin 2.0.
 Motherboard is Intel DH67BL (released Late 2011)
 Cloned using Clonezilla USB using the K1 option.
 
 I cloned the drive (but disk comparison was not 100%).

 I changed the fstab to reflect the new drive’s UUID. Note: the disk label is the same for both drives.
 
 I used this procedure a year ago (except for the k1 option in Clonezilla) and everything worked properly (but that was 2 GB to 2 GB).

 This time I get a “start job is running for dev/disk/by-uuid/” new uuid number.

 The system “sees” drive, but can’t mount it.
 
 Here are some other things that I see:
 
 In the LXQt disk command, the disk appears but under partitioning is says “Unknown” (PMBR).

 Aslo in LXQt, gparted show the drive but it is unallocated. However, in an external drive, it is seen as ext4 partition. In Webmin, it says “this has no partition yet.”
 
 In webmin, it says “Mount failed” and “can’t find “UUID” with the correct UUID number.
 
 Note: Because of the age of the motherboard, I have researched the documentation regarding support for greatedr then 2 GB drives. I have not found any information on this subject.

 I don’t think I missed a step, but the non-recognition of the existing partition has me stumped.

 
 
 Any ideas?


```

---

### Post by mosscomes on 2022-08-30
```

Here's so me additional info.

The Bios says that UEFI boot must be enabled (it is) to boot a drive larger to 2 gb. This isn't the boot drive. 

Regarding the PMBR issue, this is what fdisk, gdisk, and parted say: 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290956&d=1661861206[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290955&d=1661861189[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290954&d=1661861171[/IMG]


Could this be the recognition problem?

```

---

### Post by oldfred on 2022-08-30
Please only attach screen shots, not post in line.

And if terminal, directly post output in code tags.
Easy to add code tags with Forum's Go Advanced and # icon.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

It looks like you are trying to use MBR(msdos) partitioning on a drive over 2TB. You must use gpt.
Post this for each drive.
sudo gdisk -l /dev/sdX

If cloning, you cannot keep both drives plugged in at same time as duplicate UUIDs are not allowed.
Post this:
lsblk -f

---

### Post by mosscomes on 2022-08-30
```


Here's the output:

sdb is the boot. sdd is the problem. sdf is the original drive connected via external drive (I have not had it usually attached).

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290961&d=1661888473[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290962&d=1661888485[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290963&d=1661888497[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290964&d=1661888513[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290965&d=1661888523[/IMG]

Note: I note the problem (MBR) on sdb -next project to fix.


```

---

### Post by mosscomes on 2022-08-30
```


lsblk:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290967&d=1661888712[/IMG]

Here's the old (and working fstab) 

UUID=0fa30028-e906-11e8-9f6f-e840f20680f3 / ext4 defaults 0 0
UUID=DD36-5DF4 /boot/efi vfat defaults 0 0
/swap.img    none    swap    sw    0    0
UUID=082737a1-0371-4461-b46a-124e53c03990    /samba/dt01aca0    ext4    defaults    0    0
UUID=aa219bcc-dc66-46a1-aff2-d5fd037e4908    /samba/st2000dm008_03    ext4    defaults    0    0
UUID=1bcdc1dc-8162-436e-9d39-cbe03419969d    /samba/st2006dm006    ext4    defaults    0    0
UUID=394ad321-2ea8-452c-8614-7a6ca6e0ea82    /samba/st2000dm006_02    ext4    defaults    0    0

and the current one:

UUID=0fa30028-e906-11e8-9f6f-e840f20680f3 / ext4 defaults 0 0
UUID=DD36-5DF4 /boot/efi vfat defaults 0 0
/swap.img    none    swap    sw    0    0
UUID=082737a1-0371-4461-b46a-124e53c03990    /samba/dt01aca0    ext4    defaults    0    0
UUID=99528fa4-d6d5-461d-b402-0b3b77624f2f    /samba/st2000dm008_03    ext4    defaults    0    0
UUID=1bcdc1dc-8162-436e-9d39-cbe03419969d    /samba/st2006dm006    ext4    defaults    0    0
UUID=394ad321-2ea8-452c-8614-7a6ca6e0ea82    /samba/st2000dm006_02    ext4    defaults    0    0

Your comment about "both drives plugged in at same time as duplicate UUIDs" confuses me. All of the UUID's are different.

```

---

### Post by oldfred on 2022-08-30
Please see post #3.
And then fix your posts so we can review them easily.

And sdd shows no partitions? Did you attempt to write data, to drive, not partition?

---

### Post by mosscomes on 2022-08-30
```


I am hoping I am getting this formatting correct and you can see it.

When the drive was attacked via USB, I could read. I did not try to write. Obviously, because it won't mount as an internal disk, I can't write on it now.

here's how gparted sees it as an external drive:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290969&d=1661898872[/IMG]




```

---

### Post by oldfred on 2022-08-30
I do not know nor use Samba.
That is for mounting a drive in another system. 
I prefer labels that have some meaning. And/or mounts pre-defined that have some meaning.

Post these with external & internal.
lsblk -f

Are your Samba mounts shown from your other system?
A USB drive will default mount to /media/$USER/XXX where XXX is label or UUID.
Internal requires you to define a mount(s) like /mnt/data or just /data and then mount the partition(s).

Then if using another system, you have to define Samba.
[https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)
[https://askubuntu.com/questions/1207427/how-to-enable-full-permissions-on-internal-secondary-hdd](https://askubuntu.com/questions/1207427/how-to-enable-full-permissions-on-internal-secondary-hdd)

---

### Post by mosscomes on 2022-08-30
```


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290970&d=1661903861[/IMG]

Samba, which I use for both windows pc's and a Mac, is not the issue here. Even now in window explorer, the drive share is green and not red -x'd. (There's nothing in it).  In the above image, sdd is the 3.64 TB clone of sdf. I have traditionally cloned new drives in an external usb drive because I am out of spaces for disks. When the disk is properly recognized in the system, I remove the original from the server. In the past, I haven't even had to modify the smb.conf file, because I use the same disk label (but I can if necessary). 

The issues, if what I have seen on other internet posts is right, may be that sdd is seen as a PMBR issue (I pre-partitioned this disk as GPT before starting the Clonezilla process.) I have also seen comments about "Partition 1 does not start on physical sector boundary" and there is an unrecognized disk label error in some of the error messages I've seen.

I am not even getting to the point where the drive is mountable. In Webmin,  when I try to mount the drive, I get have gotten the following message: "Mount failed: Mount: /samba/st2000d_03 can't find UUID-UUID Number." Also in Webmin, it sees the drive, but says "This disk has no partitions yet" and "Partition table format: None created."

Here's what blkid says:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290971&d=1661905540[/IMG]

As you can see, blkid isn't picking up the UUID (see above for the fstab with the UUID of the sdd.




```

---

### Post by TheFu on 2022-08-30
I don't understand what samba has to do with this at all.  If you are replacing an existing HDD, not just adding another, then samba is meaningless to the data copy needs.

Using cloning to copy data files is a waste and not the most efficient. Use **rsync** instead to avoid all sorts of issues.  Rsync will be faster too.

MBR partition tables only support drives up to 2TB. Larger drives will not see the extra space if MBR partition is used.  Cloning would retain MBR. Not good.  GPT is superior for a number of reasons, not just the ability to handle huge drives that we cannot even imaging happening in the next 20 yrs.

Please don't use images for text.  Run the command, post the command, all options and text output AS TEXT, inside forum code tags.   I can't easily view images or copy/paste relevant parts to help you.  Please make it easy for us to help you.

Really, the easy answer is to start over.  Connect the 4TB drive, use gparted to create a GPT partition table, then create at least 1 partition, format it as ext4.  Mount the new storage to /mnt/new as a temporary location.  If the old drive is mounted to /srv/old, then the rsync command to clone everything, retaining all owners, groups, permissions is:

```
$ sudo -av /srv/old/     /mnt/new/
```
To see progress and status as the copy works, use this instead:
```
$ sudo --stats --progress    -av    /srv/old/     /mnt/new/
```

I've made lots of assumptions about your skills with mounting.  There are lots of forum posts about.  I suggested using ext4, because it is an excellent general purpose file system and works well with samba. If you have specific needs for another file system, that would be good to know BEFORE any attempt.

IMHO, there are 5 commands that every Linux/Unix end user should know just a little about.  rsync is one.  ssh is another. bash is a third.  No need to be an expert, but more than just memorizing 2 commands would be smart. rsync has so many excellent uses, especially to copy files over the internet between 2 systems when you have logins on both.

---

### Post by mosscomes on 2022-08-30
Regarding Samba, you are right. It isn't an issue at this point. The cloned disk was (sdf in the following examples) is formatted in GPT and ext4 (Now, if . I consider myself a moderately talented amateur and I have had problem mounting the drives in the past, but for the previous two drive replacements, the procedure I used worked. This time it didn't.  This is the first time I broke the 2 TB limit.

I have used disk cloning previously because of the "hooks" that I have into a number of Windows programs (and the media server software I use )that refer to specific items on the samba data disks. Hence, why I keep the drive labels the same. It has been seamless to my apps. And starting from scratch would be a major time investment.

Wait a minute!!!!!! I just discovered something sdc, the last drive I cloned, has an MSDOS partition table. Humm, makes me wonder.

```
**> lsblk -f**
NAME   FSTYPE   LABEL          UUID                                 FSAVAIL FSUSE% MOUNTPOINT
loop0  squashfs                                                           0   100% /snap/bare/5
loop1  squashfs                                                           0   100% /snap/core18/2409
loop2  squashfs                                                           0   100% /snap/core18/2538
loop3  squashfs                                                           0   100% /snap/core20/1593
loop4  squashfs                                                           0   100% /snap/core/13425
loop5  squashfs                                                           0   100% /snap/core/13308
loop6  squashfs                                                           0   100% /snap/core20/1611
loop7  squashfs                                                           0   100% /snap/gtk-common-themes/1535
loop8  squashfs                                                           0   100% /snap/okteta/15
loop9  squashfs                                                           0   100% /snap/okteta/18
loop10 squashfs                                                           0   100% /snap/lxd/22526
loop11 squashfs                                                           0   100% /snap/kde-frameworks-5-96-qt-5-15-5-core20/7
loop12 squashfs                                                           0   100% /snap/lxd/22753
loop13 squashfs                                                           0   100% /snap/kde-frameworks-5-qt-5-15-core20/14
sda                                                                                
`-sda1 ext4     st2000dm006_02 394ad321-2ea8-452c-8614-7a6ca6e0ea82  404.6G    73% /samba/st2000dm006_02
sdb                                                                                
|-sdb1 vfat                    DD36-5DF4                             505.8M     1% /boot/efi
`-sdb2 ext4                    0fa30028-e906-11e8-9f6f-e840f20680f3  104.9G    47% /
sdc                                                                                
`-sdc1 ext4     DT01ACA0       082737a1-0371-4461-b46a-124e53c03990    1.2T    26% /samba/dt01aca0
sdd                                                                                
sde                                                                                
`-sde1 ext4                    1bcdc1dc-8162-436e-9d39-cbe03419969d  757.7G    54% /samba/st2006dm006
sdf                                                                                
`-sdf1 ext4                    aa219bcc-dc66-46a1-aff2-d5fd037e4908  477.5G    69% /media/tim/aa219bcc-dc66-46a1-aff2-d5fd037e4908

```
-------------------------------------------------------------------------------------------------------------------------------------------
```
**> blkid**
/dev/sdb1: UUID="DD36-5DF4" TYPE="vfat" PARTUUID="a4cfbd16-5961-4ace-b04c-338f7eb74cc6"
/dev/sdb2: UUID="0fa30028-e906-11e8-9f6f-e840f20680f3" TYPE="ext4" PARTUUID="74583268-934b-40a9-899a-88f8bbd40f57"
/dev/sda1: LABEL="st2000dm006_02" UUID="394ad321-2ea8-452c-8614-7a6ca6e0ea82" TYPE="ext4" PARTLABEL="st2000dm006_02" PARTUUID="7e331e84-d205-41b3-b833-a965599e3479"
/dev/sdc1: LABEL="DT01ACA0" UUID="082737a1-0371-4461-b46a-124e53c03990" TYPE="ext4" PARTUUID="000a0187-01"
/dev/sde1: UUID="1bcdc1dc-8162-436e-9d39-cbe03419969d" TYPE="ext4" PARTLABEL="ST2000_1" PARTUUID="7b51c985-9da5-4ad6-ba84-814d221bdce5"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/sdf1: UUID="aa219bcc-dc66-46a1-aff2-d5fd037e4908" TYPE="ext4" PARTLABEL="ST2000DM_02" PARTUUID="edc5bd87-cac0-492d-8065-db35f6e1d1de"
/dev/sdd: PTTYPE="PMBR"


-
```--------------------------------------------------------

```
**> sudo gdisk -l /dev/sdd**
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.
Disk /dev/sdd: 7814037168 sectors, 3.6 TiB
Model: ST4000DM004-2U91
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): BE95F049-A82C-461B-AA07-6170F22DEEFC
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7814037101 sectors (3.6 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name


```------------------------------------------------------------------------------------------

```
**> lsblk -f**
NAME   FSTYPE   LABEL          UUID                                 FSAVAIL FSUSE% MOUNTPOINT
loop0  squashfs                                                           0   100% /snap/bare/5
loop1  squashfs                                                           0   100% /snap/core18/2409
loop2  squashfs                                                           0   100% /snap/core18/2538
loop3  squashfs                                                           0   100% /snap/core20/1593
loop4  squashfs                                                           0   100% /snap/core/13425
loop5  squashfs                                                           0   100% /snap/core/13308
loop6  squashfs                                                           0   100% /snap/core20/1611
loop7  squashfs                                                           0   100% /snap/gtk-common-themes/1535
loop8  squashfs                                                           0   100% /snap/okteta/15
loop9  squashfs                                                           0   100% /snap/okteta/18
loop10 squashfs                                                           0   100% /snap/lxd/22526
loop11 squashfs                                                           0   100% /snap/kde-frameworks-5-96-qt-5-15-5-core20/7
loop12 squashfs                                                           0   100% /snap/lxd/22753
loop13 squashfs                                                           0   100% /snap/kde-frameworks-5-qt-5-15-core20/14
sda                                                                                
`-sda1 ext4     st2000dm006_02 394ad321-2ea8-452c-8614-7a6ca6e0ea82  404.6G    73% /samba/st2000dm006_02
sdb                                                                                
|-sdb1 vfat                    DD36-5DF4                             505.8M     1% /boot/efi
`-sdb2 ext4                    0fa30028-e906-11e8-9f6f-e840f20680f3  104.9G    47% /
sdc                                                                                
`-sdc1 ext4     DT01ACA0       082737a1-0371-4461-b46a-124e53c03990    1.2T    26% /samba/dt01aca0
sdd                                                                                
sde                                                                                
`-sde1 ext4                    1bcdc1dc-8162-436e-9d39-cbe03419969d  757.7G    54% /samba/st2006dm006
sdf                                                                                
`-sdf1 ext4                    aa219bcc-dc66-46a1-aff2-d5fd037e4908  477.5G    69% /media/tim/aa219bcc-dc66-46a1-aff2-d5fd037e4908
```
[HR][/HR]Sorry about the formatting issues. I'm learning what works best for you folks.

General question on rsync (I don't recall using it). If I would start over (and I am beginning to head this direction), assuming that I can keep the drive names/labels the same), would rsync replicate the clone function (except for copying data from deleted files)?

[HR][/HR]

---

### Post by oldfred on 2022-08-30
Added code tags by using Forum's advanced editor and # icon. 
Easy to do and makes it easier for everyone.
Please use Code tags.

I delete all snaps as first task with new install, so forget to have users run commands to exclude them. They offer nothing in drive output info.
 lsblk -e 7   #blocks loop devices or specify specific fields, see also man lsblk:
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

As mentioned in Post #6 your sdd does not show partitions?

I normally use gparted from live installer or gparted in my install if working on another drive. You cannot modify mounted partitions.You can use gdisk, parted or now fdisk supports gpt drives. But you have to first specify drive as gpt. Most still default to MBR(msdos). 
The only place anymore for MBR, is if booting Windows in old BIOS mode which is only required for systems over 10 years old.

There is device label which you want as gpt.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
And there are partition and file system labels which you should assign to provide extra info on what you are using partition for.
Attached images are from older screens, but still they same now.

I mostly use rsync even over cp command. I have a music folder in my data folder & wanted to copy it to a data folder on a partition I do not normally mount so default mounted using label "data" on external device.
rsync -aruvlP  /mnt/data/Music /media/fred/data

---

### Post by mosscomes on 2022-08-31
I started from scratch and things are moving along, everything is mounted and accessible . I tried rsync, but I was getting "No such file or directory messages," so I am using webmin to copy. Slower, but it is something I am used more used to doing and I can do it in the background. I will go bakc and work with rsync - but I am going yo try it without the external usb.

---

### Post by TheFu on 2022-08-31
webmin is a bad idea.  It is only suitable if setup my a senior admin who is available to ensure junior admins don't trash systems using it. Consider yourself warned.  It is not a replacement for CLI/shell use and knowledge.

---

