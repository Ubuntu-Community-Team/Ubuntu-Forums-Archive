---
title: "[Special Case] What packages can I remove to achieve the minimum working installation"
date: 2013-09-20
forum: General Help
---

### Post by amjjawad on 2013-09-20
Hello everyone,

Please note that this is a very special case - [See this]("http://ubuntuforums.org/showthread.php?t=1590614&page=16&p=11832431#post11832431"). I do know for sure that I have an outdated version installed. This is not for day-to-day activities, _this is for learning purposes_.

_**Machine:**_

```
lubuntu
    description: Notebook
    version: HP OmniBook 4150 B
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.1
    configuration: chassis=notebook
  *-core
       description: Motherboard
       product: N/A
       vendor: Hewlett-Packard
       physical id: 0
       version: OmniBook TS32T5
       serial: 000000000000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: CK.M3.020
          date: 11/04/99
          size: 61KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot edd int13floppynec int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer biosbootspecification netboot
     *-cpu
          description: CPU
          product: Mobile Pentium II
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.10
          slot: JP18/JP19
          size: 366MHz
          capacity: 433MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: asynchronous external write-back
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 64MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: Internal
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: JDIMM1
             size: 64MiB
             width: 32 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: JDIMM2
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64
          resources: irq:0 memory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:fd000000-fedfffff memory:14000000-140fffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 64
                width: 32 bits
                clock: 33MHz
                capabilities: agp agp-1.0 pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:fd000000-fdffffff ioport:e800(size=256) memory:fedfe000-fedfefff memory:14000000-1401ffff
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:10 memory:14100000-14100fff ioport:1000(size=256) ioport:1400(size=256) memory:4000000-7ffffff memory:8000000-bffffff
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1225
             vendor: Texas Instruments
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5
             resources: irq:10 memory:14101000-14101fff ioport:1800(size=256) ioport:1c00(size=256) memory:c000000-fffffff memory:10000000-13ffffff
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fcf0(size=16)
           *-disk
                description: ATA Disk
                product: IBM-DBCA-204860
                vendor: IBM
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BC3O
                serial: HQ0RQQ43496
                size: 4645MiB (4871MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001dd05
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7490d338-4449-4137-aaf1-f72f8bc91f1a
                   size: 4100MiB
                   capacity: 4100MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-04-10 01:32:50 filesystem=ext4 lastmountpoint=/ modified=2012-04-10 04:33:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=1988-01-01 00:01:46 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 6940bcb9-175a-4fbe-863d-9a782d1a864d
                   size: 544MiB
                   capacity: 544MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64
             resources: irq:10 ioport:fcc0(size=32)
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1978 Maestro 2E
             vendor: ESS Technology
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ES1968 (ESS Maestro) latency=64 maxlatency=24 mingnt=2
             resources: irq:10 ioport:f800(size=256)
     *-network
          description: Wireless interface
          product: RT2500 802.11g
          vendor: Ralink corp.
          physical id: 1
          bus info: pci@0000:06:00.0
          logical name: wlan1
          version: 01
          serial: 00:0e:2e:62:61:68
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=rt2500pci driverversion=3.0.0-17-generic firmware=N/A ip=10.0.0.30 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
          resources: irq:10 memory:10000000-10001fff
     *-scsi
          physical id: 2
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 245MiB (257MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0008aab2
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/DCDB-548C
                version: FAT16
                serial: dcdb-548c
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-battery
       description: Unknown Battery
       physical id: 1
       slot: Front, near CPU Module


```

[U][B]
Installed System: [/B][/U]

```
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

```


_**CPU Info:**_

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 6
model name    : Mobile Pentium II
stepping    : 10
cpu MHz        : 364.998
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr up
bogomips    : 729.99
clflush size    : 32
cache_alignment    : 32
address sizes    : 36 bits physical, 32 bits virtual
power management:

```

[U][B]
lspci[/B][/U]:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
06:00.0 Network controller: Ralink corp. RT2500 802.11g (rev 01)


```


_**List of the installed packages:**_
```
accountsservice                    install
adduser                        install
apparmor                    install
apt                        install
apt-transport-https                install
apt-utils                    install
apt-xapian-index                install
aptitude                    install
at                        install
base-files                    install
base-passwd                    install
bash                        install
bash-completion                    install
bind9-host                    install
bsdmainutils                    install
bsdutils                    install
busybox-initramfs                install
busybox-static                    install
bzip2                        install
ca-certificates                    install
command-not-found                install
command-not-found-data                install
console-setup                    install
consolekit                    install
coreutils                    install
cpio                        install
cpp                        install
cpp-4.6                        install
cron                        install
dash                        install
dbus                        install
dbus-x11                    install
dconf-gsettings-backend                install
debconf                        install
debconf-i18n                    install
debianutils                    install
defoma                        install
dictionaries-common                install
diffutils                    install
discover                    install
discover-data                    install
dmidecode                    install
dmsetup                        install
dnsutils                    install
dosfstools                    install
dpkg                        install
e2fslibs                    install
e2fsprogs                    install
ed                        install
eject                        install
elementary-icon-theme                install
file                        install
findutils                    install
fontconfig                    install
fontconfig-config                install
friendly-recovery                install
ftp                        install
fuse-utils                    install
galculator                    install
gcc-4.6-base                    install
gconf2                        install
gconf2-common                    install
geoip-database                    install
gettext-base                    install
giblib1                        install
gir1.2-glib-2.0                    install
gksu                        install
glib-networking                    install
gnome-icon-theme                install
gnome-icon-theme-full                install
gnome-keyring                    install
gnupg                        install
gpgv                        install
grep                        install
groff-base                    install
grub-common                    install
grub-gfxpayload-lists                install
grub-pc                        install
grub-pc-bin                    install
grub2-common                    install
gsettings-desktop-schemas            install
gtk2-engines-murrine                install
gtk2-engines-pixbuf                install
gtk3-engines-unico                install
gvfs                        install
gvfs-backends                    install
gvfs-bin                    install
gvfs-fuse                    install
gzip                        install
hdparm                        install
hicolor-icon-theme                install
hostname                    install
htop                        install
ifupdown                    install
info                        install
initramfs-tools                    install
initramfs-tools-bin                install
initscripts                    install
insserv                        install
install-info                    install
installation-report                install
iproute                        install
iptables                    install
iputils-ping                    install
iputils-tracepath                install
irqbalance                    install
isc-dhcp-client                    install
isc-dhcp-common                    install
iso-codes                    install
kbd                        install
keyboard-configuration                install
klibc-utils                    install
language-pack-en                install
language-pack-en-base                install
language-pack-gnome-en                install
language-pack-gnome-en-base            install
language-selector-common            install
laptop-detect                    install
less                        install
libaccountsservice0                install
libacl1                        install
libapt-inst1.3                    install
libapt-pkg4.11                    install
libarchive1                    install
libasound2                    install
libatasmart4                    install
libatk1.0-0                    install
libatk1.0-data                    install
libattr1                    install
libavahi-client3                install
libavahi-common-data                install
libavahi-common3                install
libavahi-glib1                    install
libbind9-60                    install
libblkid1                    install
libbluetooth3                    install
libboost-iostreams1.46.1            install
libbsd0                        install
libbz2-1.0                    install
libc-bin                    install
libc6                        install
libcairo-gobject2                install
libcairo2                    install
libcanberra-gtk3-0                install
libcanberra-gtk3-module                install
libcanberra0                    install
libcap-ng0                    install
libcap2                        install
libcap2-bin                    install
libcdio-cdda0                    install
libcdio-paranoia0                install
libcdio10                    install
libck-connector0                install
libclass-accessor-perl                install
libclass-isa-perl                install
libcomerr2                    install
libcroco3                    install
libcups2                    install
libcurl3-gnutls                    install
libcwidget3                    install
libdatrie1                    install
libdb4.8                    install
libdb5.1                    install
libdbus-1-3                    install
libdbus-glib-1-2                install
libdevmapper-event1.02.1            install
libdevmapper1.02.1                install
libdiscover2                    install
libdns69                    install
libdrm-intel1                    install
libdrm-nouveau1a                install
libdrm-radeon1                    install
libdrm2                        install
libedit2                    install
libelf1                        install
libept1                        install
libexif12                    install
libexpat1                    install
libffi6                        install
libfm-data                    install
libfm-gtk-data                    install
libfm-gtk1                    install
libfm1                        install
libfontconfig1                    install
libfontenc1                    install
libfreetype6                    install
libfribidi0                    install
libfs6                        install
libfuse2                    install
libgcc1                        install
libgck-1-0                    install
libgconf2-4                    install
libgcr-3-1                    install
libgcrypt11                    install
libgd2-noxpm                    install
libgdbm3                    install
libgdk-pixbuf2.0-0                install
libgdu0                        install
libgeoip1                    install
libgif4                        install
libgirepository-1.0-1                install
libgksu2-0                    install
libgl1-mesa-dri                    install
libgl1-mesa-glx                    install
libglade2-0                    install
libglapi-mesa                    install
libglib2.0-0                    install
libglu1-mesa                    install
libgmp10                    install
libgnome-keyring0                install
libgnutls26                    install
libgpg-error0                    install
libgphoto2-2                    install
libgphoto2-l10n                    install
libgphoto2-port0                install
libgssapi-krb5-2                install
libgtk-3-0                    install
libgtk-3-bin                    install
libgtk-3-common                    install
libgtk2.0-0                    install
libgtk2.0-bin                    install
libgtk2.0-common                install
libgtop2-7                    install
libgtop2-common                    install
libgudev-1.0-0                    install
libice6                        install
libid3tag0                    install
libidn11                    install
libimlib2                    install
libimobiledevice2                install
libio-string-perl                install
libisc62                    install
libisccc60                    install
libisccfg62                    install
libiw30                        install
libjasper1                    install
libjpeg62                    install
libk5crypto3                    install
libkeyutils1                    install
libklibc                    install
libkrb5-3                    install
libkrb5support0                    install
libldap-2.4-2                    install
libllvm2.9                    install
liblocale-gettext-perl                install
liblockfile1                    install
libltdl7                    install
liblvm2app2.2                    install
liblwres60                    install
liblzma2                    install
libmagic1                    install
libmenu-cache1                    install
libmount1                    install
libmpc2                        install
libmpfr4                    install
libmtdev1                    install
libncurses5                    install
libncursesw5                    install
libnewt0.52                    install
libnfnetlink0                    install
libnih-dbus1                    install
libnih1                        install
libnl3                        install
libnotify4                    install
libobrender27                    install
libobt0                        install
libogg0                        install
libp11-kit0                    install
libpam-ck-connector                install
libpam-gnome-keyring                install
libpam-modules                    install
libpam-modules-bin                install
libpam-runtime                    install
libpam0g                    install
libpango1.0-0                    install
libparse-debianchangelog-perl            install
libparted0debian1                install
libpcap0.8                    install
libpci3                        install
libpciaccess0                    install
libpcre3                    install
libpcsclite1                    install
libpipeline1                    install
libpixman-1-0                    install
libplist1                    install
libplymouth2                    install
libpng12-0                    install
libpod-plainer-perl                install
libpolkit-agent-1-0                install
libpolkit-backend-1-0                install
libpolkit-gobject-1-0                install
libpopt0                    install
libproxy0                    install
libreadline6                    install
librsvg2-2                    install
librsvg2-common                    install
librtmp0                    install
libsasl2-2                    install
libsasl2-modules                install
libselinux1                    install
libsgutils2-2                    install
libsigc++-2.0-0c2a                install
libslang2                    install
libsm6                        install
libsmbclient                    install
libsoup-gnome2.4-1                install
libsoup2.4-1                    install
libsqlite3-0                    install
libss2                        install
libssl1.0.0                    install
libstartup-notification0            install
libstdc++6                    install
libsub-name-perl                install
libswitch-perl                    install
libtalloc2                    install
libtasn1-3                    install
libtdb1                        install
libtext-charwidth-perl                install
libtext-iconv-perl                install
libtext-wrapi18n-perl                install
libthai-data                    install
libthai0                    install
libtiff4                    install
libtimedate-perl                install
libtinfo5                    install
libudev0                    install
libusb-0.1-4                    install
libusb-1.0-0                    install
libusbmuxd1                    install
libutempter0                    install
libutouch-evemu1                install
libutouch-frame1                install
libutouch-grail1                install
libuuid1                    install
libvorbis0a                    install
libvorbisfile3                    install
libwbclient0                    install
libx11-6                    install
libx11-data                    install
libx11-xcb1                    install
libxapian22                    install
libxau6                        install
libxaw7                        install
libxcb-dri2-0                    install
libxcb-render0                    install
libxcb-shape0                    install
libxcb-shm0                    install
libxcb-util0                    install
libxcb1                        install
libxcomposite1                    install
libxcursor1                    install
libxdamage1                    install
libxdmcp6                    install
libxext6                    install
libxfixes3                    install
libxfont1                    install
libxft2                        install
libxi6                        install
libxinerama1                    install
libxkbfile1                    install
libxml2                        install
libxmu6                        install
libxmuu1                    install
libxpm4                        install
libxrandr2                    install
libxrender1                    install
libxt6                        install
libxtst6                    install
libxv1                        install
libxvmc1                    install
libxxf86dga1                    install
libxxf86vm1                    install
linux-firmware                    install
linux-generic                    install
linux-headers-3.0.0-17                install
linux-headers-3.0.0-17-generic            install
linux-headers-generic                install
linux-image-3.0.0-17-generic            install
linux-image-generic                install
locales                        install
lockfile-progs                    install
login                        install
logrotate                    install
lsb-base                    install
lsb-release                    install
lshw                        install
lsof                        install
ltrace                        install
lubuntu-artwork                    install
lubuntu-core                    install
lubuntu-default-settings            install
lubuntu-icon-theme                install
lxde-common                    install
lxde-core                    install
lxdm                        install
lxmenu-data                    install
lxpanel                        install
lxsession                    install
lxtask                        install
makedev                        install
man-db                        install
manpages                    install
manpages-dev                    install
mawk                        install
memtest86+                    install
mime-support                    install
miscfiles                    install
mlocate                        install
module-init-tools                install
mount                        install
mountall                    install
mtools                        install
mtr-tiny                    install
multiarch-support                install
nano                        install
ncurses-base                    install
ncurses-bin                    install
net-tools                    install
netbase                        install
netcat-openbsd                    install
notification-daemon                install
ntfs-3g                        install
ntpdate                        install
obconf                        install
openbox                        install
openbox-themes                    install
openssh-client                    install
openssl                        install
os-prober                    install
parted                        install
passwd                        install
pciutils                    install
pcmanfm                        install
perl                        install
perl-base                    install
perl-modules                    install
plymouth                    install
plymouth-label                    install
plymouth-theme-lubuntu-logo            install
plymouth-theme-lubuntu-text            install
plymouth-theme-ubuntu-text            install
policykit-1                    install
policykit-1-gnome                install
popularity-contest                install
powermgmt-base                    install
ppp                        install
pppconfig                    install
pppoeconf                    install
procps                        install
psmisc                        install
python                        install
python-apt                    install
python-apt-common                install
python-cairo                    install
python-chardet                    install
python-dbus                    install
python-debian                    install
python-gdbm                    install
python-glade2                    install
python-gnupginterface                install
python-gobject                    install
python-gobject-2                install
python-gobject-cairo                install
python-gtk2                    install
python-minimal                    install
python-notify                    install
python-support                    install
python-wicd                    install
python-xapian                    install
python2.7                    install
python2.7-minimal                install
readline-common                    install
rsync                        install
rsyslog                        install
scrot                        install
sed                        install
sensible-utils                    install
sgml-base                    install
shared-mime-info                install
sound-theme-freedesktop                install
strace                        install
sudo                        install
sysv-rc                        install
sysvinit-utils                    install
tar                        install
tasksel                        install
tasksel-data                    install
tcpdump                        install
telnet                        install
time                        install
ttf-dejavu-core                    install
ttf-ubuntu-font-family                install
tzdata                        install
ubuntu-keyring                    install
ubuntu-minimal                    install
ubuntu-standard                    install
ucf                        install
udev                        install
udisks                        install
ufw                        install
update-manager-core                install
upstart                        install
ureadahead                    install
usbmuxd                        install
usbutils                    install
util-linux                    install
uuid-runtime                    install
vim-common                    install
vim-tiny                    install
wget                        install
whiptail                    install
wicd                        install
wicd-daemon                    install
wicd-gtk                    install
wireless-crda                    install
wireless-tools                    install
wpasupplicant                    install
x-ttcidfont-conf                install
x11-apps                    install
x11-common                    install
x11-session-utils                install
x11-utils                    install
x11-xfs-utils                    install
x11-xkb-utils                    install
x11-xserver-utils                install
xauth                        install
xbitmaps                    install
xfonts-base                    install
xfonts-encodings                install
xfonts-scalable                    install
xfonts-utils                    install
xinit                        install
xinput                        install
xkb-data                    install
xml-core                    install
xorg                        install
xorg-docs-core                    install
xserver-common                    install
xserver-xorg                    install
xserver-xorg-core                install
xserver-xorg-input-all                install
xserver-xorg-input-evdev            install
xserver-xorg-input-mouse            install
xserver-xorg-input-synaptics            install
xserver-xorg-input-vmmouse            install
xserver-xorg-input-wacom            install
xserver-xorg-video-all                install
xserver-xorg-video-ati                install
xserver-xorg-video-cirrus            install
xserver-xorg-video-fbdev            install
xserver-xorg-video-geode            install
xserver-xorg-video-intel            install
xserver-xorg-video-mach64            install
xserver-xorg-video-mga                install
xserver-xorg-video-neomagic            install
xserver-xorg-video-nouveau            install
xserver-xorg-video-openchrome            install
xserver-xorg-video-qxl                install
xserver-xorg-video-r128                install
xserver-xorg-video-radeon            install
xserver-xorg-video-s3                install
xserver-xorg-video-savage            install
xserver-xorg-video-siliconmotion        install
xserver-xorg-video-sis                install
xserver-xorg-video-sisusb            install
xserver-xorg-video-tdfx                install
xserver-xorg-video-trident            install
xserver-xorg-video-vesa                install
xserver-xorg-video-vmware            install
xterm                        install
xz-utils                    install
zlib1g                        install


```


What I want to achieve is: Remove as much packages as possible AND possibly replace an installed package with a lighter package (including the DE and WM) and keep that machine running.

Important Note: The Physical State of that machine will not allow me to take the HDD out yet again after I have done that 2 years ago and install whatever other minimal system is and put it back in. There is a great chance I might break something so I don't want that. I want to learn how to achieve the most minimum installation and still have that machine working so this is After-Installation Tweak.

Thank you and I am looking forward to read your suggestions!

P.S.
In case you are wondering, YES, that machine is actually working (despite it is from 1999) but of course, it is very slow.

---

### Post by buzzingrobot on 2013-09-20
The best way to get to a barebones installation is to do a network/mini.iso intallation, as long as the machine has net connectivity at install time (preferably, wired ethernet).

You boot a very small ISO image that contains just enough software to boot and connect to a server. The remainder of the install components and any packages you select are downloaded and then installed.

During the install. you are asked to select from a lengthy list of desktop environment options.  If you select none of these options, you will achieve a command line-only envirionment:  No X, no DE, no window manager. Just Bash and the standard character-based tool set.  You'll boot to a prompt and can build a system as you see fit by drawing from the repos.

An exact list of what to remove from an existing installation would, first, be very lengthy, and, second, very difficult to compile given the drivers a machine needs and the dependency chains they establish. Also, removing any large number of packages that you don't want is sure to remove some dependencies that you need, and you'll need to identify those and re-install them.  Gets very messy.

---

### Post by Bucky Ball on 2013-09-20
@ buzzingrobot: OP specifically states that they want to trim the release they have installed, NOT reinstall a mini.iso or anything else. ;)

---

### Post by amjjawad on 2013-09-20
> **Bucky Ball said:**
> @ buzzingrobot: OP specifically states that they want to trim the release they have installed, NOT reinstall a mini.iso or anything else. ;)

+1

That is exactly why I have tagged this thread with [Special Case] and I have mentioned a note at the header of my first post :)

Thanks!

---

### Post by ibjsb4 on 2013-09-20
A still working PII, amazing :)

One thing that strikes me is all the extra generic drivers (xserver-xorg-video).  I think you will not see much space gain by removing them, but could speed up your boot time.

Myself, to make things a little easier, I would install synaptic package manager.  Just would make it easier to see whats getting removed.

After you get as much removed as you can, you could use the autoremove command for further cleanup.  But for a deeper cleaning I think I would install deborphan and take a very close look at the removal list before using.

---

### Post by buzzingrobot on 2013-09-20
> **Bucky Ball said:**
> @ buzzingrobot: OP specifically states that they want to trim the release they have installed, NOT reinstall a mini.iso or anything else. ;)

OK, apologies.  Then I have nothing to offer other than trial and error, or locating a list of packages in such a minimal installation, comparing it to a list of the currently installed packages, and generating a list of packages for removal.

---

### Post by amjjawad on 2013-09-20
> **ibjsb4 said:**
> A still working PII, amazing :)

Hi,

You know, old hardware are much better and stronger than new one. My newer laptops are giving me hard time!

> One thing that strikes me is all the extra generic drivers (xserver-xorg-video).  I think you will not see much space gain by removing them, but could speed up your boot time.
Space is not a problem for me, nor the booting time :)
All what I care about is the memory usage. I am not sure if I would remove some of those, it will make any difference?

>  Myself, to make things a little easier, I would install synaptic package manager.  Just would make it easier to see whats getting removed.
Synaptic will kill that machine :D
For that machine, I need to use Terminal only ;)

> But for a deeper cleaning I think I would install deborphan and take a very close look at the removal list before using.
I am sorry, I did not understand this one?

---

### Post by ibjsb4 on 2013-09-20
> Space is not a problem for me, nor the booting time :smile:
All what I care about is the memory usage. I am not sure if I would remove some of those, it will make any difference?

I wouldn't think so since I suspect they are dormant and would not use any memory.  At least thats my guess.

>  			 				But for a deeper cleaning I think I would install deborphan and take a very close look at the removal list before using. 			 		 	 I am sorry, I did not understand this one? 

Deborphan, like autoremove will look for unused (leftover) packages.  Deborphan can be over zealous and try to remove too many packages so a close look of the packages to be removed is necessary.  But if you cannot run synaptic I suspect you will not be able to use this.

---

### Post by bkline on 2013-09-20
> **amjjawad said:**
> For that machine, I need to use Terminal only ;)

I would have assumed with the hardware we're talking about that you wouldn't be bothering with X, and this comment seems to confirm that assumption.  But your original post referred to "WM" which I took to mean the window manager.  Is the graphical interface a requirement?

---

### Post by amjjawad on 2013-09-20
> **ibjsb4 said:**
> I wouldn't think so since I suspect they are dormant and would not use any memory.  At least thats my guess.
I share the same guess with you!

> Deborphan, like autoremove will look for unused (leftover) packages.  Deborphan can be over zealous and try to remove too many packages so a close look of the packages to be removed is necessary.  But if you cannot run synaptic I suspect you will not be able to use this.
I am planning to do this manually. With my special case with this machine and more than a month (see my first post) to make that machine works, I must be careful and go for manual removal for better control. That is why, I posted the list of the installed packages :)

---

### Post by amjjawad on 2013-09-20
> **bkline said:**
> I would have assumed with the hardware we're talking about that you wouldn't be bothering with X, and this comment seems to confirm that assumption.  But your original post referred to "WM" which I took to mean the window manager.  Is the graphical interface a requirement?
I think you misunderstood my post.

I need to use Terminal because loading Synaptic might take forever. We are talking about a machine from 1999 with P2 and 64MB RAM. With Terminal, my life is much easier on that machine.

That machine for now, as I posted on the first post, a running Lubuntu 11.10 (yes, I know it is outdated but I don't care about that). I do have a DE and WM since this is Lubuntu - See this: [http://ubuntuforums.org/showthread.php?t=1590614&page=16&p=11832431#post11832431](http://ubuntuforums.org/showthread.php?t=1590614&page=16&p=11832431#post11832431)

I think my best option would be getting rid of the DE (LXDE) and go for something much lighter. But I'd like first to remove some packages and see if that will make any difference.

I must be careful and NOT remove a package that will break my system and then, that machine would be not usable and I don't want that.

---

