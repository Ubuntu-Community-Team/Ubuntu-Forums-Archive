---
title: "kvm running loop device as a disk image"
date: 2021-07-11
forum: General Help
---

### Post by bardiamgtgc on 2021-07-11
hey
im trying to run a windows server vm on an ntfs partition as my ssd is almost full and i dont want to have the vm on my own ssd and on my nas all my drives are ntfs

first i tried to have the qcow2 file exactly on my network ntfs partition which failed and after some looking around no luck with that 
then according to this article i can mount my image as a loop device [https://opensos.blogspot.com/2013/06/using-kvm-disk-image-on-ntfs-partition.html](https://opensos.blogspot.com/2013/06/using-kvm-disk-image-on-ntfs-partition.html) i decided to mount the qcow2 image then use it in kvm which also failed when running kpartx -a -v myimage.qcow2 i get an error about ntfs signatures 

so i converted the qcow2 to a raw image format and i was able to mount it

now i have /dev/loop31p1 /dev/loop31p2 /dev/loop31p3 (p1 is windows bootloader, p2 is windows filesystem itself, p3 is recovery im guessing because it only has a Recovery directory inside it)
now i have no idea how to get them to work inside kvm first i tried adding them as different disks but it failed and im guessing it failed because it couldnt recognize which disk has the bootloader and which one is the filesystem(stuck at booting from hard drive)

also if this helps with anything, this vm came from one of my servers running vmware esxi then converted to qcow2 then to raw i can do a clean install if needed there isnt much data on this image

im running ubuntu 20.04 trying to run intel gvt-g which works fine on my ssd but as i said im running out of space

any solutions to this?

---

### Post by TheFu on 2021-07-11
I've never tried what you are attempting.  Seems like the hard way.

If you do the install of Windows using **virt-manager**, then you can pick the type of storage to be used. I've always used raw image files with Windows and either vdi, qcow2 or LVM LVs with every other OS.  LVs make storage management and perfect backups easier, if that is a concern.  LVM is just another storage pool type to libvirt.  On spinning disks, using either raw images, fully preallocated, or LVM LVs makes a huge performance difference. Don't know if that's a consideration or not.

```
$ sudo ls -l  /var/lib/libvirt/images/Win7Ult
total 97337360
-rw-rw---- 1 root root 36507222016 Jun 22 17:35 Win7Ult-Data2.img
-rw-rw---- 1 root root 63166218240 Jun 22 17:35 Win7Ult-os.img
```
I keep the data separate from the OS.  Windows is so very bloated compared to all other OSes I use here.
Even my most bloated Ubuntu desktop only gets 40G.
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-desk-2104      hadar-vg -wi-a-----  20.00g                                                    
  lv-blog44-1804 hadar-vg -wi-ao----  16.20g                                                    
  lv-regulus     hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2   hadar-vg -wi-ao----  10.00g                                                    
  lv-spam3       hadar-vg -wi-ao----  10.00g                                                    
  lv-vpn09-2004  hadar-vg -wi-ao----   7.50g                                                    
  lv-xen41-1804  hadar-vg -wi-ao----  12.50g                                                    
  lv-zcs45-1604  hadar-vg -wi-a-----  25.00g                                                    
  lv-zcs45-1804  hadar-vg -wi-ao----  25.00g                                                    
  lxd-lv         hadar-vg -wi-ao----  60.00g                                                    
  libvirt-lv     hadar-vg -wi-ao---- 175.00g                                                    
  root           hadar-vg -wi-ao----  32.33g                                                    
  swap_1         hadar-vg -wi-ao----   4.25g                                                    

```
The LVs above that begin with lv- are for different virtual machines (except regulus).  LVM LVs can be resized larger while the underlying OS keeps running, assuming the VG has more storage available. I leave about 20% of the VG unused for snapshot needs. These help with perfect, uncorrupted, backups.

---

### Post by MAFoElffen on 2021-07-11
What? Wait? Mounting it as a loop device? Why? No. You are over-thinking that.

I have a multi-boot of Windows and Ubuntu Linux and "Others". I do NFTS for common shared drive spaces that can be read and written to by all.  even on a mount in fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=d6eb6bcf-c93a-46d5-b7e0-25dd73eec384 /               ext4    errors=remount-ro 0       1# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=d6eb6bcf-c93a-46d5-b7e0-25dd73eec384 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=a5c5987f-82ab-4e16-a39f-aa5564a0a2ef /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=f7db5bcd-8019-46a1-abe9-44d99c84d0e7 none            swap    sw              0       0
[COLOR=#ff0000]UUID=0A24D9F224D9E0AD             /home/mafoelffen/WIN_G  ntfs    defaults        0       0 [/COLOR]
# /home was on /dev/sda4 during installation
UUID=a5c5987f-82ab-4e16-a39f-aa5564a0a2ef /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=f7db5bcd-8019-46a1-abe9-44d99c84d0e7 none            swap    sw              0       0
```
Notice there is "nothing" special about that mount. I repeat nothing: "Nothing." Well, I do mount it inside my own Home directory, because it is convenient for me to get to...

If you just do that, KVM and Linux itself, see the NTFS as read-only, that is true... Because "something else" created and manages it. So what do you do to get around that? Easy... And I do this with my network shares also. Because the common denominator is NFTS can be read and written to by  almost any OS.

Linux see's the mount and mount's it. It has gained access. But doesn't see any permissions, so it assumes read only. Make a directory, and set the ownership of the directory recursively to the KVM group. Set permissions of file recursively in that directory to users... ... Wait one... Look at this:
```
mafoelffen@Opti-Ubuntu-Main:~/WIN_G$ ls -l
total 4
drwxrwxrwx 1 root root    0 Jul  9 01:31 '$RECYCLE.BIN'
drwxrwxrwx 1 root root  192 Jul 10 23:09  ISO
drwxrwxrwx 1 root root 4096 Jul 10 21:26  KVM-VM
drwxrwxrwx 1 root root    0 Jul  8 18:29  Shared_Notes
drwxrwxrwx 1 root root    0 Jun 26 01:44 'System Volume Information'

mafoelffen@Opti-Ubuntu-Main:~/WIN_G/KVM-VM$ ls -l ~/WIN_G/KVM-VM/
total 28677308
drwxrwxrwx 1 root root         4096 Jul  2 11:42 ARM_Server
-rwxrwxrwx 1 root root   1347223552 Jul  2 00:57 CentOS-8-GenericCloud-8.4.2105-20210603.0.aarch64.qcow2
-rwxrwxrwx 1 root root  21478375424 Jul  1 17:54 fedora_34.qcow2
-rwxrwxrwx 1 root root 161086111744 Jul 11 10:40 rhev-4.4.qcow2
-rwxrwxrwx 1 root root  21478375424 Jul  5 16:22 solaris11-4-UEFI-1.qcow2
-rwxrwxrwx 1 root root  21478375424 Jul  5 16:19 solaris11-4-UEFI.qcow2
-rwxrwxrwx 1 root root  21478375424 Jul  4 09:35 solaris11.qcow2
-rwxrwxrwx 1 root root  26847870976 Jul  6 18:29 ubntu-server-20.04-template-Bios.qcow2
-rwxrwxrwx 1 root root   4061659136 Jun 30 16:37 ubuntu18.04-clone-1.qcow2
-rwxrwxrwx 1 root root   2555772928 Jun 30 15:05 ubuntu18.04-clone.qcow2
-rwxrwxrwx 1 root root  10739318784 Jun 30 21:13 ubuntu18.04.qcow2
-rwxrwxrwx 1 root root  26847870976 Jul  6 19:34 ubuntu-server-20.04-BIOS.qcow2
....Much More ...

```

You can set the permissions to what ever you want... to limit that. Mine is in a closed system. The big sticking point is that Linux type systems have to be able to determine the ownership of the directories are set to the KVM group, and that the users of that group can read and write to the files within. Not to the drive/partition itself... but to a base folder, that you are using to start out from on that mount. It doesn't matter that mount is locally attached or a network share somewhere. I do the same on network shares in my host network, from VM's. Once it is attached... set a point it, that you set the ownership and permissions. My common denominator on all my Linux-Like systems, is that they all have a KVM group that have access to this shared storage...

So the problem is not specifically the filesystem type, It is the same for SMB, NFS and Gluster managed shares. KVM has to see that it has permission to write to it. If it has group ownership, then it is happy.

As for Raw versus QCow2. I'll summarize, because that could easily be it's own thread. You said your biggest concern is lack of space. Then Raw format is the opposite of what you want A Raw disk file gets provisioned as a fixed space "sparse file format"... Meaning it is "always" the fixed max size, with the data written out as such, and the rest written as "zeroes". (Sparse file format "disks", if mounted to the disk,  requires special flags to do an rsync or copy.)  RAW format disk files do not have other features like compression, AES encryption and snapshot. Backup of Raw File Disks require full disk back-up, and have no incremental back-up,  QCow2 Disks are dynamic growing disks, with an upper user set limit size.. The initial provisioned file is written out with just the size of the data written, and grows in size as more date is written. Many refer to this as a "Thin provisioned VM Disk." It allows for compression, encryption and snapshots. Deleted files do take up space, but can be trimmed out to save space using fstrim.

Note that these KVM VM machines above are used/shared  between KVM based hypervisors from different systems. Ubuntu based KVM (and other Linux based KVM), RHEV and VDSM (oVirt). Also note that this "share" Section has both emulated and native ARM VM's that some are used by my Raspberry Pi4 hosting KVM, and mounted to it's section as a network storage resource. (Yes. I get bored and am entertained by stretching things to limits.)

Disclaimer: I do not use NTFS because I prefer it. I actually prefer many other filesystems over it... but it is something that is commonly used by most operating systems as a common ground denominator. It is something that I can access from whatever I am running as an OS. It is also something that I can make behave to do that. For example I use Plex Server as a media server... That service is up, whichever that machine's  OS is up because they point to the same shared files on storage. There are hundreds of ways to do that. This is only one. Yes you can change the mount option to change this...You could even provide it in SELinux by a boolean to do that.. This is just an easy for me to do it this way (once). That way. I can use that by any Linux-Like OS and the behavior is consistent. Maybe I am wrong and there is a better way. But it works for me on this system.

Another quark for that to work on any Linux-Like system, is that you have to turn off "fast bootup" in any Windows system that has access to that shared storage. If you don't it will screw you with all this beyond hope. It will leave the filesystem in an "opened" state.

---

### Post by cryptearth on 2021-07-11
Don't mount the partitions one by one but use the whole raw image without any mounting and set it as a disk for the KVM.
If you'Re using graphical virt-manager:
1) switch to details view
2) click add new device
3) select type: storage
4) on the right panel select "user defined"
5) click browse
6) if you don'T already have a pool set up for the directory which contains the image just click "brwose local" at the bottom
7) select the image
8) the rest of the black magic is handled by virt-manager

---

### Post by bardiamgtgc on 2021-07-11
looks like i was actually overthinking about everything

my ntfs partitions were on a cifs share and i mounted them like i always would and that was causing issues

after trying to run the os on a network ext4 samba partition i got the same issue and i realized its the samba share im having issues with

so after two more hours of looking around i found the issue

while mounting there must've been these two options 
nobrl,uid=libvirt-qemu
lets say this is my value in fstab

//10.0.0.2/p1 /home/fakeshell/p1 cifs username=username,password=password,rw,uid=1000,gid=1000 0 0

it must be like this 

//10.0.0.2/p1 /home/fakeshell/p1 cifs username=username,password=password,rw,nobrl,uid=libvirt-qemu,gid=1000 0 0

now all i have to do is shrink one of my ntfs partitions and create a new network mount point just for that partition with uid=libvirt-qemu if i mount my partition with my data with libvirt-qemu then i wont have write access to my data only read access (with root i can but not with my main user)


thanks to everyone for taking their time and responding to my thread really appreciate it

---

### Post by MAFoElffen on 2021-07-11
> **cryptearth said:**
> Don't mount the partitions one by one but use the whole raw image without any mounting and set it as a disk for the KVM.
If you'Re using graphical virt-manager:
1) switch to details view
2) click add new device
3) select type: storage
4) on the right panel select "user defined"
5) click browse
6) if you don'T already have a pool set up for the directory which contains the image just click "brwose local" at the bottom
7) select the image
8) the rest of the black magic is handled by virt-manager
No disrespect. I know nothing of your background or experience... but your post shows some inexperience. Please read and think about what is said...

Most people would ignore your post, But as a teaching/learning point:

Linux-Like systems cannot read an NTFS filesystem without a mount telling it what kind of filesystem it is dealing with (NTFS). This is before KVM/Qemu can see anything on that system. It has to mount it, somehow, at some time. I can create a Linux System with an NTFS filesystem on the Root drive. It has to mount the Root drive sometime. Right? Mounts occur. In Linux, that is just a way of life.

Linux is not a single user operating system.

Next, Linux doesn't care and doesn't read native NTFS permissions. So you have to help it.

KVM cannot see something that is invisible to that system. It is not a "mind reader", and has no "black magic" to see something that is not mounted (seen) by the system. If if is as access/permissions issue related with that mount, well... Enough said. Nothing else will happen within virt-manager, if it can't access it nor read/write to it, then none of it's utilities can either.  His"specific"  problem is below the KVM layer.

A RAW file takes more space than a qcow2 disk file. Changing that was not related to accessing an NTFS filesystem. It also causes him issues, because he doesn't have unlimited storage space. Size makes a difference to him. RAW files do have a bit better performance, but on most systems today, that is negligible.

I love and have passion for KVM and it's use. "A recommendation" has to be thought out and have to actually be able to work to promote that... Right? We want the OP to be successful in doing what he wants to do, right? But what do I know. Think about how it "actually" works. How the pieces fit together. I'm sure you have plenty to share about your experiences. I applaud your enthusiasm.

The OP's (Original Poster) basic main issue is from having a problem with access/permissions to his NTFS filesystem by his system, using KVM. He tried to work around it... but those workarounds didn't address access/permissions.

---

### Post by TheFu on 2021-07-11
Does CIFS support the necessary file locking for VMs?
I know NFS does, but I've had issues with CIFS file locks before.

BTW, my LVs that are provided to VMs are NOT mounted by the host.  They are mounted only inside the VMs.  The host only passes the LV block device into the VM.

---

### Post by MAFoElffen on 2021-07-11
> **TheFu said:**
> Does CIFS support the necessary file locking for VMs?
I know NFS does, but I've had issues with CIFS file locks before.
LOL. That is where a discussion gets even broader, where there ARE multiple users using the same shared data at once... And that there is a difference between Shares, as a system, and the underlying filesystem's data. If there are multiple users accessing data at the same time, then a Share System is needed to help coordinate that. I think (IMHO) that NFS Shares do a better job at that, and is what I use for my VDSM Storage Pools. But the "Share" System, is on top of the underlying filesystem...

I think this a good quote on that:
> Separate from the share permissions are the filesystem permissions,  which are also applied - once I've been authorized for share access. 
I feel this explains this fairly well: [URL="https://serverfault.com/questions/605485/cifs-and-nfs-permissions-and-underlying-file-systems"]https://serverfault.com/questions/605485/cifs-and-nfs-permissions-and-underlying-file-systems

[/URL]But with just dealing with the filesystem NTFS, Linux doesn't know how to deal with NTFS File permissions unless you are using something like SAMBA to do the Share system permissions. SAMBA does file locking fairly well. Am I explaining that right?

When I am "working"... I spent more time testing that a "Share" has the desired results to a group and users, when I start locking down the screws and inheritance starts taking over. And in a mixed environment, I tend to lean to what kind of system is going t be the major user of that share to determine the share type.

But this has all gone a long way from "running a loop device as a disk image"... LOL

---

### Post by cryptearth on 2021-07-12
I re-cut my reply to try to keep it polite and just to avoid an edit by mods - so, if there's anything more between you and me ... I've sent you a private message. I'd appreciate it if you'd give it a read.
The short version:
I'm aware what a file system is, how a file system driver works and why it's important for an OS to mount it before it can access any data stored on it ... that should be enough about my experience and how likely it is for others to ignore me.

From what I understood up to the point of my reply is this:

OP has some whole-disk image on some storage (the specifics acutally doesn't matter) and has mounted it as a loop device in the host OS. OP also explained the issue to not be able to start the VM.
Where does my reply come from: As far as I understood the question OP seemed to struggle to correctly add a virtual disk to the (K)VM and set the image as its source.

I'm not sure how you got off-topic about OP has issues to access the image or the FS it's stored on. OP wrote s/he was able to mount it in the host OS - so clearly there's access to the file system the image is stored on and to the image itself.

We clearly got a way different understanding of the initial question.

---

### Post by MAFoElffen on 2021-07-12
My apologies to crytoearth. Sometimes I answer before I have a time to think about it. Sometimes I am very self-conscientious about how it may come across. Not my intention at all. I have a passion for helping people. Sometimes my wording is not the best. I know what I want to say. Sometimes it doesn't come across that way My "intent" is good, and sincere.

No slight intended. I apologize for any misunderstanding. That is on me, and my fault. Let's just go on from here. Like I said, I'm sure you have a lot of experience to share.

I am excited to hear about your own experiences on what you are trying to do with your pass-through's in KVM. That is an adventure on it's own.

---

