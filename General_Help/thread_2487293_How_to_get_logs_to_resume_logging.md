---
title: "How to get logs to resume logging"
date: 2023-05-29
forum: General Help
---

### Post by tc2020 on 2023-05-29
Hello,

My logs in "/var/log/" just stop logging and I would like to know how to get them to resume logging.

I have Raspberry RPi4 running Ubuntu Server 22.04 LTS 64-bit and 5.15.0-1029-raspi kernel. After each reboot, I can see file size for logs (e.g., auth.log and syslog) increases but then stops. When I open the journal (i.e., journalctl) and compare the entries to those in /var/log/syslog, they are practically the same. However, journal continues to log records whereas syslog just stops. 

In this system, I use log2ram and syslog-ng. I get the same behavior when both packages are disabled/inactive (checked via systemctl status). I also have logrotate to rotate many of these logs daily. My logrotate configuration is in "/etc/logrotate.d/". It has "copytruncate" option (and all log files end up with 0 byte file size after rotation). 

Where do logs come from after reboot as I see about 0.5MB of syslog after reboot and then it stops?. It looks like something redirects logs to somewhere thereafter.

Any hint/help would be greatly appreciated. Thanks.

---

### Post by wyattwhiteeagle on 2023-05-30
> **tc2020 said:**
> Hello,

My logs in "/var/log/" just stop logging and I would like to know how to get them to resume logging.

I have Raspberry RPi4 running Ubuntu Server 22.04 LTS 64-bit and 5.15.0-1029-raspi kernel. After each reboot, I can see file size for logs (e.g., auth.log and syslog) increases but then stops. When I open the journal (i.e., journalctl) and compare the entries to those in /var/log/syslog, they are practically the same. However, journal continues to log records whereas syslog just stops. 

In this system, I use log2ram and syslog-ng. I get the same behavior when both packages are disabled/inactive (checked via systemctl status). I also have logrotate to rotate many of these logs daily. My logrotate configuration is in "/etc/logrotate.d/". It has "copytruncate" option (and all log files end up with 0 byte file size after rotation). 

Where do logs come from after reboot as I see about 0.5MB of syslog after reboot and then it stops?. It looks like something redirects logs to somewhere thereafter.

Any hint/help would be greatly appreciated. Thanks.

My help is very, very limited, but I can at least guide you in some form of direction.
Hopefully someone with more knowledge will chime in.

You mention that something seem's to be redirecting logs to somewhere else.
On that, my thoughts are..."sounds like log2ram and syslog-ng are doing their jobs".
Though I'm not certain of that...just going on what those package names seem to imply.

About /etc/logrotate.d
I have mine "tweaked" as well...like this...
```

daily
rotate 0
maxsize 10M

```
Everything else in the /etc/logrotate.d scripts...leave it the way it came.
It's just a measure to keep the system from filling up so much that it takes forever to do things after a couple months or so.

Please run the following command and post the results using "code" tags...
```
systemd-analyze blame
```
This will show if there's anything starting automatically at boot that might be causing the issue...or at least contributing it.

---

### Post by tc2020 on 2023-05-30
My system uses 32GB SD card and is for unattended applications. During development, its applications stopped working and it turned out that the SC card was filled with logs. It is very important for me to keep these logs under control. I keep everything in /etc/logrotate.d the same, just added my configuration for daily rotation for all logs that I find in /var/log directory. After rotation, I delete all archives leaving only the current logs, which stop logging.

This is what I have from running "systemd-analyze blame":

```
18.213s snap.lxd.activate.service
16.313s snapd.service
10.484s apt-daily-upgrade.service
 7.625s hciuart.service
 5.844s syslog-ng.service
 4.982s cv_web_auth_key_generator.service
 4.562s rpi-eeprom-update.service
 3.918s fwupd-refresh.service
 3.161s ModemManager.service
 3.022s cloud-config.service
 2.961s cloud-init-local.service
 2.845s udisks2.service
 2.810s cloud-final.service
 2.372s networkd-dispatcher.service
 2.108s redis-server.service
 1.936s cloud-init.service
 1.818s man-db.service
 1.782s ua-timer.service
 1.669s bluetooth.service
 1.446s cv_web_config_watcher.service
 1.271s polkit.service
 1.184s dev-mmcblk0p2.device
 1.058s apport.service
  926ms dev-loop2.device
  911ms systemd-logind.service
  904ms dev-loop3.device
  893ms wpa_supplicant.service
  759ms user@1000.service
  753ms dev-loop5.device
  712ms dev-loop4.device
  692ms snapd.apparmor.service
  684ms dev-loop1.device
  677ms dev-loop0.device
  659ms snapd.seeded.service
  645ms systemd-udev-trigger.service
  644ms logrotate.service
  590ms e2scrub_reap.service
  525ms log2ram.service
  494ms systemd-fsck@dev-disk-by\x2dlabel-system\x2dboot.service
  351ms systemd-resolved.service
  305ms multipathd.service
  305ms update-notifier-download.service
  276ms dpkg-db-backup.service
  247ms systemd-udevd.service
  218ms apparmor.service
  214ms ssh.service
  196ms keyboard-setup.service
  195ms cv_syslog_ng.service
  181ms systemd-timesyncd.service
  164ms modprobe@fuse.service
  163ms modprobe@pstore_blk.service
  163ms modprobe@pstore_zone.service
  162ms modprobe@ramoops.service
  152ms systemd-networkd.service
  150ms dev-hugepages.mount
  148ms dev-mqueue.mount
  144ms sys-kernel-debug.mount
  143ms systemd-tmpfiles-clean.service
  141ms sys-kernel-tracing.mount
  135ms kmod-static-nodes.service
  133ms lvm2-monitor.service
  132ms modprobe@efi_pstore.service
  132ms modprobe@chromeos_pstore.service
  132ms systemd-sysctl.service
  131ms modprobe@configfs.service
  131ms modprobe@drm.service
  116ms systemd-tmpfiles-setup-dev.service
  108ms systemd-sysusers.service
  105ms systemd-modules-load.service
   99ms systemd-remount-fs.service
   98ms systemd-tmpfiles-setup.service
   90ms bthelper@hci0.service
   89ms setvtrgb.service
   81ms systemd-random-seed.service
   80ms snap-core20-1883.mount
   72ms systemd-journald.service
   72ms nginx.service
   70ms snap-core20-1895.mount
   66ms plymouth-start.service
   63ms snap-lxd-23545.mount
   52ms snap-lxd-24326.mount
   51ms boot-firmware.mount
   49ms plymouth-quit-wait.service
   46ms systemd-user-sessions.service
   41ms systemd-journal-flush.service
   40ms snap-snapd-18940.mount
   37ms vsftpd.service
   37ms proc-sys-fs-binfmt_misc.mount
   37ms systemd-update-utmp-runlevel.service
   37ms plymouth-quit.service
   36ms systemd-rfkill.service
   35ms plymouth-read-write.service
   29ms sys-fs-fuse-connections.mount
   28ms sys-kernel-config.mount
   28ms console-setup.service
   28ms ufw.service
   28ms cv_snmptrapd.service
   27ms finalrd.service
   25ms snap-snapd-19127.mount
   25ms user-runtime-dir@1000.service
   22ms systemd-update-utmp.service
   22ms systemd-networkd-wait-online.service
   18ms snmpd.service
    7ms motd-news.service
    7ms snapd.socket
  432us blk-availability.service
```

No sure what to look for in the list above but that is from the system that has this logging stoppage issue.

Thanks for your time looking into this.

---

### Post by ian-weisser on 2023-05-30
Did you also look at the logs inside each container?

Did you set a maximum size for your journals? (separate from max-size for logs)

On a properly-working system, logs should not be growing to GB-per-day size. Have you fixed the underlying problems described by those logs?

---

### Post by wyattwhiteeagle on 2023-05-30
> **tc2020 said:**
> My system uses 32GB SD card and is for unattended applications. During development, its applications stopped working and it turned out that the SC card was filled with logs. It is very important for me to keep these logs under control. I keep everything in /etc/logrotate.d the same, just added my configuration for daily rotation for all logs that I find in /var/log directory. After rotation, I delete all archives leaving only the current logs, which stop logging.

This is what I have from running "systemd-analyze blame":

```
18.213s snap.lxd.activate.service
16.313s snapd.service
10.484s apt-daily-upgrade.service
 7.625s hciuart.service
 5.844s syslog-ng.service
 4.982s cv_web_auth_key_generator.service
 4.562s rpi-eeprom-update.service
 3.918s fwupd-refresh.service
 3.161s ModemManager.service
 3.022s cloud-config.service
 2.961s cloud-init-local.service
 2.845s udisks2.service
 2.810s cloud-final.service
 2.372s networkd-dispatcher.service
 2.108s redis-server.service
 1.936s cloud-init.service
 1.818s man-db.service
 1.782s ua-timer.service
 1.669s bluetooth.service
 1.446s cv_web_config_watcher.service
 1.271s polkit.service
 1.184s dev-mmcblk0p2.device
 1.058s apport.service
  926ms dev-loop2.device
  911ms systemd-logind.service
  904ms dev-loop3.device
  893ms wpa_supplicant.service
  759ms user@1000.service
  753ms dev-loop5.device
  712ms dev-loop4.device
  692ms snapd.apparmor.service
  684ms dev-loop1.device
  677ms dev-loop0.device
  659ms snapd.seeded.service
  645ms systemd-udev-trigger.service
  644ms logrotate.service
  590ms e2scrub_reap.service
  525ms log2ram.service
  494ms systemd-fsck@dev-disk-by\x2dlabel-system\x2dboot.service
  351ms systemd-resolved.service
  305ms multipathd.service
  305ms update-notifier-download.service
  276ms dpkg-db-backup.service
  247ms systemd-udevd.service
  218ms apparmor.service
  214ms ssh.service
  196ms keyboard-setup.service
  195ms cv_syslog_ng.service
  181ms systemd-timesyncd.service
  164ms modprobe@fuse.service
  163ms modprobe@pstore_blk.service
  163ms modprobe@pstore_zone.service
  162ms modprobe@ramoops.service
  152ms systemd-networkd.service
  150ms dev-hugepages.mount
  148ms dev-mqueue.mount
  144ms sys-kernel-debug.mount
  143ms systemd-tmpfiles-clean.service
  141ms sys-kernel-tracing.mount
  135ms kmod-static-nodes.service
  133ms lvm2-monitor.service
  132ms modprobe@efi_pstore.service
  132ms modprobe@chromeos_pstore.service
  132ms systemd-sysctl.service
  131ms modprobe@configfs.service
  131ms modprobe@drm.service
  116ms systemd-tmpfiles-setup-dev.service
  108ms systemd-sysusers.service
  105ms systemd-modules-load.service
   99ms systemd-remount-fs.service
   98ms systemd-tmpfiles-setup.service
   90ms bthelper@hci0.service
   89ms setvtrgb.service
   81ms systemd-random-seed.service
   80ms snap-core20-1883.mount
   72ms systemd-journald.service
   72ms nginx.service
   70ms snap-core20-1895.mount
   66ms plymouth-start.service
   63ms snap-lxd-23545.mount
   52ms snap-lxd-24326.mount
   51ms boot-firmware.mount
   49ms plymouth-quit-wait.service
   46ms systemd-user-sessions.service
   41ms systemd-journal-flush.service
   40ms snap-snapd-18940.mount
   37ms vsftpd.service
   37ms proc-sys-fs-binfmt_misc.mount
   37ms systemd-update-utmp-runlevel.service
   37ms plymouth-quit.service
   36ms systemd-rfkill.service
   35ms plymouth-read-write.service
   29ms sys-fs-fuse-connections.mount
   28ms sys-kernel-config.mount
   28ms console-setup.service
   28ms ufw.service
   28ms cv_snmptrapd.service
   27ms finalrd.service
   25ms snap-snapd-19127.mount
   25ms user-runtime-dir@1000.service
   22ms systemd-update-utmp.service
   22ms systemd-networkd-wait-online.service
   18ms snmpd.service
    7ms motd-news.service
    7ms snapd.socket
  432us blk-availability.service
```

No sure what to look for in the list above but that is from the system that has this logging stoppage issue.

Thanks for your time looking into this.


There are some concerns here.


You're loading a lot of things at boot.


My top concern here are snap's.
More often than not, snap's tend to cause problems especially in long-term use.
To check for snaps...
```
df -Th
```
and
```
snap list
```


Both log2ram and syslog-ng are loading up and running at boot.
I can guide you in disabling things in the list, however re-enabling is something I haven't looked into.
I'm gonna let someone else endeavor that task with you.


Other things in the list, such as ModemManager.service,  systemd-networkd-wait-online.service and others are most likely things you don't even need.


ModemManager is something needed if you connect to internet or wifi using a modem.
Transitioning to DSL and Router eliminates the need of ModemManager.


The box that your Internet Service Provider (ISP) brought to your house when they installed your internet is most likely a router, and not a modem or DSL.


The only caveat I can think of here is if log2ram or syslog-ng is using ModemManager to access/forward the internet logs inside the router for your reviewing.
If that's the case...then you need ModemManager.


systemd-networkd-wait-online may or may not be needed.
If you need your system to wait before connecting to the internet, or when you open a web-browser, I would keep it enabled.
Otherwise, I'd disable it.

---

### Post by wyattwhiteeagle on 2023-05-30
> **ian-weisser said:**
> Did you also look at the logs inside each container?

Did you set a maximum size for your journals? (separate from max-size for logs)

On a properly-working system, logs should not be growing to GB-per-day size. Have you fixed the underlying problems described by those logs?

Now, there's a few things I've never encountered before.

How exactly do we check those and change the settings if need-be?

---

### Post by tc2020 on 2023-05-30
My responses are as follows:

My journald.conf has settings of 64MB for SystemMaxUse and RuntimeMaxUse. I can confirm that it does stop at this max with "du -ch /var/log" command. Also, I can confirm that these logs do not grow uncontrollably because I have a cron job running daily to delete archives and also vacuum journal to 1M (journalctl --vacuum-size=1M). With this, my logs (/var/log total) goes to about xxMB, like 60MB. 

There are some services that I load at boot up: 4 applications with "cv_" prefix and some standard packages like log2ram, redis-server, and nginx. The rest is from system defaults. The ModemManager is included at bootup to probably handle user accounts that have tty and dialout services (i.e., [FONT=&amp]sudo usermod -a -G tty,dialout username) for remote login to the system CLI with 2FA access.

I did check syslog-ng.conf for our "cv_syslog_ng" application (collecting and monitoring syslogs from network devices) and the source does not include internal sources, so they are not being forwarded to elsewhere ("source s_network { default-network-drivers(); };" is the only source entry in this conf file). With regard to syslog-ng, it boots up with its default configuration file, i.e., no change from me.

Below is the listing for the commands (logs stop in this condition):

```
ubuntu@Demo:~$ df -Th
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  185M  3.2M  182M   2% /run
/dev/mmcblk0p2 ext4    29G  4.6G   24G  17% /
tmpfs          tmpfs  923M   52K  923M   1% /dev/shm
tmpfs          tmpfs  5.0M     0  5.0M   0% /run/lock
/dev/mmcblk0p1 vfat   253M  227M   26M  90% /boot/firmware
log2ram        tmpfs  128M   36M   93M  28% /var/log
tmpfs          tmpfs  185M  4.0K  185M   1% /run/user/1000
ubuntu@Demo:~$ snap list
Name    Version        Rev    Tracking       Publisher   Notes
core20  20230503       1895   latest/stable  canonical&#10003;  base
lxd     5.0.2-838e1b2  24326  5.0/stable/…   canonical&#10003;  -
snapd   2.59.2         19127  latest/stable  canonical&#10003;  snapd
```

There are many services to start up during boot-up by default. Which are the ones that may cause boot-up problems if the device is not internet connected; i.e., local networking only?. If those are removed, what operational impact would they have?. Sometimes, I see double reboot; i.e., I do sudo reboot, login, and it reboots again by itself after perhaps 1-2 minutes later.





 
[/FONT]

---

### Post by wyattwhiteeagle on 2023-05-30
> **tc2020 said:**
> My responses are as follows:


My journald.conf has settings of 64MB for SystemMaxUse and RuntimeMaxUse. I can confirm that it does stop at this max with "du -ch /var/log" command. Also, I can confirm that these logs do not grow uncontrollably because I have a cron job running daily to delete archives and also vacuum journal to 1M (journalctl --vacuum-size=1M). With this, my logs (/var/log total) goes to about xxMB, like 60MB.


There are some services that I load at boot up: 4 applications with "cv_" prefix and some standard packages like log2ram, redis-server, and nginx. The rest is from system defaults. The ModemManager is included at bootup to probably handle user accounts that have tty and dialout services (i.e., sudo usermod -a -G tty,dialout username) for remote login to the system CLI with 2FA access.


I did check syslog-ng.conf for our "cv_syslog_ng" application (collecting and monitoring syslogs from network devices) and the source does not include internal sources, so they are not being forwarded to elsewhere ("source s_network { default-network-drivers(); };" is the only source entry in this conf file). With regard to syslog-ng, it boots up with its default configuration file, i.e., no change from me.


Seems like everything you mention above is working normal optimally.
Though I may be falling short on that advice.


As for the following, see more below...
> **tc2020 said:**
> Below is the listing for the commands (logs stop in this condition):


```
ubuntu@Demo:~$ df -Th
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  185M  3.2M  182M   2% /run
/dev/mmcblk0p2 ext4    29G  4.6G   24G  17% /
tmpfs          tmpfs  923M   52K  923M   1% /dev/shm
tmpfs          tmpfs  5.0M     0  5.0M   0% /run/lock
/dev/mmcblk0p1 vfat   253M  227M   26M  90% /boot/firmware
log2ram        tmpfs  128M   36M   93M  28% /var/log
tmpfs          tmpfs  185M  4.0K  185M   1% /run/user/1000
```






```
ubuntu@Demo:~$ snap list
Name    Version        Rev    Tracking       Publisher   Notes
core20  20230503       1895   latest/stable  canonical&#10003;  base
lxd     5.0.2-838e1b2  24326  5.0/stable/&#8230;   canonical&#10003;  -
snapd   2.59.2         19127  latest/stable  canonical&#10003;  snapd
```


There are many services to start up during boot-up by default. Which are the ones that may cause boot-up problems if the device is not internet connected; i.e., local networking only?. If those are removed, what operational impact would they have?.


It depends on what you use your system for and what things you have setup on your system such as firewall, web browser, any software you use that you installed yourself, software you have purged but didn't remove all of its contents, ie log files, conf files, etc.


> **tc2020 said:**
> Sometimes, I see double reboot; i.e., I do sudo reboot, login, and it reboots again by itself after perhaps 1-2 minutes later.


About double rebooting like that, how is the boot-up sequence when you reboot using the desktop sequence?


In Lubuntu, using Windows method in mind...Start > Leave > Reboot

---

### Post by tc2020 on 2023-05-30
Double rebooting... I just log in via ssh or via console serial port and issue "sudo reboot". It's not every time but only sometimes it does the second reboot, in about 1-2 minutes after you see the login prompt. 

This system is an embedded headless system designed for unattended applications. It does not have any browser but it does have firewall. For testing, I disabled this firewall.

Apparently this Ubuntu version 22.04 LTS server and 5.15.0 kernel operates a bit different from the previous ones. In earlier version, snmptrapd.service is disabled by default. This version uses snmptrapd.socket instead of snmptrapd.service and it's enabled by default, so I had to troubleshoot as to why my snmptrapd could not start because udp port 162 was already taken by snmptrapd.socket on bootup. I am not sure if this version has anything to do with issues I see.

---

### Post by wyattwhiteeagle on 2023-06-03
> **tc2020 said:**
> Double rebooting... I just log in via ssh or via console serial port and issue "sudo reboot". It's not every time but only sometimes it does the second reboot, in about 1-2 minutes after you see the login prompt. 

This system is an embedded headless system designed for unattended applications. It does not have any browser but it does have firewall. For testing, I disabled this firewall.

Apparently this Ubuntu version 22.04 LTS server and 5.15.0 kernel operates a bit different from the previous ones. In earlier version, snmptrapd.service is disabled by default. This version uses snmptrapd.socket instead of snmptrapd.service and it's enabled by default, so I had to troubleshoot as to why my snmptrapd could not start because udp port 162 was already taken by snmptrapd.socket on bootup. I am not sure if this version has anything to do with issues I see.
Last year when 22.04 came out, there were quite a few changes made.
Almost to the point where everyone had to "relearn" their system's.

I remember having to read a few documentation pages and changelog's.
And we had to change some command line's within our custom script's.

One major change was Firefox being a snap, earlier version's didn't have firefox as a snap.
A lot of us, not everyone, had switched from Firefox to a different web-browser.

You might read-up on Documentation pages and changelog's to make sure your custom script's and computing practices are up-to-date.

---

### Post by tc2020 on 2023-06-04
I will look into the change logs. In the meantime, I just wonder if "gpiod" package was impacted by this. The command gpioset does not seem to set I/O pins that we use to enable/disable an external watchdog controller. This relates to double/repeated rebooting.

---

### Post by wyattwhiteeagle on 2023-06-04
> **tc2020 said:**
> ...In the meantime, I just wonder if "gpiod" package was impacted by this. The command gpioset does not seem to set I/O pins that we use to enable/disable an external watchdog controller...
Hopefully, someone with knowledge of that will chime in.
The only guidance I know on it is to check the system logs relating to the double-booting...ie, what all is happening immediately before, during, and after the double-reboot?

---

### Post by oldfred on 2023-06-05
Can you check logs:
Review log files
sudo grep -Ei 'warn|error' /var/log/*g

Do you need snaps?
I would remove them, if you do not need them.
I use Kubuntu with no snaps. Installed Firefox from ppa.

I run a regular update & houseclean script & removes some logs a bit quicker than logrotate.

 journalctl --disk-usage
Houseclean over 10 days
sudo journalctl --vacuum-time=10d
or
journalctl --vacuum-size=100M

I know nothing about wayland, but someone posted this:
Log files filling / (root)
edited custom.conf file in /etc/gdm3/custom.conf and comment line with #WaylandEnable=false

I do not think Raspberry Pi is in list of updates
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)
or:
sudo fwupdmgr get-devices
If not listed, I would then turn off/remove fwupd.
If UEFI firmware update not supported (yet)
sudo apt-get purge fwupd

Do not know any settings that may be unique to Raspberry Pi.

---

### Post by wyattwhiteeagle on 2023-07-06
Here's mine as of today
```
sudo grep -Ei 'warn|error' /var/log/*g
```
> /var/log/auth.log:Jul  6 15:14:10 wyatt-latitudee5400 sudo:    wyatt : TTY=pts/0 ; PWD=/home/wyatt ; USER=root ; COMMAND=/usr/bin/grep -Ei warn|error /var/log/auth.log /var/log/boot.log /var/log/dmesg /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/syslog /var/log/ubuntu-advantage-timer.log /var/log/Xorg.0.log


/var/log/auth.log:Jul  6 15:18:27 wyatt-latitudee5400 sudo:    wyatt : TTY=pts/0 ; PWD=/home/wyatt ; USER=root ; COMMAND=/usr/bin/grep -Ei warn|error|emerg|alert|crit|noti|info|debug /var/log/auth.log /var/log/boot.log /var/log/dmesg /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/syslog /var/log/ubuntu-advantage-timer.log /var/log/Xorg.0.log


/var/log/auth.log:Jul  6 15:21:08 wyatt-latitudee5400 sudo:    wyatt : TTY=pts/0 ; PWD=/home/wyatt ; USER=root ; COMMAND=/usr/bin/grep -Ei warn|error /var/log/auth.log /var/log/boot.log /var/log/dmesg /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/syslog /var/log/ubuntu-advantage-timer.log /var/log/Xorg.0.log


/var/log/dmesg:[    0.021235] kernel: ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/64 (20210730/tbfadt-564)


/var/log/dmesg:[    0.835322] kernel: i8042: Warning: Keylock active


/var/log/dmesg:[    2.323891] kernel: RAS: Correctable Errors collector initialized.


/var/log/gpu-manager.log:Error: can't access /sys/bus/pci/devices/0000:00:02.1/driver


/var/log/kern.log:Jul  6 12:08:34 wyatt-latitudee5400 kernel: [    0.021235] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/64 (20210730/tbfadt-564)


/var/log/kern.log:Jul  6 12:08:34 wyatt-latitudee5400 kernel: [    0.835322] i8042: Warning: Keylock active


/var/log/kern.log:Jul  6 12:08:34 wyatt-latitudee5400 kernel: [    2.323891] RAS: Correctable Errors collector initialized.


/var/log/kern.log:Jul  6 12:08:51 wyatt-latitudee5400 kernel: [   36.850874] i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun


/var/log/syslog:Jul  6 12:08:34 wyatt-latitudee5400 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.


/var/log/syslog:Jul  6 12:08:34 wyatt-latitudee5400 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (timer based) being skipped.


/var/log/syslog:Jul  6 12:08:34 wyatt-latitudee5400 kernel: [    0.021235] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Gpe0Block: 128/64 (20210730/tbfadt-564)


/var/log/syslog:Jul  6 12:08:34 wyatt-latitudee5400 kernel: [    0.835322] i8042: Warning: Keylock active


/var/log/syslog:Jul  6 12:08:34 wyatt-latitudee5400 kernel: [    2.323891] RAS: Correctable Errors collector initialized.


/var/log/syslog:Jul  6 12:08:51 wyatt-latitudee5400 kernel: [   36.850874] i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun


/var/log/Xorg.0.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

---

