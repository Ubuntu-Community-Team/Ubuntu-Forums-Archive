---
title: "Almost TEN MINUTES to Boot"
date: 2024-09-19
forum: General Help
---

### Post by bilkay on 2024-09-19
My laptop is taking a LONG time (~10 minutes)  to boot. Here are two line from syslog during boot showing an 8 minute gap between them:

```
Sep 19 12:38:44 Relic systemd[1]: Starting Daemon for power management...
Sep 19 12:46:53 Relic systemd-timesyncd[584]: Initial synchronization to time ser
```

This is on an Ubuntu 20.04 LTS laptop.

---

### Post by ajgreeny on 2024-09-19
Please run command **systemd-analyze blame** and show us the output.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by 1fallen on 2024-09-19
Also this please:
```
[FONT=monospace][COLOR=#000000]timedatectl status[/COLOR][/FONT]
```[FONT=monospace]

And this:
```
[/FONT][FONT=monospace][COLOR=#000000]journalctl --unit=systemd-timesyncd.service[/COLOR]


```
[/FONT]

---

### Post by oldfred on 2024-09-19
Also:
What brand/model system?
What video card/chip?

Have you updated UEFI firmware to latest available.
And if SSD, its firmware to latest available.

---

### Post by bilkay on 2024-09-24
$ systemd-analyze blame
```

1min 12.586s sendmail.service                                     
     56.409s mysql.service                                        
     38.887s dev-loop12.device                                    
     32.116s snapd.seeded.service                                 
     29.955s udisks2.service                                      
     28.331s snapd.service                                        
     22.163s networkd-dispatcher.service                          
     18.118s dev-sda6.device                                      
     16.449s systemd-journal-flush.service                        
     14.441s accounts-daemon.service                              
     14.155s ModemManager.service                                 
     13.895s apache2.service                                      
     12.438s NetworkManager-wait-online.service                   
      9.315s polkit.service                                       
      8.755s NetworkManager.service                               
      8.733s avahi-daemon.service                                 
      8.137s dev-loop10.device                                    
      8.061s dev-loop7.device                                     
      8.024s switcheroo-control.service                           
      7.995s dev-loop5.device                                     
      7.947s thermald.service                                     
      7.938s systemd-logind.service                               
      7.938s wpa_supplicant.service                               
      7.847s dev-loop9.device                                     
      7.688s dev-loop8.device                                     
      7.627s dev-loop0.device                                     
      7.414s dev-loop4.device                                     
      7.286s dev-loop3.device                                     
      7.180s dev-loop11.device                                    
      6.462s dev-loop6.device                                     
      6.384s dev-loop1.device                                     
      4.207s dev-loop2.device                                     
      3.956s fwupd.service                                        
      3.911s apparmor.service                                     
      3.726s gpu-manager.service                                  
      3.701s rsyslog.service                                      
      3.557s lightdm.service                                      
      3.545s plymouth-quit-wait.service                           
      3.462s colord.service                                       
      3.271s ssh.service                                          
      3.086s apport.service                                       
      2.955s autofs.service                                       
      2.807s e2scrub_reap.service                                 
      2.614s systemd-udevd.service                                
      2.399s systemd-tmpfiles-clean.service                       
      1.856s nfs-server.service                                   
      1.761s systemd-resolved.service                             
      1.636s grub-common.service                                  
      1.529s phpsessionclean.service                              
      1.175s upower.service                                       
      1.172s snapd.apparmor.service                               
      1.042s networking.service                                   
      1.022s mythtv-backend.service                               
      1.022s nfs-mountd.service                                   
       956ms systemd-tmpfiles-setup.service                       
       943ms systemd-modules-load.service                         
       935ms grub-initrd-fallback.service                         
       843ms rpcbind.service                                      
       708ms systemd-tmpfiles-setup-dev.service                   
       708ms systemd-rfkill.service                               
       699ms snap-bare-5.mount                                    
       695ms systemd-random-seed.service                          
       674ms proc-fs-nfsd.mount                                   
       638ms snap-core18-1705.mount                               
       611ms snap-core18-2829.mount                               
       605ms systemd-sysctl.service                               
       587ms systemd-sysusers.service                             
       579ms home.mount                                           
       561ms systemd-journald.service                             
       556ms swapfile.swap                                        
       538ms keyboard-setup.service                               
       530ms dns-clean.service                                    
       519ms snap-core22-1612.mount                               
       515ms lm-sensors.service                                   
       493ms host.mount                                           
       474ms systemd-udev-trigger.service                         
       447ms snap-gnome\x2d3\x2d34\x2d1804-24.mount               
       434ms rpc-statd.service                                    
       410ms snap-gnome\x2d3\x2d34\x2d1804-93.mount               
       398ms nfs-idmapd.service                                   
       375ms user@1000.service                                    
       333ms snap-gnome\x2d42\x2d2204-176.mount                   
       324ms ifupdown-pre.service                                 
       320ms systemd-timesyncd.service                            
       318ms boot-efi.mount                                       
       286ms openvpn.service                                      
       272ms systemd-remount-fs.service                           
       269ms snap-gtk\x2dcommon\x2dthemes-1506.mount              
       266ms systemd-backlight@backlight:acpi_video0.service      
       254ms alsa-restore.service                                 
       253ms plymouth-start.service                               
       251ms snap-gtk\x2dcommon\x2dthemes-1535.mount              
       250ms modprobe@efi_pstore.service                          
       243ms dev-hugepages.mount                                  
       241ms dev-mqueue.mount                                     
       237ms run-rpc_pipefs.mount                                 
       235ms modprobe@drm.service                                 
       234ms sys-kernel-debug.mount                               
       232ms sys-kernel-tracing.mount                             
       230ms hddtemp.service                                      
       229ms rpc-statd-notify.service                             
       193ms kmod-static-nodes.service                            
       190ms snap-snap\x2dstore-1216.mount                        
       187ms rtkit-daemon.service                                 
       177ms modprobe@pstore_blk.service                          
       175ms modprobe@pstore_zone.service                         
       173ms modprobe@ramoops.service                             
       168ms snap-snapd-21759.mount                               
       164ms pppd-dns.service                                     
       164ms setvtrgb.service                                     
       154ms kerneloops.service                                   
       148ms snap-snap\x2dstore-433.mount                         
       144ms console-setup.service                                
       139ms ufw.service                                          
       130ms systemd-fsck@dev-disk-by\x2duuid-35D4\x2d3631.service
       117ms nfs-blkmap.service                                   
       105ms proc-sys-fs-binfmt_misc.mount                        
       105ms systemd-update-utmp.service                          
        98ms plymouth-read-write.service                          
        83ms systemd-user-sessions.service                        
        66ms modprobe@chromeos_pstore.service                     
        30ms user-runtime-dir@1000.service                        
        22ms systemd-update-utmp-runlevel.service                 
        14ms sys-fs-fuse-connections.mount                        
         9ms sys-kernel-config.mount                              
         5ms nfs-config.service                                   
         3ms snapd.socket                                         

```
I didn't get any emails (odd) so I thought there were no responses.

Here's the syslog gap from today:
```
Sep 24 06:08:39 Relic snapd[769]: backends.go:58: AppArmor status: apparmor is enabled and all features are available
Sep 24 06:15:02 Relic systemd-timesyncd[653]: Initial synchronization to time server 185.125.190.58:123 (ntp.ubuntu.com).
```

---

### Post by Rubi1200 on 2024-09-24
I'm surprised by how many services are running.

If I run the same command on a standard Ubuntu 22.04 laptop, I don't get even half the amount of services you are showing.

Could you please show us also the output for these commands:

```
systemd-analyze critical-chain
```

```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

---

### Post by bilkay on 2024-09-24
```
root@Relic:~# timedatectl status
               Local time: Tue 2024-09-24 10:45:44 EDT  
           Universal time: Tue 2024-09-24 14:45:44 UTC  
                 RTC time: Tue 2024-09-24 14:45:44      
                Time zone: America/New_York (EDT, -0400)
System clock synchronized: yes                          
              NTP service: active                       
          RTC in local TZ: no                           

```

```
root@Relic:~# systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @2min 1.037s
&#9492;&#9472;multi-user.target @2min 1.037s
  &#9492;&#9472;sendmail.service @48.449s +1min 12.586s
    &#9492;&#9472;network-online.target @48.047s
      &#9492;&#9472;NetworkManager-wait-online.service @35.608s +12.438s
        &#9492;&#9472;NetworkManager.service @26.848s +8.755s
          &#9492;&#9472;dbus.service @26.842s
            &#9492;&#9472;basic.target @26.727s
              &#9492;&#9472;sockets.target @26.727s
                &#9492;&#9472;snapd.socket @26.722s +3ms
                  &#9492;&#9472;sysinit.target @26.539s
                    &#9492;&#9472;snapd.apparmor.service @25.366s +1.172s
                      &#9492;&#9472;apparmor.service @21.447s +3.911s
                        &#9492;&#9472;local-fs.target @21.443s
                          &#9492;&#9472;run-user-1000-doc.mount @1min 55.755s
                            &#9492;&#9472;run-user-1000.mount @1min 45.337s
                              &#9492;&#9472;local-fs-pre.target @3.320s
                                &#9492;&#9472;systemd-tmpfiles-setup-dev.service @2.611s +7>
                                  &#9492;&#9472;systemd-sysusers.service @2.021s +587ms
                                    &#9492;&#9472;systemd-remount-fs.service @1.679s +272ms
                                      &#9492;&#9472;systemd-journald.socket @1.442s
                                        &#9492;&#9472;-.mount @1.427s
                                          &#9492;&#9472;system.slice @1.427s
                                            &#9492;&#9472;-.slice @1.427s
l
```

```

root@Relic:~# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE MOUNTPOINT
sda    298.1G disk        
&#9500;&#9472;sda1   199M part ntfs   
&#9500;&#9472;sda2 267.2G part ntfs   /host
&#9500;&#9472;sda3    14G part ext4   
&#9500;&#9472;sda4     1K part        
&#9500;&#9472;sda5   512M part vfat   /boot/efi
&#9492;&#9472;sda6  16.2G part ext4   /
sr0     1024M rom         

```

---

### Post by bilkay on 2024-09-24
```

root@Relic:~# journalctl --unit=systemd-timesyncd.service^C
root@Relic:~# timedatectl status
               Local time: Tue 2024-09-24 11:13:05 EDT  
           Universal time: Tue 2024-09-24 15:13:05 UTC  
                 RTC time: Tue 2024-09-24 15:13:05      
                Time zone: America/New_York (EDT, -0400)
System clock synchronized: yes                          
              NTP service: active                       
          RTC in local TZ: no                           

```
```
root@Relic:~# journalctl --unit=systemd-timesyncd.service
-- Reboot --
Sep 23 05:54:55 Relic systemd[1]: Starting Network Time Synchronization...
Sep 23 05:54:55 Relic systemd[1]: Started Network Time Synchronization.
Sep 23 06:00:22 Relic systemd-timesyncd[603]: Initial synchronization to time s>
Sep 23 07:19:53 Relic systemd-timesyncd[603]: Initial synchronization to time s>
Sep 23 10:44:24 Relic systemd-timesyncd[603]: Initial synchronization to time s>
Sep 23 18:49:55 Relic systemd[1]: Stopping Network Time Synchronization...
Sep 23 18:49:56 Relic systemd[1]: systemd-timesyncd.service: Succeeded.
Sep 23 18:49:56 Relic systemd[1]: Stopped Network Time Synchronization.
-- Reboot --
Sep 24 06:08:09 Relic systemd[1]: Starting Network Time Synchronization...
Sep 24 06:08:09 Relic systemd[1]: Started Network Time Synchronization.
Sep 24 06:15:02 Relic systemd-timesyncd[653]: Initial synchronization to time s>
```

---

### Post by bilkay on 2024-09-24
> **oldfred said:**
> Also:
What brand/model system?
HP G62
> **oldfred said:**
> What video card/chip?
I have no idea.

> **oldfred said:**
> Have you updated UEFI firmware to latest available.
And if SSD, its firmware to latest available.
I don't know how do do that.

---

### Post by oldfred on 2024-09-24
If you can boot or boot live installer.
Some hardware info:
inxi -bz

Compare to vendors support site and info on how to update your system, varies by vendor.
sudo dmidecode -s bios-version
udisksctl status

---

### Post by oldfred on 2024-09-24
Your ten minutes must be fast. This took almost 5 days to boot.
[https://www.pcgamer.com/hardware/processors/hacking-wizard-gets-linux-to-run-on-a-1971-processor-though-it-takes-almost-5-days-to-boot-the-kernel/](https://www.pcgamer.com/hardware/processors/hacking-wizard-gets-linux-to-run-on-a-1971-processor-though-it-takes-almost-5-days-to-boot-the-kernel/)

Ok very old system.
I never have had any Linux install take more than 40 seconds. And now with SSD boot is very fast even though more is being installed on boot.

Not sure what is loading in background as it says 4 sec to graphical target, but over a minute & half to fully boot.
```
[FONT=monospace][COLOR=#54ff54]**red@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 1min 33.494s (firmware) + 4.390s (loader) + 4.343s (kernel) + 4.118s (userspace) = 1min 46.346s  
graphical.target reached after 4.085s in userspace.
[/FONT]
```

---

### Post by bilkay on 2024-09-24
```
$ inxi -bz

System:
  Kernel: 5.15.0-122-generic x86_64 bits: 64 Desktop: Unity 7.5.0 
  Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Hewlett-Packard product: HP G62 Notebook PC 
  v: 0499110003202710000020000 serial: <filter> 
  Mobo: Hewlett-Packard model: 1484 v: 77.15 serial: <filter> 
  BIOS: Hewlett-Packard v: F.11 date: 03/23/2010 
Battery:
  ID-1: BAT0 charge: 59.7 Wh condition: 59.7/73.3 Wh (81%) 
CPU:
  Dual Core: Pentium T4500 type: MCP speed: 1197 MHz min/max: 1200/2300 MHz 
Graphics:
  Device-1: Intel Mobile 4 Series Integrated Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express (CTG) 
  v: 2.1 Mesa 21.2.6 
Network:
  Device-1: Qualcomm Atheros AR9285 Wireless Network Adapter driver: ath9k 
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 
Drives:
  Local Storage: total: 298.09 GiB used: 215.43 GiB (72.3%) 
Info:
  Processes: 263 Uptime: 4h 39m Memory: 2.83 GiB used: 1.71 GiB (60.2%) 
  Shell: bash inxi: 3.0.38 

```

---

### Post by bilkay on 2024-09-24
```
$  sudo dmidecode -s bios-version
F.11
```

---

### Post by bilkay on 2024-09-24
```
$  udisksctl status 
MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
Hitachi HTS725032A9A364   PC3OC72E  100320PCKJ00VQG4H9MK sda     
hp       CDDVDW TS-L633N  0300      R3186GEZ368304       sr0     
Generic- Multi-Card       1.00      20071114173400000    sdb     

```

---

### Post by ne29914 on 2024-09-24
I've had problems with long boot times, and it almost always turned out to be problems with partition UUIDs not matching the UUIDs in the system files Can happen when restoring backups etc.).
Mainly:
```
/etc/fstab
```
But also
```
/etc/default/grub
/etc/initramfs-tools/conf.d/resume
```

If there's a mismatch between your real UUIDs and those files, Ubuntu will try finding the partitions, and it takes a lot of time.

From terminal, run:
```
blkid
```
to see the UUIDs and compare them to the files I listed.

---

### Post by bilkay on 2024-09-26
> **ne29914 said:**
> I've had problems with long boot times, and it almost always turned out to be problems with partition UUIDs not matching the UUIDs in the system files Can happen when restoring backups etc.).
Mainly:
```
/etc/fstab
```
But also
```
/etc/default/grub
/etc/initramfs-tools/conf.d/resume
```

If there's a mismatch between your real UUIDs and those files, Ubuntu will try finding the partitions, and it takes a lot of time.

From terminal, run:
```
blkid
```
to see the UUIDs and compare them to the files I listed.

They're all good.

---

### Post by ne29914 on 2024-09-26
Try adding the following line to /etc/default/grub:
```
GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT
```

---

### Post by tea for one on 2024-09-26
> **bilkay said:**
> ```
$ inxi -bz
System:
  Kernel: 5.15.0-122-generic x86_64 bits: 64 Desktop: Unity 7.5.0 
  Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Hewlett-Packard product: HP G62 Notebook PC 
  v: 0499110003202710000020000 serial: <filter> 
  Mobo: Hewlett-Packard model: 1484 v: 77.15 serial: <filter> 
  BIOS: Hewlett-Packard v: F.11 date:[COLOR="#0000FF"] 03/23/2010 [/COLOR]

```
Is your laptop 14 years old?
If so, perhaps a different flavour of the Ubuntu family may perform more responsively?
Try Lubuntu 24.04 in a live session?

---

### Post by ne29914 on 2024-09-26
> **tea for one said:**
> Is your laptop 14 years old?
If so, perhaps a different flavour of the Ubuntu family may perform more responsively?
Try Lubuntu 24.04 in a live session?

Mine is 16 years old and boots within 30 seconds. But Lubuntu might be a better choice. I recommend 20.04, later versions can't control screen brightness:

```

macro@1dk6910p:~$ inxi -bz
System:    Kernel: 5.15.0-122-generic x86_64 bits: 64 Desktop: LXQt 0.14.1 Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Hewlett-Packard product: HP Compaq 6910p v: F.13 serial: <filter> 
           Mobo: Hewlett-Packard model: 30BE v: KBC Version 68.35 serial: <filter> BIOS: Hewlett-Packard 
           v: 68MCU Ver. F.13 date: 02/20/2008 
Battery:   ID-1: C23B charge: 47.5 Wh condition: 47.5/47.5 Wh (100%) 
CPU:       Dual Core: Intel Core2 Duo T7100 type: MCP speed: 798 MHz min/max: 800/1801 MHz 
Graphics:  Device-1: Intel Mobile GM965/GL960 Integrated Graphics driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.13 driver: modesetting unloaded: fbdev,vesa resolution: 1280x800~60Hz 
           OpenGL: renderer: Mesa DRI Intel 965GM (CL) v: 2.1 Mesa 21.2.6 
Network:   Device-1: Intel 82566MM Gigabit Network driver: e1000e 
Drives:    Local Storage: total: 232.89 GiB used: 36.86 GiB (15.8%) 
Info:      Processes: 178 Uptime: 2h 04m Memory: 3.81 GiB used: 1.14 GiB (29.8%) Shell: bash inxi: 3.0.38 
macro@1dk6910p:~$ 

```

---

### Post by tea for one on 2024-09-26
> **ne29914 said:**
> Mine is 16 years old and boots within 30 seconds. But Lubuntu might be a better choice. I recommend 20.04, later versions can't control screen brightness:
Remarkable, well done.
Hopefully, your experience will be able to help the OP.
Mine is a callow youth, only 8 years old, although the UEFI firmware is a touch older.
```
Machine:
  Type: Laptop System: HP product: HP Stream Notebook 
  v: Type1ProductConfigId serial: <superuser required> 
  Mobo: HP model: 815E v: 32.0D serial: <superuser required> UEFI: Insyde 
  v: F.05 date: 11/23/2015 

```

---

### Post by oldfred on 2024-09-26
[https://support.hp.com/us-en/drivers/hp-g62-a00-notebook-pc-series/4156509](https://support.hp.com/us-en/drivers/hp-g62-a00-notebook-pc-series/4156509)
Shows a newer BIOS for this system.

But suggestion for lighter weight flavor is probably best.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

I had good results with Kubuntu on my 2006 laptop, but with an external SSD.

---

### Post by bilkay on 2024-10-10
Maybe one of the gurus here can explain why the time server would be waiting over six minutes for time synchronization with a remote time server when my system doesn't even have internet access yet.

---

### Post by bilkay on 2024-10-10
My wife's laptop, also Ubuntu 20.04, doesn't experience this problem, and "systemd-timesyncd" does not appear in its syslog. Nor does timesyncd.conf exist in its /etc/systemd.

---

### Post by oldfred on 2024-10-10
If you do not have Internet, then events have to time out. Each event then can take 1.5 minutes, so that could be the entire issue.

---

### Post by bilkay on 2024-10-10
I tried disabling systemd-timesync and now it doesn't show up in syslog on startup, but it still takes forever to boot.

---

### Post by bilkay on 2024-10-14
This is interesting. I deleted boot parameters "quiet" and "splash" on startup (to see where it was hanging up) and boot time dropped to about 2 1/2 minutes with no other action.

---

