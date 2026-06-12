---
title: "on boot luks partition is not decrypted so that the lvm root partition is mounted"
date: 2018-02-26
forum: General Help
---

### Post by harterc2 on 2018-02-26
I have a boot partition and an encrypted liuks lvm partion with mirroring on 2 hard drives.
It has been working on kernel verson 4.13.0-26-generic.  grub boots the initrd is loaded, the luks partition is decrypted/opened, the lvm is then recognized and mounted as root.
But lately it does not seem to work with more recent kernels. (4.13.0-32-generic 4.13.0-36-generic 4.14.22 )  When it fails the initramfs drops to a shell (busybox?).  I have found that this shell does not even have cryptsetup in it.  So I decided to look at the initramfs-tools.  The hooks created the initramfs and the scripts are run on boot.  By changing setup to a "y" I found that I could build initrds with cryptsetup included.  Once I was dropped ot a shell I was able to manually mount the /dev/mapper luks root file and fully boot after exiting the shell.  I was seeing error messages regarding lvmetad not being able to find the default directory (/run/lvm) where its socket file is stored.  This message would appear many times until finally I was dropped down into a shell.  It seems that lvm is not recognizing my mirrored lv group root disk because it is still encrypted and not open(LuksOpen).  I can only boot with 4.13.0-26-generic kernel.  Anything newer than that and it fails as described above.  I even built a copy of the newest stable kernel and it also failed.  It causes me to wonder if there might be some changes made in the kernel after a certain version. Or maybe I need the latest version of initramfs-tools or lvm which is not available in xenial. Or maybe some modules need to be loaded which were.
4.13.0-26-generic #29~16.04.2-Ubuntu SMP Tue Jan 9 22:00:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Here is my /etc/fstab file:
```
/dev/mapper/kubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=399abf5f-49c3-451b-a4d0-44b209ebf27a /boot           ext2    defaults        0       2
/dev/mapper/sdd7_crypt none            swap    sw              0       0

```
Here is my /etc/crypttab file:
```
sdb1_crypt UUID=C0Xirg-iI2Z-koAz-kR4y-beSy-LLz7-yFXo7f none luks
sdd7_crypt UUID=e4745848-2e97-4c79-8e27-90d404913c2f none luks

/devsda and /dev/sdb are in the same volume group and mirror each other.

lvm> lvscan
  ACTIVE            '/dev/kubuntu-vg/root' [914.99 GiB] inherit
  ACTIVE            '/dev/kubuntu-vg/swap_1' [15.94 GiB] inherit
lvm> lvs
  LV     VG         Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   kubuntu-vg rwi-aor-r- 914.99g                                    100.00          
  swap_1 kubuntu-vg -wi-s-----  15.94g    

lvm> pvs
  PV                     VG         Fmt  Attr PSize   PFree 
  /dev/mapper/sdb1_crypt kubuntu-vg lvm2 a--    1.82p  1.82p
  /dev/mapper/sdc5_crypt kubuntu-vg lvm2 a--  931.03g 96.00m

vm> lvdisplay
  --- Logical volume ---
  LV Path                /dev/kubuntu-vg/root
  LV Name                root
  VG Name                kubuntu-vg
  LV UUID                eanUsV-2PrL-0c7f-hnwY-yPdn-1AXr-k69Thf
  LV Write Access        read/write
  LV Creation host, time kubuntu, 2017-06-07 19:50:16 -0400
  LV Status              available
  # open                 1
  LV Size                914.99 GiB
  Current LE             234238
  Mirrored volumes       2
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:7
   
  --- Logical volume ---
  LV Path                /dev/kubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                kubuntu-vg
  LV UUID                pla09a-5njM-zzFS-yqb1-sk79-cPSn-t3it0q
  LV Write Access        read/write
  LV Creation host, time kubuntu, 2017-06-07 19:50:16 -0400
  LV Status              suspended
  # open                 0
  LV Size                15.94 GiB
  Current LE             4081
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:8
   
lvm> 

ii  initramfs-tools                    0.122ubuntu8.10        all                    generic modular initramfs generator (automation)
ii  initramfs-tools-bin                0.122ubuntu8.10        amd64                  binaries used by initramfs-tools
ii  initramfs-tools-core               0.122ubuntu8.10        all                    generic modular initramfs generator (core tools)

blkid
/dev/mapper/sdc5_crypt: UUID="bNwyKm-vdcz-eLBs-4fNc-g2uy-qI7P-9pQ73W" TYPE="LVM2_member"
/dev/mapper/sdb1_crypt: UUID="C0Xirg-iI2Z-koAz-kR4y-beSy-LLz7-yFXo7f" TYPE="LVM2_member"
/dev/sda1: UUID="88498ea9-f8a8-4e77-99a7-ee5e3abb9dd2" TYPE="crypto_LUKS" PARTUUID="2a5644ff-01"
/dev/sdb1: UUID="bf83a99c-d56f-47ca-80df-d10b5cada999" TYPE="crypto_LUKS" PARTUUID="2b181b1c-01"
/dev/sdc1: UUID="399abf5f-49c3-451b-a4d0-44b209ebf27a" TYPE="ext2" PARTUUID="35e4cc6f-01"
/dev/sdc5: UUID="314bbeb6-5ced-4a3a-bb4f-3c25a3be9809" TYPE="crypto_LUKS" PARTUUID="35e4cc6f-05"
/dev/sdd1: UUID="78e3e516-fb8b-4204-8bd5-2803420e3799" TYPE="crypto_LUKS" PARTUUID="00042dcf-01"
/dev/sdd5: UUID="ba279ab8-66f5-432a-a8b3-0c2864898d6d" TYPE="crypto_LUKS" PARTUUID="00042dcf-05"
/dev/sdd6: UUID="545decc3-6e04-4be4-ad31-36f4e6beaf25" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="00042dcf-06"
/dev/sdd7: UUID="e4745848-2e97-4c79-8e27-90d404913c2f" TYPE="crypto_LUKS" PARTUUID="00042dcf-07"
/dev/mapper/kubuntu--vg-root_rimage_0: UUID="968dce22-be0e-4185-ae1f-a2ae98c51ea2" TYPE="ext4"
/dev/mapper/kubuntu--vg-root: UUID="968dce22-be0e-4185-ae1f-a2ae98c51ea2" TYPE="ext4"
```

---

### Post by wildmanne39 on 2018-02-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by harterc2 on 2018-03-01
I tried to look at the source code.  It seems that the problem is in the cryptsetup package.  It supposedly builds the cryptroot hook and script file.
If you try to build it you get this message "configure: error: You need popt 1.7 or newer to compile.

"  However the latest version is 1.203. xenial has version 1.16-10.  The package won't build as is and the file is not there yet.

---

### Post by harterc2 on 2018-03-01
There are kernel command line options such as cryptops that might get things to work.  However before things worked by default.

---

### Post by harterc2 on 2018-03-02
I have looked at the source code some more.  I found what appears to be a  bug in cryptroot script.  I have found similar postings as far back as  2011.  The script tries to activate the volume group before the luks  container in which it is in is even opened.  It will fail unless vgscan  has the ability to scan inside luks containers. Maybe it did but now  does not or did at one time.
the source= parameter is the UUID or  LABEL of the ENCRYPTED volume.  the crypttarget= parameter is what would  follow the string "/dev/mapper/"  In my case that would be  "kubuntu--vg-root".  The script does not ever see the  /dev/mapper/kubuntu--vg-root so it drops to a shell.  It hasn't even  tried to luksOpen the luks container with the volume group in it.  So  maybe if it was created as a volume group with a luks container in it  then it would work.

---

### Post by harterc2 on 2018-03-11
I am back on-line with artful.  I was dropped down to a shell and able to do a luksOpen.Aslo I used all the command line parameters that were available in the cryptroot script.  There are now in my default grub file so my grub menu has them on the command line which boots the kernel image.  I was having problems getting the lv to be activated.  That was while running the live artfull disk.I kept getting a system busy message from a sysctl.
I made one change to the source code, but have not tested it yet.  I have been down so long I don't want to reboot yet.

I have attached the patch.  Someone may have already done something similar.  No it looks like I don't have permission yet to upload attachments.

Let me past it here then:

```

--- a/debian/initramfs/cryptroot-script
+++ b/debian/initramfs/cryptroot-script
@@ -223,7 +223,7 @@
        modprobe -q dm_crypt
 
        # Make sure the cryptsource device is available
-       if [ ! -e $cryptsource ]; then
+       if [[ ! -e $cryptsource && !(/sbin/cryptsetup isLuks ${cryptheader:-$cryptsource} >/dev/null 2>&1) ]]; then
                activate_vg
        fi

```

---

### Post by harterc2 on 2018-03-13
The above patch fails even though I tested the command.  It seems that busybox does not use bash and has fewer features.

---

### Post by harterc2 on 2018-03-13
I am going to try this patch.
I tested it in a dash shell.
```
--- a/debian/initramfs/cryptroot-script
+++ b/debian/initramfs/cryptroot-script
@@ -223,7 +223,7 @@
        modprobe -q dm_crypt
 
        # Make sure the cryptsource device is available
-       if [ ! -e $cryptsource ]; then
+       if  [ ! -e $cryptsource ] && ! /sbin/cryptsetup isLuks ${cryptheader:-$cryptsource} >/dev/null 2>&1 ; then
                activate_vg
        fi

```

---

### Post by harterc2 on 2018-04-28
I had some good reboots without it dropping to a shell.   There are many parameters that can be set, and it seems there are some left over from previous setups.
Some may need to be set, but don't really provide any useful information.
I did not have to make many code changes.  I mostly set parameters on the linux kernel boot command line and in some files.
Upload does not seem to work so I will paste the one patch that I made
```
--- a/debian/initramfs/cryptroot-script
+++ b/debian/initramfs/cryptroot-script
@@ -223,7 +223,7 @@
        modprobe -q dm_crypt
 
        # Make sure the cryptsource device is available
-       if [ ! -e $cryptsource ]; then
+       if  [ ! -e $cryptsource ] && ! /sbin/cryptsetup isLuks ${cryptheader:-$cryptsource} >/dev/null 2>&1 ; then
                activate_vg
        fi
 
@@ -324,7 +324,7 @@
                # See if we need to setup lvm on the crypto device
                #if [ "$FSTYPE" = "lvm" ] || [ "$FSTYPE" = "lvm2" ]; then
                if [ "$FSTYPE" = "LVM_member" ] || [ "$FSTYPE" = "LVM2_member" ]; then
-                       if [ -z "$cryptlvm" ]; then
+                       if [ -z "$cryptlvm" ]  && [ -z "cmdline_root" ] ; then
                                message "cryptsetup ($crypttarget): lvm fs found but no lvm configured"
                                return 1
                        elif ! activate_vg; then
cryptroot.diff (END)

```
I made some changes to the default grub config to set the kernel command line parameters.
In /etc/default I set:
GRUB_CMDLINE_LINUX_DEFAULT="quiet verbose root=/dev/vg1/root cryptopts=source=UUID=314bbeb6-5ced-4a3a-bb4f-3c25a3be9809,target=sdc5_crypt,cryptlvm=sdc5_crypt,rootdev"
GRUB_ENABLE_CRYPTODISK=y

My /etc/crypttab file is:
sdc5_crypt UUID=314bbeb6-5ced-4a3a-bb4f-3c25a3be9809   none luks
sdd7_crypt UUID=e4745848-2e97-4c79-8e27-90d404913c2f none luks

In my /etc/fstab file:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/vg1-root  /               ext4    errors=remount-ro 0       1
/dev/mapper/sdd7_crypt none            swap    sw              0       0
UUID=545decc3-6e04-4be4-ad31-36f4e6beaf25       /boot   ext3    defaults        0       2

blkid gives:
/dev/sdc5: UUID="314bbeb6-5ced-4a3a-bb4f-3c25a3be9809" TYPE="crypto_LUKS" PARTUUID="35e4cc6f-05"
/dev/sdd6: UUID="545decc3-6e04-4be4-ad31-36f4e6beaf25" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="00042dcf-06"
/dev/mapper/sdc5_crypt: UUID="bNwyKm-vdcz-eLBs-4fNc-g2uy-qI7P-9pQ73W" TYPE="LVM2_member"
/dev/mapper/vg1-root: UUID="968dce22-be0e-4185-ae1f-a2ae98c51ea2" TYPE="ext4"
/dev/mapper/sdd7_crypt: UUID="14337860-60ec-4c92-a436-359ab7241e8f" TYPE="swap"




My /dev/sdc5 partition is Luks formatted.  In that is a logical volume of my root partition.  My swap partition is on /dev/sdd7 and is luks formatted.
My /boot partition is unencrypted on /dev/sdd6.
I have heard that it is possible to have an encrypted boot partition, but I may try that later.
The whole crypto config is not robust.  Just one change somewhere will break it, which is probably what happened.

---

