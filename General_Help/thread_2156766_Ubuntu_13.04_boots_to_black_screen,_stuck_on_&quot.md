---
title: "Ubuntu 13.04 boots to black screen, stuck on &quot;DRM: Fill_in_dev failed.&quot;"
date: 2013-06-23
forum: General Help
---

### Post by Elad92 on 2013-06-23
Hello,

I got a new computer few days ago with i7 4770k and 660gtx, I installed Ubuntu 13.04 and when I tried to boot I saw a black screen. After some googling I understood I needed to install the nvidia drivers, I installed the drivers from this repo:
```

sudo apt-add-repository ppa:ubuntu-x-swat/x-updatessudo apt-get updatesudo apt-get install nvidia-current nvidia-settings

```

After that I still got black screen, so I boot with nomodeset and I saw that the boot fail on:
```

* Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated [OK]* Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated [fail]
```

So I disabled the avahi-daemon with an override file, like this:
```
[FONT=Ubuntu Mono]sudo sh -c "echo manual > /etc/init/avahi-daemon.override"[/FONT]
```

Again, I tried to boot and I hear the lockscreen sound but the screen is black with only a flashing line in the top left corner of the screen.
So I tried to boot with nomodeset and saw that it's stuck on this error:
[IMG]http://i.stack.imgur.com/0Qhle.jpg[/IMG]



I'm really frustrated because I can't use my new computer.
I will appreciate any help,

Thanks

---

### Post by Elad92 on 2013-06-23
I tried more things:

* Installed Ubuntu 13.04 on my HDD (now it's on SSD), same thing.
* Reinstalled nvidia drivers
* Tried to fix broken packages
* Tried to use gdm instead of lightdm

Really frustrated of this.. any help will be appreciated.

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]Elad92; Hi !

Now-a-days installing an operating system has become more and more complex what with UEFI, ISRT and secure boot to deal with.

As a first poke at this ... secure boot ! In bios do you have "secure boot" disabled ?
[/COLOR][INDENT][COLOR=#000000]
if it is not one thing it must be another

[/COLOR][/INDENT]

---

### Post by Elad92 on 2013-06-23
Hi Bashing-om,

First of all, thanks for your reply :)

I tried to check out for secure boot but couldn't find something like that, maybe there is another name for that?

This is my motherboard:
[http://www.gigabyte.com/products/product-page.aspx?pid=4570#ov](http://www.gigabyte.com/products/product-page.aspx?pid=4570#ov)

And this is a picture from my bios:
[https://docs.google.com/file/d/0By03IsybEaQ0eDFLZ09iNVVoeDg/edit?usp=sharing](https://docs.google.com/file/d/0By03IsybEaQ0eDFLZ09iNVVoeDg/edit?usp=sharing)

Thanks

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]Elad92; Wow !

Quite an impressive system. Bios is not simple anymore.
 Realize this; If we can not boot up the liveDCD into "try ubuntu", the install onto hard drive will not be successful.
Let us focus our attention on getting the liveDVD to boot.
You purchased this system with no operating system installed ? Such that Windows is not a factor ?

We are still looking in bios for settings that preclude booting any operating system:
What is in the GigaByte -> EZ setup ??
Intel virtualization support ? why should we care at this point ? Maybe set that one to disable ?

Try this now:
Cold boot the liveDVD (bios priority set as DVD drive 1st boot priority) As soon as the bios screen clears, depress and hold the shift key -> language screen; escape key to accept the default -> boot options menu -> f6 key for the preset options, try "nomodeset" first (arrow down to it, and space key to accept), enter key to continue the boot process. Do you now get to the screen to choose "try ubuntu" / "install ubuntu" ?
select "try ubuntu" ->> What results ? (degraded graphics is ok at this point)

Once we have booted into the liveDVD we can look at the hard drives and maybe see a problem, maybe in the type of partitioning ... ubuntu does not deal with Microsoft's dynamic partitioning scheme - if present.
[/COLOR][INDENT=2][COLOR=#000000]
if it ain't one thing it's another

[/COLOR][/INDENT]

---

### Post by Elad92 on 2013-06-23
Yeah, I was as surprised as you were (new computer after 5 years, lol) :)
The installation went very well and the graphics there were fine (full hd resolution), without modifying anything. Same with 'Try Ubuntu'.
Actually, with the 'Try Ubuntu' using the live CD (usb at my case) and the 'chroot' command I managed to control my installed system using the terminal.

If I can boot the 'Try Ubuntu' without any problem it means that the BIOS configuration is ok, no?

About partitioning, I first installed Windows 8, gave it about 75GB, and left the rest of the space free. Then I installed ubuntu, gave 22GB primary partition (ext4) to '/' mount point, and with the rest (about 17GB) I created another primary partition (ext4) for mount point '/home'.

Another 16GB of swap was on my HDD.

I also tried to install ubuntu on my HDD (not on the SSD), and gave it 50GB just for '/', with not other partitions with other OS (just 16GB for swap) and still had the same problem.

BTW, I found this bug here, but it seems very old I don't know if it's still related:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694)

Thanks

---

### Post by Bashing-om on 2013-06-23
Elad92; Hey,

If It seems I am confused, it is because I am.
Ok to see what is going on with graphics:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
in the originating post I saw a reference to "cups" ... which is linux's printer module interface. I do not know what that could be in regards to at this time.

Booting: bios looks for a bootloader in accordance with the priority set in bios. Now if grub is not installed where you told bios to boot from... boot will fail.
Ok,,, if you want to boot another instance of an operating system:
a) A boot loader must be installed ..primary operating system (drive). I prefer that grub be that boot loader, and handle controlling booting any operating system - will chainload other (Windows) OS. Install grub to the MBR. Then :
```

sudo update-grub

```
b) Second instance of linux OS installed to a different device -> I prefer to also install grub to the MBR on this device, That way one may boot that device -in the event that the primary system is not bootable - by resetting the bios boot priority. Do the "update-grub" thing. 
os-prober -component within update-grub -  finds all instances of any OS and along with several other files builds the booting grub.cfg
c) Boot back into the primary ubuntu OS and run "update-grub" once more to insure any changes on the grub of the other install is picked up on the primary install.

And yes, if you can boot the liveMedium (usb), bios setting should be good ... And if you can not boot into the install to the GUI, then the most likely cause is graphics related... the linux kernel is very smart.. and Kernel Mode Setting (KMS) works well such that having to manually intervene - most drivers are included or available in the kernel -  to get a working GUI is rarely required.

Now to get me unconfused; state the primary difficulty you are facing now and we will address that one. Dealing with all others, one issue at a time.

In respect to the "bug" report in launchpad... that was a long time ago and was fixed (fix -> confirmed) upstream from that reporting date.

Partitioning ... standard scheme -> can only have 4 partitions per device else one has to take one of the primary partitions and make it into an "extended" partition in which any number of "logical" partitions may be made. I hope I am not belaboring what you already know. Your partitioning scheme sizes should be fine for now ... until you see how and what you actually require... long long time down the road before any action need be taken on that front. -so long as you are not exceeding 4 primary partitions: To see - from a liveMedium (usb) so no partitions are mounted- do :
```

sudo fdisk -lu ##from live cd<-disk info
sudo parted -l ##from live cd<-disk info
sudo parted /dev/sda unit s print ##from livecd

```

As an aside, when you get to it ... only 1 swap partition is needed,,, both 'buntus can access and use what ever swap partition is designated in /etc/fstab.... this will save ya some disk space. UHH! You do not want swap on the ssd ! Too many writes to the solid state device and degrades it quickly.

 And I hope I have not confused you... I await your direction.
[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by Elad92 on 2013-06-24
Hey, to make some order in things. After I installed ubuntu, I had the cups problem, but it's no longer there so I don't think it matters now. The problem I'm facing is with the "DRM: Fill_in_dev failed."

I have grub installed in my ssd and this is where I boot from, I will update it.
About my "other ubuntu system", I installed it on my HDD just to see if the SSD is not the problem for booting, then I removed it. Now I have on my HDD only swap partition and a ntfs partition with all the rest of the space.

Output from grub update:
```
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found Windows 8 (loader) on /dev/sda1
Found Windows 8 (loader) on /dev/sda2
Adding boot menu entry for EFI firmware configuration
done


```

This is the output for the graphic commands:
```
root@ubuntu:/# lshw -C display
  *-display               
       description: VGA compatible controller
       product: GK106 [GeForce GTX 660]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:da000000-daffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:db000000-db07ffff
  *-display
       description: VGA compatible controller
       product: Haswell Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:db400000-db7fffff memory:c0000000-cfffffff ioport:f000(size=64)
root@ubuntu:/# lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell Integrated Graphics Controller [8086:0412] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Haswell HD Audio Controller [8086:0c0c] (rev 06)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK106 [GeForce GTX 660] [10de:11c0] (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:354e]
    Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0e0b] (rev a1)


```

Those are the outputs for the partitions commands (executed from live cd):
```
ubuntu@ubuntu:~$ sudo fdisk -lu ##from live cd<-disk info

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31705398

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   157695999    78488576    7  HPFS/NTFS/exFAT
/dev/sda3       157696000   200665087    21484544   83  Linux
/dev/sda4       200665088   234440703    16887808   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1327ee06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    35155967    17576960   82  Linux swap / Solaris
/dev/sdb2        35155968  3907024895  1935934464    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 4041 MB, 4041211904 bytes
128 heads, 63 sectors/track, 978 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e2ec1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7892991     3946464+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo parted -l ##from live cd<-disk info
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  368MB   367MB   primary  ntfs         boot
 2      368MB   80.7GB  80.4GB  primary  ntfs
 3      80.7GB  103GB   22.0GB  primary  ext4
 4      103GB   120GB   17.3GB  primary  ext4


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  18.0GB  18.0GB  primary  linux-swap(v1)
 2      18.0GB  2000GB  1982GB  primary  ntfs


Model: Google Android (scsi)
Disk /dev/sdc: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4041MB  4041MB  primary  fat32        boot


ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print ##from livecd
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      2048s       718847s     716800s     primary  ntfs         boot
 2      718848s     157695999s  156977152s  primary  ntfs
 3      157696000s  200665087s  42969088s   primary  ext4
 4      200665088s  234440703s  33775616s   primary  ext4

ubuntu@ubuntu:~$ 


```

As for the swap, I didn't install it on the SSD :) It's on my HDD just for the reason you just wrote before.

I hope you are understanding what I'm trying to explain and I didn't make yuou more confused :)

Thanks and waiting for your reply.

---

### Post by Elad92 on 2013-06-24
Maybe it's a problem with the i7 integrated graphics?
Is there any way to disable them in bios or something?

---

### Post by Elad92 on 2013-06-24
Ok, I've found an option in the bios to disable the i7 integrated graphic and my ubuntu boot without problem :D
Thanks a lot for your great help Bashing-om, I wouldn't fix it without you :)

---

### Post by Bashing-om on 2013-06-24
[COLOR=#000000]Elad92; Hey..
Good things do happen !

Ok Graphics... What ya got there is 2 means of utilizing graphics,per your "display" outputs, linux does not deal too well with that switchable environment,,, It gets confused too ! There are some work-a-rounds, off the top of my head I do not recall the specifics for Intel/Nvidia. These links will shed some comprehension your way.
[/COLOR][https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) switcheroo, that may directly apply
[http://linux-hybrid-graphics.blogspot.com/2011/06/hybrid-graphics-linux-on-samsung-sf310.html](http://linux-hybrid-graphics.blogspot.com/2011/06/hybrid-graphics-linux-on-samsung-sf310.html)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)[INDENT=2]
I trust you are now on your merry way and delving into the greatest operating system the world has ever seen[/INDENT]

---

### Post by Elad92 on 2013-06-25
I don't know if I want to deal with it yet, the Intel graphic is not needed when I got a separate Gpu. 
Anyway, when I will want to fix it I will look at those links. 
Thanks again for your great help! :-)

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]Elad92;

Hey, not a problem... we are all in this together...
Glad you have that awesome box up and running !

Read at ya later !
[/COLOR]Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT=3]
cheers

[/INDENT]

---

