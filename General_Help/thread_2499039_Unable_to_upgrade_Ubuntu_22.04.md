---
title: "Unable to upgrade Ubuntu 22.04"
date: 2024-07-09
forum: General Help
---

### Post by mdarstedt on 2024-07-09
Hello. I was just going to upgrade my Ubuntu 22.04 server to get some Apache fixes, but ran into some issues:
```
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent processing triggers for ntp:
 ntp depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package ntp (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for php8.0-cli:
 php8.0-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.0-cli (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.0:
 libapache2-mod-php8.0 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.0 (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.1:
 libapache2-mod-php8.1 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.1 (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent processing triggers for php8.1-cli:
 php8.1-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.1-cli (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tzdata
 ntp
 php8.0-cli
 libapache2-mod-php8.0
 libapache2-mod-php8.1
 php8.1-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I looked around for some possible solutions to this, but nothing really seems to help:
```
$ sudo dpkg --configure -a
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent processing triggers for ntp:
 ntp depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package ntp (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for php8.0-cli:
 php8.0-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.0-cli (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.0:
 libapache2-mod-php8.0 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.0 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.1:
 libapache2-mod-php8.1 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.1 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for php8.1-cli:
 php8.1-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.1-cli (--configure):
 dependency problems - leaving triggers unprocessed
Errors were encountered while processing:
 tzdata
 ntp
 php8.0-cli
 libapache2-mod-php8.0
 libapache2-mod-php8.1
 php8.1-cli
```

```

$ sudo dpkg-reconfigure tzdata
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
/usr/sbin/dpkg-reconfigure: tzdata is broken or not fully installed
```

```
$ sudo dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 tzdata               time zone and daylight-saving time data

The following packages have been triggered, but the trigger processing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 libapache2-mod-php8.0 server-side, HTML-embedded scripting language (Apache 2 
 libapache2-mod-php8.1 server-side, HTML-embedded scripting language (Apache 2 
 ntp                  Network Time Protocol daemon and utility programs
 php8.0-cli           command-line interpreter for the PHP scripting language
 php8.1-cli           command-line interpreter for the PHP scripting language

$ sudo dpkg --configure --pending
[sudo] password for daniel: 
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent processing triggers for ntp:
 ntp depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package ntp (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for php8.0-cli:
 php8.0-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.0-cli (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.0:
 libapache2-mod-php8.0 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.0 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.1:
 libapache2-mod-php8.1 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.1 (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for php8.1-cli:
 php8.1-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.1-cli (--configure):
 dependency problems - leaving triggers unprocessed
Errors were encountered while processing:
 tzdata
 ntp
 php8.0-cli
 libapache2-mod-php8.0
 libapache2-mod-php8.1
 php8.1-cli
```

And this is pretty much when I gave up:
```
$ sudo apt reinstall tzdata
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.15.0-102 linux-headers-5.15.0-102-generic linux-headers-5.15.0-105 linux-headers-5.15.0-105-generic linux-image-5.15.0-102-generic linux-image-5.15.0-105-generic linux-modules-5.15.0-102-generic linux-modules-5.15.0-105-generic linux-modules-extra-5.15.0-102-generic linux-modules-extra-5.15.0-105-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for tzdata:amd64
```

Does anyone have any good ideas on how to proceed at this point?

---

### Post by TheFu on 2024-07-09
Good idea?  That remains to be seen.

I have some ideas.

a) is the file system full?   **df -h /etc**  and **df -i /etc**  Are either at 100%?
b) did you happen to delete any tz files manually, outside the package manager?  If so, look in the APT log for a specific error around a missing file related to tz.  If one is missing, see if creating an empty one will let the **apt reinstall tzdata ** finish.  Use **sudo touch {/path/to/missing/tz-file}**
c) Not that I expect this to help, but have you tried to remove those unneeded kernel files already?  I don't think it will harm anything, but there is always a risk.  **sudo apt autoremove**

In short, you need to fix the tzdata issue before moving onto the next issue.  Then fix that and move onto the next.  If there are lots of files reported as corrupted, start looking at the storage for where the files ARE and where they will be placed.  Storage devices fail all the time.  I've seen new, quality brand, SSDs fail just after 30 days of use.  I've seen 5 yr warranty HDDs fail after 8 months.  BTW, the RMA to get it replace took about 6 weeks, so I'm glad I just bought replacements while waiting.

You can also run apt and apt-get with debug data output.  That can be helpful to get more details.

---

### Post by mdarstedt on 2024-07-09
Hello, TheFu. Thanks for taking the time to help out. First off, I currently have this problem on five servers, all identical setup since they are application frontend servers, running Apache+PHP. They are all hosted at a cloud provider, running as VMs under VMware vCloud hypervisor with enterprise grade SAN as disk backend.

> **TheFu said:**
> 
I have some ideas.

a) is the file system full?   **df -h /etc**  and **df -i /etc**  Are either at 100%?

No issues with disk space:

```
# df -h
Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              388M  1,2M  387M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   30G   16G   13G  56% /
tmpfs                              1,9G     0  1,9G   0% /dev/shm
tmpfs                              5,0M     0  5,0M   0% /run/lock
/dev/sda2                          2,0G  499M  1,3G  28% /boot
tmpfs                              388M  4,0K  388M   1% /run/user/1004

```

> **TheFu said:**
> 
b) did you happen to delete any tz files manually, outside the package manager?  If so, look in the APT log for a specific error around a missing file related to tz.  If one is missing, see if creating an empty one will let the **apt reinstall tzdata ** finish.  Use **sudo touch {/path/to/missing/tz-file}**

I honestly doubt it. Not really sure what to look for in the apt log, but if I loop around the files that the package is supposed to have installed, it appears as only a README file is missing:
```
# for i in $(dpkg -L tzdata); do ls -l "$i"; done > /dev/null
ls: cannot access '/usr/share/doc/tzdata/README.Debian': No such file or directory
```

> **TheFu said:**
> 
c) Not that I expect this to help, but have you tried to remove those unneeded kernel files already?  I don't think it will harm anything, but there is always a risk.  **sudo apt autoremove**

This basically ends up with the same issue in the end, complaining about tzdata having issues:

```
# apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-5.15.0-102 linux-headers-5.15.0-102-generic linux-headers-5.15.0-105 linux-headers-5.15.0-105-generic linux-image-5.15.0-102-generic linux-image-5.15.0-105-generic
  linux-modules-5.15.0-102-generic linux-modules-5.15.0-105-generic linux-modules-extra-5.15.0-102-generic linux-modules-extra-5.15.0-105-generic
0 upgraded, 0 newly installed, 10 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 1&#8239;166 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 240763 files and directories currently installed.)
Removing linux-headers-5.15.0-102-generic (5.15.0-102.112) ...
Removing linux-headers-5.15.0-102 (5.15.0-102.112) ...
Removing linux-headers-5.15.0-105-generic (5.15.0-105.115) ...
Removing linux-headers-5.15.0-105 (5.15.0-105.115) ...
Removing linux-modules-extra-5.15.0-102-generic (5.15.0-102.112) ...
Removing linux-modules-extra-5.15.0-105-generic (5.15.0-105.115) ...
Removing linux-image-5.15.0-102-generic (5.15.0-102.112) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-102-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-113-generic
Found initrd image: /boot/initrd.img-5.15.0-113-generic
Found linux image: /boot/vmlinuz-5.15.0-112-generic
Found initrd image: /boot/initrd.img-5.15.0-112-generic
Found linux image: /boot/vmlinuz-5.15.0-105-generic
Found initrd image: /boot/initrd.img-5.15.0-105-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
Removing linux-image-5.15.0-105-generic (5.15.0-105.115) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-105-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45764: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45764: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45777: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45777: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45790: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45790: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45803: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45803: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45866: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 45866: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-5.15.0-113-generic
Found initrd image: /boot/initrd.img-5.15.0-113-generic
Found linux image: /boot/vmlinuz-5.15.0-112-generic
Found initrd image: /boot/initrd.img-5.15.0-112-generic
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 46260: /usr/sbin/grub-probe
File descriptor 11 (/var/lib/dpkg/triggers/linux-update-5.15.0-102-generic (deleted)) leaked on vgs invocation. Parent PID 46260: /usr/sbin/grub-probe
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
Removing linux-modules-5.15.0-102-generic (5.15.0-102.112) ...
Removing linux-modules-5.15.0-105-generic (5.15.0-105.115) ...
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent processing triggers for ntp:
 ntp depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package ntp (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for php8.0-cli:
 php8.0-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.0-cli (--configure):
 dependency problems - leaving triggers unprocessed
dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.0:
 libapache2-mod-php8.0 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.0 (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent processing triggers for libapache2-mod-php8.1:
 libapache2-mod-php8.1 depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package libapache2-mod-php8.1 (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent processing triggers for php8.1-cli:
 php8.1-cli depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package php8.1-cli (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tzdata
 ntp
 php8.0-cli
 libapache2-mod-php8.0
 libapache2-mod-php8.1
 php8.1-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

> **TheFu said:**
> 
In short, you need to fix the tzdata issue before moving onto the next issue.  Then fix that and move onto the next.  If there are lots of files reported as corrupted, start looking at the storage for where the files ARE and where they will be placed.  Storage devices fail all the time.  I've seen new, quality brand, SSDs fail just after 30 days of use.  I've seen 5 yr warranty HDDs fail after 8 months.  BTW, the RMA to get it replace took about 6 weeks, so I'm glad I just bought replacements while waiting.

Yeah, I figured as much, and it is tzdata I am focusing on getting sorted first with this post. As I mentioned at the top of this reply, I'm experiencing the same issue on multiple servers, so I'm not sure that this is an issue with broken or corrupted disks/filesystems. Also, dmesg doesn't display anything related to corrupted filesystems or the like.

> **TheFu said:**
> 
You can also run apt and apt-get with debug data output.  That can be helpful to get more details.

Do you have any suggestions on debug options useful for this case - and how to use them? I tried a few (Debug::pkgProblemResolver,  Debug::pkgAcquire and Debug::pkgDPkgPM) but they didn't yield much.

---

### Post by currentshaft on 2024-07-09
Try with:

export DEBIAN_FRONTEND="noninteractive"

---

### Post by mdarstedt on 2024-07-09
> **currentshaft said:**
> Try with:

export DEBIAN_FRONTEND="noninteractive"

Sadly, this did not help.

**Something really interesting though**: I fired up a fresh Ubuntu 22.04 machine locally in Vagrant (using a slightly older VirtualBox image that therefore had a lot of packages to upgrade after initial deploy), and allowed it be configured by Puppet the same way as the problematic servers (this is how we normally test our Puppet configuration before deploying it to production), and then logged in and performed an apt update && apt upgrade - and ran into exactly the same issue!

```

# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  redis-server libheif1 redis-tools libde265-0
Learn more about Ubuntu Pro at https://ubuntu.com/pro
#
# OpenSSH CVE-2024-6387 fix is available for all affected Ubuntu releases.
# RegreSSHion: Possible RCE Due To A Race Condition In Signal Handling.
# For more details see: https://ubuntu.com/blog/ubuntu-regresshion-security-fix
#
The following NEW packages will be installed:
  linux-headers-5.15.0-113 linux-headers-5.15.0-113-generic linux-image-5.15.0-113-generic linux-modules-5.15.0-113-generic
The following packages have been kept back:
  python3-update-manager ubuntu-minimal ubuntu-server ubuntu-standard update-manager-core
The following packages will be upgraded:
  bind9-dnsutils bind9-host bind9-libs bsdextrautils bsdutils cloud-init cpio distro-info-data eject fdisk git git-man klibc-utils landscape-common less libarchive13 libblkid1 libc-bin libfdisk1 libglib2.0-0
  libglib2.0-bin libglib2.0-data libgnutls30 libklibc libmount1 libnetplan0 libnghttp2-14 libnspr4 libnss3 libpcre2-8-0 libsmartcols1 libssl3 libtss2-esys-3.0.2-0 libtss2-mu0 libtss2-sys1 libtss2-tcti-cmd0
  libtss2-tcti-device0 libtss2-tcti-mssim0 libtss2-tcti-swtpm0 libuuid1 libxml2 linux-headers-generic linux-headers-virtual linux-image-virtual linux-virtual locales mount netplan.io openssl python3-idna
  python3-jinja2 snapd tzdata ubuntu-advantage-tools ubuntu-pro-client ubuntu-pro-client-l10n util-linux uuid-runtime vim vim-common vim-runtime vim-tiny wget xxd
64 upgraded, 4 newly installed, 0 to remove and 5 not upgraded.
47 standard LTS security updates
Need to get 108 MB of archives.
After this operation, 234 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 bsdutils amd64 1:2.37.2-4ubuntu3.4 [80.9 kB]
Get:2 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 libpcre2-8-0 amd64 10.42-3+ubuntu22.04.1+deb.sury.org+1 [230 kB]
Get:3 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 libxml2 amd64 2.9.14+dfsg-0.1+ubuntu22.04.1+deb.sury.org+1 [839 kB]
Get:4 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 util-linux amd64 2.37.2-4ubuntu3.4 [1063 kB]
Get:5 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-bin amd64 2.35-0ubuntu3.8 [706 kB]
Get:6 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 mount amd64 2.37.2-4ubuntu3.4 [114 kB]
Get:7 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libsmartcols1 amd64 2.37.2-4ubuntu3.4 [50.9 kB]
Get:8 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libuuid1 amd64 2.37.2-4ubuntu3.4 [23.8 kB]
Get:9 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 uuid-runtime amd64 2.37.2-4ubuntu3.4 [32.0 kB]
Get:10 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libblkid1 amd64 2.37.2-4ubuntu3.4 [103 kB]
Get:11 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libmount1 amd64 2.37.2-4ubuntu3.4 [122 kB]
Get:12 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libssl3 amd64 3.0.2-0ubuntu1.16 [1905 kB]
Get:13 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgnutls30 amd64 3.7.3-4ubuntu1.5 [966 kB]
Get:14 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 distro-info-data all 0.52ubuntu0.7 [5326 B]
Get:15 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 eject amd64 2.37.2-4ubuntu3.4 [26.8 kB]
Get:16 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 less amd64 590-1ubuntu0.22.04.3 [142 kB]
Get:17 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libglib2.0-data all 2.72.4-0ubuntu2.3 [4666 B]
Get:18 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libglib2.0-bin amd64 2.72.4-0ubuntu2.3 [80.8 kB]
Get:19 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libglib2.0-0 amd64 2.72.4-0ubuntu2.3 [1466 kB]
Get:20 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 netplan.io amd64 0.106.1-7ubuntu0.22.04.4 [106 kB]
Get:21 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnetplan0 amd64 0.106.1-7ubuntu0.22.04.4 [111 kB]
Get:22 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 locales all 2.35-0ubuntu3.8 [4245 kB]
Get:23 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 openssl amd64 3.0.2-0ubuntu1.16 [1186 kB]
Get:24 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 tzdata all 2024a-0ubuntu0.22.04.1 [349 kB]
Get:25 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 ubuntu-pro-client-l10n amd64 32.3.1~22.04 [20.3 kB]
Get:26 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 ubuntu-pro-client amd64 32.3.1~22.04 [209 kB]
Get:27 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 ubuntu-advantage-tools all 32.3.1~22.04 [10.9 kB]
Get:28 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim amd64 2:8.2.3995-1ubuntu2.17 [1734 kB]
Get:29 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim-tiny amd64 2:8.2.3995-1ubuntu2.17 [709 kB]
Get:30 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim-runtime all 2:8.2.3995-1ubuntu2.17 [6827 kB]
Get:31 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 xxd amd64 2:8.2.3995-1ubuntu2.17 [53.7 kB]
Get:32 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim-common all 2:8.2.3995-1ubuntu2.17 [81.5 kB]
Get:33 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnghttp2-14 amd64 1.43.0-1ubuntu0.2 [76.9 kB]
Get:34 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 bind9-host amd64 1:9.18.24-0ubuntu0.22.04.1 [52.5 kB]
Get:35 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 bind9-dnsutils amd64 1:9.18.24-0ubuntu0.22.04.1 [157 kB]
Get:36 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 bind9-libs amd64 1:9.18.24-0ubuntu0.22.04.1 [1247 kB]
Get:37 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 bsdextrautils amd64 2.37.2-4ubuntu3.4 [71.4 kB]
Get:38 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpio amd64 2.13+dfsg-7ubuntu0.1 [84.5 kB]
Get:39 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 wget amd64 1.21.2-2ubuntu1.1 [339 kB]
Get:40 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libfdisk1 amd64 2.37.2-4ubuntu3.4 [140 kB]
Get:41 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 fdisk amd64 2.37.2-4ubuntu3.4 [122 kB]
Get:42 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.11 [955 kB]
Get:43 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.11 [3165 kB]
Get:44 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 klibc-utils amd64 2.0.10-4ubuntu0.1 [99.9 kB]
Get:45 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libklibc amd64 2.0.10-4ubuntu0.1 [46.0 kB]
Get:46 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 landscape-common amd64 23.02-0ubuntu1~22.04.2 [88.7 kB]
Get:47 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libarchive13 amd64 3.6.0-1ubuntu1.1 [369 kB]
Get:48 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnspr4 amd64 2:4.35-0ubuntu0.22.04.1 [119 kB]
Get:49 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnss3 amd64 2:3.98-0ubuntu0.22.04.2 [1347 kB]
Get:50 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtss2-mu0 amd64 3.2.0-1ubuntu1.1 [65.6 kB]
Get:51 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtss2-tcti-cmd0 amd64 3.2.0-1ubuntu1.1 [16.7 kB]
Get:52 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtss2-tcti-device0 amd64 3.2.0-1ubuntu1.1 [15.3 kB]
Get:53 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtss2-tcti-mssim0 amd64 3.2.0-1ubuntu1.1 [15.4 kB]
Get:54 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtss2-tcti-swtpm0 amd64 3.2.0-1ubuntu1.1 [15.4 kB]
Get:55 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtss2-sys1 amd64 3.2.0-1ubuntu1.1 [41.0 kB]
Get:56 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtss2-esys-3.0.2-0 amd64 3.2.0-1ubuntu1.1 [150 kB]
Get:57 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-5.15.0-113 all 5.15.0-113.123 [12.3 MB]
Get:58 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-5.15.0-113-generic amd64 5.15.0-113.123 [2895 kB]
Get:59 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-modules-5.15.0-113-generic amd64 5.15.0-113.123 [22.6 MB]
Get:60 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-image-5.15.0-113-generic amd64 5.15.0-113.123 [11.5 MB]
Get:61 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-virtual amd64 5.15.0.113.113 [1672 B]                                                                                                       
Get:62 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-image-virtual amd64 5.15.0.113.113 [2436 B]                                                                                                 
Get:63 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-virtual amd64 5.15.0.113.113 [1632 B]                                                                                               
Get:64 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-generic amd64 5.15.0.113.113 [2346 B]                                                                                               
Get:65 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 python3-idna all 3.3-1ubuntu0.1 [52.1 kB]                                                                                                         
Get:66 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 python3-jinja2 all 3.0.3-1ubuntu0.2 [108 kB]                                                                                                      
Get:67 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 snapd amd64 2.63+22.04 [25.9 MB]                                                                                                                  
Get:68 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 cloud-init all 24.1.3-0ubuntu1~22.04.5 [560 kB]                                                                                                   
Fetched 108 MB in 8s (13.6 MB/s)                                                                                                                                                                                   
Extracting templates from packages: 100%
Preconfiguring packages ...
tzdata failed to preconfigure, with exit status 10
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../bsdutils_1%3a2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking bsdutils (1:2.37.2-4ubuntu3.4) over (1:2.37.2-4ubuntu3.3) ...
Setting up bsdutils (1:2.37.2-4ubuntu3.4) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../util-linux_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking util-linux (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Setting up util-linux (2.37.2-4ubuntu3.4) ...
fstrim.service is a disabled or a static unit not running, not starting it.
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../libc-bin_2.35-0ubuntu3.8_amd64.deb ...
Unpacking libc-bin (2.35-0ubuntu3.8) over (2.35-0ubuntu3.6) ...
Setting up libc-bin (2.35-0ubuntu3.8) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../mount_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking mount (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Preparing to unpack .../libsmartcols1_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking libsmartcols1:amd64 (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Setting up libsmartcols1:amd64 (2.37.2-4ubuntu3.4) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../libuuid1_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking libuuid1:amd64 (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Setting up libuuid1:amd64 (2.37.2-4ubuntu3.4) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../uuid-runtime_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking uuid-runtime (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Preparing to unpack .../libblkid1_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking libblkid1:amd64 (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Setting up libblkid1:amd64 (2.37.2-4ubuntu3.4) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../libmount1_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking libmount1:amd64 (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Setting up libmount1:amd64 (2.37.2-4ubuntu3.4) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../libssl3_3.0.2-0ubuntu1.16_amd64.deb ...
Unpacking libssl3:amd64 (3.0.2-0ubuntu1.16) over (3.0.2-0ubuntu1.15) ...
Setting up libssl3:amd64 (3.0.2-0ubuntu1.16) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../libgnutls30_3.7.3-4ubuntu1.5_amd64.deb ...
Unpacking libgnutls30:amd64 (3.7.3-4ubuntu1.5) over (3.7.3-4ubuntu1.4) ...
Setting up libgnutls30:amd64 (3.7.3-4ubuntu1.5) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../libpcre2-8-0_10.42-3+ubuntu22.04.1+deb.sury.org+1_amd64.deb ...
Unpacking libpcre2-8-0:amd64 (10.42-3+ubuntu22.04.1+deb.sury.org+1) over (10.39-3ubuntu0.1) ...
Setting up libpcre2-8-0:amd64 (10.42-3+ubuntu22.04.1+deb.sury.org+1) ...
(Reading database ... 127474 files and directories currently installed.)
Preparing to unpack .../00-distro-info-data_0.52ubuntu0.7_all.deb ...
Unpacking distro-info-data (0.52ubuntu0.7) over (0.52ubuntu0.6) ...
Preparing to unpack .../01-eject_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking eject (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Preparing to unpack .../02-less_590-1ubuntu0.22.04.3_amd64.deb ...
Unpacking less (590-1ubuntu0.22.04.3) over (590-1ubuntu0.22.04.2) ...
Preparing to unpack .../03-libglib2.0-data_2.72.4-0ubuntu2.3_all.deb ...
Unpacking libglib2.0-data (2.72.4-0ubuntu2.3) over (2.72.4-0ubuntu2.2) ...
Preparing to unpack .../04-libglib2.0-bin_2.72.4-0ubuntu2.3_amd64.deb ...
Unpacking libglib2.0-bin (2.72.4-0ubuntu2.3) over (2.72.4-0ubuntu2.2) ...
Preparing to unpack .../05-libglib2.0-0_2.72.4-0ubuntu2.3_amd64.deb ...
Unpacking libglib2.0-0:amd64 (2.72.4-0ubuntu2.3) over (2.72.4-0ubuntu2.2) ...
Preparing to unpack .../06-netplan.io_0.106.1-7ubuntu0.22.04.4_amd64.deb ...
Unpacking netplan.io (0.106.1-7ubuntu0.22.04.4) over (0.106.1-7ubuntu0.22.04.2) ...
Preparing to unpack .../07-libnetplan0_0.106.1-7ubuntu0.22.04.4_amd64.deb ...
Unpacking libnetplan0:amd64 (0.106.1-7ubuntu0.22.04.4) over (0.106.1-7ubuntu0.22.04.2) ...
Preparing to unpack .../08-locales_2.35-0ubuntu3.8_all.deb ...
Unpacking locales (2.35-0ubuntu3.8) over (2.35-0ubuntu3.6) ...
Preparing to unpack .../09-openssl_3.0.2-0ubuntu1.16_amd64.deb ...
Unpacking openssl (3.0.2-0ubuntu1.16) over (3.0.2-0ubuntu1.15) ...
Preparing to unpack .../10-tzdata_2024a-0ubuntu0.22.04.1_all.deb ...
Unpacking tzdata (2024a-0ubuntu0.22.04.1) over (2024a-0ubuntu0.22.04) ...
Preparing to unpack .../11-ubuntu-pro-client-l10n_32.3.1~22.04_amd64.deb ...
Unpacking ubuntu-pro-client-l10n (32.3.1~22.04) over (31.2~22.04) ...
Preparing to unpack .../12-ubuntu-pro-client_32.3.1~22.04_amd64.deb ...
Unpacking ubuntu-pro-client (32.3.1~22.04) over (31.2~22.04) ...
Preparing to unpack .../13-ubuntu-advantage-tools_32.3.1~22.04_all.deb ...
Unpacking ubuntu-advantage-tools (32.3.1~22.04) over (31.2~22.04) ...
Preparing to unpack .../14-vim_2%3a8.2.3995-1ubuntu2.17_amd64.deb ...
Unpacking vim (2:8.2.3995-1ubuntu2.17) over (2:8.2.3995-1ubuntu2.16) ...
Preparing to unpack .../15-vim-tiny_2%3a8.2.3995-1ubuntu2.17_amd64.deb ...
Unpacking vim-tiny (2:8.2.3995-1ubuntu2.17) over (2:8.2.3995-1ubuntu2.16) ...
Preparing to unpack .../16-vim-runtime_2%3a8.2.3995-1ubuntu2.17_all.deb ...
Unpacking vim-runtime (2:8.2.3995-1ubuntu2.17) over (2:8.2.3995-1ubuntu2.16) ...
Preparing to unpack .../17-xxd_2%3a8.2.3995-1ubuntu2.17_amd64.deb ...
Unpacking xxd (2:8.2.3995-1ubuntu2.17) over (2:8.2.3995-1ubuntu2.16) ...
Preparing to unpack .../18-vim-common_2%3a8.2.3995-1ubuntu2.17_all.deb ...
Unpacking vim-common (2:8.2.3995-1ubuntu2.17) over (2:8.2.3995-1ubuntu2.16) ...
Preparing to unpack .../19-libnghttp2-14_1.43.0-1ubuntu0.2_amd64.deb ...
Unpacking libnghttp2-14:amd64 (1.43.0-1ubuntu0.2) over (1.43.0-1ubuntu0.1) ...
Preparing to unpack .../20-libxml2_2.9.14+dfsg-0.1+ubuntu22.04.1+deb.sury.org+1_amd64.deb ...
Unpacking libxml2:amd64 (2.9.14+dfsg-0.1+ubuntu22.04.1+deb.sury.org+1) over (2.9.13+dfsg-1ubuntu0.4) ...
Preparing to unpack .../21-bind9-host_1%3a9.18.24-0ubuntu0.22.04.1_amd64.deb ...
Unpacking bind9-host (1:9.18.24-0ubuntu0.22.04.1) over (1:9.18.18-0ubuntu0.22.04.2) ...
Preparing to unpack .../22-bind9-dnsutils_1%3a9.18.24-0ubuntu0.22.04.1_amd64.deb ...
Unpacking bind9-dnsutils (1:9.18.24-0ubuntu0.22.04.1) over (1:9.18.18-0ubuntu0.22.04.2) ...
Preparing to unpack .../23-bind9-libs_1%3a9.18.24-0ubuntu0.22.04.1_amd64.deb ...
Unpacking bind9-libs:amd64 (1:9.18.24-0ubuntu0.22.04.1) over (1:9.18.18-0ubuntu0.22.04.2) ...
Preparing to unpack .../24-bsdextrautils_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking bsdextrautils (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Preparing to unpack .../25-cpio_2.13+dfsg-7ubuntu0.1_amd64.deb ...
Unpacking cpio (2.13+dfsg-7ubuntu0.1) over (2.13+dfsg-7) ...
Preparing to unpack .../26-wget_1.21.2-2ubuntu1.1_amd64.deb ...
Unpacking wget (1.21.2-2ubuntu1.1) over (1.21.2-2ubuntu1) ...
Preparing to unpack .../27-libfdisk1_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking libfdisk1:amd64 (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Preparing to unpack .../28-fdisk_2.37.2-4ubuntu3.4_amd64.deb ...
Unpacking fdisk (2.37.2-4ubuntu3.4) over (2.37.2-4ubuntu3.3) ...
Preparing to unpack .../29-git-man_1%3a2.34.1-1ubuntu1.11_all.deb ...
Unpacking git-man (1:2.34.1-1ubuntu1.11) over (1:2.34.1-1ubuntu1.10) ...
Preparing to unpack .../30-git_1%3a2.34.1-1ubuntu1.11_amd64.deb ...
Unpacking git (1:2.34.1-1ubuntu1.11) over (1:2.34.1-1ubuntu1.10) ...
Preparing to unpack .../31-klibc-utils_2.0.10-4ubuntu0.1_amd64.deb ...
Unpacking klibc-utils (2.0.10-4ubuntu0.1) over (2.0.10-4) ...
Preparing to unpack .../32-libklibc_2.0.10-4ubuntu0.1_amd64.deb ...
Unpacking libklibc:amd64 (2.0.10-4ubuntu0.1) over (2.0.10-4) ...
Preparing to unpack .../33-landscape-common_23.02-0ubuntu1~22.04.2_amd64.deb ...
Unpacking landscape-common (23.02-0ubuntu1~22.04.2) over (19.12-0ubuntu13) ...
Preparing to unpack .../34-libarchive13_3.6.0-1ubuntu1.1_amd64.deb ...
Unpacking libarchive13:amd64 (3.6.0-1ubuntu1.1) over (3.6.0-1ubuntu1) ...
Preparing to unpack .../35-libnspr4_2%3a4.35-0ubuntu0.22.04.1_amd64.deb ...
Unpacking libnspr4:amd64 (2:4.35-0ubuntu0.22.04.1) over (2:4.32-3build1) ...
Preparing to unpack .../36-libnss3_2%3a3.98-0ubuntu0.22.04.2_amd64.deb ...
Unpacking libnss3:amd64 (2:3.98-0ubuntu0.22.04.2) over (2:3.68.2-0ubuntu1.2) ...
Preparing to unpack .../37-libtss2-mu0_3.2.0-1ubuntu1.1_amd64.deb ...
Unpacking libtss2-mu0:amd64 (3.2.0-1ubuntu1.1) over (3.2.0-1ubuntu1) ...
Preparing to unpack .../38-libtss2-tcti-cmd0_3.2.0-1ubuntu1.1_amd64.deb ...
Unpacking libtss2-tcti-cmd0:amd64 (3.2.0-1ubuntu1.1) over (3.2.0-1ubuntu1) ...
Preparing to unpack .../39-libtss2-tcti-device0_3.2.0-1ubuntu1.1_amd64.deb ...
Unpacking libtss2-tcti-device0:amd64 (3.2.0-1ubuntu1.1) over (3.2.0-1ubuntu1) ...
Preparing to unpack .../40-libtss2-tcti-mssim0_3.2.0-1ubuntu1.1_amd64.deb ...
Unpacking libtss2-tcti-mssim0:amd64 (3.2.0-1ubuntu1.1) over (3.2.0-1ubuntu1) ...
Preparing to unpack .../41-libtss2-tcti-swtpm0_3.2.0-1ubuntu1.1_amd64.deb ...
Unpacking libtss2-tcti-swtpm0:amd64 (3.2.0-1ubuntu1.1) over (3.2.0-1ubuntu1) ...
Preparing to unpack .../42-libtss2-sys1_3.2.0-1ubuntu1.1_amd64.deb ...
Unpacking libtss2-sys1:amd64 (3.2.0-1ubuntu1.1) over (3.2.0-1ubuntu1) ...
Preparing to unpack .../43-libtss2-esys-3.0.2-0_3.2.0-1ubuntu1.1_amd64.deb ...
Unpacking libtss2-esys-3.0.2-0:amd64 (3.2.0-1ubuntu1.1) over (3.2.0-1ubuntu1) ...
Selecting previously unselected package linux-headers-5.15.0-113.
Preparing to unpack .../44-linux-headers-5.15.0-113_5.15.0-113.123_all.deb ...
Unpacking linux-headers-5.15.0-113 (5.15.0-113.123) ...
Selecting previously unselected package linux-headers-5.15.0-113-generic.
Preparing to unpack .../45-linux-headers-5.15.0-113-generic_5.15.0-113.123_amd64.deb ...
Unpacking linux-headers-5.15.0-113-generic (5.15.0-113.123) ...
Selecting previously unselected package linux-modules-5.15.0-113-generic.
Preparing to unpack .../46-linux-modules-5.15.0-113-generic_5.15.0-113.123_amd64.deb ...
Unpacking linux-modules-5.15.0-113-generic (5.15.0-113.123) ...
Selecting previously unselected package linux-image-5.15.0-113-generic.
Preparing to unpack .../47-linux-image-5.15.0-113-generic_5.15.0-113.123_amd64.deb ...
Unpacking linux-image-5.15.0-113-generic (5.15.0-113.123) ...
Preparing to unpack .../48-linux-virtual_5.15.0.113.113_amd64.deb ...
Unpacking linux-virtual (5.15.0.113.113) over (5.15.0.101.98) ...
Preparing to unpack .../49-linux-image-virtual_5.15.0.113.113_amd64.deb ...
Unpacking linux-image-virtual (5.15.0.113.113) over (5.15.0.101.98) ...
Preparing to unpack .../50-linux-headers-virtual_5.15.0.113.113_amd64.deb ...
Unpacking linux-headers-virtual (5.15.0.113.113) over (5.15.0.101.98) ...
Preparing to unpack .../51-linux-headers-generic_5.15.0.113.113_amd64.deb ...
Unpacking linux-headers-generic (5.15.0.113.113) over (5.15.0.101.98) ...
Preparing to unpack .../52-python3-idna_3.3-1ubuntu0.1_all.deb ...
Unpacking python3-idna (3.3-1ubuntu0.1) over (3.3-1) ...
Preparing to unpack .../53-python3-jinja2_3.0.3-1ubuntu0.2_all.deb ...
Unpacking python3-jinja2 (3.0.3-1ubuntu0.2) over (3.0.3-1ubuntu0.1) ...
Preparing to unpack .../54-snapd_2.63+22.04_amd64.deb ...
Unpacking snapd (2.63+22.04) over (2.61.3+22.04) ...
Preparing to unpack .../55-cloud-init_24.1.3-0ubuntu1~22.04.5_all.deb ...
Unpacking cloud-init (24.1.3-0ubuntu1~22.04.5) over (23.4.4-0ubuntu0~22.04.1) ...
Setting up cpio (2.13+dfsg-7ubuntu0.1) ...
Setting up snapd (2.63+22.04) ...
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ...
snapd.failure.service is a disabled or a static unit not running, not starting it.
snapd.snap-repair.service is a disabled or a static unit not running, not starting it.
Failed to restart snapd.mounts-pre.target: Operation refused, unit snapd.mounts-pre.target may be requested by dependency only (it is configured to refuse manual start/stop).
See system logs and 'systemctl status snapd.mounts-pre.target' for details.
Could not execute systemctl:  at /usr/bin/deb-systemd-invoke line 142.
Setting up bsdextrautils (2.37.2-4ubuntu3.4) ...
Setting up linux-headers-5.15.0-113 (5.15.0-113.123) ...
Setting up wget (1.21.2-2ubuntu1.1) ...
Setting up libglib2.0-0:amd64 (2.72.4-0ubuntu2.3) ...
Setting up distro-info-data (0.52ubuntu0.7) ...
Setting up libtss2-mu0:amd64 (3.2.0-1ubuntu1.1) ...
Setting up libtss2-tcti-swtpm0:amd64 (3.2.0-1ubuntu1.1) ...
Setting up libnghttp2-14:amd64 (1.43.0-1ubuntu0.2) ...
Setting up less (590-1ubuntu0.22.04.3) ...
Setting up libnetplan0:amd64 (0.106.1-7ubuntu0.22.04.4) ...
Setting up locales (2.35-0ubuntu3.8) ...
Generating locales (this might take a while)...
error: Bad entry 'en_IE '
  en_IE.ISO-8859-1... done
  en_IE.UTF-8... done
error: Bad entry 'es_ES '
  es_ES.ISO-8859-1... done
  es_ES.UTF-8... done
error: Bad entry 'sv_SE '
  sv_SE.ISO-8859-1... done
  sv_SE.UTF-8... done
Generation complete.
Setting up landscape-common (23.02-0ubuntu1~22.04.2) ...
Setting up xxd (2:8.2.3995-1ubuntu2.17) ...
Setting up libtss2-tcti-device0:amd64 (3.2.0-1ubuntu1.1) ...
Setting up netplan.io (0.106.1-7ubuntu0.22.04.4) ...
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 10
Setting up eject (2.37.2-4ubuntu3.4) ...
Setting up libklibc:amd64 (2.0.10-4ubuntu0.1) ...
Setting up python3-jinja2 (3.0.3-1ubuntu0.2) ...
Setting up libtss2-tcti-cmd0:amd64 (3.2.0-1ubuntu1.1) ...
Setting up libglib2.0-data (2.72.4-0ubuntu2.3) ...
Setting up vim-common (2:8.2.3995-1ubuntu2.17) ...
Setting up libnspr4:amd64 (2:4.35-0ubuntu0.22.04.1) ...
Setting up python3-idna (3.3-1ubuntu0.1) ...
Setting up libtss2-tcti-mssim0:amd64 (3.2.0-1ubuntu1.1) ...
Setting up libfdisk1:amd64 (2.37.2-4ubuntu3.4) ...
Setting up mount (2.37.2-4ubuntu3.4) ...
Setting up uuid-runtime (2.37.2-4ubuntu3.4) ...
uuidd.service is a disabled or a static unit not running, not starting it.
Setting up git-man (1:2.34.1-1ubuntu1.11) ...
Setting up linux-headers-5.15.0-113-generic (5.15.0-113.123) ...
Setting up vim-runtime (2:8.2.3995-1ubuntu2.17) ...
Setting up klibc-utils (2.0.10-4ubuntu0.1) ...
Setting up openssl (3.0.2-0ubuntu1.16) ...
Setting up libxml2:amd64 (2.9.14+dfsg-0.1+ubuntu22.04.1+deb.sury.org+1) ...
Setting up ubuntu-pro-client (32.3.1~22.04) ...
Installing new version of config file /etc/apparmor.d/ubuntu_pro_apt_news ...
Setting up ubuntu-pro-client-l10n (32.3.1~22.04) ...
Setting up cloud-init (24.1.3-0ubuntu1~22.04.5) ...
Installing new version of config file /etc/cloud/cloud.cfg ...
Installing new version of config file /etc/cloud/cloud.cfg.d/05_logging.cfg ...
Installing new version of config file /etc/cloud/templates/chrony.conf.cos.tmpl ...
Installing new version of config file /etc/cloud/templates/chrony.conf.debian.tmpl ...
Installing new version of config file /etc/cloud/templates/chrony.conf.ubuntu.tmpl ...
Installing new version of config file /etc/cloud/templates/hosts.alpine.tmpl ...
Installing new version of config file /etc/cloud/templates/hosts.mariner.tmpl ...
Installing new version of config file /etc/cloud/templates/ntp.conf.ubuntu.tmpl ...
Installing new version of config file /etc/cloud/templates/sources.list.ubuntu.deb822.tmpl ...
Installing new version of config file /etc/profile.d/Z99-cloud-locale-test.sh ...
Removing obsolete conffile /etc/cloud/clean.d/README ...
Setting up vim (2:8.2.3995-1ubuntu2.17) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/vim.basic because link group vim is broken
Setting up libtss2-sys1:amd64 (3.2.0-1ubuntu1.1) ...
Setting up bind9-libs:amd64 (1:9.18.24-0ubuntu0.22.04.1) ...
Setting up libarchive13:amd64 (3.6.0-1ubuntu1.1) ...
Setting up libglib2.0-bin (2.72.4-0ubuntu2.3) ...
Setting up libnss3:amd64 (2:3.98-0ubuntu0.22.04.2) ...
Setting up linux-headers-generic (5.15.0.113.113) ...
Setting up vim-tiny (2:8.2.3995-1ubuntu2.17) ...
Setting up fdisk (2.37.2-4ubuntu3.4) ...
Setting up libtss2-esys-3.0.2-0:amd64 (3.2.0-1ubuntu1.1) ...
Setting up git (1:2.34.1-1ubuntu1.11) ...
Setting up ubuntu-advantage-tools (32.3.1~22.04) ...
Setting up bind9-host (1:9.18.24-0ubuntu0.22.04.1) ...
Setting up linux-headers-virtual (5.15.0.113.113) ...
Setting up bind9-dnsutils (1:9.18.24-0ubuntu0.22.04.1) ...
Setting up linux-image-5.15.0-113-generic (5.15.0-113.123) ...
I: /boot/vmlinuz is now a symlink to vmlinuz-5.15.0-113-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.15.0-113-generic
Setting up linux-image-virtual (5.15.0.113.113) ...
Setting up linux-modules-5.15.0-113-generic (5.15.0-113.123) ...
Setting up linux-virtual (5.15.0.113.113) ...
dpkg: dependency problems prevent processing triggers for ntp:
 ntp depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package ntp (--configure):
 dependency problems - leaving triggers unprocessed
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for install-info (6.8-4build1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-101-generic
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
Processing triggers for rsyslog (8.2112.0-2ubuntu2.2) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for linux-image-5.15.0-113-generic (5.15.0-113.123) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-113-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50-cloudimg-settings.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-113-generic
Found initrd image: /boot/initrd.img-5.15.0-113-generic
Found linux image: /boot/vmlinuz-5.15.0-101-generic
Found initrd image: /boot/initrd.img-5.15.0-101-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
Errors were encountered while processing:
 tzdata
 ntp
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Excerpt of relevant(?) errors from above output:
```

...
Setting up locales (2.35-0ubuntu3.8) ...
Generating locales (this might take a while)...
error: Bad entry 'en_IE '
  en_IE.ISO-8859-1... done
  en_IE.UTF-8... done
error: Bad entry 'es_ES '
  es_ES.ISO-8859-1... done
  es_ES.UTF-8... done
error: Bad entry 'sv_SE '
  sv_SE.ISO-8859-1... done
  sv_SE.UTF-8... done
Generation complete.
...
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 10
...
Setting up linux-virtual (5.15.0.113.113) ...
dpkg: dependency problems prevent processing triggers for ntp:
 ntp depends on tzdata; however:
  Package tzdata is not configured yet.

dpkg: error processing package ntp (--configure):
 dependency problems - leaving triggers unprocessed
...
Errors were encountered while processing:
 tzdata
 ntp
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

After that, I tried a much more minimalistic Puppet profile that installs less packages, and the same thing happened there.

Bug with the new tzdata package?

---

### Post by TheFu on 2024-07-09
I only have a few 22.04 systems. None of them has had this issue.  

My main systems are still on 20.04 Server, but will be moving to either Debian12 or 22.04 before the end of the year.  I doubt I'll go to 24.04. That's too new for me and the desktop versions don't support LVM installs, so I'm not interested.  Moved my desktop to Mint a little over a year ago to avoid snaps. That has worked well enough.  Of course, there's a huge difference in managing a few desktops and managing 20-2000 servers.

Have you considered NOT using puppet to see if that's the root cause of the tzdata issue?

If the README file is part of the package and it has been removed, that will make the package manager think it is broken.  Create a file in the place it thinks it should be and force a reinstall.  My notes for timezone data say:
```
# set the server timezone
$ echo "America/New_York" | sudo tee /etc/timezone
$ sudo timedatectl set-timezone "America/New_York"
```
You can look up the text timezone for your needs, if needed.

---

### Post by mdarstedt on 2024-07-09
> **TheFu said:**
> I only have a few 22.04 systems. None of them has had this issue.  

My main systems are still on 20.04 Server, but will be moving to either Debian12 or 22.04 before the end of the year.  I doubt I'll go to 24.04. That's too new for me and the desktop versions don't support LVM installs, so I'm not interested.  Moved my desktop to Mint a little over a year ago to avoid snaps. That has worked well enough.  Of course, there's a huge difference in managing a few desktops and managing 20-2000 servers.

Have you considered NOT using puppet to see if that's the root cause of the tzdata issue?

If the README file is part of the package and it has been removed, that will make the package manager think it is broken.  Create a file in the place it thinks it should be and force a reinstall.  My notes for timezone data say:
```
# set the server timezone
$ echo "America/New_York" | sudo tee /etc/timezone
$ sudo timedatectl set-timezone "America/New_York"
```
You can look up the text timezone for your needs, if needed.

Actually, the /etc/timezone file was the issue. Our (in some parts ancient) puppet code inserted **CET** into this file. I would assume that this format is now completely deprecated in the tzdata package, and that's why it failed. Once I ran **timedatectl set-timezone Europe/Stockholm** everything went through.

---

### Post by deadflowr on 2024-07-09
You can mark it as solved this way:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by TheFu on 2024-07-09
> **mdarstedt said:**
> Actually, the /etc/timezone file was the issue. Our (in some parts ancient) puppet code inserted **CET** into this file. I would assume that this format is now completely deprecated in the tzdata package, and that's why it failed. Once I ran **timedatectl set-timezone Europe/Stockholm** everything went through.

I didn't know they deprecated using timezone abbreviations.  Perhaps they just changed. I know EST5EDT is what I have to use now, if not NYC.  /usr/share/zoneinfo/ has the choices.  I remember it was easier before the city-centric stuff happened.

It is always the dumb things that get changed that screw us.  I vaguely remember when they switched from timezones to cities-inside-the-timezone. Guess they were trying to be more user friendly.  BTW, my servers aren't anywhere near NYC, but they are in the same timezone.

Was this just a puppet problem or where these systems upgraded since 16.04?   Any fresh installs wouldn't have this issue, unless puppet wasn't using the correct method to set the timezone.

After I attended puppet training, I decided that puppet was worse than the problem it was supposed to solve.  As an old admin, we just wrote our own scripts to manage systems.  That meant that new people had to learn our scripts. That's why the main DevOPS tools are popular.  Expertise in the problems that each tool brings with it.  ;)

Ever notice how we don't hear "code as infrastructure" marketing any more?

---

### Post by mdarstedt on 2024-07-10
> **TheFu said:**
> I didn't know they deprecated using timezone abbreviations.  Perhaps they just changed. I know EST5EDT is what I have to use now, if not NYC.  /usr/share/zoneinfo/ has the choices.  I remember it was easier before the city-centric stuff happened.

It is always the dumb things that get changed that screw us.  I vaguely remember when they switched from timezones to cities-inside-the-timezone. Guess they were trying to be more user friendly.  BTW, my servers aren't anywhere near NYC, but they are in the same timezone.

Was this just a puppet problem or where these systems upgraded since 16.04?   Any fresh installs wouldn't have this issue, unless puppet wasn't using the correct method to set the timezone.

Yeah, I don't know what this is about to be honest, because according to timedatectl, [FONT=courier new]CET[/FONT] is a valid value:
```
vagrant@tztest:~$ timedatectl list-timezones |grep CET
CET
```

 I noticed the difference when I booted up a Vagrant machine without applying the puppet code. It then sets the timezone to:
```
vagrant@tztest:~$ cat /etc/timezone 
Etc/UTC
```

Running an upgrade with this worked just fine. What our puppet code does, is to set it to CET through a hiera value ([FONT=courier new]timezone::timezone: 'CET'[/FONT]) that I found when digging. As I mentioned, I used an older Vagrant box file (20240403.0.0) in order to be sure that I had the old version of the tzdata package so that I could simulate an upgrade:
```
vagrant@tztest:~$ dpkg -l tzdata
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version              Architecture Description
+++-==============-====================-============-=======================================
ii  tzdata         2024a-0ubuntu0.22.04 all          time zone and daylight-saving time data
```

Now, after the upgrade, if I keep the [FONT=courier new]Etc/UTC[/FONT] value and re-install the updated version of the package, everything works fine:
```
vagrant@tztest:~$ dpkg -l tzdata
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version                Architecture Description
+++-==============-======================-============-=======================================
ii  tzdata         2024a-0ubuntu0.22.04.1 all          time zone and daylight-saving time data

vagrant@tztest:~$ sudo apt reinstall tzdata
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 5 not upgraded.
Need to get 349 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 tzdata all 2024a-0ubuntu0.22.04.1 [349 kB]
Fetched 349 kB in 0s (1417 kB/s)
Preconfiguring packages ...
(Reading database ... 93621 files and directories currently installed.)
Preparing to unpack .../tzdata_2024a-0ubuntu0.22.04.1_all.deb ...
Unpacking tzdata (2024a-0ubuntu0.22.04.1) over (2024a-0ubuntu0.22.04.1) ...
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...

Current default time zone: 'Etc/UTC'
Local time is now:      Wed Jul 10 05:23:43 UTC 2024.
Universal Time is now:  Wed Jul 10 05:23:43 UTC 2024.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

Scanning processes...                                                                                                                                                                                               
Scanning linux images...                                                                                                                                                                                            

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
```

But, if I change the timezone to [FONT=courier new]CET[/FONT] and attempt to re-install the package, it breaks:
```
vagrant@tztest:~$ sudo timedatectl set-timezone CET

vagrant@tztest:~$ cat /etc/timezone 
CET

vagrant@tztest:~$ sudo apt reinstall tzdata
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 5 not upgraded.
Need to get 349 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 tzdata all 2024a-0ubuntu0.22.04.1 [349 kB]
Fetched 349 kB in 0s (1794 kB/s)
Preconfiguring packages ...
tzdata failed to preconfigure, with exit status 10
(Reading database ... 93621 files and directories currently installed.)
Preparing to unpack .../tzdata_2024a-0ubuntu0.22.04.1_all.deb ...
Unpacking tzdata (2024a-0ubuntu0.22.04.1) over (2024a-0ubuntu0.22.04.1) ...
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...
dpkg: error processing package tzdata (--configure):
 installed tzdata package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 tzdata
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And if I now set it to [FONT=courier new]Europe/Stockholm [/FONT]and run configure on it, it goes through without issues:
```
vagrant@tztest:~$ sudo timedatectl set-timezone "Europe/Stockholm"

vagrant@tztest:~$ sudo dpkg --configure -a
Setting up tzdata (2024a-0ubuntu0.22.04.1) ...

Current default time zone: 'Europe/Stockholm'
Local time is now:      Wed Jul 10 07:30:54 CEST 2024.
Universal Time is now:  Wed Jul 10 05:30:54 UTC 2024.
Run 'dpkg-reconfigure tzdata' if you wish to change it.
```

---

### Post by TheFu on 2024-07-10
Interesting.  I have a fetish about computer time and timezones.  Can't explain it.  Since all our systems actually use UTC internally, and use the TZ variable just for humans to be convenient, maybe for your servers, it would be a good idea to set them all the UTC to avoid the next wild-hair that happens?  
Of course, every user/daemon can have their own TZ environment variable set which should be honored for all display of local times.  OTOH, that's just pushing the issue to the users instead of handling it server-wide.

Anyway, did all the other packages install/update now?  I see the thread is SOLVED, but ....

---

### Post by mdarstedt on 2024-07-10
Yeah, everything went through. So I just went and changed the puppet hiera parameter to [FONT=courier new]timezone::timezone: 'Europe/Stockholm' [/FONT]and allowed it to propagate to all our hosts. After that, I had no issues upgrading the [FONT=courier new]tzdata[/FONT] package on the rest of our 22.04 machines. All is good now.

Thanks for sticking with me through this. It was actually a bit of a funny coincident, just after I had started playing with the timezone stuff myself in vagrant, and found the solution, I came back to write about it, and noticed you had suggested the same thing in your edit of [post 7]("https://ubuntuforums.org/showthread.php?t=2499039&p=14196853#post14196853"). :)

---

