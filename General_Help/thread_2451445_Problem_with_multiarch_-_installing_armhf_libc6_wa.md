---
title: "Problem with multiarch - installing armhf libc6 wants to uninstall essential packages"
date: 2020-10-04
forum: General Help
---

### Post by techvj on 2020-10-04
I'm new to using multiarch with dpkg. On my Ubuntu 20.04 machine I setup armhf by running:

```
dpkg --add-architecture armhf
```

After fixing the repo list and running update, I'm trying to install libc6 using:

```
apt install libc6:armhf
```

The problem is, it then wants to delete a lot of standard, essential packages. I'm not sure what I'm missing or doing wrong.

Below is the apt output.

Any help is greatly appreciated!

sudo apt install libc6:armhf
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  alsa-topology-conf alsa-ucm-conf amd64-microcode apport-symptoms binutils-common cgroupfs-mount distro-info-data
  finalrd gcc-10-cross-base gcc-9-arm-linux-gnueabihf-base gcc-9-base gcc-9-cross-base git-man glib-networking-common
  gnupg-l10n iso-codes klibc-utils krb5-locales libasan5-armhf-cross libasound2-data libatomic1-armhf-cross
  libc6-armhf-cross libc6-dev-armhf-cross libdrm-common libgcc-9-dev-armhf-cross libgcc-s1-armhf-cross libglib2.0-data
  libgomp1-armhf-cross libjson-glib-1.0-common libklibc libldap-common libmagic-mgc libpthread-stubs0-dev
  libsensors-config libstdc++6-armhf-cross libubsan1-armhf-cross libx11-data libx11-xcb1 linux-libc-dev
  linux-libc-dev-armhf-cross manpages-dev ncurses-term pci.ids powermgmt-base publicsuffix python-apt-common
  sound-theme-freedesktop usb.ids vim-runtime wireless-regdb xkb-data xtrans-dev
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gcc-10-base:armhf libcrypt1:armhf libgcc-s1:armhf libidn2-0:armhf libunistring2:armhf
Suggested packages:
  glibc-doc:armhf debconf:armhf | debconf-2.0:armhf locales:armhf
The following packages will be REMOVED:
  accountsservice adduser apparmor apport apt apt-transport-https apt-utils at aufs-tools base-files base-passwd bash
  bc bcache-tools bind9-dnsutils bind9-host bind9-libs binfmt-support binutils binutils-arm-linux-gnueabihf
  binutils-x86-64-linux-gnu bison bolt bridge-utils bsdmainutils bsdutils btrfs-progs build-essential
  busybox-initramfs byobu bzip2 ca-certificates cloud-guest-utils cloud-init cloud-initramfs-copymods
  cloud-initramfs-dyn-netconf command-not-found console-setup console-setup-linux containerd.io coreutils cpio cpp
  cpp-9 cpp-9-arm-linux-gnueabihf cpp-arm-linux-gnueabihf crda cron cryptsetup cryptsetup-bin cryptsetup-initramfs
  cryptsetup-run curl dash dbus dbus-user-session dconf-gsettings-backend dconf-service debconf debconf-i18n
  debianutils diffutils dirmngr dmeventd dmidecode dmsetup dnsutils docker-ce docker-ce-cli dosfstools dpkg dpkg-dev
  e2fsprogs eatmydata ed eject ethtool fakeroot fdisk file findutils flex friendly-recovery ftp fuse fwupd
  fwupd-signed g++ g++-9 g++-9-multilib gawk gcc gcc-9 gcc-9-arm-linux-gnueabihf gcc-9-multilib
  gcc-arm-linux-gnueabihf gdisk gettext-base gir1.2-glib-2.0 gir1.2-packagekitglib-1.0 git glib-networking
  glib-networking-services gnupg gnupg-agent gnupg-utils gperf gpg gpg-agent gpg-wks-client gpg-wks-server gpgconf
  gpgsm gpgv grep groff-base grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
  gsettings-desktop-schemas gzip hdparm hostname htop info init init-system-helpers initramfs-tools
  initramfs-tools-bin initramfs-tools-core install-info intel-microcode iproute2 iptables iptables-persistent
  iputils-ping iputils-tracepath irqbalance isc-dhcp-client isc-dhcp-common iucode-tool iw jq kbd
  keyboard-configuration kmod kpartx landscape-common language-selector-common less lib32asan5 lib32atomic1
  lib32gcc-9-dev lib32gcc-s1 lib32gcc1 lib32gomp1 lib32itm1 lib32ncurses-dev lib32ncurses6 lib32ncursesw6
  lib32quadmath0 lib32stdc++-9-dev lib32stdc++6 lib32tinfo6 lib32ubsan1 lib32z1 lib32z1-dev libaccountsservice0
  libacl1 libaio1 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libapparmor1 libappstream4
  libapt-pkg6.0 libarchive13 libargon2-1 libasan5 libasn1-8-heimdal libasound2 libassuan0 libatm1 libatomic1 libattr1
  libaudit1 libbinutils libblkid1 libbrotli1 libbsd0 libbz2-1.0 libc-bin libc-dev-bin libc6 libc6-dev libc6-dev-i386
  libc6-dev-x32 libc6-i386 libc6-x32 libcanberra0 libcap-ng0 libcap2 libcap2-bin libcbor0.6 libcc1-0 libcom-err2
  libcrypt-dev libcrypt1 libcryptsetup12 libctf-nobfd0 libctf0 libcurl3-gnutls libcurl4 libdb5.3 libdbus-1-3
  libdbus-glib-1-2 libdconf1 libdebconfclient0 libdevmapper-event1.02.1 libdevmapper1.02.1 libdns-export1109
  libdpkg-perl libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libeatmydata1 libedit2 libefiboot1
  libefivar1 libegl-dev libegl-mesa0 libegl1 libelf1 liberror-perl libestr0 libevent-2.1-7 libexpat1 libexpat1-dev
  libext2fs2 libfakeroot libfastjson4 libfdisk1 libffi7 libfido2-1 libfile-fcntllock-perl libfl-dev libfl2
  libfreetype6 libfribidi0 libfuse2 libfwupd2 libfwupdplugin1 libgbm1 libgcab-1.0-0 libgcc-9-dev libgcc-s1 libgcc1
  libgcrypt20 libgdbm-compat4 libgdbm6 libgirepository-1.0-1 libgl-dev libgl1 libgl1-mesa-dev libgl1-mesa-dri
  libglapi-mesa libgles-dev libgles1 libgles2 libglib2.0-0 libglib2.0-bin libglvnd-dev libglvnd0 libglx-dev
  libglx-mesa0 libglx0 libgmp10 libgnutls30 libgomp1 libgpg-error0 libgpgme11 libgpm2 libgssapi-krb5-2
  libgssapi3-heimdal libgstreamer1.0-0 libgudev-1.0-0 libgusb2 libhcrypto4-heimdal libheimbase1-heimdal
  libheimntlm0-heimdal libhogweed5 libhx509-5-heimdal libicu66 libidn2-0 libip4tc2 libip6tc2 libisc-export1105
  libisl22 libisns0 libitm1 libjq1 libjson-c4 libjson-glib-1.0-0 libk5crypto3 libkeyutils1 libkmod2 libkrb5-26-heimdal
  libkrb5-3 libkrb5support0 libksba8 libldap-2.4-2 libllvm10 liblmdb0 liblocale-gettext-perl liblsan0 libltdl7
  liblvm2cmd2.03 liblz4-1 liblzma5 liblzo2-2 libmagic1 libmaxminddb0 libmnl0 libmount1 libmpc3 libmpdec2 libmpfr6
  libmspack0 libncurses-dev libncurses6 libncursesw6 libnetfilter-conntrack3 libnetplan0 libnettle7 libnewt0.52
  libnfnetlink0 libnftnl11 libnghttp2-14 libnl-3-200 libnl-genl-3-200 libnpth0 libnss-systemd libntfs-3g883 libnuma1
  libogg0 libonig5 libopengl-dev libopengl0 libp11-kit0 libpackagekit-glib2-18 libpam-cap libpam-modules
  libpam-modules-bin libpam-runtime libpam-systemd libpam0g libparted2 libpcap0.8 libpci3 libpciaccess0 libpcre2-8-0
  libpcre3 libperl5.30 libpipeline1 libplymouth5 libpng16-16 libpolkit-agent-1-0 libpolkit-gobject-1-0 libpopt0
  libprocps8 libproxy1v5 libpsl5 libpython3-dev libpython3-stdlib libpython3.8 libpython3.8-dev libpython3.8-minimal
  libpython3.8-stdlib libquadmath0 libreadline5 libreadline8 libroken18-heimdal librtmp1 libsasl2-2 libsasl2-modules
  libsasl2-modules-db libseccomp2 libselinux1 libsemanage1 libsensors5 libsepol1 libsgutils2-2 libsigsegv2 libslang2
  libsmartcols1 libsmbios-c2 libsoup2.4-1 libsqlite3-0 libss2 libssh-4 libssl1.1 libstdc++-9-dev libstdc++6
  libstemmer0d libsystemd0 libtasn1-6 libtdb1 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl
  libtinfo6 libtsan0 libtss2-esys0 libubsan1 libuchardet0 libudev1 libunistring2 libunwind8 liburcu6 libusb-1.0-0
  libutempter0 libuuid1 libuv1 libvorbis0a libvorbisfile3 libvulkan1 libwayland-client0 libwayland-server0
  libwind0-heimdal libwrap0 libx11-6 libx11-dev libx32asan5 libx32atomic1 libx32gcc-9-dev libx32gcc-s1 libx32gcc1
  libx32gomp1 libx32itm1 libx32quadmath0 libx32stdc++-9-dev libx32stdc++6 libx32ubsan1 libxau-dev libxau6
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-randr0 libxcb-sync1 libxcb-xfixes0 libxcb1
  libxcb1-dev libxdamage1 libxdmcp-dev libxdmcp6 libxext6 libxfixes3 libxml2 libxml2-utils libxmlb1 libxmlsec1
  libxmlsec1-openssl libxmuu1 libxshmfence1 libxslt1.1 libxtables12 libxxf86vm1 libyaml-0-2 libzstd1 linux-base
  linux-generic linux-headers-5.4.0-45 linux-headers-5.4.0-45-generic linux-headers-5.4.0-48
  linux-headers-5.4.0-48-generic linux-headers-generic linux-image-5.4.0-45-generic linux-image-5.4.0-48-generic
  linux-image-generic linux-modules-extra-5.4.0-45-generic linux-modules-extra-5.4.0-48-generic locales login
  logrotate logsave lsb-release lshw lsof lsscsi ltrace lvm2 lz4 m4 make man-db mawk mdadm mesa-vulkan-drivers mount
  mtr-tiny multipath-tools nano ncurses-bin netcat-openbsd netfilter-persistent netplan.io networkd-dispatcher ntfs-3g
  open-iscsi open-vm-tools openssh-client openssh-server openssh-sftp-server openssl os-prober overlayroot packagekit
  packagekit-tools parted passwd pastebinit patch pciutils perl perl-base perl-modules-5.30 pigz pinentry-curses
  plymouth plymouth-theme-ubuntu-text policykit-1 pollinate popularity-contest procps psmisc python-pip-whl python3
  python3-apport python3-apt python3-attr python3-automat python3-blinker python3-certifi python3-cffi-backend
  python3-chardet python3-click python3-colorama python3-commandnotfound python3-configobj python3-constantly
  python3-cryptography python3-dbus python3-debconf python3-debian python3-dev python3-distro python3-distro-info
  python3-distupgrade python3-distutils python3-entrypoints python3-gdbm python3-gi python3-hamcrest python3-httplib2
  python3-hyperlink python3-idna python3-importlib-metadata python3-incremental python3-jinja2 python3-json-pointer
  python3-jsonpatch python3-jsonschema python3-jwt python3-keyring python3-launchpadlib python3-lazr.restfulclient
  python3-lazr.uri python3-lib2to3 python3-markupsafe python3-minimal python3-more-itertools python3-netifaces
  python3-newt python3-oauthlib python3-openssl python3-pexpect python3-pip python3-pkg-resources
  python3-problem-report python3-ptyprocess python3-pyasn1 python3-pyasn1-modules python3-pyrsistent python3-requests
  python3-requests-unixsocket python3-secretstorage python3-serial python3-service-identity python3-setuptools
  python3-simplejson python3-six python3-software-properties python3-systemd python3-twisted python3-twisted-bin
  python3-update-manager python3-urllib3 python3-venv python3-wadllib python3-wheel python3-yaml python3-zipp
  python3-zope.interface python3.8 python3.8-dev python3.8-minimal python3.8-venv readline-common rsync rsyslog
  run-one sbsigntool screen secureboot-db sed sg3-utils sg3-utils-udev shared-mime-info snapd
  software-properties-common sosreport squashfs-tools ssh-import-id strace sudo systemd systemd-sysv systemd-timesyncd
  sysvinit-utils tar tcpdump telnet thermald thin-provisioning-tools time tmux tpm-udev tzdata ubuntu-advantage-tools
  ubuntu-minimal ubuntu-release-upgrader-core ubuntu-server ubuntu-standard ucf udev ufw unattended-upgrades unzip
  update-manager-core update-notifier-common usbutils util-linux uuid-runtime vim vim-common vim-tiny wget whiptail
  xauth xdg-user-dirs xfsprogs xsltproc xxd xz-utils zerofree zip zlib1g zlib1g-dev
The following NEW packages will be installed:
  gcc-10-base:armhf libc6:armhf libcrypt1:armhf libgcc-s1:armhf libidn2-0:armhf libunistring2:armhf
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt adduser (due to apt) gpgv (due to apt) libapt-pkg6.0 (due to apt) libc6 (due to apt) libgcc-s1 (due to apt)
  libgnutls30 (due to apt) libseccomp2 (due to apt) libstdc++6 (due to apt) libsystemd0 (due to apt) base-files
  libcrypt1 (due to base-files) base-passwd libdebconfclient0 (due to base-passwd) bash libtinfo6 (due to bash)
  debianutils (due to bash) bsdutils coreutils libacl1 (due to coreutils) libattr1 (due to coreutils)
  libselinux1 (due to coreutils) dash dpkg (due to dash) debconf (due to dash) diffutils libbz2-1.0 (due to dpkg)
  liblzma5 (due to dpkg) libzstd1 (due to dpkg) zlib1g (due to dpkg) tar (due to dpkg) e2fsprogs
  libblkid1 (due to e2fsprogs) libcom-err2 (due to e2fsprogs) libext2fs2 (due to e2fsprogs) libss2 (due to e2fsprogs)
  libuuid1 (due to e2fsprogs) logsave (due to e2fsprogs) fdisk libfdisk1 (due to fdisk) libmount1 (due to fdisk)
  libncursesw6 (due to fdisk) libsmartcols1 (due to fdisk) findutils grep libpcre3 (due to grep)
  install-info (due to grep) gzip hostname init systemd-sysv (due to init) init-system-helpers (due to init)
  perl-base (due to init-system-helpers) libc-bin login libaudit1 (due to login) libpam0g (due to login)
  libpam-runtime (due to login) libpam-modules (due to login) mount util-linux (due to mount) ncurses-bin sed
  sysvinit-utils libcap-ng0 (due to util-linux) libudev1 (due to util-linux)
0 upgraded, 6 newly installed, 684 to remove and 0 not upgraded.
Need to get 2,696 kB of archives.
After this operation, 2,332 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]

---

