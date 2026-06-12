---
title: "unattended updates not working?"
date: 2017-06-02
forum: General Help
---

### Post by ardouronerous on 2017-06-02
The unattended-upgrades package is installed on Xubuntu 16.04 by default, but I'm getting prompts from Software Updater. Is that normal? Because I thought unattended-upgrades is suppose to install software silently in the background.

How do I activate unattended-upgrades?

---

### Post by deadflowr on 2017-06-02
If you have the default set then only security updates would get installed unattended.

You can edit the file in /etc/apt/apt.conf.d/50unattended-upgrades to add or subtract any archive you wish.
Just add or remove the // from the front of the lines. The // means do not read this line so removing them makes the system read that line.

You can also add extra repositories that are not listed such as ppas.
To do so you need to list the origin  and the archive.
You can find them in the release files located in the /var/lib/apt/lists folder.
You take the origin and the codename (codename=archive in this case).
They must be exact.
And they must be encapsulated in quotes like "origin:archive"; and then end the line with a semi-colon.

You can add or subtract as many repos as you want as long as they are added to the section : Unattended-Upgrade::Allowed-Origins
and place in between the two {brackets}, like all the other listed repos.

hope it makes some bit of sense.

---

### Post by ardouronerous on 2017-06-02
On PPAs, I'd rather be informed of updates for that because they aren't officially supported by Ubuntu's repos, but when it comes to support software from the repos such as Firefox and such, I'd like that to be automatically updated.

```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}";
    "${distro_id}:${distro_codename}-security";
    // Extended Security Maintenance; doesn't necessarily exist for
    // every release and this system may not have it installed, but if
    // available, the policy for updates is such that unattended-upgrades
    // should also install from here by default.
    "${distro_id}ESM:${distro_codename}";
    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";
};
```

This is what I've done to * /etc/apt/apt.conf.d/50unattended-upgrades*, I've removed the // from [I]"${distro_id}:${distro_codename}-updates";
[/I]
Is this okay?

[ATTACH=CONFIG]275503[/ATTACH]

I'm still getting security update prompts despite the fact that unattended updates is installed.

*/var/log/unattended-upgrades/unattended-upgrades.log *is blank, there's nothing inside the log.

---

### Post by deadflowr on 2017-06-06
What does it show when you run
```
sudo unattended-upgrades -d
```

---

### Post by ardouronerous on 2017-06-07
```
~$ sudo unattended-upgrades -d
Initial blacklisted packages: 
Initial whitelisted packages: 
Starting unattended upgrades script
Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=UbuntuESM,a=xenial', 'o=Ubuntu,a=xenial-updates']
Checking: libnl-3-200 ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: libnl-genl-3-200 ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: libnl-route-3-200 ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: lintian ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-generic ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-headers-generic ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-image-generic ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-libc-dev ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
pkgs that look like they should be upgraded: libnl-3-200
libnl-genl-3-200
libnl-route-3-200
lintian
linux-generic
linux-headers-generic
linux-image-generic
linux-libc-dev
Get:1 http://security.ubuntu.com/ubuntu xenial-security/main i386 libnl-route-3-200 i386 3.2.27-1ubuntu0.16.04.1 [132 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security/main i386 libnl-genl-3-200 i386 3.2.27-1ubuntu0.16.04.1 [12.0 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security/main i386 libnl-3-200 i386 3.2.27-1ubuntu0.16.04.1 [55.1 kB]
Get:4 http://security.ubuntu.com/ubuntu xenial-security/main i386 lintian all 2.5.43ubuntu0.1 [626 kB]
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-4.4.0-79-generic i386 4.4.0-79.100 [20.5 MB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-extra-4.4.0-79-generic i386 4.4.0-79.100 [35.6 MB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-generic i386 4.4.0.79.85 [1786 B]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-generic i386 4.4.0.79.85 [2310 B]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-4.4.0-79 all 4.4.0-79.100 [9991 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-4.4.0-79-generic i386 4.4.0-79.100 [772 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-generic i386 4.4.0.79.85 [2282 B]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-libc-dev i386 4.4.0-79.100 [842 kB]
Fetched 68.5 MB in 6s (214 kB/s)                                               
fetch.run() result: 0
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 131576 DestFile:'/var/cache/apt/archives/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' ID:1 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb')
found pkg: libnl-route-3-200
No conffiles in deb '/var/cache/apt/archives/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 12032 DestFile:'/var/cache/apt/archives/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' ID:2 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb')
found pkg: libnl-genl-3-200
No conffiles in deb '/var/cache/apt/archives/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 55114 DestFile:'/var/cache/apt/archives/libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' ID:3 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb')
found pkg: libnl-3-200
conffile line: '/etc/libnl-3/classid 3e07259e58674631830b152e983ca995'
current md5: 3e07259e58674631830b152e983ca995
conffile line: '/etc/libnl-3/pktloc 7613dbc41b2dc3258195b6b6abd0f179'
current md5: 7613dbc41b2dc3258195b6b6abd0f179
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 625922 DestFile:'/var/cache/apt/archives/lintian_2.5.43ubuntu0.1_all.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/lintian/lintian_2.5.43ubuntu0.1_all.deb' ID:4 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/lintian_2.5.43ubuntu0.1_all.deb')
found pkg: lintian
conffile line: '/etc/lintianrc d5b00f3d9e2f7df6b62ef5e2d48c125a'
current md5: d5b00f3d9e2f7df6b62ef5e2d48c125a
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 20522794 DestFile:'/var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb' ID:5 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb')
No conffiles in deb '/var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 35570426 DestFile:'/var/cache/apt/archives/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb' ID:6 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb')
No conffiles in deb '/var/cache/apt/archives/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1786 DestFile:'/var/cache/apt/archives/linux-generic_4.4.0.79.85_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_4.4.0.79.85_i386.deb' ID:7 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-generic_4.4.0.79.85_i386.deb')
found pkg: linux-generic
No conffiles in deb '/var/cache/apt/archives/linux-generic_4.4.0.79.85_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 2310 DestFile:'/var/cache/apt/archives/linux-image-generic_4.4.0.79.85_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_4.4.0.79.85_i386.deb' ID:8 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-image-generic_4.4.0.79.85_i386.deb')
found pkg: linux-image-generic
No conffiles in deb '/var/cache/apt/archives/linux-image-generic_4.4.0.79.85_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 9991324 DestFile:'/var/cache/apt/archives/linux-headers-4.4.0-79_4.4.0-79.100_all.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-4.4.0-79_4.4.0-79.100_all.deb' ID:9 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-headers-4.4.0-79_4.4.0-79.100_all.deb')
No conffiles in deb '/var/cache/apt/archives/linux-headers-4.4.0-79_4.4.0-79.100_all.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 771910 DestFile:'/var/cache/apt/archives/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb' ID:10 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb')
No conffiles in deb '/var/cache/apt/archives/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 2282 DestFile:'/var/cache/apt/archives/linux-headers-generic_4.4.0.79.85_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_4.4.0.79.85_i386.deb' ID:11 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-headers-generic_4.4.0.79.85_i386.deb')
found pkg: linux-headers-generic
No conffiles in deb '/var/cache/apt/archives/linux-headers-generic_4.4.0.79.85_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 842270 DestFile:'/var/cache/apt/archives/linux-libc-dev_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_4.4.0-79.100_i386.deb' ID:12 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-libc-dev_4.4.0-79.100_i386.deb')
found pkg: linux-libc-dev
No conffiles in deb '/var/cache/apt/archives/linux-libc-dev_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
blacklist: []
whitelist: []
Packages that will be upgraded: libnl-3-200 libnl-genl-3-200 libnl-route-3-200 lintian linux-generic linux-headers-generic linux-image-generic linux-libc-dev
Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log'
(Reading database ... 265475 files and directories currently installed.)
Preparing to unpack .../libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-route-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Preparing to unpack .../libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-genl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Preparing to unpack .../libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Preparing to unpack .../lintian_2.5.43ubuntu0.1_all.deb ...
Unpacking lintian (2.5.43ubuntu0.1) over (2.5.43) ...
Selecting previously unselected package linux-image-4.4.0-79-generic.
Preparing to unpack .../linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb ...
Done.
Unpacking linux-image-4.4.0-79-generic (4.4.0-79.100) ...
Selecting previously unselected package linux-image-extra-4.4.0-79-generic.
Preparing to unpack .../linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb ...
Unpacking linux-image-extra-4.4.0-79-generic (4.4.0-79.100) ...
Preparing to unpack .../linux-generic_4.4.0.79.85_i386.deb ...
Unpacking linux-generic (4.4.0.79.85) over (4.4.0.78.84) ...
Preparing to unpack .../linux-image-generic_4.4.0.79.85_i386.deb ...
Unpacking linux-image-generic (4.4.0.79.85) over (4.4.0.78.84) ...
Selecting previously unselected package linux-headers-4.4.0-79.
Preparing to unpack .../linux-headers-4.4.0-79_4.4.0-79.100_all.deb ...
Unpacking linux-headers-4.4.0-79 (4.4.0-79.100) ...
Selecting previously unselected package linux-headers-4.4.0-79-generic.
Preparing to unpack .../linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb ...
Unpacking linux-headers-4.4.0-79-generic (4.4.0-79.100) ...
Preparing to unpack .../linux-headers-generic_4.4.0.79.85_i386.deb ...
Unpacking linux-headers-generic (4.4.0.79.85) over (4.4.0.78.84) ...
Preparing to unpack .../linux-libc-dev_4.4.0-79.100_i386.deb ...
Unpacking linux-libc-dev:i386 (4.4.0-79.100) over (4.4.0-78.99) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db (2.7.5-1) ...
Setting up libnl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up libnl-route-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up libnl-genl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up lintian (2.5.43ubuntu0.1) ...
Setting up linux-image-4.4.0-79-generic (4.4.0-79.100) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.4.0-79-generic (4.4.0-79.100) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (4.4.0.79.85) ...
Setting up linux-headers-4.4.0-79 (4.4.0-79.100) ...
Setting up linux-headers-4.4.0-79-generic (4.4.0-79.100) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Setting up linux-headers-generic (4.4.0.79.85) ...
Setting up linux-generic (4.4.0.79.85) ...
Setting up linux-libc-dev:i386 (4.4.0-79.100) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
All upgrades installed
InstCount=0 DelCount=0 BrokenCount=0
Extracting content from '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log' since '2017-06-07 15:52:09'
~$ 
```

Bump

---

### Post by deadflowr on 2017-06-08
See what the files in /etc/apt/apt.conf.d for 10periodic and/or 20auto-upgrades tell you.
Should be 1 for on and  0 for off.

---

### Post by ardouronerous on 2017-06-08
*/etc/apt/apt.conf.d/10periodic*:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
```

*/etc/apt/apt.conf.d/20auto-upgrades*:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
```

---

### Post by deadflowr on 2017-06-08
So it's set to off, in general.
See if you have either Software and Updates, or software sources listed as a menu option
(it can also show as the settings option in Software Updater, or can be opened with software-properties-gtk)
Try opening that and go to updates and see if you can change the settings for when there are security updates to Download and Install(it'll invoke you to enter your password) and then close.

Or, alternately, edit the above files and change the entries for the Unattended-Upgrade lines from ) to 1 and save.

---

### Post by ardouronerous on 2017-06-08
There is Software & Updates listed in Settings.
Okay, I've set security updates to download and install immediately, and I've checked both *10periodic* and *20auto-upgrades*, both have Download-Upgradeable-Packages and Unattended-Upgrade from 0 to 1.

I guess unattended updates should be working now.

Question, what about other updates though? I've removed the // from *"${distro_id}:${distro_codename}-updates"; *in */etc/apt/apt.conf.d/50unattended-upgrades.*

Will other updates be included? Because there is no option in Software & Updates for other updates to download and install immediately, only to display immediately.

Unattended updates doesn't seem to work.

I got this error message:
> The update information is outdated. This may be caused by  network problems or by a repository that is no longer available. Please  update manually by selecting ‘Show updates’ from indicator menu, and watching for any failing repositories.

When I click check 'show updates', it tells me I have 72.2MB security updates available.

Here's */var/log/unattended-upgrades/unattended-upgrades.log*
```
2017-06-13 08:05:43,326 INFO Initial blacklisted packages: 
2017-06-13 08:05:43,338 INFO Initial whitelisted packages: 
2017-06-13 08:05:43,338 INFO Starting unattended upgrades script
2017-06-13 08:05:43,338 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=UbuntuESM,a=xenial', 'o=Ubuntu,a=xenial-updates', 'o=Ubuntu,a=xenial-backports']
2017-06-13 08:05:50,158 INFO No packages found that can be upgraded unattended and no pending auto-removals
```

What's going on?

---

### Post by howefield on 2017-06-13
As I understand it, unattended-upgrades will only upgrade already installed packages, it won't install new ones, eg kernels..

What are the updates waiting for you ?

You can list pending updates with..

```
sudo apt update
```
```
apt list --upgradable
```

---

### Post by ardouronerous on 2017-06-13
> **howefield said:**
> As I understand it, unattended-upgrades will only upgrade already installed packages, it won't install new ones, eg kernels..

Well, that sucks. The purpose of why I want to activate unattended-upgrades is because my dad's a senior citizen and he has zero computer experience besides from using Facebook, so for him to do updates by himself is difficult and he usually ignores them when they popup.

Based off my conversions on this site, which is found here, [https://ubuntuforums.org/showthread.php?t=2362553](https://ubuntuforums.org/showthread.php?t=2362553), since my dad shuts down the laptop after usage, usually 8 to 10 hours, updates that require restarts are taken care of by the shut downs, and I thought, since kernel updates requires restarts, that would take care of that.

> **howefield said:**
> What are the updates waiting for you ?

You can list pending updates with..

```
sudo apt update
```
```
apt list --upgradable
```

```
~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [536 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [462 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [4,692 B]
Fetched 1,309 kB in 18s (70.8 kB/s)                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
~$ apt list --upgradable
Listing... Done
libnl-3-200/xenial-updates,xenial-security 3.2.27-1ubuntu0.16.04.1 i386 [upgradable from: 3.2.27-1]
libnl-genl-3-200/xenial-updates,xenial-security 3.2.27-1ubuntu0.16.04.1 i386 [upgradable from: 3.2.27-1]
libssl1.0.0/xenial-updates 1.0.2g-1ubuntu4.8 i386 [upgradable from: 1.0.2g-1ubuntu4.6]
libtasn1-6/xenial-updates,xenial-security 4.7-3ubuntu0.16.04.2 i386 [upgradable from: 4.7-3ubuntu0.16.04.1]
linux-generic-hwe-16.04/xenial-updates,xenial-security 4.8.0.54.25 i386 [upgradable from: 4.8.0.53.24]
linux-headers-generic-hwe-16.04/xenial-updates,xenial-security 4.8.0.54.25 i386 [upgradable from: 4.8.0.53.24]
linux-image-generic-hwe-16.04/xenial-updates,xenial-security 4.8.0.54.25 i386 [upgradable from: 4.8.0.53.24]
openssl/xenial-updates 1.0.2g-1ubuntu4.8 i386 [upgradable from: 1.0.2g-1ubuntu4.6]
~$ 
```

---

### Post by deadflowr on 2017-06-13
unattended-upgrade does indeed install new packages such as newer kernels.
It'll install every package that is listed in the marked repos in the configuration file.

Something else is going on here that's causing the issues with it.

What happens when you run 
```
sudo apt-get dist-upgrade
```
how similar is the output from that to the output from the earlier unattended-upgrade -d output here:

```
~$ sudo unattended-upgrades -d
Initial blacklisted packages: 
Initial whitelisted packages: 
Starting unattended upgrades script
Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=UbuntuESM,a=xenial', 'o=Ubuntu,a=xenial-updates']
Checking: libnl-3-200 ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: libnl-genl-3-200 ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: libnl-route-3-200 ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: lintian ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-generic ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-headers-generic ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-image-generic ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
Checking: linux-libc-dev ([<Origin component:'main' archive:'xenial-security' origin:'Ubuntu' label:'Ubuntu' site:'security.ubuntu.com' isTrusted:True>, <Origin component:'main' archive:'xenial-updates' origin:'Ubuntu' label:'Ubuntu' site:'archive.ubuntu.com' isTrusted:True>])
pkgs that look like they should be upgraded: libnl-3-200
libnl-genl-3-200
libnl-route-3-200
lintian
linux-generic
linux-headers-generic
linux-image-generic
linux-libc-dev
Get:1 http://security.ubuntu.com/ubuntu xenial-security/main i386 libnl-route-3-200 i386 3.2.27-1ubuntu0.16.04.1 [132 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security/main i386 libnl-genl-3-200 i386 3.2.27-1ubuntu0.16.04.1 [12.0 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security/main i386 libnl-3-200 i386 3.2.27-1ubuntu0.16.04.1 [55.1 kB]
Get:4 http://security.ubuntu.com/ubuntu xenial-security/main i386 lintian all 2.5.43ubuntu0.1 [626 kB]
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-4.4.0-79-generic i386 4.4.0-79.100 [20.5 MB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-extra-4.4.0-79-generic i386 4.4.0-79.100 [35.6 MB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-generic i386 4.4.0.79.85 [1786 B]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-generic i386 4.4.0.79.85 [2310 B]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-4.4.0-79 all 4.4.0-79.100 [9991 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-4.4.0-79-generic i386 4.4.0-79.100 [772 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-generic i386 4.4.0.79.85 [2282 B]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-libc-dev i386 4.4.0-79.100 [842 kB]
Fetched 68.5 MB in 6s (214 kB/s)                                               
fetch.run() result: 0
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 131576 DestFile:'/var/cache/apt/archives/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' ID:1 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb')
found pkg: libnl-route-3-200
No conffiles in deb '/var/cache/apt/archives/libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 12032 DestFile:'/var/cache/apt/archives/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' ID:2 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb')
found pkg: libnl-genl-3-200
No conffiles in deb '/var/cache/apt/archives/libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 55114 DestFile:'/var/cache/apt/archives/libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb' ID:3 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb')
found pkg: libnl-3-200
conffile line: '/etc/libnl-3/classid 3e07259e58674631830b152e983ca995'
current md5: 3e07259e58674631830b152e983ca995
conffile line: '/etc/libnl-3/pktloc 7613dbc41b2dc3258195b6b6abd0f179'
current md5: 7613dbc41b2dc3258195b6b6abd0f179
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 625922 DestFile:'/var/cache/apt/archives/lintian_2.5.43ubuntu0.1_all.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/lintian/lintian_2.5.43ubuntu0.1_all.deb' ID:4 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/lintian_2.5.43ubuntu0.1_all.deb')
found pkg: lintian
conffile line: '/etc/lintianrc d5b00f3d9e2f7df6b62ef5e2d48c125a'
current md5: d5b00f3d9e2f7df6b62ef5e2d48c125a
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 20522794 DestFile:'/var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb' ID:5 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb')
No conffiles in deb '/var/cache/apt/archives/linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 35570426 DestFile:'/var/cache/apt/archives/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb' ID:6 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb')
No conffiles in deb '/var/cache/apt/archives/linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1786 DestFile:'/var/cache/apt/archives/linux-generic_4.4.0.79.85_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_4.4.0.79.85_i386.deb' ID:7 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-generic_4.4.0.79.85_i386.deb')
found pkg: linux-generic
No conffiles in deb '/var/cache/apt/archives/linux-generic_4.4.0.79.85_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 2310 DestFile:'/var/cache/apt/archives/linux-image-generic_4.4.0.79.85_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_4.4.0.79.85_i386.deb' ID:8 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-image-generic_4.4.0.79.85_i386.deb')
found pkg: linux-image-generic
No conffiles in deb '/var/cache/apt/archives/linux-image-generic_4.4.0.79.85_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 9991324 DestFile:'/var/cache/apt/archives/linux-headers-4.4.0-79_4.4.0-79.100_all.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-4.4.0-79_4.4.0-79.100_all.deb' ID:9 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-headers-4.4.0-79_4.4.0-79.100_all.deb')
No conffiles in deb '/var/cache/apt/archives/linux-headers-4.4.0-79_4.4.0-79.100_all.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 771910 DestFile:'/var/cache/apt/archives/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb' ID:10 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb')
No conffiles in deb '/var/cache/apt/archives/linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 2282 DestFile:'/var/cache/apt/archives/linux-headers-generic_4.4.0.79.85_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_4.4.0.79.85_i386.deb' ID:11 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-headers-generic_4.4.0.79.85_i386.deb')
found pkg: linux-headers-generic
No conffiles in deb '/var/cache/apt/archives/linux-headers-generic_4.4.0.79.85_i386.deb' (There is no member named 'conffiles')
<apt_pkg.AcquireItem object:Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 842270 DestFile:'/var/cache/apt/archives/linux-libc-dev_4.4.0-79.100_i386.deb' DescURI: 'http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_4.4.0-79.100_i386.deb' ID:12 ErrorText: ''>
check_conffile_prompt('/var/cache/apt/archives/linux-libc-dev_4.4.0-79.100_i386.deb')
found pkg: linux-libc-dev
No conffiles in deb '/var/cache/apt/archives/linux-libc-dev_4.4.0-79.100_i386.deb' (There is no member named 'conffiles')
blacklist: []
whitelist: []
Packages that will be upgraded: libnl-3-200 libnl-genl-3-200 libnl-route-3-200 lintian linux-generic linux-headers-generic linux-image-generic linux-libc-dev
Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log'
(Reading database ... 265475 files and directories currently installed.)
Preparing to unpack .../libnl-route-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-route-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Preparing to unpack .../libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-genl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Preparing to unpack .../libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Preparing to unpack .../lintian_2.5.43ubuntu0.1_all.deb ...
Unpacking lintian (2.5.43ubuntu0.1) over (2.5.43) ...
Selecting previously unselected package linux-image-4.4.0-79-generic.
Preparing to unpack .../linux-image-4.4.0-79-generic_4.4.0-79.100_i386.deb ...
Done.
Unpacking linux-image-4.4.0-79-generic (4.4.0-79.100) ...
Selecting previously unselected package linux-image-extra-4.4.0-79-generic.
Preparing to unpack .../linux-image-extra-4.4.0-79-generic_4.4.0-79.100_i386.deb ...
Unpacking linux-image-extra-4.4.0-79-generic (4.4.0-79.100) ...
Preparing to unpack .../linux-generic_4.4.0.79.85_i386.deb ...
Unpacking linux-generic (4.4.0.79.85) over (4.4.0.78.84) ...
Preparing to unpack .../linux-image-generic_4.4.0.79.85_i386.deb ...
Unpacking linux-image-generic (4.4.0.79.85) over (4.4.0.78.84) ...
Selecting previously unselected package linux-headers-4.4.0-79.
Preparing to unpack .../linux-headers-4.4.0-79_4.4.0-79.100_all.deb ...
Unpacking linux-headers-4.4.0-79 (4.4.0-79.100) ...
Selecting previously unselected package linux-headers-4.4.0-79-generic.
Preparing to unpack .../linux-headers-4.4.0-79-generic_4.4.0-79.100_i386.deb ...
Unpacking linux-headers-4.4.0-79-generic (4.4.0-79.100) ...
Preparing to unpack .../linux-headers-generic_4.4.0.79.85_i386.deb ...
Unpacking linux-headers-generic (4.4.0.79.85) over (4.4.0.78.84) ...
Preparing to unpack .../linux-libc-dev_4.4.0-79.100_i386.deb ...
Unpacking linux-libc-dev:i386 (4.4.0-79.100) over (4.4.0-78.99) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for doc-base (0.10.7) ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db (2.7.5-1) ...
Setting up libnl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up libnl-route-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up libnl-genl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up lintian (2.5.43ubuntu0.1) ...
Setting up linux-image-4.4.0-79-generic (4.4.0-79.100) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.4.0-79-generic (4.4.0-79.100) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (4.4.0.79.85) ...
Setting up linux-headers-4.4.0-79 (4.4.0-79.100) ...
Setting up linux-headers-4.4.0-79-generic (4.4.0-79.100) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-79-generic /boot/vmlinuz-4.4.0-79-generic
Setting up linux-headers-generic (4.4.0.79.85) ...
Setting up linux-generic (4.4.0.79.85) ...
Setting up linux-libc-dev:i386 (4.4.0-79.100) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
All upgrades installed
InstCount=0 DelCount=0 BrokenCount=0
Extracting content from '/var/log/unattended-upgrades/unattended-upgrades-dpkg.log' since '2017-06-07 15:52:09'
~$
```
this was your output from post #7

---

### Post by ardouronerous on 2017-06-13
Here's the output:

```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.8.0-54 linux-headers-4.8.0-54-generic
  linux-image-4.8.0-54-generic linux-image-extra-4.8.0-54-generic
The following packages will be upgraded:
  libnl-3-200 libnl-genl-3-200 libssl1.0.0 libtasn1-6 linux-generic-hwe-16.04
  linux-headers-generic-hwe-16.04 linux-image-generic-hwe-16.04 openssl
8 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 72.2 MB of archives.
After this operation, 252 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 libssl1.0.0 i386 1.0.2g-1ubuntu4.8 [908 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 libtasn1-6 i386 4.7-3ubuntu0.16.04.2 [45.4 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 openssl i386 1.0.2g-1ubuntu4.8 [506 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 libnl-genl-3-200 i386 3.2.27-1ubuntu0.16.04.1 [12.0 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 libnl-3-200 i386 3.2.27-1ubuntu0.16.04.1 [55.1 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-image-4.8.0-54-generic i386 4.8.0-54.57~16.04.1 [22.1 MB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-image-extra-4.8.0-54-generic i386 4.8.0-54.57~16.04.1 [37.5 MB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-generic-hwe-16.04 i386 4.8.0.54.25 [1,804 B]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-image-generic-hwe-16.04 i386 4.8.0.54.25 [2,388 B]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-headers-4.8.0-54 all 4.8.0-54.57~16.04.1 [10.3 MB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-headers-4.8.0-54-generic i386 4.8.0-54.57~16.04.1 [824 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 linux-headers-generic-hwe-16.04 i386 4.8.0.54.25 [2,370 B]
Fetched 72.2 MB in 10min 22s (116 kB/s)                                        
Preconfiguring packages ...
(Reading database ... 152329 files and directories currently installed.)
Preparing to unpack .../libssl1.0.0_1.0.2g-1ubuntu4.8_i386.deb ...
Unpacking libssl1.0.0:i386 (1.0.2g-1ubuntu4.8) over (1.0.2g-1ubuntu4.6) ...
Preparing to unpack .../libtasn1-6_4.7-3ubuntu0.16.04.2_i386.deb ...
Unpacking libtasn1-6:i386 (4.7-3ubuntu0.16.04.2) over (4.7-3ubuntu0.16.04.1) ...
Preparing to unpack .../openssl_1.0.2g-1ubuntu4.8_i386.deb ...
Unpacking openssl (1.0.2g-1ubuntu4.8) over (1.0.2g-1ubuntu4.6) ...
Preparing to unpack .../libnl-genl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-genl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Preparing to unpack .../libnl-3-200_3.2.27-1ubuntu0.16.04.1_i386.deb ...
Unpacking libnl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) over (3.2.27-1) ...
Selecting previously unselected package linux-image-4.8.0-54-generic.
Preparing to unpack .../linux-image-4.8.0-54-generic_4.8.0-54.57~16.04.1_i386.deb ...
Done.
Unpacking linux-image-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Selecting previously unselected package linux-image-extra-4.8.0-54-generic.
Preparing to unpack .../linux-image-extra-4.8.0-54-generic_4.8.0-54.57~16.04.1_i386.deb ...
Unpacking linux-image-extra-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Preparing to unpack .../linux-generic-hwe-16.04_4.8.0.54.25_i386.deb ...
Unpacking linux-generic-hwe-16.04 (4.8.0.54.25) over (4.8.0.53.24) ...
Preparing to unpack .../linux-image-generic-hwe-16.04_4.8.0.54.25_i386.deb ...
Unpacking linux-image-generic-hwe-16.04 (4.8.0.54.25) over (4.8.0.53.24) ...
Selecting previously unselected package linux-headers-4.8.0-54.
Preparing to unpack .../linux-headers-4.8.0-54_4.8.0-54.57~16.04.1_all.deb ...
Unpacking linux-headers-4.8.0-54 (4.8.0-54.57~16.04.1) ...
Selecting previously unselected package linux-headers-4.8.0-54-generic.
Preparing to unpack .../linux-headers-4.8.0-54-generic_4.8.0-54.57~16.04.1_i386.deb ...
Unpacking linux-headers-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Preparing to unpack .../linux-headers-generic-hwe-16.04_4.8.0.54.25_i386.deb ...
Unpacking linux-headers-generic-hwe-16.04 (4.8.0.54.25) over (4.8.0.53.24) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.8) ...
Setting up libtasn1-6:i386 (4.7-3ubuntu0.16.04.2) ...
Setting up openssl (1.0.2g-1ubuntu4.8) ...
Setting up libnl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up libnl-genl-3-200:i386 (3.2.27-1ubuntu0.16.04.1) ...
Setting up linux-image-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-54-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-54-generic
Found initrd image: /boot/initrd.img-4.8.0-54-generic
Found linux image: /boot/vmlinuz-4.8.0-53-generic
Found initrd image: /boot/initrd.img-4.8.0-53-generic
Found linux image: /boot/vmlinuz-4.8.0-52-generic
Found initrd image: /boot/initrd.img-4.8.0-52-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-54-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-54-generic
Found initrd image: /boot/initrd.img-4.8.0-54-generic
Found linux image: /boot/vmlinuz-4.8.0-53-generic
Found initrd image: /boot/initrd.img-4.8.0-53-generic
Found linux image: /boot/vmlinuz-4.8.0-52-generic
Found initrd image: /boot/initrd.img-4.8.0-52-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-hwe-16.04 (4.8.0.54.25) ...
Setting up linux-headers-4.8.0-54 (4.8.0-54.57~16.04.1) ...
Setting up linux-headers-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Setting up linux-headers-generic-hwe-16.04 (4.8.0.54.25) ...
Setting up linux-generic-hwe-16.04 (4.8.0.54.25) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
~$ 
```

---

### Post by deadflowr on 2017-06-13
Are these two different machines? 
Because you already installed quite a few of those packages when you ran the unattended-upgrades -d command a few days ago.
And the dist-upgrade output shows an entirely different kernel series.
(The uu -d output shows it installed the 4.4 kernel.
And now the d-u output shows the hwe-4.8 kernel._

---

### Post by ardouronerous on 2017-06-13
Sorry about that, yeah, I'm maintaining my Xubuntu desktop and my dad's Lubuntu laptop.

The output of posts #13 and #17 comes from my dad's Lubuntu laptop.

---

