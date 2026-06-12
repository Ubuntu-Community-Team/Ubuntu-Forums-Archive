---
title: "Total boot time over 45seconds"
date: 2018-07-23
forum: General Help
---

### Post by vineeth.k on 2018-07-23
I am using Ubuntu 18.04. The boot time is more than 45seconds. First, after I choose ubuntu on grub, it stays blank and pink for a lot of time. Then the ubuntu splash screen comes in a wrong and huge resolution. Then suddenly it shows all those green [OK] messages for a second and gets me to login screen. Once i fill the password and hit enter, screen goes black for some seconds again before showing desktop. 
                                   I used to have nouveau but then switched to nvidia drivers to see if that would help solve this problem. I also tried changing the "quiet splash" command to nothing, but I couldn't find what is the problem. With no "quiet splash", instead of pink, the screen goes black. That is the only change.
                                   I have asked this at ask ubuntu also,but got no answers. It is really annoying to wait around 1 minute to get my computer on. I really need help.
 

Thanks

---

### Post by oldfred on 2018-07-23
Your 45 sec may not be excessive. It depends on hardware. My 2006 system took  5 Minutes to boot XP, after chkdsk it was 3 min. So Ubuntu booting in 45 sec was a real plus. But that was old system with slow HDD.
I think my flash drives with full install still table over 30 sec to boot.

What brand/model system? Some need boot parameters.
Is nVidia driver correct version for your nVidia card?
What card/chip?
Post these:
       systemd-analyze 
    cat /etc/fstab
lsblk -f

See also this:
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)

Is this an upgrade? What flavor of Ubuntu?

---

### Post by monkeybrain20122 on 2018-07-23
It could be your system being old as old fred said but since you find it surprising that it takes so long to boot it may be this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1779961") in kernel 4.15.0-24. You can check by booting into kernel 4.15.0-23 (press esc or shift when boot to see the grub screen, choose advanced options and choose the older kernel) and see if it still takes that long.

If confirm it is the bad kernel, see post 14 in[ this thread]("https://ubuntuforums.org/showthread.php?t=2395459&page=2") for the simple workaround.

---

### Post by vineeth.k on 2018-07-29
I have a comparatively new system. It has 8GB ram, AMD® Fx(tm)-6300 six-core processor and 1TB HDD. I think I am using the nouveau driver and not NVDIA driver. I tried NVDIA drivers,  they causes a mess of other problems with boot. Should  I actually switch to NVDIA drivers?

systemd-analyze :
Startup finished in 4.747s (kernel) + 1min 50.534s (userspace) = 1min 55.281s
graphical.target reached after 32.724s in userspace


cat /etc/fstab :
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=f43b5401-f675-4814-ace9-acb9eb75d5b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=26fbf865-b5f0-4154-9e90-3a355a24ba0a none            swap    sw              0       0


lsblk -f :
NAME   FSTYPE  LABEL           UUID                                 MOUNTPOINT
loop0  squashf                                                      /snap/canoni
loop1  squashf                                                      /snap/irssi/
loop2  squashf                                                      /snap/core/4
loop3  squashf                                                      /snap/core/4
loop4  squashf                                                      /snap/vlc/15
loop5  squashf                                                      /snap/vlc/36
loop6  squashf                                                      /snap/core/4
loop7  squashf                                                      /snap/spotif
loop8  squashf                                                      /snap/vlc/19
sda                                                                 
&#9500;&#9472;sda1 ntfs    System Reserved 8E4AEFC04AEFA2E7                     
&#9500;&#9472;sda2 ntfs                    AC1E0E311E0DF55C                     
&#9500;&#9472;sda3 ntfs                    82AE6D70AE6D5E23                     
&#9500;&#9472;sda4                                                              
&#9500;&#9472;sda5 ntfs    Films           1A8E9FDA8E9FACAF                     
&#9500;&#9472;sda6 swap                    26fbf865-b5f0-4154-9e90-3a355a24ba0a [SWAP]
&#9492;&#9472;sda7 ext4                    f43b5401-f675-4814-ace9-acb9eb75d5b5 /
sr0

---

### Post by vineeth.k on 2018-07-29
It is an upgrade of ubuntu and it is currently running 18.04. Also, if the boot time is ok, is there a way to get rid of this annoying black/pink screens and just load the splash screen?

---

### Post by vineeth.k on 2018-07-29
Thought I would post this also, if it helps
systemd-analyze blame :
         41.455s apt-daily-upgrade.service
         37.583s apt-daily.service
         14.961s systemd-journal-flush.service
         13.549s dev-sda7.device
         12.274s keyboard-setup.service
          9.454s systemd-udevd.service
          8.220s systemd-sysctl.service
          7.759s plymouth-quit-wait.service
          6.528s NetworkManager-wait-online.service
          4.451s udisks2.service
          4.230s accounts-daemon.service
          3.978s ModemManager.service
          3.873s grub-common.service
          3.845s plymouth-start.service
          3.473s apparmor.service
          3.132s networkd-dispatcher.service
          3.095s avahi-daemon.service
          3.092s thermald.service
          3.084s apport.service
          3.082s gpu-manager.service
          3.082s alsa-restore.service
          3.079s speech-dispatcher.service
          3.076s switcheroo-control.service
          3.075s pppd-dns.service
          3.074s systemd-logind.service
          3.071s lm-sensors.service
          3.070s rsyslog.service
          2.945s fwupd.service
          2.807s snapd.service
          2.693s NetworkManager.service
          1.517s systemd-random-seed.service
          1.062s dev-loop8.device
           958ms systemd-modules-load.service
           800ms apache2.service
           677ms systemd-tmpfiles-setup-dev.service
           663ms dev-disk-by\x2duuid-26fbf865\x2db5f0\x2d4154\x2d9e90\x2d3a355a24ba0a.swap
           598ms sys-kernel-debug.mount

---

### Post by oldfred on 2018-07-29
What brand motherboard.
That boot time is a bit long, but some motherboards need additional boot parameters.

If Gigabyte it may need this:
        GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by Yellow Pasque on 2018-07-29
[https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297](https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297)

---

### Post by goatboy73 on 2018-07-29
I had a [similar problem]("https://ubuntuforums.org/showthread.php?t=2396985&p=13787989#post13787989") which I resolved by fixing the system's expectations with regards to suspend/resume/hibernate.

---

