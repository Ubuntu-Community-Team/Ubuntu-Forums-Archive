---
title: "'cp' issue - fast copying of copies, slow copying of originals"
date: 2014-10-04
forum: General Help
---

### Post by Si_F on 2014-10-04
Hi

While working on some scripting I had some performance issues and after lengthy efforts came to an odd conclusion that 'cp' performs better on copied files than on the originals and 'rsync' behaves the other way round!

I'm running the following on a VM:
    Linux unixtest 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Below is my testing

Create some data:
```
mkdir 1
cd 1
for i in {1..50000}; do dd if=/dev/urandom of=$i.xml bs=1K count=10; done
cd ..
cp -r 1 2

```

Try copying and rsyncing the data in directory 1 and 2, flushing disk cache between each operation:
```
$ rm -rf 1copy 2copy; sync; sudo sh -c 'echo 3 > /proc/sys/vm/drop_caches'; echo "Rsync 1"; /usr/bin/time rsync -a 1 1copy; sync; sudo sh -c 'echo 3 > /proc/sys/vm/drop_caches'; echo "Rsync 2"; /usr/bin/time rsync -a 2 2copy
Rsync 1
    3.62user 3.76system 0:13.00elapsed 56%CPU (0avgtext+0avgdata 5072maxresident)k
    1230600inputs+1200000outputs (13major+2684minor)pagefaults 0swaps
Rsync 2
    4.87user 6.52system 5:06.24elapsed 3%CPU (0avgtext+0avgdata 5076maxresident)k
    1231832inputs+1200000outputs (13major+2689minor)pagefaults 0swaps


$ rm -rf 1copy 2copy; sync; sudo sh -c 'echo 3 > /proc/sys/vm/drop_caches'; echo "Copy 1"; /usr/bin/time cp -r 1 1copy; sync; sudo sh -c 'echo 3 > /proc/sys/vm/drop_caches'; echo "Copy 2"; /usr/bin/time cp -r 2 2copy
Copy 1
    0.48user 6.42system 5:05.30elapsed 2%CPU (0avgtext+0avgdata 1212maxresident)k
    1229432inputs+1200000outputs (6major+415minor)pagefaults 0swaps
Copy 2
    0.33user 4.17system 0:11.13elapsed 40%CPU (0avgtext+0avgdata 1212maxresident)k
    1230416inputs+1200000outputs (6major+414minor)pagefaults 0swaps

```
As you can see cp of previously copied data is way faster and rsync of the original data is way faster but reversed they both perform slowly and I'm at a loss as to why.

I've tried this on both Server and Desktop versions of Ubuntu 14.04.1

The underlying disk is a simple SATA drive, no RAID. I've also tried this on an older version of Ubuntu Server, 12 I think on a physical machine with RAID 5 SAS drives and the behaviour is the same.

Appreciate any insight into what is going on?

Thanks

Si

---

### Post by matt_symes on 2014-10-04
Hi

I'm intrigued.

Let's take cp first.

Try dropping the caches before *both* cp commands; the original data and the copied data. Does that make any difference ?

Certainly in the first copy it will not have the locations of the files to copy cached as you have dropped all the caches but if you don't drop the caches before the second cp command then it may have the locations and possible the some file data cached still.

Drop the caches before both cp commands to make it a fair fight and post back the results.

Kind regards

---

### Post by TheFu on 2014-10-04
Which VM?
Which storage (virtio / passthru)?
Which storage type?  qcow2, raw, vmdk, vdi, something else?
Any LVM anywhere?
Have you disabled caching of the storage inside the VMs?

When it comes to storage performance inside VMs - there are many choices which impact performance.

---

### Post by Si_F on 2014-10-04
Hi

I do drop the cache before each, I just strung it all together on one long command, if you check there is a cache clear before each command :-)

Si

---

### Post by matt_symes on 2014-10-04
Hi

> **TheFu said:**
> Which VM?
Which storage (virtio / passthru)?
Which storage type?  qcow2, raw, vmdk, vdi, something else?
Any LVM anywhere?
Have you disabled caching of the storage inside the VMs?

When it comes to storage performance inside VMs - there are many choices which impact performance.

These are excellent questions.

Kind regards

---

### Post by matt_symes on 2014-10-04
Hi

> **Si_F said:**
> 

I do drop the cache before each, I just strung it all together on one long command, if you check there is a cache clear before each command :-)

Si

Crickey. How'd i miss that :)

Kind regards

---

### Post by Si_F on 2014-10-04
> **TheFu said:**
> Which VM?
Which storage (virtio / passthru)?
Which storage type?  qcow2, raw, vmdk, vdi, something else?
Any LVM anywhere?
Have you disabled caching of the storage inside the VMs?

When it comes to storage performance inside VMs - there are many choices which impact performance.

I think these are the right answers to your questions, I basically setup a new VM with defaults for almost everything just to test this:
[LIST]
[*]VMWare version 8
[*]Not sure it's running on a SCSI controller VMWare created
[*]VMDK Thick Provisioned Lazy Zeroed
[*]No idea, I accepted all the defaults when I installed Ubuntu
[/LIST]

I get the same issue on a physical server too btw, I can just do more messing around with the VM so using that at the moment.

Si

---

### Post by Si_F on 2014-10-04
I hunted around and found some relevant commands to get as much disk info as I could:

```
$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/unixtest-vg/root
  LV Name                root
  VG Name                unixtest-vg
  LV UUID                oVOxic-Sw4W-uQE9-brmt-HPrW-IJK7-FAXM8c
  LV Write Access        read/write
  LV Creation host, time unixtest, 2014-10-02 19:17:54 +0100
  LV Status              available
  # open                 1
  LV Size                91.74 GiB
  Current LE             23486
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0


  --- Logical volume ---
  LV Path                /dev/unixtest-vg/swap_1
  LV Name                swap_1
  VG Name                unixtest-vg
  LV UUID                DzwfIK-1CL4-lPWu-4caT-J0hm-4cZe-idOIp5
  LV Write Access        read/write
  LV Creation host, time unixtest, 2014-10-02 19:17:54 +0100
  LV Status              available
  # open                 2
  LV Size                8.00 GiB
  Current LE             2047
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1


$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               unixtest-vg
  PV Size               99.76 GiB / not usable 2.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              25538
  Free PE               5
  Allocated PE          25533
  PV UUID               Bejkm6-aibd-n1HO-qLpR-uMag-GKMy-yrdGLc

$ cat /proc/scsi/scsi
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: NECVMWar Model: VMware IDE CDR10 Rev: 1.00
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: VMware   Model: Virtual disk     Rev: 1.0
  Type:   Direct-Access                    ANSI  SCSI revision: 02

$ sudo lshw -class disk
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       size: 100GiB (107GB)
       capabilities: partitioned partitioned:dos
       configuration: sectorsize=512 signature=00079035
  *-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram partitioned partitioned:dos
       configuration: signature=56d7f18d status=ready

```

---

### Post by TheFu on 2014-10-04
Double buffering is to be avoided.  Let either the hostOS **or** the VM do disk buffering. Generally (always?) - I use LVM on VM hosts, but NEVER (generally?) inside a VM-GuestOS.

I haven't used VMware Workstation since the early 2000s - sorry - can't help more. I get excellent disk performance with KVM on LVM hosts (with disk buffering disable inside the clientVM settings (this is a VM setting, not something the client OS does).

BTW - a slow disk is a slow disk with or without VMs.  My play machine as a WD-Blue inside and it sucks compared to the WD-Blacks.  I always use virtio (not SATA/SCSI) for virtual HDDs.

---

### Post by Si_F on 2014-10-04
> **TheFu said:**
> Double buffering is to be avoided.  Let either the hostOS **or** the VM do disk buffering. Generally (always?) - I use LVM on VM hosts, but NEVER (generally?) inside a VM-GuestOS.

I haven't used VMware Workstation since the early 2000s - sorry - can't help more. I get excellent disk performance with KVM on LVM hosts (with disk buffering disable inside the clientVM settings (this is a VM setting, not something the client OS does).

BTW - a slow disk is a slow disk with or without VMs.  My play machine as a WD-Blue inside and it sucks compared to the WD-Blacks.  I always use virtio (not SATA/SCSI) for virtual HDDs.

Sadly there are no options in the VMWare to fiddle with the buffering or that I can see to select virtio (unless that's the "permanent" disk option).

The issue though isn't really a VM one as this happens on a big physical server I have that isn't a VM, just I can hack around with Ubuntu settings on the VM as much as I like as I built it just to test this.

My next thoughts are to maybe try and download other types of Linux to see if this is an Ubuntu specific issue.

Thanks

Si

---

### Post by TheFu on 2014-10-04
Also - be certain to read-up on the rsync options. It behaves different than expected for local copies (vs remote) unless you specifically tell it do something smarter.  It only thinks storage is remote if it isn't mounted.

For me, it was bad enough that I stopped using rsync for backups of VMs and started using rdiff-backup inside each VM just like it was a physical installation. That got my backups which were taking almost an hour for each VM down to 1-3 minutes, depending on the services I need to quiesce before the backup starts.  The entire email communications server takes a longer to stop, backup, restart than I'd like, but the email front-ends are still up and accepting inbound messages always.

---

