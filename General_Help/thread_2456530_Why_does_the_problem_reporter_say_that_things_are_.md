---
title: "Why does the problem reporter say that things are always out of date?"
date: 2021-01-13
forum: General Help
---

### Post by ski-brimson on 2021-01-13
I have automatic updates turned on.  It runs regularly.  I have for years.  The problem reporter always says things are out of date. Seems to complain every time I boot, yet things seem to be fine.  How do I remove it, as it is useless?

For instance I always see something like this:

The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

apt, apt-utils, ca-certificates, dbus, dbus-x11, file, glib-networking, glib-networking-common, glib-networking-services, krb5-locales, libapt-inst2.0, libapt-pkg5.0, libarchive13, libblkid1, libc6, libcups2, libcurl3-gnutls, libdbus-1-3, libexif12, libfdisk1, libfreetype6, libgd3, libglib2.0-0, libglib2.0-data, libgnutls30, libgssapi-krb5-2, libicu55, libjpeg-turbo8, libk5crypto3, libkrb5-3, libkrb5support0, libldap-2.4-2, libmagic1, libmount1, libnss3, libnss3-nssdb, libp11-kit0, libpam-modules, libpam-modules-bin, libpam-runtime, libpam-systemd, libpam0g, libprocps4, libproxy1v5, libpython2.7, libpython2.7-minimal, libpython2.7-stdlib, librsvg2-2, librsvg2-common, libsane, libsane-common, libsasl2-2, libsasl2-modules, libsasl2-modules-db, libseccomp2, libsmartcols1, libsmbclient, libsqlite3-0, libssl1.0.0, libsystemd0, libudev1, libuuid1, libwbclient0, libx11-6, libx11-data, libx11-xcb1, libxml2, mount, multiarch-support, openssl, p11-kit, p11-kit-modules, perl-base, procps, python2.7, python2.7-minimal, samba-libs, systemd, ubuntu-keyring, udev, util-linux, uuid-runtime

ii  apt                                            1.2.32                       amd64                        commandline package manager

I have 16.04.6 LTS

---

### Post by TheFu on 2021-01-13
I think auto-updates only do security updates, not everything.
I don't do auto-updates, been burned a few times, left with unworking systems.

Anyways, every week, run these:
```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove
```
apt shouldn't be used in any crontab script. Use **apt-get** instead if that is your intention. apt has a warning about the API not being stable. Believe it.

Also, check whether the system needs to be rebooted afterwards and reboot within the next 24 hrs, if needed.  Some desktop apps can have issue when their unloaded libraries get updated and they are still running, then get loaded. Servers tend to handle these updates better and can handle reboot delays a few days, usually. Most of the time, reboots aren't necessary.

This link seems a bit dated, but [https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates) . At this point, really should be using **sudoedit** to edit system files. 
Another set of options: [https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

---

