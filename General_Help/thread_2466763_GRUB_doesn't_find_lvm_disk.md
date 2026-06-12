---
title: "GRUB doesn't find lvm disk"
date: 2021-09-05
forum: General Help
---

### Post by theyeetster on 2021-09-05
So for a few days i've been trying to use lvm to combine/merge/resize 3 disks (for a server). First time i tried to merge them, it worked, restarted and found out that grub doesn't find/boot from the lvm disk, so then i googled how to modify grub so it loads, tried what was suggested to other people, also didn't work, tried myself to modify grub so it can boot, still a no go. 

GRUB Error: [FONT=arial black]"Error: disk 'lvmid/(uuid of disk i persume) not found"


[FONT=arial]Also I want to say that [/FONT][/FONT][FONT=arial black][FONT=arial]I'm more of a beginner with linux.

Tell me if you need any more info.
[/FONT][/FONT]

---

### Post by TheFu on 2021-09-05
Probably best if you run boot-repair (there's a program that can be installed), then post the "boot info" output URL here for more help. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

**_DO NOT let it attempt to repair anything!_**

Linux beginners really shouldn't be doing too much with LVM, unless you have experience with enterprise storage and volume management like AIX, HPUX, Solaris, and VeritasVM have.

---

### Post by theyeetster on 2021-09-06
So I did the boot info, however it only worked when I deleted/formated the disks, so I decided to send 2 output URL's, one from when I formatted the disks and the 2nd when I setup LVM again.

1.Deleted Disks: [https://pastebin.ubuntu.com/p/Ts9sg7SdWy/](https://pastebin.ubuntu.com/p/Ts9sg7SdWy/)
2.New LVM Install: [https://pastebin.ubuntu.com/p/msz8d6PP8V/](https://pastebin.ubuntu.com/p/msz8d6PP8V/)

Also, all I was trying to do with LVM was to merge/resize a disk, since I'm using the PC as a server.

---

### Post by TheFu on 2021-09-06
So, you've completely wiped the system and did a fresh install?
Have you worked through an LVM tutorial?

**I'd love to see the output from **
```
sudo pvs
sudo vgs
sudo lvs
```
Please.
Can't believe that boot-info doesn't include this. ;(

You can't resize a physical disk.  Perhaps you want to resize a partition or resize a logical volume?
Merging storage that is contained on 2 separate storage devices (disks), to be displayed as a single device has lots of points of failure.  If you stripe or concatenate the storage, should 1 disk fail, all the data on both devices that is in the merged LV will be lost. Be 100% certain this is what you actually want to do ... and that you either don't care at all about that data or have excellent backups - large enough to hold it all.

When I look at the 2nd output, it appears you've decided to make root LV 1.5TB in size?  The root LV should be 35G, at most, IMHO.  
I'd keep the OS, applications, and home LVs on a single disk, so that the other storage devices don't need to work for the OS to still boot.  
Create a data LV if you want to have data that spans storage devices.  
Definitely don't have a swap LV span devices either.

Just to save others from getting to deal with the new ubuntu-pastebin junk:
```
$ lsblk .... 
NAME                FSTYPE      UUID                                   PARTUUID                             LABEL PARTLABEL
sda                                                                                                               
&#9500;&#9472;sda1              vfat        0502-AFF4                              9ac5417b-01                                
&#9500;&#9472;sda2                                                                 9ac5417b-02                                
&#9492;&#9472;sda5              LVM2_member bDQXsw-0pGj-XwF8-VMfq-chwU-oveb-2hsDEe 9ac5417b-05                                
  &#9500;&#9472;vgubuntu-root   ext4        8891872e-cb0e-4c4d-a1ee-396889865348                                              
  &#9492;&#9472;vgubuntu-swap_1 swap        d9abe1ba-a6d1-4a8c-a78b-d281469973e3                                              
sdb                                                                                                               
&#9492;&#9472;sdb1              LVM2_member a0qfvN-1NJL-Rf93-74qY-rkbi-SqmV-ZVLo6g 1f2f5ad1-aa8c-4404-9114-1bfa4672559c       
  &#9500;&#9472;vgubuntu-root   ext4        8891872e-cb0e-4c4d-a1ee-396889865348                                              
  &#9492;&#9472;vgubuntu-swap_1 swap        d9abe1ba-a6d1-4a8c-a78b-d281469973e3                                              
sdc                                                                                                               
&#9492;&#9472;sdc1              LVM2_member jAxWuk-i8CU-QWhv-WVsS-39hW-CIsO-VkiJEL cc2dd901-01                                
  &#9492;&#9472;vgubuntu-root   ext4        8891872e-cb0e-4c4d-a1ee-396889865348

$ lvscan
  ACTIVE            '/dev/vgubuntu/root' [1.63 TiB] inherit
  ACTIVE            '/dev/vgubuntu/swap_1' [<3.96 GiB] inherit

$ parted -lm
sda:480GB:scsi:512:512:msdos:ATA CT480BX500SSD1:;
1:1049kB:538MB:537MB:fat32::boot;
2:539MB:480GB:480GB:::;
5:539MB:480GB:480GB:::lvm;
sdb:1000GB:scsi:512:4096:gpt:ATA WDC WD10EFRX-68F:;
1:1049kB:1000GB:1000GB:::lvm;
sdc:320GB:scsi:512:512:msdos:ATA ST3320613AS:;
1:1049kB:320GB:320GB:::lvm;

```

---

### Post by theyeetster on 2021-09-06
Yes, I've wiped the system, didn't have anything other than LVM on there (as it was my 10th attempt trying to get it to work)
The Tutorial I went thru is this : [https://www.youtube.com/watch?v=214rUhQe7B4](https://www.youtube.com/watch?v=214rUhQe7B4)

Code from the commands:

pvs: ```
 PV         VG       Fmt  Attr PSize    PFree
  /dev/sda5  vgubuntu lvm2 a--   446,62g    0
  /dev/sdb1  vgubuntu lvm2 a--  <931,51g    0
  /dev/sdc1  vgubuntu lvm2 a--  <298,09g    0

```

vgs: ```
 VG       #PV #LV #SN Attr   VSize  VFree
  vgubuntu   3   2   0 wz--n- <1,64t    0

```

lvs: ```
  LV     VG       Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgubuntu -wi-ao----  1,63t                                                    
  swap_1 vgubuntu -wi-ao---- <3,96g                                                    


```

And yes, I meant logical volume, sorry.
Yes, I know that merging disks will give it that risk.

And yes, I need root  (or another partition) to be that big, since I'm using [Pterodactyl]("https://pterodactyl.io/project/introduction.html") to host servers, unless there's some other method to use a different partition that is.

the 1TB and 320GB disk's (the 2 other ones) are not required to boot (atleast I think so, resizing root may have done that)
Alright, I'll try using a data LV.

---

### Post by TheFu on 2021-09-06
The root LV should be 35G or less.

Where do the docker containers get placed?  Create a separate LV for just that and mount it where needed. Reduce the risk for the OS crashing when it is just a docker containers that need to be impacted.  From a performance standpoint, I'd put the OS on a separate SSD from the docker junk.
You aren't limited to just 1 VG. It is fine to have more.

---

### Post by theyeetster on 2021-09-06
Alright, So I'll resize root and make it 35G's. Make 2 more VG's (for docker containers and for storage) Tho this will make it harder, if not impossible since I don't think you can use different VG's/Volumes for Pterodactyl's storage. I'll re-install ubuntu again and try it. This should make grub happy, correct?

EDIT: Resizing root to 35G breaks it, I'll re-install Ubuntu (again) and make it like 50G.

---

### Post by TheFu on 2021-09-06
> **theyeetster said:**
> Alright, So I'll resize root and make it 35G's. Make 2 more VG's (for docker containers and for storage) Tho this will make it harder, if not impossible since I don't think you can use different VG's/Volumes for Pterodactyl's storage. I'll re-install ubuntu again and try it. This should make grub happy, correct?

EDIT: Resizing root to 35G breaks it, I'll re-install Ubuntu (again) and make it like 50G.

If it were me, I'd have 1 VG for the OS and anything on the same single disk. 
And another VG to span across multiple physical disks.  We do want to keep this as simple as possible, but not lose the best things that LVM provides, which are:
[LIST]
[*]snapshots
[*]trivial to create new LVs
[*]trivial to extend existing LVs, as needed (I target only 3 months of expected storage use)
[/LIST]

After 25+ yrs as a Unix admin, I've never been able to guess how much storage will be needed in advance. That's partially why I love LVM.  It provides options when I didn't guess right last year - so I can add storage exactly where it is needed.

However, after losing 80% of all my data, I do not span LVs across physical disks and never will, unless I also have excellent backups.  The largest LV I'll ever create (for certain values of "ever" ;) ) will be 4TB.  I have a few 8TB HDDs, but because most of my other HDDs are 4TB and smaller, I chose to make no LV larger than 4TB so I could always get a replacement HDD for ~$50 for either primary or backup storage.

For example:
```
$ sudo lvs
  LV             VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  desk-2104      hadar-vg -wi-a-----  20.00g                                                    
  libvirt-lv     hadar-vg -wi-ao---- 175.00g                                                    
  lv-blog44-1804 hadar-vg -wi-ao----  16.20g                                                    
  lv-regulus     hadar-vg -wi-ao----  30.00g                                                    
  lv-regulus-2   hadar-vg -wi-ao----  10.00g                                                    
  lv-spam3       hadar-vg -wi-a-----  10.00g                                                    
  lv-tp-lxd      hadar-vg twi-a-tz--  32.23g             0.00   10.06                           
  lv-vpn09-2004  hadar-vg -wi-ao----   7.50g                                                    
  lv-xen41-1804  hadar-vg -wi-ao----  12.50g                                                    
  lv-zcs45-1604  hadar-vg -wi-ao----  25.00g                                                    
  lv-zcs45-1804  hadar-vg -wi-a-----  25.00g                                                    
  lxd-lv         hadar-vg -wi-ao----  60.00g                                                    
  root           hadar-vg -wi-ao----  32.33g                                                    
  swap_1         hadar-vg -wi-ao----   4.25g                                                    
  lv-backups     vg-hadar -wi-ao---- 465.72g         
```      
Most of those aren't mounted on the system. They are presented to either VMs or containers.  For the extra storage just for VMs and containers, those are directly mounted exactly where needed:  
```
$ dft
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   18G   13G  58% /
/dev/sdb1                         ext2  720M  165M  519M  25% /boot
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   15G   42G  26% **/var/lib/lxd**
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  145G   19G  89% **/var/lib/libvirt**
```
The libvirt mount is only for toy VMs.  Production VMs get an LV directly presented. Most of that storage is for a Windows VM that I've moved around between 3+ different VM host systems and never got around to converting the file-based VM storage into LVM storage.

When doing a new install, I stop the installation program and go setup the desired storage layout using a custom script that forces little things like GPT, and the sizes for /, /home, /var, /boot/ and /boot/efi that I want. **sgdisk**, **mkswap** and **mkfs** are the primary tools. After many years of putting up with whatever the installer did, just got tired of having to go back and fix everything post-install.  

It is also handy to have the partition types consistently correct and file systems created correctly. After that is all done, back inside the install, the "Do Something Else" --> Custom Storage layout just needs picking which LVs and partitions get used for which install locations.  That's 100x easier than trying to use the installer to create exactly what is needed, IMHO.  I actually make the root and home LVs smaller, since it is trivial to resize larger in a few months. I've setup so both legacy and UEFI booting can work with LVM.  At some point in the future, I might understand how to get /boot/ setup as an LV that can be booted.  I've not seen that with Ubuntu.  Plus, my laptops have been LUKS encrypted for a very long time, and I think LUKs requires a separate /boot/ partition.

---

### Post by theyeetster on 2021-09-07
Alright, that's fine and all, but I'm still not entirely sure what I should be doing.

---

### Post by TheFu on 2021-09-07
> **theyeetster said:**
> Alright, that's fine and all, but I'm still not entirely sure what I should be doing.

And I'm not sure what you've done.  I've suggested a single disk for the OS and normal applications.  That would use 1 VG.
Then add 2 more disks and merge them together (knowing the failure issues) into another VG.

Inside the OS VG (call it vg00), create LVs that should never span multiple disks.  You don't want to have an OS failure just because some data storage fails, right?

Inside the spanning VG (call it vg-span), create LVs for anything you want to span multiple disks and don't care if they disappear when 1 disk fails.

You can mount LVs anywhere it is needed, at any level of directory.  That was the point of the post showing /dev/mapper/hadar--vg-libvirt--lv as an LV that was mounted to /var/lib/libvirt.  I suppose I could have mounted it on /var, but that would impact what is needed for the OS to boot, not just for the OS to run virtual machines.  

I hope that's clearer.

In the end, you'll have 3 disks, 2 VGs, and probably 4 LVs and 2 partitions with file systems along with 3 partitions marked for LVM use.
In the last few months, I drew a diagram to show a simple LVM setup on 1 disk.  It shows a LUKS encryption container, but you can ignore that and just see the partition (sda3) holding a PV/VG on the single disk.  Don't worry if the exact partition names/numbers don't match what you have.

Sorry that I didn't show 2 more disks using the same VG.
[ATTACH=CONFIG]289136[/ATTACH]

Heck, I'm tempted to create a little VM to show this.  Maybe later this week, if you are still stuck.

---

### Post by theyeetster on 2021-09-08
Alright, I'll try doing that, will post again when I've done it/failed to do it.

---

### Post by theyeetster on 2021-09-11
Good news, I managed to do it, and it worked, thank you for the help :)

---

