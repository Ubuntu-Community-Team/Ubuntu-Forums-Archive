---
title: "Restart cupsd?"
date: 2006-12-30
forum: General Help
---

### Post by rudiz on 2006-12-30
Hi

Whats the code to restart cupsd?

---

### Post by angkor on 2006-12-30
Dunno for sure but try:

```
sudo /etc/init.d/cupsd restart
```

---

### Post by rudiz on 2006-12-30
Output: command not known

---

### Post by koenn on 2006-12-30
sudo  /etc/init.d/cupsys restart

---

### Post by rudiz on 2006-12-30
The same otput

---

### Post by ~LoKe on 2006-12-30
That should have worked.  Did you remove cupsys or something?

> loke@x04d:~$ ls /etc/init.d
acpid               hdparm                           procps.sh
acpi-support        hostname.sh                      rc
alsa-utils          hotkey-setup                     rc.local
anacron             hplip                            rcS
apmd                hwclock.sh                       readahead
apport              keyboard-setup                   readahead-desktop
atd                 keymap.sh                        README
avahi-daemon        killprocs                        reboot
bind                klogd                            resolvconf
bind9               laptop-mode                      rmnologin
binfmt-support      linux-restricted-modules-common  rsync
bittorrent          loopback                         screen
bluetooth           lvm                              sendsigs
bluetooth.dpkg-new  makedev                          single
bootclean           mdadm                            skeleton
bootlogd            mdadm-raid                       stop-bootlogd
bootmisc.sh         module-init-tools                stop-bootlogd-single
brltty              mountall-bootclean.sh            stop-readahead
checkfs.sh          mountall.sh                      sysklogd
checkroot.sh        mountdevsubfs.sh                 udev
console-screen.sh   mountkernfs.sh                   umountfs
console-setup       mountnfs-bootclean.sh            umountnfs.sh
cron                mpd                              umountroot
**cupsys**              mtab.sh                          urandom
dbus                networking                       usplash
dns-clean           nvidia-kernel                    vbesave
dnsmasq             pcmcia                           waitnfs.sh
evms                pcmciautils                      wpa-ifupdown
festival            powernowd                        wpasupplicant
gdm                 powernowd.early                  x11-common
glibc.sh            ppp
halt                pppd-dns

---

### Post by rudiz on 2006-12-30
Maybe somebody can tell how to connect in Dapper Kubuntu a hp psc 2171 printer?

---

### Post by koenn on 2006-12-30
find out if there's a cupsd on your system:
```
which cupsd
```

the return should be something like:
/usr/sbin/cupsd

---

### Post by rudiz on 2006-12-30
cupsys en cupsd  are there!

---

### Post by koenn on 2006-12-30
>  	Maybe somebody can tell how to connect in Dapper Kubuntu a hp psc 2171 printer?
first make sure you have cups installed and working (see higher).

Then it's just clicking : system : administration : printing -> New Printer -> and so on

---

### Post by rudiz on 2006-12-30
Sorry i am in Kubuntu, not ubuntu.

---

### Post by koenn on 2006-12-30
ah, Google ... they know everything !
> 
Kubuntu features the impressive KDE Printing Manager, which sports a host of useful features. Click on the K Menu button in your Toolbar and choose Utilities->Printing Manager to start the Printing Manager Control Module. You can add, or connect to, a printer using this module.

[http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html](http://www.kubuntu.org/docs/kquickguide/C/ch02s05.html)

---

### Post by rudiz on 2006-12-30
Thank you . It was not for me but for somebody i helping istallinng kubuntu with IM.  I myself have Ubuntu/Gnome as syteem..

---

