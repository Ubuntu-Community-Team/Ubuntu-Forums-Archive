---
title: "snap - How to disable or remove from offline system"
date: 2018-11-12
forum: General Help
---

### Post by jimpster1 on 2018-11-12
My server Ubuntu 16.04 broke after I installed snapd and then used snap to install nextcloud. It rebooted during the command.

I managed to get the system disk volume mounted remotely and my tools are limited to busybox.

How do I disable snapd and nextcloud so I can try to boot the system and then apt remove them? 

The logs in /var/log seems not to tell me much, but I can post them if needed.

Is it as easy as disabling services?

---

### Post by Frogs Hair on 2018-11-12
To remove  the snap I think you need it running.Though I don't know if you can do this from busybox. 
 ```
sudo snap remove nextcloud 
```

You can kill a process from busybox using kill or killall.

```
killall name
```

---

### Post by jimpster1 on 2018-11-12
Thanks for the reply. 
I don't have the snap command, only busybox tools. I am in a initramfs logged into a dropbear ssh server. Managed to use #/sbin/cryptsetup luksOpen to decrypt and mount the system drive.

I was using a initramfs to remotely ssh in and give password to decrypt and start the server. Installing snapd and nextcloud was the last thing I did before it up and rebooted on its own.

edit: I think I may try moving stuff out of /etc/init.d (wherever upstart or systemd keeps them)

Here is what I found
```
# find /3 -iname "*snap*"
/3/usr/bin/snap-dna
/3/usr/bin/snapfuse
/3/usr/bin/snap
/3/usr/bin/snapctl
/3/usr/lib/snap
/3/usr/lib/snap/snap
/3/usr/lib/snapd
/3/usr/lib/snapd/snapd.run-from-snap
/3/usr/lib/snapd/snap-confine
/3/usr/lib/snapd/snap-exec
/3/usr/lib/snapd/snapd.core-fixup.sh
/3/usr/lib/snapd/snap-discard-ns
/3/usr/lib/snapd/snap-repair
/3/usr/lib/snapd/snap-update-ns
/3/usr/lib/snapd/snapd
/3/usr/lib/snapd/snap-device-helper
/3/usr/lib/snapd/snap-seccomp
/3/usr/lib/snapd/snap-mgmt
/3/usr/lib/snapd/snap-gdb-shim
/3/usr/lib/environment.d/990-snapd.conf
/3/usr/local/mysql-5.7.19/libmysqld/examples/builder-sample/snapshot.jpg
/3/usr/local/mysql-5.7.19/bld/boost_1_59_0/libs/date_time/xmldoc/snap_to_details.xml
/3/usr/local/mysql-5.7.19/mysql-test/t/consistent_snapshot.test
/3/usr/local/mysql-5.7.19/mysql-test/r/consistent_snapshot.result
/3/usr/local/mysql-5.7.19/storage/ndb/mcc/frontend/dojo/dojox/data/SnapLogicStore.js.uncompressed.js
/3/usr/local/mysql-5.7.19/storage/ndb/mcc/frontend/dojo/dojox/data/SnapLogicStore.js
/3/usr/share/polkit-1/actions/io.snapcraft.snapd.policy
/3/usr/share/snap
/3/usr/share/dbus-1/services/io.snapcraft.Launcher.service
/3/usr/share/dbus-1/services/io.snapcraft.Settings.service
/3/usr/share/mime/application/vnd.snap.xml
/3/usr/share/man/man1/snap-dna.1.gz
/3/usr/share/man/man1/snap-confine.1.gz
/3/usr/share/man/man1/snap.1.gz
/3/usr/share/man/man5/snap-discard-ns.5.gz
/3/usr/share/doc/snap
/3/usr/share/doc/snapd
/3/usr/share/bash-completion/completions/snap
/3/root/snap
/3/snap
/3/etc/udev/rules.d/70-snap.core.rules
/3/etc/apparmor.d/local/usr.lib.snapd.snap-confine.real
/3/etc/apparmor.d/usr.lib.snapd.snap-confine.real
/3/etc/apparmor.d/cache/usr.lib.snapd.snap-confine.real
/3/etc/xdg/autostart/snap-userd-autostart.desktop
/3/etc/systemd/system/snap-core-5745.mount
/3/etc/systemd/system/multi-user.target.wants/snap-core-5745.mount
/3/etc/systemd/system/multi-user.target.wants/snap.nextcloud.mdns-publisher.service
/3/etc/systemd/system/multi-user.target.wants/snapd.autoimport.service
/3/etc/systemd/system/multi-user.target.wants/snap.nextcloud.nextcloud-cron.service
/3/etc/systemd/system/multi-user.target.wants/snap.nextcloud.redis-server.service
/3/etc/systemd/system/multi-user.target.wants/snap-nextcloud-9571.mount
/3/etc/systemd/system/multi-user.target.wants/snap.nextcloud.apache.service
/3/etc/systemd/system/multi-user.target.wants/snapd.service
/3/etc/systemd/system/multi-user.target.wants/snapd.core-fixup.service
/3/etc/systemd/system/multi-user.target.wants/snapd.seeded.service
/3/etc/systemd/system/multi-user.target.wants/snap.nextcloud.renew-certs.service
/3/etc/systemd/system/multi-user.target.wants/snap.nextcloud.php-fpm.service
/3/etc/systemd/system/multi-user.target.wants/snap.nextcloud.mysql.service
/3/etc/systemd/system/final.target.wants/snapd.system-shutdown.service
/3/etc/systemd/system/snap.nextcloud.mdns-publisher.service
/3/etc/systemd/system/timers.target.wants/snapd.snap-repair.timer
/3/etc/systemd/system/sockets.target.wants/snapd.socket
/3/etc/systemd/system/snap.nextcloud.nextcloud-cron.service
/3/etc/systemd/system/snap.nextcloud.redis-server.service
/3/etc/systemd/system/snap-nextcloud-9571.mount
/3/etc/systemd/system/snap.nextcloud.apache.service
/3/etc/systemd/system/cloud-final.service.wants/snapd.seeded.service
/3/etc/systemd/system/snap.nextcloud.renew-certs.service
/3/etc/systemd/system/snap.nextcloud.php-fpm.service
/3/etc/systemd/system/snap.nextcloud.mysql.service
/3/lib/udev/snappy-app-dev
/3/lib/udev/rules.d/66-snapd-autoimport.rules
/3/lib/modules/3.14.79-115/kernel/drivers/md/dm-snapshot.ko
/3/lib/modules/3.14.79-115/kernel/net/802/psnap.ko
/3/lib/aarch64-linux-gnu/device-mapper/libdevmapper-event-lvm2snapshot.so
/3/lib/aarch64-linux-gnu/libdevmapper-event-lvm2snapshot.so
/3/lib/systemd/system-generators/snapd-generator
/3/lib/systemd/system/snapd.snap-repair.service
/3/lib/systemd/system/snapd.snap-repair.timer
/3/lib/systemd/system/snapd.autoimport.service
/3/lib/systemd/system/snapd.system-shutdown.service
/3/lib/systemd/system/snapd.service
/3/lib/systemd/system/snapd.core-fixup.service
/3/lib/systemd/system/snapd.socket
/3/lib/systemd/system/snapd.seeded.service
/3/var/snap
/3/var/lib/dpkg/info/snapd.prerm
/3/var/lib/dpkg/info/snapd.md5sums
/3/var/lib/dpkg/info/snapd.preinst
/3/var/lib/dpkg/info/snapd.conffiles
/3/var/lib/dpkg/info/snapd.list
/3/var/lib/dpkg/info/snapd.postinst
/3/var/lib/dpkg/info/snap.md5sums
/3/var/lib/dpkg/info/snap.list
/3/var/lib/dpkg/info/snapd.postrm
/3/var/lib/snapd
/3/var/lib/snapd/snaps
/3/var/lib/snapd/snaps/nextcloud_9571.snap
/3/var/lib/snapd/snaps/core_5745.snap
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.renew-certs.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.hook.configure.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.hook.configure.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mdns-publisher.bin
/3/var/lib/snapd/seccomp/bpf/snap.core.hook.configure.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.enable-https.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.import.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mdns-publisher.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.export.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.redis-server.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.nextcloud-cron.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.disable-https.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.redis-server.src
/3/var/lib/snapd/seccomp/bpf/snap.core.hook.configure.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mysql-client.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.occ.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.export.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mysqldump.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.php-fpm.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.disable-https.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mysql-client.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.manual-install.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.occ.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mysql.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.apache.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.apache.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.import.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.enable-https.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.renew-certs.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.manual-install.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.nextcloud-cron.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mysql.bin
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.mysqldump.src
/3/var/lib/snapd/seccomp/bpf/snap.nextcloud.php-fpm.bin
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.mysql-client
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.mdns-publisher
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.renew-certs
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.nextcloud-cron
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.import
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.mysql
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.php-fpm
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.hook.configure
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.disable-https
/3/var/lib/snapd/apparmor/profiles/snap-update-ns.nextcloud
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.manual-install
/3/var/lib/snapd/apparmor/profiles/snap-update-ns.core
/3/var/lib/snapd/apparmor/profiles/snap-confine.core.5745
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.occ
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.export
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.enable-https
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.mysqldump
/3/var/lib/snapd/apparmor/profiles/snap.core.hook.configure
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.apache
/3/var/lib/snapd/apparmor/profiles/snap.nextcloud.redis-server
/3/var/lib/snapd/apparmor/snap-confine
/3/var/lib/snapd/cookie/snap.core
/3/var/lib/snapd/cookie/snap.nextcloud
/3/var/lib/snapd/assertions/asserts-v0/snap-revision
/3/var/lib/snapd/assertions/asserts-v0/snap-declaration
/3/var/lib/systemd/deb-systemd-helper-enabled/multi-user.target.wants/snapd.autoimport.service
/3/var/lib/systemd/deb-systemd-helper-enabled/multi-user.target.wants/snapd.service
/3/var/lib/systemd/deb-systemd-helper-enabled/multi-user.target.wants/snapd.core-fixup.service
/3/var/lib/systemd/deb-systemd-helper-enabled/multi-user.target.wants/snapd.seeded.service
/3/var/lib/systemd/deb-systemd-helper-enabled/final.target.wants/snapd.system-shutdown.service
/3/var/lib/systemd/deb-systemd-helper-enabled/timers.target.wants/snapd.snap-repair.timer
/3/var/lib/systemd/deb-systemd-helper-enabled/snapd.service.dsh-also
/3/var/lib/systemd/deb-systemd-helper-enabled/sockets.target.wants/snapd.socket
/3/var/lib/systemd/deb-systemd-helper-enabled/snapd.core-fixup.service.dsh-also
/3/var/lib/systemd/deb-systemd-helper-enabled/snapd.snap-repair.timer.dsh-also
/3/var/lib/systemd/deb-systemd-helper-enabled/snapd.system-shutdown.service.dsh-also
/3/var/lib/systemd/deb-systemd-helper-enabled/snapd.autoimport.service.dsh-also
/3/var/lib/systemd/deb-systemd-helper-enabled/snapd.socket.dsh-also
/3/var/lib/systemd/deb-systemd-helper-enabled/snapd.seeded.service.dsh-also
/3/var/lib/systemd/deb-systemd-helper-enabled/cloud-final.service.wants/snapd.seeded.service
/3/var/cache/apparmor/snap.nextcloud.mysql-client
/3/var/cache/apparmor/snap.nextcloud.mdns-publisher
/3/var/cache/apparmor/snap.nextcloud.renew-certs
/3/var/cache/apparmor/snap.nextcloud.nextcloud-cron
/3/var/cache/apparmor/snap.nextcloud.import
/3/var/cache/apparmor/snap.nextcloud.mysql
/3/var/cache/apparmor/snap.nextcloud.php-fpm
/3/var/cache/apparmor/snap.nextcloud.hook.configure
/3/var/cache/apparmor/snap.nextcloud.disable-https
/3/var/cache/apparmor/snap-update-ns.nextcloud
/3/var/cache/apparmor/snap.nextcloud.manual-install
/3/var/cache/apparmor/snap-update-ns.core
/3/var/cache/apparmor/snap-confine.core.5745
/3/var/cache/apparmor/snap.nextcloud.occ
/3/var/cache/apparmor/snap.nextcloud.export
/3/var/cache/apparmor/snap.nextcloud.enable-https
/3/var/cache/apparmor/snap.nextcloud.mysqldump
/3/var/cache/apparmor/snap.core.hook.configure
/3/var/cache/apparmor/snap.nextcloud.apache
/3/var/cache/apparmor/snap.nextcloud.redis-server
/3/var/cache/snapd



```

I am thinking about moving the above out of /3/etc/systemd/system/multi-user.target.wants/*snap* and seeing if the system will boot.

---

### Post by jimpster1 on 2018-11-12
Solved I manually moved files out of /etc/systemd/ that mentioned snap or snapd and a few others in the list above. Rebooted, entered password and server started normally.

---

