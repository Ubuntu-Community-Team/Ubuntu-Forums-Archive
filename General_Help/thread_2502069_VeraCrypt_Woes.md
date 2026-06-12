---
title: "VeraCrypt Woes"
date: 2024-10-31
forum: General Help
---

### Post by cohaku1359 on 2024-10-31
Hey guys, i am a brand new Ubuntu user. I have a dual boot set up with windows 11 and Ubuntu 24.04 LTS. My question has to do with veracrypt, It is installed on both my windows and ubuntu partitions, and on the windows side everything works great. In Ubuntu, i can only open the encrypted files that were created in windows 11 in Read Only mode. and if i attempt to make a new encrypted file in ubuntu, it will create the drive, but when i try to mount it, ill get a permission denied error. i have been googling for hours to try and get this figured out and im at the point of giving up unless anyone has the magic bullet. yes i have turned off quick boot in my windows partition. 

if it matters, the hard drive the files are being encrypted on is an OpenMediaVault raspberry Pi NAS, im connected to it over NFS in ubuntu

please help before i lose what little hair i have left.

---

### Post by TheFu on 2024-11-01
When it comes to file access, we need to know which file system is being used and see the permissions for the files and the directory causing problems.  NFS is the client-side file access protocol, but I suspect you are still using NTFS, which brings other issues.

Why not use LUKS encryption on Linux?  It is solid, secure, and has never been cracked when brute force methods were applied and there is a sufficiently complex unlocking method.  My LUKS containers use a challenge/response method with a yubikey. I don't even know what the passphrase that get's sent to LUKS is.  I know that Ubuntu Mate's file manager integrates access to the LUKS container and will mount and file systems inside, once unlocked.

BTW, forget what MSFT has called "drives".  Those are most likely partitions, so you need to unlearn that.  Since the days of the first 10MB HDDs with MS-DOS 3.x, MSFT has been over simplifying partitions down to "drives", incorrectly.

---

### Post by cohaku1359 on 2024-11-01
To answer your questions, the format of the partitions ive made on  windows are exFat, and the ones made on linux are Fat32. And i chose  Veracrypt because i need to be able to access the files from windows and  linux machines. 

As far as permissions. That'd definitely the issue for both, the  partitions made on windows and in linux. If i set the permissions of the  files to decrypt for Owner, Group, and Others all to "Read and Write"  then everything works fine. so now my question is, since i am the owner  of the file, why do i have to set the permissions for everyone to read  and write and not just myself? Is VeraCrypt somehow not running under my  user? that doesn't seem to make a lot of sense.

If ALL of the permission category's are "read and write" then it work  great, but if i change the "Others" permissions to "Read only", the  partition gets mounted as read only by veracrypt.

---

### Post by TheFu on 2024-11-01
When we use non-native file system, the owner, group, permissions, ACLs and xattrs are all lost when it is umounted for any reason.

Unix permissions need to be applied.  When we choose non-native Linux file systems, then the mount program needs to be explicitly told the owner, group, and permissions, every time.

If you use network access for these files, there's no need to use non-native file systems.  This is a common mistake made by people new to Linux. The permissions are handled by the network protocol be that Samba or NFS.  OTOH, getting non-native file systems working with either popular network sharing protocol is a bit of a hassle.  If you choose NOT to use native Linux file systems, then it is your responsibility to manage those things in a way that Linux expects, like mounting the storage, every time, with the owner, group, and permissions you want it to have.  The mount, autofs and systemd-mount tools all provide ways to pass in those things at mount time.

Things that seem like common sense and don't actually work that way are that way for a multitude of reasons.  File and directory permissions are the core security model of all Unix-like OSes.  Any file (directories are files too BTW), needs to have those things set. Unix doesn't like to assume things when it comes to lessor security.

FAT32 is a terrible file system, BTW.  It should only be used if there isn't **any** other choice.  For cheap USB flash storage, exFAT is better, but it is still a foreign file system.  exFAT is well supported on Linux - for a foreign file system.  For SSDs and HDDs, NTFS is better still, if the storage will be physically, directly, connected, to an MS-Windows computer.  If not, then always choose a native Linux file system where normal permissions can be managed using chown, chmod, chgrp and normal Unix-style permissions.  

If dealing with Linux-only cheap flash storage, choose f2fs for the file system.  It does all the POSIX standard things Linux expects, but drops the journaling which we should always want for HDD and SSD file systems.  Non-journaled file system lose some safety, but gain fewer writes, which is good for cheap flash storage (USB/SDHC/microSD/CF/...)  NTFS, ext4, xfs all are journaled file systems and should be preferred when write counts aren't important.

There's no method that I know to mount foreign file systems efficiently that doesn't use the /etc/fstab file or a systemd-unit file (those are ugly!).  If you use native Linux file systems inside a LUKS container, then a GUI mount (Gnome-Disks) will be at the best performance, just like the fstab method AND meet all the POSIX expectations.  I think Gnome-Disks actually modifies the /etc/fstab file if you ask it to mount a file system.

I'm still confused how the client accessing encrypted storage through a r-pi needs veracrypt or any foreign file system at all. It isn't like a r-pi will be running MS-Windows.  I've got to be misunderstanding something important or missed that key point somewhere above.  Just reread everything and I still don't understand what storage connected to OMV has to do with any need for Veracrypt or foreign file systems.

---

### Post by cohaku1359 on 2024-11-01
The way i understand it(and im very new to this so i could be totally wrong) is when you created an encrypted partition in VeraCrypt, you have to tell veracrypt which type of file system to use. Fat, NTFS, etc... and since i need to be able to mount that partition on a windows machine, i cant choose a native linux file system since that wouldn't mount to a windows machine, correct? or if it did mount it would not work since its not a supported file system. the r-pi NAS just shows up as a network drive(correct use of drive? it is in fact a hard drive?), on that drive is the encrypted file that veracrypt then mounts as another partition.

---

### Post by TheFu on 2024-11-01
> **cohaku1359 said:**
> The way i understand it(and im very new to this so i could be totally wrong) is when you created an encrypted partition in VeraCrypt, you have to tell veracrypt which type of file system to use. Fat, NTFS, etc... and since i need to be able to mount that partition on a windows machine, i cant choose a native linux file system since that wouldn't mount to a windows machine, correct? or if it did mount it would not work since its not a supported file system. the r-pi NAS just shows up as a network drive(correct use of drive? it is in fact a hard drive?), on that drive is the encrypted file that veracrypt then mounts as another partition.

If the file system will be directly connected to both MS-Windows AND Linux systems, then **you are correct.**

If the file system will be directly connected to your NAS AND accessed over the network by any OSes, then **you are incorrect.**  The network protocol handles any compatibility layer requirements and since a r-pi is likely running some version of Linux, then you should be using LUKS + some native Linux file system inside.

I think you are being confused by the r-pi in the mix.  If that is where the storage is physically connected (don't get me started why using a r-pi for most server needs isn't the best idea), then the file systems need to be native Linux.  Well, "need' is perhaps too strong a term, but it will make your life 10x easier.

And again, it isn't about hard drives. It is all about file systems, usually inside partitions.  MSFT has been misleading you for decades.  

Typically, this is how storage is handled.
```
HDD
&#9500;&#9472;&#9472; part-01
&#9474;** &#9492;&#9472;&#9472; Encryption-Container-01
&#9474;**     &#9492;&#9472;&#9472; File_System-01
&#9500;&#9472;&#9472; part-02
&#9474;** &#9492;&#9472;&#9472; Encryption-Container-02
&#9474;**     &#9492;&#9472;&#9472; File_System-02
&#9492;&#9472;&#9472; part-03
    &#9492;&#9472;&#9472; Encryption-Container-03
        &#9492;&#9472;&#9472; File_System-03

```
That's all within 1 HDD.  The fact that many people don't create separate partitions or separate encryption-containers doesn't change anything.  This is just as valid:
```
HDD
&#9492;&#9472;&#9472; part-01
    &#9492;&#9472;&#9472; Encryption-Container-01
        &#9492;&#9472;&#9472; File_System-01

```
In the simplest use.
Of course, Veracrypt can put a hidden encryption-container inside the same partition, if we ask it to do this. There would be another file system inside that.

Anyway, I guess the question is why did you mention the r-pi at all, if the storage isn't directly connected to it?  That's what I find confusing.  Time for bed here.

---

### Post by cohaku1359 on 2024-11-01
The NAS is literally just a HDD connected to a r-pi via a SATA to usb adapter, with the r-pi running PI-OS lite and OpenMediaVault installed. i followed this NetworkChuck tutorial --> [https://www.youtube.com/watch?v=gyMpI8csWis](https://www.youtube.com/watch?v=gyMpI8csWis)

im SURE this is not the best way to run a NAS but it was just a project i found interesting and it works for me for now. 

the actual filesystem that the NAS is using is EXT4, i think the confusing thing for me is that when the encrypted file system gets mounted, it shows up as a totally separate partition from my actual NAS (in windows it shows up as a "K: insertpartitionnamehere"). So it makes me think that the NAS software on the pi isnt actually handling it. is it? i mean my NAS dashbord does not recognize another partition once its mounted. 

This is making my brain hurt lol, just for shiggles im gonna make a veracrypt partition in ubuntu using a native linux filesystem and see if i can access it in windows, ill report back

---

### Post by cohaku1359 on 2024-11-01
well this isnt going well... i am unable to create a EXT4 partition in veracrypt, It prompts for a password, if i use my user password i get a permission denied error, if i use the root password i get an "unable to obtain administrator privileges" error... not sure if its something i dont have configured right or a bug in veracrypt, but im leaning toward some kind of permission with the OMV r-pi, i can create partitions on my local drive in ext4 just not on the r-pi NAS for some reason

---

### Post by TheFu on 2024-11-02
> **cohaku1359 said:**
> The NAS is literally just a HDD connected to a r-pi via a SATA to usb adapter, with the r-pi running PI-OS lite and OpenMediaVault installed. i followed this NetworkChuck tutorial --> [https://www.youtube.com/watch?v=gyMpI8csWis](https://www.youtube.com/watch?v=gyMpI8csWis)
I've never used OMV, but know a few people who do.

> **cohaku1359 said:**
> im SURE this is not the best way to run a NAS but it was just a project i found interesting and it works for me for now. 
That's very reasonable.  Beware that connecting storage via USB for use in a network service, like a NAS, is a bad idea, but as long as the connection is stable, it will mostly work.  USB storage protocols don't support the full SATA/SCSI/SAS storage instruction set.  It is a fine way to test things out and a r-pi can be used for many test needs.  It is a great learning tool.  I have 4 r-pis here, but they don't contain any data. They get their data from a server elsewhere on the network.
If you want a list of projects to try out and learn from, [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) and [https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted) can provide some ideas.

> **cohaku1359 said:**
> 
the actual filesystem that the NAS is using is EXT4, i think the confusing thing for me is that when the encrypted file system gets mounted, it shows up as a totally separate partition from my actual NAS (in windows it shows up as a "K: insertpartitionnamehere"). So it makes me think that the NAS software on the pi isnt actually handling it. is it? i mean my NAS dashbord does not recognize another partition once its mounted. 
In Linux servers, storage/file systems aren't automatically mounted unless you set that up.  With LUKS+ext4, there are native methods using the crypttab and fstab to make this possible.  I don't have any clue about Veracrypt.  Of course, you can script nearly anything. It won't be plug-n-play, however.

> **cohaku1359 said:**
> 
This is making my brain hurt lol, just for shiggles im gonna make a veracrypt partition in ubuntu using a native linux filesystem and see if i can access it in windows, ill report back

MS-Windows won't be able to access a native Linux file system if directly connected.  Over a network protocol like CIFS/Samba or NFS, MS-Windows can access directories and files stored on native Linux. That's the job of the network protocol. The file system isn't seen by the client computer.

The rule is simple.  If the computer is directly connected to the storage with a SATA/SAS cable, then it needs the file system to be native for that computer.  In a dual boot situation with DAS - Directly Attached Storage - then a compromise is necessary. Typically, that would be something like Veracrypt + NTFS.   Mounting NTFS under Linux is a bit of a hassle, since we have to explicitly tell it the things that Linux needs for all mounted storage - owner, group, permissions are the minimal for every file and directory.  With NTFS, the only way to set those things is through mount options. There's no other method.

---

### Post by cohaku1359 on 2024-11-02
"MS-Windows won't be able to access a native Linux file system if  directly connected.  Over a network protocol like CIFS/Samba or NFS,  MS-Windows can access directories and files stored on native Linux.  That's the job of the network protocol. The file system isn't seen by  the client computer."

So am i correct in that my r-pi would not be "directly connected" it is accessed over the network by NFS on linux and whatever protocol windows uses, i cant remember the name

---

### Post by TheFu on 2024-11-02
Where is the storage physically connected?  I suspect your idea that the r-pi is the NAS is incorrect.

---

### Post by cohaku1359 on 2024-11-02
> **TheFu said:**
> Where is the storage physically connected?  I suspect your idea that the r-pi is the NAS is incorrect.

It's connected via ethernet to my router

---

### Post by cohaku1359 on 2024-11-02
[ATTACH=CONFIG]294455[/ATTACH]

---

### Post by TheFu on 2024-11-02
> **cohaku1359 said:**
> It's connected via ethernet to my router

Wow.  You've completely missed the question.  There is a HDD.  It is connected to power and to some computer directly using a SATA/SAS/SCSI or USB connection.  Which computer is it connected into?

---

### Post by cohaku1359 on 2024-11-02
> **TheFu said:**
> Wow.  You've completely missed the question.  There is a HDD.  It is connected to power and to some computer directly using a SATA/SAS/SCSI or USB connection.  Which computer is it connected into?

The hdd is connected to the r-pi via a sata to usb adaptor. The r-pi is connected to my network router via ethernet. That's all of the physical connections

---

### Post by TheFu on 2024-11-02
> **cohaku1359 said:**
> The hdd is connected to the r-pi via a sata to usb adaptor. The r-pi is connected to my network router via ethernet. That's all of the physical connections

If the r-pi is where the storage is physically connected, then the r-pi has to be used to unlock the encrypted container AND mount the file system inside.  Any other computers cannot do this.  They are clients using some network protocol like Samba, CIFS, 9p, NFS, sshfs, or some other protocol that is used even less often.

There is no way for MS-Windows to see the storage unless it is shared by the PI using some network protocol. Typically, samba would be used for this.

There is no way for a Linux desktop (not the Pi) to the the storage unless it is shared by the PI using some network protocol.

Only the PI sees the actual file system.  You should be using LUKS + ext4 on that storage.

Hope this clears things up.

---

