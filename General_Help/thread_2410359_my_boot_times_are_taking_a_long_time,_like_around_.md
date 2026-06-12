---
title: "my boot times are taking a long time, like around 2 to 3 minuts"
date: 2019-01-14
forum: General Help
---

### Post by 1337-m3m3r on 2019-01-14
here what i get when i do dmesg
[https://paste.ubuntu.com/p/mDgSBKp95h/](https://paste.ubuntu.com/p/mDgSBKp95h/)

---

### Post by TheFu on 2019-01-14
systemd-analyze blame?

[https://www.tecmint.com/systemd-analyze-monitor-linux-bootup-performance/](https://www.tecmint.com/systemd-analyze-monitor-linux-bootup-performance/) has a guide with more details.

---

### Post by 1337-m3m3r on 2019-01-14
i did that and the longest time was 6 seconds

---

### Post by TheFu on 2019-01-14
If you have 500 things, each taking 5.5sec, that isn't good.

I recently built a new system and startup is/was very slow.
```
graphical.target @1min 8.020s
&#9492;&#9472;multi-user.target @1min 8.020s
  &#9492;&#9472;smbd.service @1min 7.748s +271ms
    &#9492;&#9472;nmbd.service @49.653s +18.093s
      &#9492;&#9472;network-online.target @49.652s
        &#9492;&#9472;network.target @47.711s
          &#9492;&#9472;networking.service @40.214s +7.496s
            &#9492;&#9472;apparmor.service @39.118s +1.087s
              &#9492;&#9472;local-fs.target @39.076s
                &#9492;&#9472;run-cgmanager-fs.mount @43.430s
                  &#9492;&#9472;local-fs-pre.target @35.377s
                    &#9492;&#9472;lvm2-monitor.service @2.082s +33.294s
                      &#9492;&#9472;lvm2-lvmetad.service @2.418s
                        &#9492;&#9472;lvm2-lvmetad.socket @2.081s
                          &#9492;&#9472;-.mount @2.077s
                            &#9492;&#9472;system.slice @2.079s
                              &#9492;&#9472;-.slice @2.077s
```
I removed network-manager and lxd.  I don't use NM and lxd was left over from the system I pulled the install out of.  I haven't rebooted yet.  One of my SATA devices is complaining a bunch.  I already swapped the device out (dvd --> bluray), but it is still complaining. Hope the issue is a bad SATA cable. That's the next thing I try when the system isn't busy.

I use LVM, so disabling the LVM2 stuff isn't an option for me. LVM is too important to give up for a 2 min startup to me, especially since the machine basically runs 24/7/365 and only gets rebooted when a new libc or kernel requires it.

---

### Post by MartyBuntu on 2019-01-14
Have you moved around or altered disks or partitions lately?

---

### Post by CatKiller on 2019-01-14
Do you use Bluetooth? Your dmesg shows it waiting for some 90 seconds between doing the sound and the Bluetooth being initialised. If you don't use it, you might simply disable it.

---

### Post by 1337-m3m3r on 2019-01-14
no there is only one thing that took 6 seconds

---

### Post by 1337-m3m3r on 2019-01-14
when i do systemd-analyze blame his is what i get          6.104s NetworkManager-wait-online.service
6.104s NetworkManager-wait-online.service
          1.406s plymouth-start.service
           922ms motd-news.service
           886ms fwupd.service
           853ms dev-nvme0n1p2.device
           598ms snapd.service
           343ms vboxdrv.service
           264ms systemd-logind.service
           250ms NetworkManager.service
           211ms [email]systemd-fsck@dev-disk-by\x2duuid-7619\x2d8E97.servic[/email]e
           182ms snap-vlc-768.mount
           179ms snap-gnome\x2dsystem\x2dmonitor-51.mount
           171ms dev-loop0.device
           168ms systemd-resolved.service
           167ms systemd-timesyncd.service
           158ms snap-gtk\x2dcommon\x2dthemes-818.mount
           153ms dev-loop1.device
           150ms snap-gnome\x2dlogs-37.mount
           149ms snap-gnome\x2dcharacters-139.mount
           142ms dev-loop2.device
           139ms dev-loop5.device
           129ms phpsessionclean.service
           127ms dev-loop10.device

---

