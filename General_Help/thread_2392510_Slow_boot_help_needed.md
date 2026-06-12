---
title: "Slow boot help needed"
date: 2018-05-22
forum: General Help
---

### Post by priyankkjain on 2018-05-22
Hi, I am new to Ubuntu. I have installed Ubuntu 4 times but every time i get slow boot while startup i learned some commands which shows the problem but i don't know what to do next. Please help me. this are all details that can help.

I have only Ubuntu so during installation i have selected something else and manually partitioned my 1TB hard disk. I have partitioned disk by following [https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)  guide.

My partition are as follow --> 

[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD]Name[/TD]
[TD]Size[/TD]
[TD]Type of Partition[/TD]
[TD]Location of Partition[/TD]
[TD]Use As[/TD]
[TD]Mount Point[/TD]
[/TR]
[TR]
[TD]EFI 
/dev/sda1[/TD]
[TD]536 MB[/TD]
[TD]Primary[/TD]
[TD]Beginning of space[/TD]
[TD]EFI system[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Swap Space
/dev/sda2[/TD]
[TD]20 GB[/TD]
[TD]Primary[/TD]
[TD]Beginning of space[/TD]
[TD]Swap Area[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Partition 3
/dev/sda3[/TD]
[TD]50 GB[/TD]
[TD]Logical[/TD]
[TD]Beginning of space[/TD]
[TD]Ext4[/TD]
[TD]/ (root)[/TD]
[/TR]
[TR]
[TD]Partition 4
/dev/sda4[/TD]
[TD]2 GB[/TD]
[TD]Logical[/TD]
[TD]Beginning of space[/TD]
[TD]Ext4[/TD]
[TD]/boot[/TD]
[/TR]
[TR]
[TD]Partition 5
/dev/sda5[/TD]
[TD]12 GB[/TD]
[TD]Logical[/TD]
[TD]Beginning of space[/TD]
[TD]Ext4[/TD]
[TD]/var[/TD]
[/TR]
[TR]
[TD]Partition 6
/dev/sda6[/TD]
[TD]12 GB[/TD]
[TD]Logical[/TD]
[TD]Beginning of space[/TD]
[TD]Ext4[/TD]
[TD]/tmp[/TD]
[/TR]
[TR]
[TD]Partition 7
/dev/sda7[/TD]
[TD]900 GB[/TD]
[TD]Logical[/TD]
[TD]Beginning of space[/TD]
[TD]Ext4[/TD]
[TD]/home[/TD]
[/TR]
[TR]
[TD]Free Space
/dev/sda[/TD]
[TD]4 GB[/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

After running "[SIZE=2]**systemd-analyze**[/SIZE]" --> 

```
Startup finished in 4.854s (firmware) + 4.174s (loader) + 4.555s (kernel) + 48.579s (userspace) = 1min 2.163s
graphical.target reached after 48.464s in userspace
```

and after running "[SIZE=2]**systemd-analyze blame**[/SIZE]" --> 

```
27.105s plymouth-start.service
         13.431s plymouth-read-write.service
         11.924s plymouth-quit-wait.service
         10.468s NetworkManager-wait-online.service
          7.046s dev-sda3.device
          6.744s systemd-journal-flush.service
          5.974s systemd-rfkill.service
          5.784s systemd-backlight@backlight:intel_backlight.service
          5.554s home.mount
          5.342s snap-gnome\x2dcalculator-154.mount
          5.285s snap-gnome\x2dlogs-25.mount
          4.965s ModemManager.service
          4.887s snap-gnome\x2dsystem\x2dmonitor-39.mount
          4.732s snapd.service
          4.691s snap-gnome\x2dsystem\x2dmonitor-36.mount
          4.659s snap-canonical\x2dlivepatch-39.mount
          4.439s snap-gnome\x2dcharacters-69.mount
          4.380s snap-core-4486.mount
          4.360s udisks2.service
          4.350s snap-gnome\x2dlogs-31.mount
          4.290s snap-gnome\x2dcharacters-86.mount
          4.250s snap-gnome\x2d3\x2d26\x2d1604-59.mount
          4.217s snap-gnome\x2d3\x2d26\x2d1604-64.mount
          4.199s snap-core-4571.mount
          4.159s NetworkManager.service
          4.143s snap-gnome\x2dcalculator-167.mount
          3.950s accounts-daemon.service
          3.583s apparmor.service
          3.431s networkd-dispatcher.service
          2.415s systemd-fsck@dev-disk-by\x2duuid-92ce21be\x2d0ee9\x2d475a\x2dad
          2.091s grub-common.service
          2.061s systemd-fsck@dev-disk-by\x2duuid-4e777e4a\x2dc890\x2d4c09\x2dbe
          2.044s dev-loop10.device
          1.996s dev-loop8.device
          1.958s dev-loop9.device
          1.911s wpa_supplicant.service
          1.902s dev-loop11.device
          1.650s thermald.service
          1.615s systemd-fsck@dev-disk-by\x2duuid-45AE\x2dAE7F.service
          1.603s systemd-fsck@dev-disk-by\x2duuid-2f5dcd51\x2d81da\x2d42d6\x2d8f
          1.597s dev-loop3.device
          1.575s dev-loop0.device
          1.540s polkit.service
          1.491s dev-loop6.device
          1.406s dev-loop4.device
          1.360s systemd-fsck@dev-disk-by\x2duuid-918cbf63\x2d7418\x2d4780\x2d9f
          1.359s speech-dispatcher.service
          1.296s bluetooth.service
          1.280s lvm2-monitor.service
          1.252s dev-loop7.device
          1.216s dev-loop5.device
          1.191s rsyslog.service
          1.108s fwupd.service
          1.067s keyboard-setup.service
          1.021s dev-loop2.device
           904ms dev-loop12.device
           831ms dev-loop1.device
           823ms avahi-daemon.service
           818ms systemd-logind.service
           813ms pppd-dns.service
           808ms gpu-manager.service
           741ms tmp.mount
           697ms alsa-restore.service
           670ms systemd-sysctl.service
           659ms systemd-modules-load.service
           654ms systemd-udevd.service
           613ms apport.service
           606ms systemd-remount-fs.service
           586ms systemd-tmpfiles-setup.service
           572ms packagekit.service
           537ms dev-mqueue.mount
           536ms dev-hugepages.mount
           534ms sys-kernel-debug.mount
           522ms dns-clean.service
           483ms systemd-tmpfiles-setup-dev.service
           390ms var.mount
           387ms systemd-timesyncd.service
           367ms colord.service
           344ms systemd-resolved.service
           267ms kmod-static-nodes.service
           266ms gdm.service
           260ms user@120.service
           220ms boot.mount
           217ms upower.service
           217ms networking.service
           216ms boot-efi.mount
           213ms console-setup.service
           201ms snapd.seeded.service
           177ms systemd-update-utmp.service
           172ms systemd-random-seed.service
           157ms bolt.service
           142ms kerneloops.service
           122ms dev-disk-by\x2duuid-a2d9decd\x2dde65\x2d4d63\x2d9e29\x2d58dcc03
           117ms systemd-user-sessions.service
           115ms systemd-udev-trigger.service
           108ms setvtrgb.service
            84ms blk-availability.service
            79ms systemd-journald.service
            75ms ufw.service
            56ms user@1000.service
            28ms rtkit-daemon.service
            15ms systemd-update-utmp-runlevel.service
             8ms ureadahead-stop.service
             2ms sys-fs-fuse-connections.mount
             2ms sys-kernel-config.mount
           808us snapd.socket
lines 84-106/106 (END)
[1]+  Stopped                 systemd-analyze blame

```

and after running "[SIZE=2]**systemd-analyze critical-chain**[/SIZE]"

```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @48.464s
&#9492;&#9472;multi-user.target @48.464s
  &#9492;&#9472;kerneloops.service @46.937s +142ms
    &#9492;&#9472;network-online.target @46.886s
      &#9492;&#9472;NetworkManager-wait-online.service @36.418s +10.468s
        &#9492;&#9472;NetworkManager.service @32.257s +4.159s
          &#9492;&#9472;dbus.service @31.482s
            &#9492;&#9472;basic.target @31.472s
              &#9492;&#9472;sockets.target @31.472s
                &#9492;&#9472;snapd.socket @31.470s +808us
                  &#9492;&#9472;sysinit.target @31.429s
                    &#9492;&#9472;cryptsetup.target @31.153s
                      &#9492;&#9472;systemd-ask-password-wall.path @2.637s
                        &#9492;&#9472;-.mount @2.635s
                          &#9492;&#9472;system.slice @2.637s
                            &#9492;&#9472;-.slice @2.635s


```

after running "[SIZE=2]**sudo blkid**[/SIZE]"

```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="45AE-AE7F" TYPE="vfat" PARTUUID="8290266c-b7b9-485f-8ff7-523d5f2a5ec5"
/dev/sda2: UUID="a2d9decd-de65-4d63-9e29-58dcc03a58bc" TYPE="swap" PARTUUID="69911122-bf4a-4b73-ac7e-e626314c7974"
/dev/sda3: UUID="3b3668ad-8088-4572-b297-679b81652f5c" TYPE="ext4" PARTUUID="8ebc233b-c431-449a-8800-d17f0ea2c2dc"
/dev/sda4: UUID="918cbf63-7418-4780-9f04-06f47fb69779" TYPE="ext4" PARTUUID="ae11acfd-17bc-47bd-be3a-415bfab35899"
/dev/sda5: UUID="4e777e4a-c890-4c09-be1e-39388461b330" TYPE="ext4" PARTUUID="abefd938-0912-4724-ae71-3ee214f7b77b"
/dev/sda6: UUID="2f5dcd51-81da-42d6-8fa1-6ea6bd0df0bf" TYPE="ext4" PARTUUID="edd8c8cc-d226-46b1-9b3f-55b467182ea0"
/dev/sda7: UUID="92ce21be-0ee9-475a-ad7b-ccd6d06934db" TYPE="ext4" PARTUUID="5981f509-60ae-4ba6-b102-2a2c11a6d6c9"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
```

After running "[SIZE=2]**lsblk**[/SIZE]" --> 
```

  NAME   MAJ:MIN  RM   SIZE         RO       TYPE     MOUNTPOINT
loop0    7:0                0      12.2M        1          loop       /snap/gnome-characters/69
loop1    7:1                0      86.6M        1          loop       /snap/core/4650
loop2    7:2                0      21M           1          loop       /snap/gnome-logs/25
loop3    7:3                0      3.3M          1          loop      /snap/gnome-system-monitor/36
loop4    7:4                0    1.6M             1          loop      /snap/gnome-calculator/154
loop5    7:5                0     140M          1          loop         /snap/gnome-3-26-1604/59
loop6    7:6                0     86.6M        1           loop         /snap/core/4486
loop7    7:7                0   2.3M            1           loop          /snap/gnome-calculator/167
loop8    7:8                0    139.5M      1           loop         /snap/gnome-3-26-1604/64
loop9    7:9                0      3.7M         1           loop        /snap/gnome-system-monitor/39
loop10   7:10             0     13M           1          loop           /snap/gnome-characters/86
loop11   7:11             0    4.9M           1          loop             /snap/canonical-livepatch/39
loop12   7:12            0     21.6M         1           loop           /snap/gnome-logs/31
loop13   7:13            0     86.6M           1           loop            /snap/core/4571
sda           8:0              0    931.5G       0              disk 
&#9500;&#9472;sda1   8:1               0   571M           0             part           /boot/efi
&#9500;&#9472;sda2   8:2              0    18.6G           0            part             [SWAP]
&#9500;&#9472;sda3   8:3               0    46.6G         0            part                  /
&#9500;&#9472;sda4   8:4               0     1.9G          0            part              /boot
&#9500;&#9472;sda5   8:5              0    11.2G          0             part                 /var
&#9500;&#9472;sda6   8:6              0   11.2G           0            part               /tmp
&#9492;&#9472;sda7   8:7              0    838.2G        0            part            /home
sr0     11:0                   1  1024M         0             rom  



```



my disk image is attached with this thread. also i am runnig on 8 GB RAM and i have only Ubuntu running on laptop no other OS. Hope all of this information helps please help me to overcome this problem.

---

### Post by dino99 on 2018-05-22
'journalctl -b' can teach you about some issues: bright line = warning, red line = error

if 'ureadahead' is installed, then purge it (it cause more trouble than benefits) (sudo apt-get purge ureadahead)

---

### Post by TheFu on 2018-05-22
I appreciate all the effort formatting the post above, but just using code tags and showing the exact command/output is sufficient.  No fancy formatting.

For the disk partition data, the output from df -hT would be preferred (and much easier to post).  We ***like*** text.

On spinning HDDs, it is possible for improper layout alignment to reduce disk performance significantly. It matters on SSDs too, but not nearly as much.
[https://www.ibm.com/developerworks/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/library/l-linux-on-4kb-sector-disks/)
[https://ubuntuforums.org/showthread.php?t=1889531](https://ubuntuforums.org/showthread.php?t=1889531)

BTW, your partition layout seems overly complex. Some good ideas implemented, but some seems to be based on old information that doesn't apply.  
I think the swap is 4-5x too large too.  For a desktop, 4.1G for swap is the best answer for low memory systems AND systems with 32G of RAM (and everything in between), assuming you don't hibernate (and really nobody should hibernate if they care at all about security).  The goal for swap is to provide feedback as system RAM gets low.  The system should slow down some, enough that the users "feel it".   Systems that have more swap are useful for shared resources like VM hosts if you don't like your customers much.  IMHO.

---

