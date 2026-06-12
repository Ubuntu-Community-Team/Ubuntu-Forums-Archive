---
title: "Slow Boot UP Dell Inspirion 3422"
date: 2023-12-13
forum: General Help
---

### Post by gaynorblueyes on 2023-12-13
I have Dell  Inspiron 3442 Certified Ubuntu Laptop  the boot times are slow 
 Startup finished in 2.241s (firmware) + 3.843s (loader) + 4.151s (kernel) + 59.149s (userspace) = 1min 9.385s 


raphical.target @59.137s
&#9492;&#9472;multi-user.target @59.136s
  &#9492;&#9472;snapd.seeded.service @44.809s +9.230s
    &#9492;&#9472;snapd.service @26.503s +18.270s
      &#9492;&#9472;basic.target @24.349s
        &#9492;&#9472;sockets.target @24.349s
          &#9492;&#9472;snapd.socket @24.320s +29ms
            &#9492;&#9472;sysinit.target @24.091s
              &#9492;&#9472;snapd.apparmor.service @21.788s +2.302s
                &#9492;&#9472;apparmor.service @19.584s +2.169s
                  &#9492;&#9472;local-fs.target @19.553s
                    &#9492;&#9472;run-user-1000-gvfs.mount @59.057s
                      &#9492;&#9472;run-user-1000.mount @40.047s
                        &#9492;&#9472;local-fs-pre.target @9.023s
                          &#9492;&#9472;systemd-tmpfiles-setup-dev.service @6.172s +2.850s
                            &#9492;&#9472;systemd-sysusers.service @5.248s +901ms
                              &#9492;&#9472;systemd-remount-fs.service @5.060s +151ms
                                &#9492;&#9472;systemd-fsck-root.service @4.966s +89ms
                                  &#9492;&#9472;systemd-journald.socket @4.908s
                                    &#9492;&#9472;-.mount @4.878s
Is there anything I can do to speed things up

Thanks

---

### Post by oldfred on 2023-12-13
My 2017 build with NVMe drive now as boot drive:
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 47min 29.231s (firmware) + 4.579s (loader) + 4.214s (kernel) + 5.601s (userspace) = 47min 43.626s  
graphical.target reached after 5.580s in userspace
[/FONT]
```

Not sure why now it says firmware so long as I ran above command immediately after rebooting or within 10 sec. And entire reboot was quick.

If not using SSD that speeds things up the most.
I use Kubuntu which is a bit more lightweight than Ubuntu with Gnome.
I do not allow snaps, which it looks like you have. They take longer to load.
I install only .debs, main one I have to change is Firefox.

I do change some settings.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

---

### Post by MAFoElffen on 2023-12-13
> **gaynorblueyes said:**
> 
```

Graphical.target @59.137s
...
&#9492;&#9472;local-fs.target @19.553s
                    &#9492;&#9472;run-user-1000-gvfs.mount @59.057s
                      &#9492;&#9472;run-user-1000.mount @40.047s
                        &#9492;&#9472;local-fs-pre.target @9.023s
                          &#9492;&#9472;systemd-tmpfiles-setup-dev.service @6.172s +2.850s
                            &#9492;&#9472;systemd-sysusers.service @5.248s +901ms
                              &#9492;&#9472;systemd-remount-fs.service @5.060s +151ms
                                &#9492;&#9472;systemd-fsck-root.service @4.966s +89ms

```

Besides Snaps loading... Most of these are mounts

Please post the output of this within CODE Tags...
```

mount | grep -v 'snap\|sys\|run\|proc\|tmpfs\|mqueue\|binderfs\|hugetlbfs\|devpts'

```

---

### Post by gaynorblueyes on 2023-12-14
mount | grep -v 'snap\|sys\|run\|proc\|tmpfs\|mqueue\|binderfs\|hugetlbfs\|devpts'
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

---

