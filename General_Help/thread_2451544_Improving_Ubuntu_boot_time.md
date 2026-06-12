---
title: "Improving Ubuntu boot time"
date: 2020-10-06
forum: General Help
---

### Post by liubomirwm on 2020-10-06
systemd-analyze:
Startup finished in 8.126s (firmware) + 5.546s (loader) + 16.335s (kernel) + 2min 5.698s (userspace) = 2min 35.706s 
graphical.target reached after 2min 5.648s in userspace

systemd-analyze critical-chain:
graphical.target @2min 5.648s
&#9492;&#9472;multi-user.target @2min 5.647s
  &#9492;&#9472;networkd-dispatcher.service @38.643s +47.965s
    &#9492;&#9472;basic.target @38.551s
      &#9492;&#9472;sockets.target @38.551s
        &#9492;&#9472;libvirtd-ro.socket @38.551s
          &#9492;&#9472;libvirtd.socket @38.548s +2ms
            &#9492;&#9472;sysinit.target @38.440s
              &#9492;&#9472;systemd-timesyncd.service @38.234s +205ms
                &#9492;&#9472;systemd-tmpfiles-setup.service @34.053s +4.151s
                  &#9492;&#9472;local-fs.target @34.046s
                    &#9492;&#9472;run-snapd-ns-canonical\x2dlivepatch.mnt.mount @1min 2.269s
                      &#9492;&#9472;run-snapd-ns.mount @59.190s
                        &#9492;&#9472;swap.target @30.804s
                          &#9492;&#9472;dev-zram0.swap @43.923s
                            &#9492;&#9472;dev-zram0.device @43.918s +5ms


I have disabled NetworkManager-wait-online.service which was taking maybe about 26-30 seconds of time. Is any of these services preventing the Gnome Desktop Manager appearance? Why my boot is so slow? Please help me.

---

### Post by liubomirwm on 2020-10-06
[ATTACH=CONFIG]287108[/ATTACH]

---

### Post by liubomirwm on 2020-10-06
Since my last post i've ran systemd-analyze critical-chain gdm3.service and that showed that gdm3.service depends on systemd-user-sessions.service which depends on network.target, which took between 14 and 20 seconds to be reached because of NetworkManager. I've overriden systemd-user-sessions.service and removed network.target as a dependency of systemd-user-sessions.service, but gdm still starts slooow.
Before:
[ATTACH=CONFIG]287109[/ATTACH]

After:
[ATTACH=CONFIG]287110[/ATTACH]

---

### Post by liubomirwm on 2020-10-06
Also, every time i boot my Ubuntu is says Press Ctrl + C to cancel all filesystem checks, maybe this is an/the issue??

---

### Post by ActionParsnip on 2020-10-06
> **liubomirwm said:**
> Also, every time i boot my Ubuntu is says Press Ctrl + C to cancel all filesystem checks, maybe this is an/the issue??

Worth a try. Boot to the Ubuntu install media and to the live USB / CD desktop. You can then run an fsck on your file system while it is unmounted.
[https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)

---

### Post by oldfred on 2020-10-06
Please do not post screen shots of terminal output.
But do use code tags to preserve formatting. 
Code tags are easy to add with Forum's Go Advanced editor and # icon.

That swap takes so long may indicate a bad UUID. Check fstab & UUIDs.
cat /etc/fstab
lsblk -f

Other threads with suggestions on slow boot issues.
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

[https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything) & 
[https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do](https://askubuntu.com/questions/1018576/what-does-networkmanager-wait-online-service-do) & 
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

These are the changes I have done.
turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

If UEFI firmware update not supported (yet)
sudo apt-get purge fwupd

Boot from SSD, my UEFI has setting for 3 sec delay (rather than fast boot) and grub at 3 sec, so I have time to press a key if needed:
```
[FONT=monospace][FONT=arial][COLOR=#000000]fred@z97-focal-kubuntu:~$ systemd-analyze
Startup finished in 10.173s (firmware) + 4.575s (loader) + 4.279s (kernel) + 4.743s (userspace) = 23.771s 
graphical.target reached after 4.170s in userspace[/COLOR][/FONT]
[/FONT]
```

---

