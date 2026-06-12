---
title: "main deskktop environment as VM using KVM"
date: 2024-07-13
forum: General Help
---

### Post by ValentynPrumers on 2024-07-13
I am thinking about running my main OS as a VM (using KVM).

My plan is to do a bare metal install of ubuntu on my laptop. I will not install any software on this OS, and only use
it to run a VM (kubuntu, using KVM, a type 1 hypervisor).  And then use that VM for all my work.  The reason is that 
its super easy to rollback if you break your system (using screenshots). Also its easy to backup the entire VM (by 
copying the .qcow2 and xml settings files). After working with some VMs it just seems super conveniant to also use it as
your main OS>

The only downside of this approach is of course performance. I am not a resource heavy user. No video editing and minimal
photo editing. 

My hardware: Dell XPS 17 9720. 16GB DRAM, CPU (12 x physical cores and 8 threads for a total of 20 virtual cores). If I will implement 
this setup i am even thinking about upgrading to 32GB of ram (just to make the VM run as fast as possible)


Couple of questions:

1. Does this seem like a good idea? And is ubuntu the best choice for the host OS?

2. Will my hardware be fast enough to let the experience of the VM be "virtually" (lol) the same as if i had done a bare metal install?

3. I want to give this VM as much cpus and memory in KVM as possible. But the host also needs something to operate the VM. Any guidance how much
i can give the VM?

Thanks :)

---

### Post by currentshaft on 2024-07-13
I run virtualized instances on my laptop (for a different reason: security isolation) and the big downside is graphical applications are painfully slow.

What are you doing to break your system so often that it needs to be snapshotted? I've rarely come across an issue that wasn't able to be fixed from live boot.

---

### Post by TheFu on 2024-07-13
Since 2008, I've been doing this. My main desktop is currently running inside a Linux Mint VM with KVM/QEMU.  I use LVM LVs for the storage backend for each guest VM.  The LV is provided to each guest VM as a block device.  The storage isn't available to the hostOS to screw up without some specific commands.  I treat every VM like it is a physical machine for backup and restore purposes.  LVM supports volume manager snapshots.  If you aren't used to volume managers, you don't really know what a snapshot is.

Is Ubuntu the best choice?  It depends.  Many considerations.  More and more, I think the answer is no.  In 10.04, the answer was definitely yes.

You can tune VMs to provide really great performance. Storage is the most important thing to get correct.  If you keep everything on an NVMe SSD - the hostOS and all the guestOSes, then most storage tuning isn't required.  Always leave at least 1GB of RAM for the hostOS. Don't provide too much RAM to any guestOS. You can always increase the RAM later. Same for the number of CPUs. Don't provide too many.

Here's what my desktop VM sees from inside:
```
$ inxi -bz
System:
  Kernel: 5.15.0-113-generic x86_64 bits: 64 Desktop: N/A
    **Distro: Linux Mint 21.3 Virginia**
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996)
    v: pc-i440fx-focal serial: <superuser required>
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.13.0-1ubuntu1.1
    date: 04/01/2014
CPU:
  Info: **2x 1-core AMD EPYC**-Rome [SMP] speed (MHz): avg: 4200
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel
  Display: server: X.Org v: 1.20.13 driver: X: loaded: N/A
    unloaded: fbdev,modesetting,vesa gpu: qxl note:  X driver n/a
    resolution: 1920x1200~60Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge
    driver: piix4_smbus
  Device-2: Red Hat Virtio network driver: virtio-pci
Drives:
  Local Storage: total: **raw: 40 GiB** usable: 76.16 GiB used: 21.45 GiB (28.2%)
Info:
  Processes: 251 Uptime: 4d 22h 41m **Memory: 5.74 GiB** used: 4.98 GiB (86.8%)
  Shell: Bash inxi: 3.3.13
```
So, to summarize the VM, it has 2 vCPUs, 6GB of RAM, uses the QXL video driver, runs Linux Mind Virginia (21.3).  Currently, the largest 2 processes are Firefox and Thunderbird (lots of bloat in Mozilla stuff) and I use virt-io for disk and network drivers.  The hostOS is a hexacore Ryzen 5600G w/ 32G of RAM, 1TB NVMe and about 10TB of HDD storage (I didn't count it).

I'm in the process of replacing 4 x 2TB HDDs in RAID1 with 2x 8TB HDDs which won't have RAID, but will be delay-mirrored daily. This will reduce the power requirements for the system and the remaining HDDs will have better cooling, increasing the lifespan for each.  That's the theory.

Beware, if you use file-based (qcow2) VM storage, you'll need to have room in /var/lib/libvirt/ to hold the VMs if you use libvirt+kvm+qemu and virt-manager.  I allocate separate storage for VMs.

Oh, I forgot, my Linux Mint install uses ZFS for the internal file system, so it shows up in the hostOS storage layout a little different from the other VMs.
```
nvme0n1                      disk             
&#9500;&#9472;nvme0n1p1                  part vfat          50M   43.2M    12% EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                  part ext4         600M  237.1M    51% boot       /boot
&#9492;&#9472;nvme0n1p3                  part LVM2_membe   465G                           
  &#9500;&#9472;vg00-swap                lvm  swap         4.1G                           [SWAP]
  &#9500;&#9472;vg00-root--00            lvm  ext4          35G   23.7G    25% root       /
  &#9500;&#9472;vg00-var                 lvm  ext4          55G   32.9G    34% var        /var
  &#9500;&#9472;vg00-home                lvm  ext4          26G     14G    40% home       /home
  &#9500;&#9472;vg00-ubuntu2204--srv     lvm                15G                           
  &#9500;&#9472;vg00-ubuntu22.04--srv--2 lvm                15G                           
  &#9500;&#9472;**vg00-Mint21.1**            lvm  **zfs_member**    **40G**                rpool      
  &#9500;&#9472;vg00-lxd                 lvm  zfs_member    50G                lxd        
  &#9500;&#9472;vg00-lv--vpn09--2004     lvm               7.5G                           
  &#9500;&#9472;vg00-lv--blog44          lvm              30.2G                           
  &#9500;&#9472;vg00-lv--xen41--1204     lvm              12.5G                           
  &#9492;&#9472;vg00-lv--zcs45--1604     lvm                35G                           

```  
The storage that doesn't show mounts is either swap or for VMs.  Anyway, hope this is useful.

---

### Post by TheFu on 2024-07-13
If you do things correctly, you can pick up VMs and drop it onto completely different hardware and have "your desktop" in very little time. OTOH, if you backup/restore process is good, you can do the same thing in 30 minutes without using VMs.  I've had a laptop stolen when traveling overseas - it disappears in the airport security check line. I was happy that I'd made an image of the VM to a flash drive.  When to the local big-box computer store and bought a $300 "used" replacement, then setup a minimal Linux with the hypervisor (type 1 or type 2 really are just marketing, IMHO. Meaningless).  Copied over the VM storage, setup the VM with the same settings as before, and I had my desktop from the instant of the snapshot.

QXL video drivers are really great compared to what we had before. For everything, except FPS or racing games, the video performance should be fine. I know a guy that uses autocad in Windows with QXL drivers and he claims it is good performance.  There are newer video drivers than QXL these days, but my VM hosts don't support them, so I don't have any experience.

These days, when I travel, I remote back home using x2go (NX-based remote desktop) so any data is left at home.  If my travel laptop gets stolen, I can get a $90 used laptop, load up and x2go client, copy my ssh-keys from a flash drive to have secure access into my home LAN and then be 100% back running with my desktop.

I don't use any DE with my desktop, so the extra 1GB of RAM that most DEs demand doesn't matter to me and the DEs that demand direct GPU access don't matter either.  KDE and Gnome don't work with x2go due to those requirements.  Older DEs like those based on Gnome2 or LXQt are lighter and work fine, if you don't want a pure WM-only desktop GUI.  I know openbox and fvwm work extremely well both locally, inside a VM and over remote connections.

---

### Post by ValentynPrumers on 2024-07-17
Thanks a lot! Really helpful comments! :)

I have installed a couple of VMs (using virt-manager). All those VMS are stored as .qcow2 files. Can you install a VM and store it as a block device using virt-manager?

2nd: Do you use the snapshot feature of kvm/virt-manager or the snapshot feature of LVM?

---

### Post by Dennis N on 2024-07-17
> I have installed a couple of VMs (using virt-manager). All those VMS are stored as .qcow2 files. Can you install a VM and store it as a block device using virt-manager?

Yes you can. You use the "custom storage" option when creating the VM, and would have a storage pool of logical volumes set up to select from as storage for the VM. An advantage over qcow2 is that the storage can be easily expanded to create more storage space even while in use. The unanswered question I have had is how you would move them to another computer. That is easy with .qcow2

I don't use VMs for regular use. I use them as reference and testing. I have cursor stability problems on my computers when VMs use Xorg. The graphics performance is not as good in VMs. In Ubuntu the dock will not unhide if you are using a hide option and a full screen application in a VM which is annoying.

---

### Post by TheFu on 2024-07-17
> **ValentynPrumers said:**
> Thanks a lot! Really helpful comments! :)

I have installed a couple of VMs (using virt-manager). All those VMS are stored as .qcow2 files. Can you install a VM and store it as a block device using virt-manager?
You have to setup the storage pool. virt-manager/virsh (this are just a GUI/CLI interface for libvirt) will access existing storage pools, once you tell it about them.  I point virt-manger at my LVM VGs and then when it is time to setup a VM storage, I just tell virt-manager to use the VG and create a new LV of Xyz size to be presented to the VM.  Here's an edited output from LVM:
```
$ sudo lvs
  lv-blog44         vg00           -wi-ao----   30.20g                                                    
  lv-vpn09-2004     vg00           -wi-ao----    7.50g                                                    
  lv-xen41-1204     vg00           -wi-ao----   12.50g                                                    
  lv-zcs45-1604     vg00           -wi-ao----   35.00g                                                    
  lxd               vg00           -wi-ao----   50.00g                                                    

```
showing some LVs that are only used by each of the VMs. As with all good volume managers, creating an LV is sub-second, just like creating a snapshot.

> **ValentynPrumers said:**
> 2nd: Do you use the snapshot feature of kvm/virt-manager or the snapshot feature of LVM?
LVM.  Always use the volume manager snapshot, since the backing-storage is what libvirt will use.  There is no "built-in" snapshot for virt-manager and definitely not for KVM/QEMU.

When I'm doing backups, I treat my lxc and VMs like they are physical machines, so any snapshots happen from "inside" the VM using LVM there, if the VM is large enough to need any volume management.  Most of my server VMs aren't that large.  I keep large data outside both the VMs and the containers and use NFS for access so the VMs can be relocated to any physical system here.  

Also, lxd has a problem. If you try to start any lxc container and all the storage it expects to have access into, even just for data for an app, isn't available, the container will refuse to start.  I mostly see this with my nextcloud container that uses a snap package.  I make lots of read-only data available inside nextcloud because that is an easy way to pull it to android devices, but I don't trust nextcloud with all that data, so it is read-only and I consider it optional.  Sadly, lxc considers that extra storage mandatory.  At least with NFS, missing data doesn't prevent a system from booting.

Similarly, LXD doesn't have any built-in snapshotting that isn't provided by ZFS.  As I wrote before, I've never gotten LVM to work with LXD.  I suspect it is because the LXD team decided to ensure ZFS worked and LVM was an afterthought.  There are all sorts of mandated things (that aren't standard) in the LVM requirements for LXD.  Plus, they use ZFS/LXD terms, not LVM terms for what is needed, so I struggle to understand what they really want. It is maddening to be forced to ask for help in discord for anything they don't use themselves.  Sigh.  Or perhaps I'm just stupid. Some days, it is hard to tell. 
LXD/LXC might call things "snapshots"  when creating a snapshot for the "export" command to create a tgz backup of a lxc container (new since lxd v4, I think).  Anyone using tgz for backups is doing it wrong if they have more than 500MB to backup.  Of course, there are different opinions about that.  I'm a huge believer in automatic, daily, pulled, verstioned, backups.  tgz exports with everything, every time, don't make versioned backups easy.  They are more for non-professional people who might vaguely remember, monthly or quarterly that they hadn't made any backup in some time, so they manually do it.  OTOH, people like me have between 90 and 366 days of versioned backups for all our systems, because it doesn't take very much storage when only daily changed data is included in the backup versions.

It has been about a year since I looked at the built-in lxd backup capabilities. Maybe they are doing it better now.  IDK, so do your own homework on that.  My backups don't care if it is a container, a VM, or a physical system.  I use "pulled" backups so my client systems can't access any of the backup storage, so any malware or cryptoware can't harm the backups except by making huge changes on the source system, which the backup server(s) will see as huge daily changes and longer backup times required.

---

