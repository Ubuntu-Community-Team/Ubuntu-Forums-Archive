---
title: "Hello. How can I improve boot up time in laptop?"
date: 2016-01-02
forum: General Help
---

### Post by rebelrobot on 2016-01-02
Hello everyone,  I'm new in Ubuntu, I installed Ubuntu 14.04 in my acer aspire laptop and it's amazing. However, it takes my laptop  50seconds to boot up. Is it normal?  I'd appreciate any advice to improve this time.  Thanks in advanced.

---

### Post by coldraven on 2016-01-02
I don't know the specs of your laptop but my 5 year old dual core HP 2Ghz with 4GB memory boots in about 30 secs. For a friend I put a SSD in a similar laptop and it boots in 12 secs

---

### Post by pqwoerituytrueiwoq on 2016-01-02
post the output of these commands and we will see if we can find any delays
```
cat /var/log/boot.log
dmesg
```
you could also give us a [bootchart](apt:bootchart), when installed it will put a chart in [FONT=courier new]/var/log/bootchart/[/FONT] a png file will show up in there a minute or 2 after login, please upload the image to imgur, the forums will scale the image down so it will me unreadable

---

### Post by rebelrobot on 2016-01-03
> **coldraven said:**
> I don't know the specs of your laptop but my 5 year old dual core HP 2Ghz with 4GB memory boots in about 30 secs. For a friend I put a SSD in a similar laptop and it boots in 12 secs  Hi there, my laptop is an Acer Aspire AMD quad-core 3.30Ghz with 8Gb memory. That's why I'm worried about the long time it takes it to boot. I have to say that this laptop has windows 10 and I installed Ubuntu to try it making a new partition.

---

### Post by mcduck on 2016-01-03
The boot time pretty much just depends on your hard drive. (Booting mainly just requires the system to read all the necessary stuff from the drive to memory, there really isn't much of computing work to do so the CPU doesn't mater that much, and the amount/speed of RAM doesn't make difference either as it's going to be orders of magnitude faster than your hard drive is anyway).

SSD or a hard drive with built-in SSD is pretty much the way to improve yuur boot speed. Or a faster hard drive, of course, although the benefit is much smaller.

 Windows 10 tricks you a bit by using a hybrid between shutting down ans suspending so that's why it might get up and running in less time (full boot of Win10 tends to still be pretty slow on normal hard drives), and also some laptops have small SSD's which are just used as a cache to load Windows files quicker, that kind of setups often rely on software (unlike hard drive with built-in SSD cache) so they don't help with Ubuntu.

---

### Post by rebelrobot on 2016-01-03
> **pqwoerituytrueiwoq said:**
> post the output of these commands and we will see if we can find any delays
```
cat /var/log/boot.log
dmesg
```
you could also give us a [bootchart]("apt:bootchart"), when installed it will put a chart in [FONT=courier new]/var/log/bootchart/[/FONT] a png file will show up in there a minute or 2 after login, please upload the image to imgur, the forums will scale the image down so it will me unreadable


Hi there I saved the output for both those commands in two files hope you can read them but I warn you, they are very long!
Also I installed bootchart and saved the image to imgur this is the link: [http://imgur.com/XBU5IcF](http://imgur.com/XBU5IcF)

I  think this may be important: This laptop originaly has Windows 10, I  installed ubuntu some days ago making a partition in the disk which is a  1000Gb Hdd. So I have a dual boot. 

Thank you so much for your interest and I would appreciate your help. 

bye.

---

### Post by pqwoerituytrueiwoq on 2016-01-03
i may be able to save you about 20 seconds
but lets take a look at this to make sure the issue is what i think it is
```
cat /etc/fstab
ls -l /dev/disk/by-uuid/
sudo parted -l
```

also look at your firewall settings, use [gufw](apt:gufw) if you want a gui for it

---

### Post by rebelrobot on 2016-01-03
> **pqwoerituytrueiwoq said:**
> i may be able to save you about 20 seconds
but lets take a look at this to make sure the issue is what i think it is
```
cat /etc/fstab
ls -l /dev/disk/by-uuid/
sudo parted -l
```

also look at your firewall settings, use [gufw]("apt:gufw") if you want a gui for it


```
marcelomgm@Marcelo1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=202176b3-3c84-47b2-bfc7-38c8481f7bc1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=AA5C-6921  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda7 during installation
UUID=195569fb-edda-4e2e-8da5-995cee500341 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=e89cb682-1089-4976-9736-31f7a0f73a79 none            swap    sw              0       0
```


```
marcelomgm@Marcelo1:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 ene  3 15:59 195569fb-edda-4e2e-8da5-995cee500341 -> ../../sda7
lrwxrwxrwx 1 root root 10 ene  3 15:59 202176b3-3c84-47b2-bfc7-38c8481f7bc1 -> ../../sda6
lrwxrwxrwx 1 root root 10 ene  3 15:59 40225DDB225DD70E -> ../../sda4
lrwxrwxrwx 1 root root 10 ene  3 15:59 940459E40459C9BE -> ../../sda1
lrwxrwxrwx 1 root root 10 ene  3 15:59 94725F66725F4BDC -> ../../sda5
lrwxrwxrwx 1 root root 10 ene  3 15:59 AA5C-6921 -> ../../sda2
lrwxrwxrwx 1 root root 10 ene  3 15:59 e89cb682-1089-4976-9736-31f7a0f73a79 -> ../../sda8
```

```
marcelomgm@Marcelo1:~$ sudo parted -l
[sudo] password for marcelomgm: 
Modelo: ATA ST1000LM024 HN-M (scsi)
Disco /dev/sda: 1000GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones. gpt

Numero  Inicio  Fin     Tamaño  Sistema de archivos  Nombre                        Banderas
 1      1049kB  630MB   629MB   ntfs                 Basic data partition          oculta, diag
 2      630MB   945MB   315MB   fat32                EFI system partition          arranque
 3      945MB   1079MB  134MB                        Microsoft reserved partition  msftres
 4      1079MB  669GB   668GB   ntfs                 Basic data partition          msftdata
 6      669GB   819GB   150GB   ext4
 7      819GB   909GB   90,0GB  ext4
 8      909GB   910GB   1100MB  linux-swap(v1)
 5      983GB   1000GB  16,7GB  ntfs                 Basic data partition          oculta, diag
```

thanks 4 all dude

---

### Post by pqwoerituytrueiwoq on 2016-01-03
no issue there, but just maybe, this should look this this for you
```
marcelomgm@Marcelo1:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=E89CB682-1089-4976-9736-31F7A0F73A79
```
if not that could be the issue

---

### Post by rebelrobot on 2016-01-03
> **pqwoerituytrueiwoq said:**
> no issue there, but just maybe, this should look this this for you
```
marcelomgm@Marcelo1:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=E89CB682-1089-4976-9736-31F7A0F73A79
```
if not that could be the issue

I ran the code and the result is exactly the same:

```
marcelomgm@Marcelo1:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=e89cb682-1089-4976-9736-31f7a0f73a79
```

---

### Post by pqwoerituytrueiwoq on 2016-01-03
then why is there a 15 second delay here :?
[FONT=courier new][4.976476] Switched to clocksource tsc
[5.168732] random: nonblocking pool is initialized
[5.193363] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[20.342585] Adding 1074172k swap on /dev/sda8. Priority:-1 extents:1 across:1074172k FS
[20.497932] systemd-udevd[301]: starting version 204
[20.580416] lp: driver loaded but no devices found[/FONT]
*looks at boot chart*
oh it just happened to be checking the partition  during that boot (1 in 20 chance of that)
maybe someone else has an idea
on  the note of a ssd upgrade on my laptop i have a SSD and a 7200 WD black  drive installed i replaced my optical drive with a  [caddy](http://www.lindy.co.uk/images/ultra-slim-odd-caddy-for-2-5-sata-hdd-9-5mm-height-p6605-3276_zoom.jpg)

---

### Post by rebelrobot on 2016-01-03
> **pqwoerituytrueiwoq said:**
> then why is there a 15 second delay here :?
[FONT=courier new][4.976476] Switched to clocksource tsc
[5.168732] random: nonblocking pool is initialized
[5.193363] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[20.342585] Adding 1074172k swap on /dev/sda8. Priority:-1 extents:1 across:1074172k FS
[20.497932] systemd-udevd[301]: starting version 204
[20.580416] lp: driver loaded but no devices found[/FONT]
*looks at boot chart*
oh it just happened to be checking the partition  during that boot (1 in 20 chance of that)
maybe someone else has an idea
on  the note of a ssd upgrade on my laptop i have a SSD and a 7200 WD black  drive installed i replaced my optical drive with a  [caddy]("http://www.lindy.co.uk/images/ultra-slim-odd-caddy-for-2-5-sata-hdd-9-5mm-height-p6605-3276_zoom.jpg")

Ok thanks for your help anyways

---

### Post by rebelrobot on 2016-01-04
Hello everyone, 

I recently installed Lubuntu in an 'old' laptop. Intel celeron processor 1.46Ghz, ram=1Gb ddr2. And I'm experiencing very slow boot up. Timed 80 seconds and its kinda sad as I come from Windows XP which used to take about 40 seconds.

I hope someone can give an advice, I'm new in Ubuntu.
I ran dmesg and the output is:
```
[   27.302009] Adding 1040380k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:1040380k FS
[   31.853178] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   31.960991] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   34.934050] audit: type=1400 audit(1451901170.644:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=594 comm="apparmor_parser"
[   34.934068] audit: type=1400 audit(1451901170.644:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=594 comm="apparmor_parser"
[   35.047666] audit: type=1400 audit(1451901170.760:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=594 comm="apparmor_parser"
[   35.047687] audit: type=1400 audit(1451901170.760:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=594 comm="apparmor_parser"
[   35.047697] audit: type=1400 audit(1451901170.760:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=594 comm="apparmor_parser"
[   35.047708] audit: type=1400 audit(1451901170.760:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=594 comm="apparmor_parser"
[   35.545556] audit: type=1400 audit(1451901171.256:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=594 comm="apparmor_parser"
[   35.545579] audit: type=1400 audit(1451901171.256:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=594 comm="apparmor_parser"
[   35.545590] audit: type=1400 audit(1451901171.256:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=594 comm="apparmor_parser"
[   35.545601] audit: type=1400 audit(1451901171.256:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=594 comm="apparmor_parser"
[   51.879317] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   51.889347] r8169 0000:02:00.0 enp2s0: link down
[   51.889896] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   51.906075] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.048058] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   52.136176] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   52.263491] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.536190] wlan0: authenticate with dc:53:7c:61:65:ff
[   53.548306] wlan0: send auth to dc:53:7c:61:65:ff (try 1/3)
[   53.550159] wlan0: authenticated
[   53.552163] wlan0: associate with dc:53:7c:61:65:ff (try 1/3)
[   53.554506] wlan0: RX AssocResp from dc:53:7c:61:65:ff (capab=0x411 status=0 aid=2)
[   53.554951] wlan0: associated
[   53.554999] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  139.709990] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ce:43:4a:a8:dc:53:7c:61:65:fd:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=54376 PROTO=2 
[  264.715172] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ce:43:4a:a8:dc:53:7c:61:65:fd:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=54377 PROTO=2 
[  389.720310] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ce:43:4a:a8:dc:53:7c:61:65:fd:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=54378 PROTO=2 
```

Note how in sec35.54 to 51.87 there's a delay I don't know why, and also from 53sec to 139.70 sec there's another delay.

---

### Post by matt_symes on 2016-01-04
Hi

It's not really fair to compare the boot times of a new OS to a 15 year old OS. Even service pack 3 was released in 2008.

The specs of that laptop are pretty low.

Anyway you may want to install bootchart to see what's going on.

Kind regards

---

### Post by mörgæs on 2016-01-04
> **rebelrobot said:**
> 
Note how in sec35.54 to 51.87 there's a delay

Yes, you could try to disable IP v 6 and see if it goes faster after that.

---

### Post by rebelrobot on 2016-01-04
> **mörgæs said:**
> Yes, you could try to disable IP v 6 and see if it goes faster after that.    Thank you guys for your response I appreciate it.  Can I disable Ipv6 safely? and how can I do it? sorry but I'm newish in ubuntu.

---

### Post by matt_symes on 2016-01-04
Hi

IPv6 can be safely disabled.

Open a terminal and type

```
sudo nano /etc/sysctl.conf
```

Enter your password. It will not be echoed to the screen. This is normal.

Type these extra lines into the file.

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

Hit <ctrl>  + o to save and <ctrl> + x to exit.

The reboot and time it.

Kind regards

---

### Post by rebelrobot on 2016-01-04
Hi there, I reinstalled Ubuntu 14.04 because I think it maybe would help. In fact I've timed a boot up time of 40 seconds.  Here are some terminal output maybe you people can check it. THanks.
```
marcelomgm@marxmgm1:~$ cat /var/log/boot.log
 * Stopping adjust system clock and timezone                                   [ OK ]
 * Starting Read required files in advance                                     [ OK ]
 * Starting Mount filesystems on boot                                          [ OK ]
 * Starting Fix-up sensitive /proc filesystem entries                          [ OK ]
 * Starting Populate /dev filesystem                                           [ OK ]
 * Starting Populate and link to /run filesystem                               [ OK ]
 * Stopping Fix-up sensitive /proc filesystem entries                          [ OK ]
 * Stopping Populate /dev filesystem                                           [ OK ]
 * Stopping Populate and link to /run filesystem                               [ OK ]
 * Stopping Track if upstart is running in a container                         [ OK ]
 * Starting Initialize or finalize resolvconf                                  [ OK ]
 * Starting set console keymap                                                 [ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted               [ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted               [ OK ]
 * Starting set sysctls from /etc/sysctl.conf                                  [ OK ]
 * Starting Bridge udev events into upstart                                    [ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted                [ OK ]
 * Stopping set console keymap                                                 [ OK ]
 * Stopping set sysctls from /etc/sysctl.conf                                  [ OK ]
 * Starting device node and kernel event manager                               [ OK ]
 * Starting load modules from /etc/modules                                     [ OK ]
 * Starting cold plug devices                                                  [ OK ]
 * Starting log initial device creation                                        [ OK ]
 * Stopping load modules from /etc/modules                                     [ OK ]
 * Starting Signal sysvinit that the rootfs is mounted                         [ OK ]
 * Starting Clean /tmp directory                                               [ OK ]
 * Starting Uncomplicated firewall                                             [ OK ]
 * Stopping Clean /tmp directory                                               [ OK ]
 * Stopping Read required files in advance (for other mountpoints)             [ OK ]
 * Starting configure network device security                                  [ OK ]
 * Starting configure network device security                                  [ OK ]
 * Starting configure network device security                                  [ OK ]
 * Starting Mount network filesystems                                          [ OK ]
 * Stopping Mount network filesystems                                          [ OK ]
 * Starting Bridge socket events into upstart                                  [ OK ]
 * Starting configure network device                                           [ OK ]
 * Starting configure network device                                           [ OK ]
 * Starting configure network device                                           [ OK ]
 * Stopping Read required files in advance (for other mountpoints)             [ OK ]
 * Starting Signal sysvinit that local filesystems are mounted                 [ OK ]
 * Starting restore software rfkill state                                      [ OK ]
 * Starting Flush boot log to disk                                             [ OK ]
 * Starting flush early job output to logs                                     [ OK ]
 * Stopping Mount filesystems on boot                                          [ OK ]
 * Stopping restore software rfkill state                                      [ OK ]
 * Stopping Flush boot log to disk                                             [ OK ]
 * Stopping flush early job output to logs                                     [ OK ]
 * Stopping Failsafe Boot Delay                                                [ OK ]
 * Starting System V initialisation compatibility                              [ OK ]
 * Starting Bridge file events into upstart                                    [ OK ]
 * Starting system logging daemon                                              [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles        * Starting D-Bus system message bus       [ OK ]
                                                                               [ OK ]
 * Stopping cold plug devices                                                  [ OK ]
 * Starting modem connection manager                                           [ OK ]
 * Starting configure network device security                                  [ OK ]
 * Stopping log initial device creation                                        [ OK ]
 * Starting configure network device security                                  [ OK ]
 * Starting save udev log and update rules                                     [ OK ]
 * Starting set console font                                                   [ OK ]
 * Stopping set console font                                                   [ OK ]
 * Starting userspace bootsplash                                               [ OK ]
 * Starting SystemD login management service                                   [ OK ]
 * Starting Send an event to indicate plymouth is up                           [ OK ]
 * Stopping save udev log and update rules                                     [ OK ]
 * Starting bluetooth daemon                                                   [ OK ]
 * Starting configure virtual network devices                                  [ OK ]
 * Starting mDNS/DNS-SD daemon                                                 [ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [ OK ]
 * Stopping Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                   [ OK ]
 * Starting network connection manager                                         [ OK ]
 * Stopping userspace bootsplash                                               [ OK ]
 * Setting up X socket directories...                                          [ OK ]
 * Stopping System V initialisation compatibility                              [ OK ]
 * Starting System V runlevel compatibility                                    [ OK ]
 * Starting Restore Sound Card State                                           [ OK ]
 * Starting anac(h)ronistic cron                                               [ OK ]
 * Starting save kernel messages                                               [ OK ]
 * Stopping Restore Sound Card State                                           [ OK ]
 * Starting cups-browsed - Bonjour remote printer browsing daemon              [ OK ]
 * Starting automatic crash report generation                                  [ OK ]
 * Stopping Restore Sound Card State                                           [ OK ]
 * Starting CPU interrupts balancing daemon                                    [ OK ]
 * Starting ACPI daemon                                                        [ OK ]
 * Starting regular background program processing daemon                       [ OK ]
 * Stopping save kernel messages                                               [ OK ]
 * speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Restoring resolver state...                                                 [ OK ]
 * Stopping System V runlevel compatibility                                    [ OK ]
 * Starting crash report submission daemon                                     [ OK ]
 * Starting Mount network filesystems                                          [ OK ]
 * Stopping Mount network filesystems                                          [ OK ]
marcelomgm@marxmgm1:~$ 


```

```
[    9.990996] acpi device:00: registered as cooling_device4
[    9.991077] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    9.991206] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    9.991611] acpi device:02: registered as cooling_device5
[    9.991680] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:01/input/input9
[   10.286591] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.291049] wmi: Mapper loaded
[   10.312597] ACPI Warning: SystemIO range 0x0000000000000b00-0x0000000000000b07 conflicts with OpRegion 0x0000000000000b00-0x0000000000000b0f (\_SB_.PCI0.SMBS.SMB0) (20141107/utaddress-258)
[   10.312605] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.378776] MCE: In-kernel MCE decoding enabled.
[   10.532683] [drm] Initialized drm 1.1.0 20060810
[   10.617305] EDAC MC: Ver: 3.0.0
[   10.620045] cfg80211: Calling CRDA to update world regulatory domain
[   10.654456] AMD64 EDAC driver v3.4.0
[   10.654504] EDAC amd64: DRAM ECC disabled.
[   10.654513] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.654513]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.654513]  (Note that use of the override may cause unknown side effects.)
[   11.323011] [drm] radeon kernel modesetting enabled.
[   11.323036] VGA switcheroo: detected switching method \_SB_.PCI0.VGA_.ATPX handle
[   11.430760] AVX version of gcm_enc/dec engaged.
[   11.430765] AES CTR mode by8 optimization enabled
[   11.443991] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.443997] Disabling lock debugging due to kernel taint
[   11.449524] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   11.478518] snd_hda_intel 0000:00:01.1: Force to non-snoop mode
[   11.542852] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   11.542856] AMD IOMMUv2 functionality not available on this system
[   11.569657] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input10
[   11.578229] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   11.633623] Found CRAT image with size=1360
[   11.633628] Parsing CRAT table with 1 nodes
[   11.633631] Found CU entry in CRAT table with proximity_domain=0 caps=0
[   11.633633] CU CPU: cores=4 id_base=16
[   11.633634] Found CU entry in CRAT table with proximity_domain=0 caps=0
[   11.633636] CU GPU: simds=32 id_base=-2147483648
[   11.633638] Found memory entry in CRAT table with proximity_domain=0
[   11.633639] Found memory entry in CRAT table with proximity_domain=0
[   11.633641] Found cache entry in CRAT table with processor_id=16
[   11.633642] Found cache entry in CRAT table with processor_id=16
[   11.633644] Found cache entry in CRAT table with processor_id=16
[   11.633646] Found cache entry in CRAT table with processor_id=17
[   11.633647] Found cache entry in CRAT table with processor_id=18
[   11.633648] Found cache entry in CRAT table with processor_id=18
[   11.633649] Found cache entry in CRAT table with processor_id=18
[   11.633650] Found cache entry in CRAT table with processor_id=19
[   11.633652] Found TLB entry in CRAT table (not processing)
[   11.633653] Found TLB entry in CRAT table (not processing)
[   11.633654] Found TLB entry in CRAT table (not processing)
[   11.633655] Found TLB entry in CRAT table (not processing)
[   11.633656] Found TLB entry in CRAT table (not processing)
[   11.633657] Found TLB entry in CRAT table (not processing)
[   11.633658] Found TLB entry in CRAT table (not processing)
[   11.633659] Found TLB entry in CRAT table (not processing)
[   11.633660] Found TLB entry in CRAT table (not processing)
[   11.633661] Found TLB entry in CRAT table (not processing)
[   11.633662] Creating topology SYSFS entries
[   11.633692] Finished initializing topology ret=0
[   11.633765] kfd kfd: Initialized module
[   11.634083] checking generic (e0000000 420000) vs hw (e0000000 10000000)
[   11.634086] fb: switching to radeondrmfb from EFI VGA
[   11.634126] Console: switching to colour dummy device 80x25
[   11.634622] [drm] initializing kernel modesetting (KAVERI 0x1002:0x1309 0x1025:0x0864).
[   11.634640] [drm] register mmio base: 0xF0B00000
[   11.634641] [drm] register mmio size: 262144
[   11.634648] [drm] doorbell mmio base: 0xF0000000
[   11.634649] [drm] doorbell mmio size: 8388608
[   11.634654] [drm] ACPI VFCT contains a BIOS for 00:01.0 1002:1309, size 62976
[   11.634680] ATOM BIOS: BR45399.001
[   11.634726] [drm] Changing default dispclk from 533Mhz to 600Mhz
[   11.634747] radeon 0000:00:01.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   11.634750] radeon 0000:00:01.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[   11.634752] [drm] Detected VRAM RAM=1024M, BAR=256M
[   11.634754] [drm] RAM width 128bits DDR
[   11.634823] [TTM] Zone  kernel: Available graphics memory: 3511764 kiB
[   11.634825] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   11.634827] [TTM] Initializing pool allocator
[   11.634834] [TTM] Initializing DMA pool allocator
[   11.634863] [drm] radeon: 1024M of VRAM memory ready
[   11.634865] [drm] radeon: 1024M of GTT memory ready.
[   11.634898] [drm] Loading kaveri Microcode
[   11.728023] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   11.728029] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.728033] sound hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   11.728035] sound hdaudioC1D0:    mono: mono_out=0x0
[   11.728037] sound hdaudioC1D0:    inputs:
[   11.728039] sound hdaudioC1D0:      Mic=0x12
[   11.771233] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   11.921815] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   11.996388] [drm] Internal thermal controller without fan control
[   11.997953] [drm] radeon: dpm initialized
[   12.069879] kvm: Nested Virtualization enabled
[   12.069889] kvm: Nested Paging enabled
[   12.085268] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[   12.085303] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   12.108492] [drm] PCIE GART of 1024M enabled (table at 0x000000000078C000).
[   12.108708] radeon 0000:00:01.0: WB enabled
[   12.108731] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88008de5fc00
[   12.108737] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff88008de5fc04
[   12.108743] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff88008de5fc08
[   12.108748] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff88008de5fc0c
[   12.108753] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff88008de5fc10
[   12.109388] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc900050b6c98
[   12.109508] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000040000c18 and cpu addr 0xffff88008de5fc18
[   12.109512] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000040000c1c and cpu addr 0xffff88008de5fc1c
[   12.109517] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   12.109519] [drm] Driver supports precise vblank timestamp query.
[   12.109570] radeon 0000:00:01.0: radeon: using MSI.
[   12.109607] [drm] radeon: irq initialized.
[   12.116068] [drm] ring test on 0 succeeded in 3 usecs
[   12.116171] [drm] ring test on 1 succeeded in 2 usecs
[   12.116192] [drm] ring test on 2 succeeded in 2 usecs
[   12.116378] [drm] ring test on 3 succeeded in 5 usecs
[   12.116388] [drm] ring test on 4 succeeded in 4 usecs
[   12.162216] [drm] ring test on 5 succeeded in 2 usecs
[   12.182121] [drm] UVD initialized successfully.
[   12.291418] input:     UNKNOWN as /devices/pci0000:00/0000:00:13.0/usb6/6-1/6-1:1.0/0003:06CB:2970.0003/input/input12
[   12.291510] [drm] ring test on 6 succeeded in 17 usecs
[   12.291525] [drm] ring test on 7 succeeded in 3 usecs
[   12.291528] [drm] VCE initialized successfully.
[   12.291775] hid-multitouch 0003:06CB:2970.0003: input,hiddev0,hidraw2: USB HID v1.11 Mouse [   ] on usb-0000:00:13.0-1/input0
[   12.295251] [drm] ib test on ring 0 succeeded in 0 usecs
[   12.354728] Bluetooth: Core ver 2.20
[   12.354777] NET: Registered protocol family 31
[   12.354781] Bluetooth: HCI device and connection manager initialized
[   12.354790] Bluetooth: HCI socket layer initialized
[   12.354795] Bluetooth: L2CAP socket layer initialized
[   12.354809] Bluetooth: SCO socket layer initialized
[   12.477242] usbcore: registered new interface driver btusb
[   12.488377] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-04ca-2009.hcd failed with error -2
[   12.488390] Bluetooth: hci0: BCM: patch brcm/BCM43142A0-04ca-2009.hcd not found
[   12.489321] audit: type=1400 audit(1451907612.773:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=443 comm="apparmor_parser"
[   12.489336] audit: type=1400 audit(1451907612.773:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=443 comm="apparmor_parser"
[   12.489345] audit: type=1400 audit(1451907612.773:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=443 comm="apparmor_parser"
[   12.489358] audit: type=1400 audit(1451907612.773:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=521 comm="apparmor_parser"
[   12.489369] audit: type=1400 audit(1451907612.773:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=521 comm="apparmor_parser"
[   12.489379] audit: type=1400 audit(1451907612.773:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=521 comm="apparmor_parser"
[   12.489404] audit: type=1400 audit(1451907612.773:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=428 comm="apparmor_parser"
[   12.489421] audit: type=1400 audit(1451907612.773:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=428 comm="apparmor_parser"
[   12.489431] audit: type=1400 audit(1451907612.773:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=428 comm="apparmor_parser"
[   12.490106] audit: type=1400 audit(1451907612.773:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=428 comm="apparmor_parser"
[   12.498931] media: Linux media interface: v0.10
[   12.514909] acer_wmi: Acer Laptop ACPI-WMI Extras
[   12.515144] acer_wmi: Function bitmap for Communication Button: 0x801
[   12.515161] acer_wmi: Brightness must be controlled by acpi video driver
[   12.525100] acer_wmi: Enabling Launch Manager failed: 0xe2 - 0x0
[   12.525224] input: Acer WMI hotkeys as /devices/virtual/input/input14
[   12.525971] input: Acer BMA150 accelerometer as /devices/virtual/input/input15
[   12.562570] Linux video capture interface: v2.00
[   12.792580] [drm] ib test on ring 1 succeeded in 0 usecs
[   12.957356] uvcvideo: Found UVC 1.00 device HD WebCam (04f2:b455)
[   12.966517] input: HD WebCam as /devices/pci0000:00/0000:00:12.2/usb3/3-3/3-3:1.0/input/input16
[   12.966712] usbcore: registered new interface driver uvcvideo
[   12.966717] USB Video Class driver (1.1.1)
[   13.177914] cfg80211: World regulatory domain updated:
[   13.177922] cfg80211:  DFS Master region: unset
[   13.177924] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.177930] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.177934] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.177937] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.177941] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.177944] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.293067] [drm] ib test on ring 2 succeeded in 0 usecs
[   13.293182] [drm] ib test on ring 3 succeeded in 0 usecs
[   13.293266] [drm] ib test on ring 4 succeeded in 0 usecs
[   13.813544] [drm] ib test on ring 5 succeeded
[   13.834364] [drm] ib test on ring 6 succeeded
[   13.835148] [drm] ib test on ring 7 succeeded
[   13.841395] [drm] radeon atom DIG backlight initialized
[   13.841404] [drm] Radeon Display Connectors
[   13.841407] [drm] Connector 0:
[   13.841410] [drm]   eDP-1
[   13.841412] [drm]   HPD2
[   13.841416] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[   13.841418] [drm]   Encoders:
[   13.841421] [drm]     LCD1: INTERNAL_UNIPHY2
[   13.841423] [drm] Connector 1:
[   13.841425] [drm]   HDMI-A-1
[   13.841427] [drm]   HPD3
[   13.841430] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[   13.841432] [drm]   Encoders:
[   13.841434] [drm]     DFP1: INTERNAL_UNIPHY2
[   13.841436] [drm] Connector 2:
[   13.841437] [drm]   VGA-1
[   13.841439] [drm]   HPD1
[   13.841442] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[   13.841444] [drm]   Encoders:
[   13.841446] [drm]     CRT1: INTERNAL_UNIPHY
[   13.841448] [drm]     CRT1: NUTMEG
[   14.666660] [drm] fb mappable at 0xE0990000
[   14.666667] [drm] vram apper at 0xE0000000
[   14.666669] [drm] size 4325376
[   14.666672] [drm] fb depth is 24
[   14.666674] [drm]    pitch is 5632
[   14.666923] fbcon: radeondrmfb (fb0) is primary device
[   14.667036] Console: switching to colour frame buffer device 170x48
[   14.667079] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[   14.667083] radeon 0000:00:01.0: registered panic notifier
[   14.696346] kfd kfd: error getting iommu info. is the iommu enabled?
[   14.696355] kfd kfd: Error initializing iommuv2 for device (1002:1309)
[   14.696385] Creating topology SYSFS entries
[   14.697739] kfd kfd: device (1002:1309) NOT added due to errors
[   14.697747] [drm] Initialized radeon 2.40.0 20080528 for 0000:00:01.0 on minor 0
[   14.697895] radeon 0000:01:00.0: enabling device (0002 -> 0003)
[   14.698636] [drm] initializing kernel modesetting (OLAND 0x1002:0x6604 0x1025:0x086A).
[   14.698665] [drm] register mmio base: 0xF0A00000
[   14.698668] [drm] register mmio size: 262144
[   14.698673] vga_switcheroo: enabled
[   14.699564] ATPX version 1, functions 0x00000003
[   14.852853] ATOM BIOS: Acer/Compal
[   14.852875] [drm] GPU not posted. posting now...
[   14.857311] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   14.857316] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   14.857320] [drm] Detected VRAM RAM=2048M, BAR=256M
[   14.857323] [drm] RAM width 128bits DDR
[   14.857347] [drm] radeon: 2048M of VRAM memory ready
[   14.857350] [drm] radeon: 1024M of GTT memory ready.
[   14.857377] [drm] Loading oland Microcode
[   15.119551] [drm] Internal thermal controller without fan control
[   15.119763] [drm] probing gen 2 caps for device 1022:1425 = 733d01/e
[   15.130480] [drm] radeon: dpm initialized
[   15.160157] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   15.162012] [drm] probing gen 2 caps for device 1022:1425 = 733d01/e
[   15.162020] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[   16.394833] init: failsafe main process (711) killed by TERM signal
[   16.567985] [drm] PCIE GART of 1024M enabled (table at 0x0000000000277000).
[   16.568165] radeon 0000:01:00.0: WB enabled
[   16.568170] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88008c3c4c00
[   16.568174] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88008c3c4c04
[   16.568178] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88008c3c4c08
[   16.568181] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88008c3c4c0c
[   16.568184] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88008c3c4c10
[   16.569720] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90006835a18
[   16.569724] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   16.569726] [drm] Driver supports precise vblank timestamp query.
[   16.569728] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[   16.569773] radeon 0000:01:00.0: radeon: using MSI.
[   16.569812] [drm] radeon: irq initialized.
[   16.797226] [drm] ring test on 0 succeeded in 1 usecs
[   16.797236] [drm] ring test on 1 succeeded in 1 usecs
[   16.797243] [drm] ring test on 2 succeeded in 1 usecs
[   16.797253] [drm] ring test on 3 succeeded in 3 usecs
[   16.797262] [drm] ring test on 4 succeeded in 4 usecs
[   16.973867] [drm] ring test on 5 succeeded in 1 usecs
[   16.973879] [drm] UVD initialized successfully.
[   16.974437] [drm] ib test on ring 0 succeeded in 0 usecs
[   16.974476] [drm] ib test on ring 1 succeeded in 0 usecs
[   16.974513] [drm] ib test on ring 2 succeeded in 0 usecs
[   16.974549] [drm] ib test on ring 3 succeeded in 0 usecs
[   16.974583] [drm] ib test on ring 4 succeeded in 0 usecs
[   17.625203] [drm] ib test on ring 5 succeeded
[   17.626743] [drm] Radeon Display Connectors
[   17.636104] radeon 0000:01:00.0: No connectors reported connected with modes
[   17.636114] [drm] Cannot find any crtc or sizes - going 1024x768
[   17.638300] [drm] fb mappable at 0xD0479000
[   17.638303] [drm] vram apper at 0xD0000000
[   17.638305] [drm] size 3145728
[   17.638308] [drm] fb depth is 24
[   17.638310] [drm]    pitch is 4096
[   17.638508] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[   17.639113] [drm:radeon_acpi_init [radeon]] *ERROR* Cannot find a backlight controller
[   17.639296] [drm] Initialized radeon 2.40.0 20080528 for 0000:01:00.0 on minor 1
[   17.892038] audit_printk_skb: 174 callbacks suppressed
[   17.892046] audit: type=1400 audit(1451907618.169:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=934 comm="apparmor_parser"
[   17.892065] audit: type=1400 audit(1451907618.169:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=934 comm="apparmor_parser"
[   17.892832] audit: type=1400 audit(1451907618.169:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=934 comm="apparmor_parser"
[   18.068351] Bluetooth: RFCOMM TTY layer initialized
[   18.068362] Bluetooth: RFCOMM socket layer initialized
[   18.068370] Bluetooth: RFCOMM ver 1.11
[   18.183665] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.183671] Bluetooth: BNEP filters: protocol multicast
[   18.183679] Bluetooth: BNEP socket layer initialized
[   18.753695] init: cups main process (966) killed by HUP signal
[   18.753712] init: cups main process ended, respawning
[   21.363007] r8169 0000:02:00.1 eth0: link down
[   21.363147] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.206739] audit: type=1400 audit(1451907622.481:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1107 comm="apparmor_parser"
[   24.719268] [drm] probing gen 2 caps for device 1022:1425 = 733d01/e
[   24.719278] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[   26.107456] [drm] PCIE GART of 1024M enabled (table at 0x0000000000277000).
[   26.107588] radeon 0000:01:00.0: WB enabled
[   26.107594] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88008c3c4c00
[   26.107598] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88008c3c4c04
[   26.107601] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88008c3c4c08
[   26.107605] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88008c3c4c0c
[   26.107608] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88008c3c4c10
[   26.109164] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90006835a18
[   26.338499] [drm] ring test on 0 succeeded in 1 usecs
[   26.338511] [drm] ring test on 1 succeeded in 1 usecs
[   26.338518] [drm] ring test on 2 succeeded in 1 usecs
[   26.338529] [drm] ring test on 3 succeeded in 4 usecs
[   26.338538] [drm] ring test on 4 succeeded in 4 usecs
[   26.515171] [drm] ring test on 5 succeeded in 2 usecs
[   26.515181] [drm] UVD initialized successfully.
[   26.515230] [drm] ib test on ring 0 succeeded in 0 usecs
[   26.515268] [drm] ib test on ring 1 succeeded in 0 usecs
[   26.515304] [drm] ib test on ring 2 succeeded in 0 usecs
[   26.515340] [drm] ib test on ring 3 succeeded in 0 usecs
[   26.515374] [drm] ib test on ring 4 succeeded in 0 usecs
[   27.166680] [drm] ib test on ring 5 succeeded
[   33.516014] init: plymouth-upstart-bridge main process ended, respawning
[   33.538235] init: plymouth-upstart-bridge main process ended, respawning
[   43.360547] init: anacron main process (1098) killed by TERM signal
[   48.465608] audit: type=1400 audit(1451907648.706:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2074 comm="apparmor_parser"
[   48.465626] audit: type=1400 audit(1451907648.706:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2074 comm="apparmor_parser"
[   48.466393] audit: type=1400 audit(1451907648.706:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2074 comm="apparmor_parser"
[   51.246089] [drm] probing gen 2 caps for device 1022:1425 = 733d01/e
[   51.246099] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[   52.633227] [drm] PCIE GART of 1024M enabled (table at 0x0000000000277000).
[   52.633358] radeon 0000:01:00.0: WB enabled
[   52.633364] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff88008c3c4c00
[   52.633368] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff88008c3c4c04
[   52.633371] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff88008c3c4c08
[   52.633375] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff88008c3c4c0c
[   52.633378] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff88008c3c4c10
[   52.634914] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90006835a18
[   52.862801] [drm] ring test on 0 succeeded in 1 usecs
[   52.862808] [drm] ring test on 1 succeeded in 1 usecs
[   52.862815] [drm] ring test on 2 succeeded in 1 usecs
[   52.862825] [drm] ring test on 3 succeeded in 4 usecs
[   52.862834] [drm] ring test on 4 succeeded in 4 usecs
[   53.039649] [drm] ring test on 5 succeeded in 1 usecs
[   53.039661] [drm] UVD initialized successfully.
[   53.039711] [drm] ib test on ring 0 succeeded in 0 usecs
[   53.039752] [drm] ib test on ring 1 succeeded in 0 usecs
[   53.039788] [drm] ib test on ring 2 succeeded in 0 usecs
[   53.039824] [drm] ib test on ring 3 succeeded in 0 usecs
[   53.039858] [drm] ib test on ring 4 succeeded in 0 usecs
[   53.690573] [drm] ib test on ring 5 succeeded

```

bootchart image uploaded to imgur:[http://imgur.com/Tl7vzM5](http://imgur.com/Tl7vzM5)


thanks for your help

---

### Post by ian-weisser on 2016-01-04
> **rebelrobot said:**
> In fact I've timed a boot up time of 40 seconds.

Wait...40 second is *bad*?
For such old hardware, I don't consider 60-80 seconds unusual.
Five-six years ago, boot time was 60-90 seconds.
Currently, 30-40 seconds is about average for my new, much more powerfullaptop.

I think you won't see significantly faster boot without an SSD or other hardware improvement.
There simply aren't many services anymore to turn off or reorder, nor services that hog resources during boot. Those were squeezed dry, optimized, and reorganized years ago.

---

### Post by rebelrobot on 2016-01-04
> **matt_symes said:**
> Hi

IPv6 can be safely disabled.

...

The reboot and time it.

Kind regards
Hi, thanks for your help. I disabled IPV6 and now it boots in 70 secs, it has decreased. I run demsg

```
[    0.000000]   Normal zone: 2190 pages used for memmap

[    8.225381] systemd[1]: Listening on Syslog Socket.
[    8.226620] systemd[1]: Starting Journal Service...
[    8.679290] lp: driver loaded but no devices found
[    8.685846] systemd[1]: Started udev Coldplug all Devices.
[    8.793029] ppdev: user-space parallel port driver
[    8.955875] systemd[1]: Started Load Kernel Modules.
[    8.957371] systemd[1]: Starting Apply Kernel Variables...
[    8.958565] systemd[1]: Mounting FUSE Control File System...
[    8.967390] systemd[1]: Mounted FUSE Control File System.
[    9.984215] systemd[1]: Started Journal Service.
[   10.125518] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.321315] nf_conntrack version 0.5.0 (15856 buckets, 63424 max)
[   10.821539] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   15.011980] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   15.588202] systemd-journald[211]: Received request to flush runtime journal from PID 1
[   16.776126] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.931157] NET: Registered protocol family 23
[   17.211697] intel_rng: FWH not detected
[   17.812233] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102F conflicts with OpRegion 0x0000000000001000-0x000000000000107F (\PMIO) (20150619/utaddress-254)
[   17.812248] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.812254] ACPI Warning: SystemIO range 0x00000000000011B0-0x00000000000011BF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20150619/utaddress-254)
[   17.812262] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.812265] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011AF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20150619/utaddress-254)
[   17.812272] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.812275] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   18.092060] leds_ss4200: no LED devices found
[   18.511683] yenta_cardbus 0000:0a:06.0: CardBus bridge found [1025:0107]
[   18.511715] yenta_cardbus 0000:0a:06.0: Using CSCINT to route CSC interrupts to PCI
[   18.511719] yenta_cardbus 0000:0a:06.0: Routing CardBus interrupts to PCI
[   18.511727] yenta_cardbus 0000:0a:06.0: TI: mfunc 0x01aa1b22, devctl 0x64
[   18.740895] yenta_cardbus 0000:0a:06.0: ISA IRQ mask 0x0cf8, PCI irq 22
[   18.740905] yenta_cardbus 0000:0a:06.0: Socket status: 30000006
[   18.740912] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0a to #0e
[   18.740923] yenta_cardbus 0000:0a:06.0: pcmcia: parent PCI bridge window: [io  0x6000-0x6fff]
[   18.740928] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x6fff:
[   18.742475]  excluding 0x6000-0x60ff 0x6400-0x64ff
[   18.763207] yenta_cardbus 0000:0a:06.0: pcmcia: parent PCI bridge window: [mem 0xd0000000-0xd00fffff]
[   18.763215] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0000000-0xd00fffff:
[   18.763220]  excluding 0xd0000000-0xd000ffff
[   20.575335] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   20.604057] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   20.604083] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 8, Version 0
[   20.616331] Broadcom 43xx driver loaded [ Features: PNL ]
[   20.744061] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC883: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   20.744070] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.744075] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.744079] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   20.744083] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
[   20.744086] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   20.744091] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[   20.744094] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   20.905334] acer_wmi: Acer Laptop ACPI-WMI Extras
[   20.909992] acer_wmi: Function bitmap for Communication Device: 0x27
[   20.912225] input: Acer BMA150 accelerometer as /devices/virtual/input/input16
[   22.446136] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   22.591270] media: Linux media interface: v0.10
[   22.745411] Linux video capture interface: v2.00
[   22.910422] gspca_main: v2.14.0 registered
[   23.180154] gspca_main: ALi m5602-2.14.0 probing 0402:5602
[   23.276396] gspca_m5602: Sensor reported 0xffff
[   23.297139] gspca_m5602: Detected a s5k83a sensor
[   23.338567] usbcore: registered new interface driver ALi m5602
[   24.106012] cfg80211: World regulatory domain updated:
[   24.106022] cfg80211:  DFS Master region: unset
[   24.106025] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   24.106030] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   24.106034] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   24.106037] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   24.106042] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   24.106046] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   24.106050] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   24.106053] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   24.106057] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[COLOR=#ff0000][   26.850311] Adding 1040380k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:1040380k FS
[   31.667944] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem[/COLOR]
[   31.733413] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   34.369938] audit: type=1400 audit(1451911373.064:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=581 comm="apparmor_parser"
[   34.369957] audit: type=1400 audit(1451911373.064:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=581 comm="apparmor_parser"
[   34.506536] audit: type=1400 audit(1451911373.200:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=581 comm="apparmor_parser"
[   34.506557] audit: type=1400 audit(1451911373.200:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
[   34.506567] audit: type=1400 audit(1451911373.200:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=581 comm="apparmor_parser"
[   34.506578] audit: type=1400 audit(1451911373.200:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
[   34.915608] audit: type=1400 audit(1451911373.608:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=581 comm="apparmor_parser"
[   34.915631] audit: type=1400 audit(1451911373.608:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=581 comm="apparmor_parser"
[   34.915643] audit: type=1400 audit(1451911373.608:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=581 comm="apparmor_parser"
[   34.915653] audit: type=1400 audit(1451911373.608:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=581 comm="apparmor_parser"
[   49.173415] r8169 0000:02:00.0 enp2s0: link down
[   49.328062] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   50.796986] wlan0: authenticate with dc:53:7c:61:65:ff
[   50.808328] wlan0: send auth to dc:53:7c:61:65:ff (try 1/3)
[   50.810165] wlan0: authenticated
[   50.812278] wlan0: associate with dc:53:7c:61:65:ff (try 1/3)
[   50.814648] wlan0: RX AssocResp from dc:53:7c:61:65:ff (capab=0x411 status=0 aid=4)
[  [COLOR=#ff0000] 50.815085] wlan0: associated
[   64.324594] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ce:43:4a:a8:dc:53:7c:61:65:fd:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=54457 PROTO=2 
[  189.328374] [UFW [/COLOR]BLOCK] IN=wlan0 OUT= MAC=00:16:ce:43:4a:a8:dc:53:7c:61:65:fd:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=54458 PROTO=2 
$ 


```
Please check there is a gap from 26.85 to 31.86 which to me looks worrying. Besides, do you think this gap from 50.81 to 64.32 to 189.32 is normal? is there something we can do?

Kind regards,

---

### Post by Bucky Ball on 2016-01-04
*Threads merged. *

Please do not start duplicates about the same issue under any circumstances, but least of all when you are already getting plenty of help on the original thread.

---

### Post by rebelrobot on 2016-01-04
> **Bucky Ball said:**
> *Threads merged. *

Please do not start duplicates about the same issue under any circumstances, but least of all when you are already getting plenty of help on the original thread.

I'm having this trouble with 2 laptops, the first one with Ubuntu 14.04 and the second one with Lubuntu. That's why I created two separated posts and I think it's clear if you read the first message of each post.

---

### Post by mörgæs on 2016-01-04
Still the problems are so closely related that they should be dealt with in one thread.

---

### Post by ian-weisser on 2016-01-04
> **rebelrobot said:**
> 
[  [COLOR=#ff0000] 50.815085] wlan0: associated
[   64.324594] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ce:43:4a:a8:dc:53:7c:61:65:fd:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=54457 PROTO=2 
[  189.328374] [UFW [/COLOR]BLOCK] IN=wlan0 OUT= MAC=00:16:ce:43:4a:a8:dc:53:7c:61:65:fd:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=54458 PROTO=2 


Not part of boot-up.
The items at 64 and 189 are packets rejected by the firewall during normal (post-boot) operation.

---

