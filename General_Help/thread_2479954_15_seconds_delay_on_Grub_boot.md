---
title: "15 seconds delay on Grub boot"
date: 2022-10-14
forum: General Help
---

### Post by georgesgiralt on 2022-10-14
Hello Guys,
I have a laptop (Lenovo ThinkPad E540 )with a plain disk and an M.2 SATA card. The ESP partition is the first on the M.2 SATA. (this device holds an windows 10 install and a lvm PV).
The big disk hold a windows partition (storage for files) and an lvm pv. 
Grub is set up on the M.2 which is known as /dev/sdb.
Everything Ubuntu is on the lvm vg made with the two pv. For security reasons, /boot, /usr, /var, /tmp, /var/log and /var/tmp are on separate logical volumes.
I had to switch to GRUB_TERMINAL=console because the last BIOS security upgrade broke the graphical grub menu display making this menu invisible but active.
When I boot, I have the grub menu displayed properly, now.
When I select the default entry (ubuntu) the screen clears and I get a dash (-) on the upper left corner of the screen and nothing happen for at least 15 seconds (measured), then the info about secure boot being enabled and the kernel messages appears and boot takes place. 
Question : 
Why is there this 15 seconds delay ? 
How could I get rid of it ? 
Many thanks in advance for your help.
Have a nice and bright day.

---

### Post by ActionParsnip on 2022-10-14
what is the output of 
```

cat -n /etc/default/grub

```
Thanks

---

### Post by yancek on 2022-10-14
Look in the file mentioned in post 2 for a line:  GRUB_TIMEOUT=10  and change the 15 to a lower number.  If that doesn't change things post back with details on what happens.

---

### Post by ActionParsnip on 2022-10-14
Did you run:
```

sudo update-grub

```
After making the change?

---

### Post by georgesgiralt on 2022-10-14
> **ActionParsnip said:**
> what is the output of 
```

cat -n /etc/default/grub

```
Thanks
Here you are : 
```
cat -n /etc/default/grub
     1	# If you change this file, run 'update-grub' afterwards to update
     2	# /boot/grub/grub.cfg.
     3	# For full documentation of the options in this file, see:
     4	#   info -f grub -n 'Simple configuration'
     5	
     6	GRUB_DEFAULT=0
     7	GRUB_TIMEOUT_STYLE=menu
     8	GRUB_TIMEOUT=10
     9	GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    10	GRUB_CMDLINE_LINUX_DEFAULT=""
    11	#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    12	GRUB_CMDLINE_LINUX="iommu="force" security=yama "
    13	
    14	# Uncomment to enable BadRAM filtering, modify to suit your needs
    15	# This works with Linux (no patch required) and with any kernel that obtains
    16	# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
    17	#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
    18	
    19	# Uncomment to disable graphical terminal (grub-pc only)
    20	GRUB_TERMINAL=console
    21	
    22	# The resolution used on graphical terminal
    23	# note that you can use only modes which your graphic card supports via VBE
    24	# you can see them in real GRUB with the command `vbeinfo'
    25	#GRUB_GFXMODE=1920x1080
    26	
    27	# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
    28	#GRUB_DISABLE_LINUX_UUID=true
    29	
    30	# Uncomment to disable generation of recovery mode menu entries
    31	#GRUB_DISABLE_RECOVERY="true"
    32	
    33	# Uncomment to get a beep at grub start
    34	#GRUB_INIT_TUNE="480 440 1"
    35	

```

---

### Post by georgesgiralt on 2022-10-14
> **yancek said:**
> Look in the file mentioned in post 2 for a line:  GRUB_TIMEOUT=10  and change the 15 to a lower number.  If that doesn't change things post back with details on what happens.
Thank you for your answer, but as you can see in the above post, my timeout is set to 10 and IMHO this timeout is the delay *before* the default entry is started automatically. 
I'll try to reduce it to 2 in order to check if I'm right or not and report back.

---

### Post by georgesgiralt on 2022-10-14
> **ActionParsnip said:**
> Did you run:
```

sudo update-grub

```
After making the change?

Thank you for your answer,
Yes I did update the grub config file. Actually as I tried a lot of things in order to suppress this delay, update-grub is everywhere in my history file.

---

### Post by georgesgiralt on 2022-10-14
So I changed the "GRUB_TIMEOUT=10" to 5 seconds in order to be able to press a key before the default entry gets fired. 
And this time I had my watch on the hand before hitting the "enter" key. 
So the grub ubuntu entry is highlighted, and I press the "enter" key on the keyboard. 
The screen clears and there is a dash ( - ) displayed in the upper left corner of the screen. 
I started the count when I hit the return key. The dash was displayed for exactly 28 seconds before the message about secure boot being active and the messages from the Linux kernel start appearing. 
So I was right that GRUB_TIMEOUT has nothing to do in this delay, but was wrong when I said 15 sec. It is definitely closer to 30.... 
Thanks all for your help.

---

### Post by tea for one on 2022-10-14
If you run this command in a terminal, it may provide a clue for further investigation:-
```
systemd-analyze blame
```

---

### Post by Dennis N on 2022-10-14
Doesn't sound like a grub problem.
Check the UUIDs in /etc/fstab to be sure they all match the actual device UUIDs found by **lsblk** as shown below:
```

dmn@Sydney-vm:~$ lsblk -o name,uuid
NAME   UUID
vda    
&#9500;&#9472;vda1 5DEE-3D58
&#9492;&#9472;vda2 aebebd26-07a8-4db3-8758-3e94647f2948
vdb    
&#9492;&#9472;vdb1 5996937d-69ba-4827-8af9-45f7e584a8c5

```

---

### Post by georgesgiralt on 2022-10-14
> **tea for one said:**
> If you run this command in a terminal, it may provide a clue for further investigation:-
```
systemd-analyze blame
```

Here you are. Nothing about finding/starting the kernel...
```
$ systemd-analyze blame
13.790s apt-daily.service                                    
 6.434s systemd-journal-flush.service                        
 6.344s NetworkManager-wait-online.service                   
 2.137s apt-daily-upgrade.service                            
 1.828s user@1000.service                                    
 1.764s nfs-server.service                                   
 1.503s accounts-daemon.service                              
 1.430s udisks2.service                                      
 1.356s grub-common.service                                  
 1.297s lvm2-pvscan@8:21.service                             
 1.248s winbind.service                                      
 1.232s smartmontools.service                                
 1.191s vboxdrv.service                                      
 1.190s systemd-fsck@dev-mapper-isengrin\x2dhome.service     
 1.152s systemd-fsck@dev-mapper-isengrin\x2dvartmp.service   
 1.152s systemd-fsck@dev-mapper-isengrin\x2dvarlog.service   
 1.107s systemd-fsck@dev-mapper-isengrin\x2dboot.service     
  929ms systemd-fsck@dev-mapper-isengrin\x2dtmp.service      
  835ms dev-mapper-isengrin\x2dslash.device                  
  832ms dev-mapper-isengrin\x2dusr.device                    
  823ms systemd-tmpfiles-setup.service                       
  641ms lvm2-pvscan@8:4.service                              
  565ms tlp.service                                          
  481ms systemd-logind.service                               
  314ms systemd-resolved.service                             
  306ms gpm.service                                          
  286ms avahi-daemon.service                                 
  281ms ua-timer.service                                     
  275ms apport.service                                       
  256ms bluetooth.service                                    
  255ms NetworkManager.service                               
  255ms networkd-dispatcher.service                          
  247ms gdm.service                                          
  239ms upower.service                                       
  220ms var-log.mount                                        
  218ms var-tmp.mount                                        
  189ms home.mount                                           
  180ms inetutils-inetd.service                              
  174ms e2scrub_reap.service                                 
  168ms gpu-manager.service                                  
  159ms polkit.service                                       
  149ms lm-sensors.service                                   
  146ms ModemManager.service                                 
  136ms switcheroo-control.service                           
  133ms boot.mount                                           
  130ms grub-initrd-fallback.service                         
  121ms secureboot-db.service                                
  117ms systemd-udev-trigger.service                         
  115ms thermald.service                                     
  113ms rsyslog.service                                      
  106ms systemd-udevd.service                                
  105ms pppd-dns.service                                     
   98ms lvm2-monitor.service                                 
   98ms dev-hugepages.mount                                  
   97ms dev-mqueue.mount                                     
   97ms proc-fs-nfsd.mount                                   
   96ms run-rpc_pipefs.mount                                 
   95ms wpa_supplicant.service                               
   95ms sys-kernel-debug.mount                               
   94ms sys-kernel-tracing.mount                             
   94ms systemd-journald.service                             
   91ms colord.service                                       
   82ms tmp.mount                                            
   78ms keyboard-setup.service                               
   77ms blk-availability.service                             
   77ms kmod-static-nodes.service                            
   75ms systemd-fsck@dev-mapper-isengrin\x2dvar.service      
   70ms systemd-timesyncd.service                            
   69ms modprobe@drm.service                                 
   67ms systemd-modules-load.service                         
   66ms modprobe@efi_pstore.service                          
   62ms alsa-restore.service                                 
   59ms systemd-update-utmp.service                          
   59ms modprobe@chromeos_pstore.service                     
   57ms modprobe@ramoops.service                             
   56ms binfmt-support.service                               
   54ms autofs.service                                       
   51ms kerneloops.service                                   
   50ms systemd-remount-fs.service                           
   50ms ssh.service                                          
   46ms fprintd.service                                      
   45ms fwupd-refresh.service                                
   45ms nfs-mountd.service                                   
   44ms ufw.service                                          
   43ms systemd-fsck@dev-disk-by\x2duuid-2076\x2d6A4A.service
   38ms systemd-tmpfiles-clean.service                       
   35ms dev-mapper-isengrin\x2dswap.swap                     
   35ms dns-clean.service                                    
   33ms hddtemp.service                                      
   32ms openvpn.service                                      
   24ms proc-sys-fs-binfmt_misc.mount                        
   22ms systemd-user-sessions.service                        
   20ms systemd-backlight@backlight:intel_backlight.service  
   18ms systemd-sysusers.service                             
   18ms motd-news.service                                    
   18ms user-runtime-dir@1000.service                        
   16ms console-setup.service                                
   15ms plymouth-read-write.service                          
   13ms systemd-tmpfiles-setup-dev.service                   
   12ms boot-efi.mount                                       
   12ms systemd-random-seed.service                          
   12ms rpcbind.service                                      
   12ms nfs-idmapd.service                                   
   11ms vboxweb-service.service                              
   11ms systemd-sysctl.service                               
   10ms nfs-blkmap.service                                   
   10ms setvtrgb.service                                     
    9ms systemd-update-utmp-runlevel.service                 
    8ms var.mount                                            
    7ms modprobe@pstore_zone.service                         
    7ms vboxballoonctrl-service.service                      
    7ms vboxautostart-service.service                        
    6ms nfs-config.service                                   
    6ms modprobe@pstore_blk.service                          
    5ms rtkit-daemon.service                                 
    5ms sys-fs-fuse-connections.mount                        
    5ms nvidia-persistenced.service                          
    5ms sys-kernel-config.mount                              
    4ms plymouth-quit-wait.service   
```

---

### Post by georgesgiralt on 2022-10-14
> **Dennis N said:**
> Doesn't sound like a grub problem.
Check the UUIDs in /etc/fstab to be sure they all match the actual device UUIDs found by **lsblk** as shown below:
```

dmn@Sydney-vm:~$ lsblk -o name,uuid
NAME   UUID
vda    
&#9500;&#9472;vda1 5DEE-3D58
&#9492;&#9472;vda2 aebebd26-07a8-4db3-8758-3e94647f2948
vdb    
&#9492;&#9472;vdb1 5996937d-69ba-4827-8af9-45f7e584a8c5

```
Thank you for your help !
No joy there. 
```

$ lsblk -o name,uuid
NAME                UUID
sda                 
&#9500;&#9472;sda1              1B725690308A214E
&#9492;&#9472;sda4              KLAUoU-rNts-fWCC-SnUa-mX76-ZpSH-1Oe5eJ
  &#9500;&#9472;isengrin-varlog 3091675d-18e7-4ee7-abc5-717d65f513d2
  &#9500;&#9472;isengrin-vartmp d634638a-ce30-4bf0-af15-cd2946e9f49e
  &#9500;&#9472;isengrin-tmp    fae8a95c-9431-4def-ba06-6096da5f4591
  &#9500;&#9472;isengrin-boot   9b8e9a05-2bc6-45f7-beb8-243cc19a725a
  &#9500;&#9472;isengrin-home   9d490826-8bf8-45f8-afa5-21b1cd9ff56b
  &#9492;&#9472;isengrin-swap   c920829a-cc5a-40c2-aa9f-6bf8e8c56618
sdb                 
&#9500;&#9472;sdb1              2076-6A4A
&#9500;&#9472;sdb2              
&#9500;&#9472;sdb3              38DB881F386CB2F5
&#9500;&#9472;sdb4              A292231E9222F687
&#9492;&#9472;sdb5              rVZqYR-v9i0-ensn-v6ek-s84E-4hpq-LWCZG6
  &#9500;&#9472;isengrin-slash  2f3255f5-4f43-45b9-9911-a7042c6bc1e6
  &#9500;&#9472;isengrin-usr    5a1ccad7-a2b4-4ffb-9284-ca968840101c
  &#9492;&#9472;isengrin-var    aa0c7e1d-d74a-402c-9a78-7ea11d0eb91c
sr0                 
georges@isengrin:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/isengrin-slash /               ext4    errors=remount-ro 0       1
/dev/mapper/isengrin-boot /boot           ext4    defaults,nosuid,nodev,noexec        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=2076-6A4A  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/isengrin-home /home           ext4    defaults,nosuid,nodev       0       2
/dev/mapper/isengrin-tmp /tmp            ext4    defaults,nosuid,nodev,noexec        0       2
/dev/mapper/isengrin-usr /usr            ext4    defaults,nodev        0       2
/dev/mapper/isengrin-var /var            ext4    defaults,nosuid,nodev        0       2
/dev/mapper/isengrin-varlog /var/log        ext4    defaults,nosuid,nodev,noexec        0       2
/dev/mapper/isengrin-vartmp /var/tmp        ext4    defaults,nosuid,nodev,noexec        0       2
/dev/mapper/isengrin-swap none            swap    sw              0       0

```
And on /boot/grub/efi/EFI/ubuntu/grub.cfg : 
```

 cat -n /boot/efi/EFI/ubuntu/grub.cfg 
     1	search.fs_uuid 9b8e9a05-2bc6-45f7-beb8-243cc19a725a root lvmid/UkadPJ-1Wz9-40nc-P1GJ-nEV7-PaIp-Zw1gaT/t5mFoa-zRB7-9OVI-cf1B-s4F8-gJf6-bojOKz 
     2	set prefix=($root)'/grub'
     3	configfile $prefix/grub.cfg

```
As I previously said, the delay happens BEFORE the kernel start displaying anything. So IMHO it is between grub and EFI/ESP stuff...
Have a nice day !

---

### Post by georgesgiralt on 2022-10-14
Hello Guys,
Having trouble to sleep, I decided I could use my brain a little.
I thought that I could instrument the grub.cfg file to see what was causing delay. 
So i put "echo 'starting this' " lines to see if some time was "lost"   loading/doing something in grub. 
```

menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2f3255f5-4f43-45b9-9911-a7042c6bc1e6' {
        recordfail
echo 'Load Video'
        load_video
echo 'load gfxmode'
        gfxmode $linux_gfx_mode
echo 'insmod gzio'
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
echo 'load part,gpt,lvm,ext...'
        insmod part_gpt
        insmod part_gpt
        insmod lvm
        insmod ext2
echo 'set root'
        set root='lvmid/UkadPJ-1Wz9-40nc-P1GJ-nEV7-PaIp-Zw1gaT/t5mFoa-zRB7-9OVI-cf1B-s4F8-gJf6-bojOKz'
        if [ x$feature_platform_search_hint = xy ]; then
echo ' Search root uuid-lvm'
          search --no-floppy --fs-uuid --set=root --hint='lvmid/UkadPJ-1Wz9-40nc-P1GJ-nEV7-PaIp-Zw1gaT/t5mFoa-zRB7-9OVI-cf1B-s4F8-gJf6-bojOKz'  9b8e9a05-2bc6-45f7-beb8-243cc19a725a
        else
echo 'search root uuid'
          search --no-floppy --fs-uuid --set=root 9b8e9a05-2bc6-45f7-beb8-243cc19a725a
        fi
echo 'linux ...et initrd'
        linux   /vmlinuz-5.4.0-128-generic root=/dev/mapper/isengrin-slash ro
echo 'load intrd'
        initrd  /initrd.img-5.4.0-128-generic
}

```
And the printing of lines stop after the "linux et  initrd"  line is printed for a few seconds then the "load intrd" line is displayed along the "EFI stub : Secure boot is ..." line and everything goes on. 
So the biggest part of the delay is spent in the linux.... line. Now we have to search why ....
Nota : I've cleared  the kernel  options to have a bare one thinking that passing/loading extra things to the kernel may cause delays. No luck here...

---

### Post by georgesgiralt on 2022-10-15
Hello Guys,
As always, a bug is not where one search for it.... 
Today I had to use Windows to update a device using a piece of software only running in Windows.... Grrr.... And after this chore, i restarted the laptop without going through power off. And Ubuntu fired right away, instantly. 
So it seems the bug and the delay lies in the had disk drive is taking some time to be ready and/or Grub take it's time to access it... 
So once booted I did move the boot lv on the M.2 SATA drive (pvmove -A y -n isengrin/boot /dev/sda4 /dev/sdb5) and then, power off the computer. 
After a few seconds, boot it up  and...¡BINGO! The computer boots right away ! 
So now I've to find why the Seagate disk takes that time to be ready. Is it the drive itself or the laptop's interface having a problem or something else entirely... 
Anyway, thanks all for your help !

---

### Post by georgesgiralt on 2022-10-16
Hello !
I've found what was wrong. 
At first I had made the boot logical volume sized at 2 GB. Then I decided to give a try at grml and for this I extended the boot LV to 10 GB. This make it having TWO extends because there was no place around the first extend to increase it. 
And this wreck the boot process because activating this lv is a bit more complicated. 
When I moved it to the other physical volume, the boot lv was made into a single extend volume (all the data was written in one piece on the free extends of the quite free pv). And today, willing to restore things as they where before I tryied everything at random, I moved the single extend PV back to it's original large "plain" mechanical drive. 

And guess what ? Boot is as fast as it should be. 
Now I'm happy. An I thank you for your support. You gave me some leads to explore and I learned something in the process. 
Have a nice and bright day !

---

