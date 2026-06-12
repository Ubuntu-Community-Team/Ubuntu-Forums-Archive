---
title: "Slow boot time (&gt;2min)"
date: 2019-05-26
forum: General Help
---

### Post by smaxyx on 2019-05-26
Hi,
  my Kubuntu is booting very slow. I am on Kubuntu 19.04, Plasma  Version 5.15.4, Kernel 5.0.0.15-generic, 64bit. My system is a 8 core i7  with 15GB Ram.
  I spent the last few days trying to figure out, how to improve my boot time. Any help / ideas?  
Thanks
[U][B]
  systemd-analyze blame:     
[/B][/U]
  ```
1min 59.244s apt-daily.service  
     37.807s apt-daily-upgrade.service  
     23.772s dev-sdb4.device  
     22.941s networkd-dispatcher.service  
     22.906s ModemManager.service  
     22.824s wicd.service  
     22.470s snapd.service  
     21.207s gpu-manager.service  
     20.488s accounts-daemon.service  
     19.625s udisks2.service  
     18.369s mpd.service  
     16.101s grub-common.service  
     15.788s stunnel4.service  
     15.206s apport.service  
     15.132s dev-loop25.device  
     15.070s avahi-daemon.service  
     15.000s networking.service  
     14.897s rsyslog.service  
     14.890s NetworkManager.service  
     14.798s thermald.service  
     14.689s wpa_supplicant.service  
     14.340s dev-loop17.device  
     14.286s dev-loop23.device  
     14.179s dev-loop28.device  
```

  I am wondering if it has something to do with the differences from what I see in /etc/fstab and the blkid output:  

  _**/etc/fstab:**_
```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
 / was on /dev/sdb4 during installation
UUID=51ec0aae-6365-41fa-898f-208a63b99775 /               ext4    errors=remount-ro 0       1
/boot/efi was on /dev/sda1 during installation
UUID=ECA3-78BB  /boot/efi       vfat    umask=0077      0       1
swap was on /dev/sdb5 during installation
UUID=8ee4e011-7b46-4513-bf51-684f14e044c7 none            swap    sw              0       0  
```

  _**blkid:**_
```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: LABEL="ESP" UUID="ECA3-78BB" TYPE="vfat" PARTLABEL="EFI  system partition" PARTUUID="fec0f7fa-c016-494d-8e43-da3cdc875b61"  
  /dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="45651152-71e0-4c2d-90c1-38a74417b5df"  
  /dev/sda3: LABEL="OS" UUID="90185C2C185C1396" TYPE="ntfs"  PARTLABEL="Basic data partition"  PARTUUID="0dc7ac77-f3cf-4c2f-93de-0d2b658ef499"  
  /dev/sda4: LABEL="WINRETOOLS" UUID="F25A91785A913A75" TYPE="ntfs" PARTUUID="b00bfd17-a58c-4299-bba0-1039f5f3338b"  
  /dev/sda5: LABEL="Image" UUID="2C3292273291F5D4" TYPE="ntfs" PARTUUID="73cfa92d-6731-45ef-b00c-9e23f19750f6"  
  /dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="792b4f70-2139-4b3b-b5f2-c6611da9e7bb"  
  /dev/sdb2: LABEL="DATA" UUID="2AD6699DD66969D1" TYPE="ntfs"  PARTLABEL="Basic data partition"  PARTUUID="96d92b38-00cb-4fc8-86bf-eb597e639932"  
  /dev/sdb3: UUID="3A1C-1C7D" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="7e96a801-5d7a-4ed3-9ca2-b0c6ba9ad88a"  
  /dev/sdb4: UUID="51ec0aae-6365-41fa-898f-208a63b99775" TYPE="ext4" PARTUUID="dbafaf11-27dd-49b6-a5e0-dca42c5f5f49"  
  /dev/sdb5: UUID="8ee4e011-7b46-4513-bf51-684f14e044c7" TYPE="swap" PARTUUID="25731f61-23da-4787-941f-0816c3359507"  
  /dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
```

there seems to be a problem with the re-mounting?

```

[INDENT] grep -hiE "mount|dhcp" <(dmesg) <(journalctl -b0) 

 [/INDENT]  [    0.202339] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)  
  [    0.202366] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)  
  Hint: You are currently not seeing messages from other users and the system.       Users in groups 'adm', 'systemd-journal' can see all messages.       Pass -q to turn off this notice.  
  [    3.603684] EXT4-fs (sdb4): mounted filesystem with ordered data mode. Opts: (null)  
  [    9.834815] systemd[1]: Mounting Kernel Debug File System...  
  [   10.332194] EXT4-fs (sdb4): re-mounted. Opts: errors=remount-ro  
  [   34.526315] audit: type=1400 audit(1558906707.476:6):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper"  pid=994 comm="apparmor_parser"  
  May 26 14:39:42 sunshine systemd[1824]: run-user-118.mount: Succeeded.
```

---

### Post by oldfred on 2019-05-26
See if any of the fixes in these help.
They realize snaps are slower loading and have made some improvements. Are you using snaps?

[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

I am booting from a SSD which is the best thing you can do to improve boot time. Before the changes in above posts I was in mid 30 sec range.

Now:
fred@Bionic-Z170N:~$  systemd-analyze
Startup finished in 3.052s (kernel) + 9.289s (userspace) = 12.341s
graphical.target reached after 6.281s in userspace

---

### Post by smaxyx on 2019-05-26
seems like snap is being used a bit

```

&#10140;  ~ snap list
Name                  Version                     Rev   Tracking  Publisher   Notes
core                  16-2.39                     6964  stable    canonical&#10003;  core
core18                20190508                    970   stable    canonical&#10003;  base
gnome-3-26-1604       3.26.0.20190228             82    stable/&#8230;  canonical&#10003;  -
gnome-3-28-1804       3.28.0-10-gaa70833.aa70833  40    stable    canonical&#10003;  -
gnome-calculator      3.32.1                      406   stable/&#8230;  canonical&#10003;  -
gnome-characters      v3.32.1+git1.2050bba        258   stable/&#8230;  canonical&#10003;  -
gnome-logs            3.32.0-4-ge8f3f37ca8        61    stable/&#8230;  canonical&#10003;  -
gnome-system-monitor  3.32.1-1-g531f14fd7b        81    stable/&#8230;  canonical&#10003;  -
gtk-common-themes     0.1-16-g2287c87             1198  stable/&#8230;  canonical&#10003;  -
spotify               1.1.5.153.gf614956d-16      35    stable    spotify&#10003;    - 
```

I am usinig UEFI
```

  ~ dmesg | grep "EFI v"
[    0.000000] efi: EFI v2.40 by American Megatrends


```

btw I am running Linux on a Dell Inspiron 15 7559. I didn't see any issues in dmesg regarding to snap

---

### Post by oldfred on 2019-05-27
Some other Dell in 7000 series, but almost all models of Dell have similar UEFI and then issues. More differences if AMD or Intel based.

DELL Inspiron 15 7577 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
Post installation issues Ubuntu 18.04-Dell inspiron 7559
[https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559](https://askubuntu.com/questions/1072382/post-installation-issues-ubuntu-18-04-dell-inspiron-7559)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)

---

### Post by smaxyx on 2019-05-27
So, I got rid of snap and checked the UEFI links - even though my system is very stable (but boots slow). 

```
&#10140;  ~ systemd-analyze critical-chain                      
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @55.869s
&#9492;&#9472;multi-user.target @55.869s
  &#9492;&#9472;mpd.service @34.483s +21.384s
    &#9492;&#9472;network.target @34.264s
      &#9492;&#9472;NetworkManager.service @23.573s +10.533s
        &#9492;&#9472;dbus.service @23.570s
          &#9492;&#9472;basic.target @22.890s
            &#9492;&#9472;sockets.target @22.890s
              &#9492;&#9472;cups.socket @22.890s
                &#9492;&#9472;sysinit.target @22.588s
                  &#9492;&#9472;systemd-timesyncd.service @22.177s +410ms
                    &#9492;&#9472;systemd-tmpfiles-setup.service @20.413s +1.612s
                      &#9492;&#9472;systemd-journal-flush.service @4.389s +16.022s
                        &#9492;&#9472;systemd-remount-fs.service @4.162s +184ms
                          &#9492;&#9472;systemd-journald.socket @4.066s
                            &#9492;&#9472;system.slice @4.021s
                              &#9492;&#9472;-.slice @4.021s
&#10140;  ~ 
```

I followed the instruction regarding the journal flush here: [https://askubuntu.com/questions/1094389/what-is-the-use-of-systemd-journal-flush-service](https://askubuntu.com/questions/1094389/what-is-the-use-of-systemd-journal-flush-service)
Didn't help my boot time though.

---

### Post by oldfred on 2019-05-27
Have you updated UEFI and if SSD updated firmware?

Are all entries in fstab correct?

---

### Post by mdurham on 2019-05-28
Hi, I had a similar problem because I had removed the swap partition. Use the system monitor to check that you have a valid swap.
Cheers, Mike

---

