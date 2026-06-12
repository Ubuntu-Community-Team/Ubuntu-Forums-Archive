---
title: "loopback file with lvm at boot, how do I?"
date: 2008-05-22
forum: General Help
---

### Post by aktxyz on 2008-05-22
I install the LVM packages...

sudo apt-get install lvm2 dmsetup mdadm reiserfsprogs xfsprogs
sudo modprobe dm-mod
sudo modprobe dm-snapshot

setup a LV and filesystem and mounts...

sudo dd if=/dev/zero of=/mysql_loop bs=4096 count=2883584
sudo losetup /dev/loop0 /mysql_loop
sudo pvcreate /dev/loop0
sudo vgcreate mysql_vg /dev/loop0
sudo lvcreate -L7G -n mysql_lv mysql_vg
sudo mkfs -t ext3 /dev/mysql_vg/mysql_lv
sudo mkdir -p /mysql_lv
sudo mount /dev/mysql_vg/mysql_lv /mysql_lv

But when I REBOOT...I have to do some steps over...

sudo losetup /dev/loop0 /mysql_loop
sudo vgchange -ay
sudo mount /dev/mysql_vg/mysql_lv /mysql_lv

I have tried various rc2.X things, but I don't really know what I am doing, any one know the proper way to get this all setup at boot.  It needs to be done before MYSQL cranks up as well, so before /etc/rc.local

---

### Post by aktxyz on 2008-05-22
This worked...let me know if I am doing something dumb!

========== save to /etc/init.d/mysql-loop
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin

do_start() {
    /sbin/modprobe dm-mod
    /sbin/modprobe dm-snapshot
    /sbin/losetup /dev/loop0 /mysql_loop
    /sbin/vgscan
    /sbin/vgchange -ay
    /bin/mount /dev/mysql_vg/mysql_lv /mysql_lv
}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
==========

install script with:
sudo update-rc.d -f mysql-loop start 14 2 3 4 5 .

uinstall script with:
sudo update-rc.d -f mysql-loop remove

---

