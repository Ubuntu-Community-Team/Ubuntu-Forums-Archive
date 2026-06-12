---
title: "[REOPENED] How to fix HDMI Audio on Ubuntu 14.04 LTS Intel NUC (update broke it)?"
date: 2015-09-10
forum: General Help
---

### Post by nuc_buntu on 2015-09-10
hi!

i know this question is often asked and has a lot of solutions, but none worked for me. After running the package-update from GUI i was watching movie with xbmc and everything worked (and has worked for months). Next day i power on and sound is gone. I had this problem once and if i remember correctly i was able to fix it with adding the the daily-alsa repository and installing the oem package (or i deinstalled pulseaudio/alsa and reinstalled, not sure). I tried everything i found on the web and nothing works. I know some stuff about Linux, but i'm stuck here - please help, this is my HTPC and having no sound is a true PITA :(

System: Intel NUC-Kit D34010WYK (i3)
OS: Ubuntu 14.04 LTS

i tried:

[LIST]
[*]deinstalled/reinstalled alsa-base, alsa-utils, pulseaudio, linux-sound-base, oem-audio-hda-daily-dkms
[*]sudo alsa force-reload
[/LIST]

things worth to mention (maybe?)

[LIST]
[*]i found no .asoundrc nor do i have a ~/.pulse folder
[*]alsamixer shows one channel (s/pdif) and i cant change the volume on it
[*]pulseaudio cmd results in error:
[/LIST]
```
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

```
I think i have the update-log which broke my audio:

```
Start-Date: 2015-09-08  23:20:20
Commandline: aptdaemon role='role-commit-packages' sender=':1.60'
Install: linux-image-extra-3.13.0-63-generic:amd64 (3.13.0-63.103)
libplatform1:amd64 (1.0.10-1~trusty, automatic)
linux-image-3.13.0-63-generic:amd64 (3.13.0-63.103)
linux-headers-3.13.0-63-generic:amd64 (3.13.0-63.103)
libcec3:amd64 (3.0.1-1~trusty)
linux-signed-image-3.13.0-63-generic:amd64 (3.13.0-63.103)
linux-headers-3.13.0-63:amd64 (3.13.0-63.103)
Upgrade: bind9-host:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
shim-signed:amd64 (1.6+0.4-0ubuntu4, 1.9+0.8-0ubuntu2)
initscripts:amd64 (2.88dsf-41ubuntu6.1, 2.88dsf-41ubuntu6.2)
python3-problem-report:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12)
oxideqt-codecs:amd64 (1.7.8-0ubuntu0.14.04.1, 1.8.4-0ubuntu0.14.04.2)
oem-audio-hda-daily-dkms:amd64 (0.201506190242~ubuntu14.04.1, 0.201509081346~ubuntu14.04.1)
liblwres90:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
gir1.2-udisks-2.0:amd64 (2.1.3-1, 2.1.3-1ubuntu0.1)
apt:amd64 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10)
hplip:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4)
libfontembed1:amd64 (1.0.52-0ubuntu1.4, 1.0.52-0ubuntu1.5)
libasan0:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libsystemd-login0:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
linux-headers-generic:amd64 (3.13.0.55.62, 3.13.0.63.71)
libquadmath0:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
gcc-4.8-base:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
gcc-4.8-base:i386 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
grub-efi-amd64-bin:amd64 (2.02~beta2-9ubuntu1.2, 2.02~beta2-9ubuntu1.3)
gdisk:amd64 (0.8.8-1build1, 0.8.8-1ubuntu0.1)
libwmf0.2-7:amd64 (0.2.8.4-10.3ubuntu1, 0.2.8.4-10.3ubuntu1.14.04.1)
libpython2.7-stdlib:amd64 (2.7.6-8, 2.7.6-8ubuntu0.2)
libdns100:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
python-samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
libisccfg90:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
systemd-services:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
grub-efi-amd64:amd64 (2.02~beta2-9ubuntu1.2, 2.02~beta2-9ubuntu1.3)
apt-transport-https:amd64 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10)
python-pkg-resources:amd64 (3.3-1ubuntu1, 3.3-1ubuntu2)
isc-dhcp-common:amd64 (4.2.4-7ubuntu12.2, 4.2.4-7ubuntu12.3)
libbind9-90:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
openjdk-6-jre-lib:amd64 (6b35-1.13.7-1ubuntu0.14.04.1, 6b36-1.13.8-0ubuntu1~14.04)
libsane-hpaio:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4)
firefox-locale-en:amd64 (38.0+build3-0ubuntu0.14.04.1, 40.0.3+build1-0ubuntu0.14.04.1)
python3.4:amd64 (3.4.0-2ubuntu1, 3.4.0-2ubuntu1.1)
cpp-4.8:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libgomp1:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
dkms:amd64 (2.2.0.3-1.1ubuntu5.14.04, 2.2.0.3-1.1ubuntu5.14.04.1)
xul-ext-ubufox:amd64 (3.0-0ubuntu0.14.04.1, 3.1-0ubuntu0.14.04.1)
libtsan0:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libgdk-pixbuf2.0-common:amd64 (2.30.7-0ubuntu1, 2.30.7-0ubuntu1.1)
apt-utils:amd64 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10)
iproute2:amd64 (3.12.0-2, 3.12.0-2ubuntu1)
udisks2:amd64 (2.1.3-1, 2.1.3-1ubuntu0.1)
thunderbird:amd64 (31.7.0+build1-0ubuntu0.14.04.1, 38.2.0+build1-0ubuntu0.14.04.1)
libhpmud0:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4)
libtag1c2a:amd64 (1.9.1-2, 1.9.1-2.2~ppa~trusty)
ubuntu-drivers-common:amd64 (0.2.91.9, 0.2.91.11)
firefox:amd64 (38.0+build3-0ubuntu0.14.04.1, 40.0.3+build1-0ubuntu0.14.04.1)
mount:amd64 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6)
icedtea-6-jre-cacao:amd64 (6b35-1.13.7-1ubuntu0.14.04.1, 6b36-1.13.8-0ubuntu1~14.04)
samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
python3.4-minimal:amd64 (3.4.0-2ubuntu1, 3.4.0-2ubuntu1.1)
parted:amd64 (2.3-19ubuntu1, 2.3-19ubuntu1.14.04.1)
libsystemd-daemon0:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
libgudev-1.0-0:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
libgs9-common:amd64 (9.10~dfsg-0ubuntu10.2, 9.10~dfsg-0ubuntu10.4)
tzdata-java:amd64 (2015d-0ubuntu0.14.04, 2015f-0ubuntu0.14.04)
grub-common:amd64 (2.02~beta2-9ubuntu1.2, 2.02~beta2-9ubuntu1.3)
dh-python:amd64 (1.20140128-1ubuntu8, 1.20140128-1ubuntu8.2)
libwmf0.2-7-gtk:amd64 (0.2.8.4-10.3ubuntu1, 0.2.8.4-10.3ubuntu1.14.04.1)
libapparmor1:amd64 (2.8.95~2430-0ubuntu5.1, 2.8.95~2430-0ubuntu5.3)
libpython3.4-stdlib:amd64 (3.4.0-2ubuntu1, 3.4.0-2ubuntu1.1)
libpam-systemd:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
python3-pkg-resources:amd64 (3.3-1ubuntu1, 3.3-1ubuntu2)
gir1.2-gdkpixbuf-2.0:amd64 (2.30.7-0ubuntu1, 2.30.7-0ubuntu1.1)
python2.7:amd64 (2.7.6-8, 2.7.6-8ubuntu0.2)
openjdk-6-jre-headless:amd64 (6b35-1.13.7-1ubuntu0.14.04.1, 6b36-1.13.8-0ubuntu1~14.04)
flashplugin-installer:amd64 (11.2.202.466ubuntu0.14.04.1, 11.2.202.508ubuntu0.14.04.1)
python3-requests:amd64 (2.2.1-1ubuntu0.2, 2.2.1-1ubuntu0.3)
libapt-inst1.5:amd64 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10)
libuuid1:amd64 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6)
libnss3-1d:amd64 (3.17.4-0ubuntu0.14.04.1, 3.19.2-0ubuntu0.14.04.1)
libmount1:amd64 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6)
libsnmp-base:amd64 (5.7.2~dfsg-8.1ubuntu3, 5.7.2~dfsg-8.1ubuntu3.1)
kodi:amd64 (14.2~git20150327.1058-final-0trusty, 15.1~git20150816.1137-final-0trusty)
libpython3.4:amd64 (3.4.0-2ubuntu1, 3.4.0-2ubuntu1.1)
dnsutils:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
kodi-bin:amd64 (14.2~git20150327.1058-final-0trusty, 15.1~git20150816.1137-final-0trusty)
ssh-askpass-gnome:amd64 (6.6p1-2ubuntu2, 6.6p1-2ubuntu2.3)
udev:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
base-files:amd64 (7.2ubuntu5.2, 7.2ubuntu5.3)
patch:amd64 (2.7.1-4ubuntu2, 2.7.1-4ubuntu2.3)
printer-driver-postscript-hp:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4)
samba-dsdb-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
grub2-common:amd64 (2.02~beta2-9ubuntu1.2, 2.02~beta2-9ubuntu1.3)
bash-completion:amd64 (2.1-4, 2.1-4ubuntu0.1)
libatomic1:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libnss3-nssdb:amd64 (3.17.4-0ubuntu0.14.04.1, 3.19.2-0ubuntu0.14.04.1)
ghostscript-x:amd64 (9.10~dfsg-0ubuntu10.2, 9.10~dfsg-0ubuntu10.4)
libsqlite3-0:amd64 (3.8.2-1ubuntu2, 3.8.2-1ubuntu2.1)
libpython3.4-minimal:amd64 (3.4.0-2ubuntu1, 3.4.0-2ubuntu1.1)
libunity-control-center1:amd64 (14.04.3+14.04.20140922-0ubuntu1, 14.04.3+14.04.20140922-0ubuntu1.1)
gir1.2-gudev-1.0:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
samba-common-bin:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
openjdk-6-jre:amd64 (6b35-1.13.7-1ubuntu0.14.04.1, 6b36-1.13.8-0ubuntu1~14.04)
cups-browsed:amd64 (1.0.52-0ubuntu1.4, 1.0.52-0ubuntu1.5)
libparted0debian1:amd64 (2.3-19ubuntu1, 2.3-19ubuntu1.14.04.1)
liboxideqtcore0:amd64 (1.7.8-0ubuntu0.14.04.1, 1.8.4-0ubuntu0.14.04.2)
libudev1:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
libudev1:i386 (204-5ubuntu20.12, 204-5ubuntu20.13)
binutils:amd64 (2.24-5ubuntu3.1, 2.24-5ubuntu13)
linux-image-extra-3.13.0-55-generic:amd64 (3.13.0-55.92, 3.13.0-55.94)
cups-filters-core-drivers:amd64 (1.0.52-0ubuntu1.4, 1.0.52-0ubuntu1.5)
linux-headers-3.13.0-55:amd64 (3.13.0-55.92, 3.13.0-55.94)
linux-image-3.13.0-55-generic:amd64 (3.13.0-55.92, 3.13.0-55.94)
bsdutils:amd64 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6)
libapparmor-perl:amd64 (2.8.95~2430-0ubuntu5.1, 2.8.95~2430-0ubuntu5.3)
linux-signed-generic:amd64 (3.13.0.55.62, 3.13.0.63.71)
grub-efi-amd64-signed:amd64 (1.34.3+2.02~beta2-9ubuntu1.2, 1.34.4+2.02~beta2-9ubuntu1.3)
samba-libs:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
openssh-client:amd64 (6.6p1-2ubuntu2, 6.6p1-2ubuntu2.3)
libapt-pkg4.12:amd64 (1.0.1ubuntu2.8, 1.0.1ubuntu2.10)
efibootmgr:amd64 (0.5.4-7ubuntu1.1, 0.5.4-7ubuntu1.2)
uuid-runtime:amd64 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6)
libgcc-4.8-dev:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libpython2.7:amd64 (2.7.6-8, 2.7.6-8ubuntu0.2)
libpcre3-dev:amd64 (8.31-2ubuntu2, 8.31-2ubuntu2.1)
mysql-common:amd64 (5.5.43-0ubuntu0.14.04.1, 5.5.44-0ubuntu0.14.04.1)
python-six:amd64 (1.5.2-1, 1.5.2-1ubuntu1)
xbmc:amd64 (14.2~git20150327.1058-final-0trusty, 15.1~git20150816.1137-final-0trusty)
thunderbird-gnome-support:amd64 (31.7.0+build1-0ubuntu0.14.04.1, 38.2.0+build1-0ubuntu0.14.04.1)
libtag1-vanilla:amd64 (1.9.1-2, 1.9.1-2.2~ppa~trusty)
gcc-4.8:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libsystemd-journal0:amd64 (204-5ubuntu20.12, 204-5ubuntu20.13)
isc-dhcp-client:amd64 (4.2.4-7ubuntu12.2, 4.2.4-7ubuntu12.3)
libnss3:amd64 (3.17.4-0ubuntu0.14.04.1, 3.19.2-0ubuntu0.14.04.1)
libmysqlclient18:amd64 (5.5.43-0ubuntu0.14.04.1, 5.5.44-0ubuntu0.14.04.1)
sysv-rc:amd64 (2.88dsf-41ubuntu6.1, 2.88dsf-41ubuntu6.2)
cups-filters:amd64 (1.0.52-0ubuntu1.4, 1.0.52-0ubuntu1.5)
unity-settings-daemon:amd64 (14.04.0+14.04.20140606-0ubuntu2, 14.04.0+14.04.20140606-0ubuntu3)
smbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
linux-headers-3.13.0-55-generic:amd64 (3.13.0-55.92, 3.13.0-55.94)
printer-driver-hpcups:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4)
unity-control-center:amd64 (14.04.3+14.04.20140922-0ubuntu1, 14.04.3+14.04.20140922-0ubuntu1.1)
apport-gtk:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12)
lightdm:amd64 (1.10.5-0ubuntu1, 1.10.5-0ubuntu1.1)
liboxideqtquick0:amd64 (1.7.8-0ubuntu0.14.04.1, 1.8.4-0ubuntu0.14.04.2)
passwd:amd64 (4.1.5.1-1ubuntu9, 4.1.5.1-1ubuntu9.1)
apport:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12)
libgs9:amd64 (9.10~dfsg-0ubuntu10.2, 9.10~dfsg-0ubuntu10.4)
libpcrecpp0:amd64 (8.31-2ubuntu2, 8.31-2ubuntu2.1)
linux-signed-image-generic:amd64 (3.13.0.55.62, 3.13.0.63.71)
linux-firmware:amd64 (1.127.12, 1.127.15)
python-requests:amd64 (2.2.1-1ubuntu0.2, 2.2.1-1ubuntu0.3)
python2.7-minimal:amd64 (2.7.6-8, 2.7.6-8ubuntu0.2)
sysvinit-utils:amd64 (2.88dsf-41ubuntu6.1, 2.88dsf-41ubuntu6.2)
liboxideqt-qmlplugin:amd64 (1.7.8-0ubuntu0.14.04.1, 1.8.4-0ubuntu0.14.04.2)
libblkid1:amd64 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6)
liblightdm-gobject-1-0:amd64 (1.10.5-0ubuntu1, 1.10.5-0ubuntu1.1)
login:amd64 (4.1.5.1-1ubuntu9, 4.1.5.1-1ubuntu9.1)
libgdk-pixbuf2.0-0:amd64 (2.30.7-0ubuntu1, 2.30.7-0ubuntu1.1)
hplip-data:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4)
libexpat1:amd64 (2.1.0-4ubuntu1, 2.1.0-4ubuntu1.1)
libexpat1:i386 (2.1.0-4ubuntu1, 2.1.0-4ubuntu1.1)
python3-apport:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12)
apparmor:amd64 (2.8.95~2430-0ubuntu5.1, 2.8.95~2430-0ubuntu5.3)
tzdata:amd64 (2015d-0ubuntu0.14.04, 2015f-0ubuntu0.14.04)
libwbclient0:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
samba-vfs-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
libvdpau1:amd64 (0.7-1, 0.7-1ubuntu0.1)
linux-libc-dev:amd64 (3.13.0-55.92, 3.13.0-63.103)
util-linux:amd64 (2.20.1-5.1ubuntu20.4, 2.20.1-5.1ubuntu20.6)
iproute:amd64 (3.12.0-2, 3.12.0-2ubuntu1)
ghostscript:amd64 (9.10~dfsg-0ubuntu10.2, 9.10~dfsg-0ubuntu10.4)
samba-common:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
python3-six:amd64 (1.5.2-1, 1.5.2-1ubuntu1)
libstdc++6:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libstdc++6:i386 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
libpcre3:amd64 (8.31-2ubuntu2, 8.31-2ubuntu2.1)
icedtea-6-jre-jamvm:amd64 (6b35-1.13.7-1ubuntu0.14.04.1, 6b36-1.13.8-0ubuntu1~14.04)
libudisks2-0:amd64 (2.1.3-1, 2.1.3-1ubuntu0.1)
libitm1:amd64 (4.8.2-19ubuntu1, 4.8.4-2ubuntu1~14.04)
unattended-upgrades:amd64 (0.82.1ubuntu2.2, 0.82.1ubuntu2.3)
libsnmp30:amd64 (5.7.2~dfsg-8.1ubuntu3, 5.7.2~dfsg-8.1ubuntu3.1)
libpython2.7-minimal:amd64 (2.7.6-8, 2.7.6-8ubuntu0.2)
linux-signed-image-3.13.0-55-generic:amd64 (3.13.0-55.92, 3.13.0-55.94)
linux-image-generic:amd64 (3.13.0.55.62, 3.13.0.63.71)
irqbalance:amd64 (1.0.6-2ubuntu0.14.04.1, 1.0.6-2ubuntu0.14.04.2)
libisccc90:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
shim:amd64 (0.4-0ubuntu4, 0.8-0ubuntu2)
libsmbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.7, 4.1.6+dfsg-1ubuntu2.14.04.9)
libisc95:amd64 (9.9.5.dfsg-3ubuntu0.2, 9.9.5.dfsg-3ubuntu0.5)
linux-generic:amd64 (3.13.0.55.62, 3.13.0.63.71)
libcupsfilters1:amd64 (1.0.52-0ubuntu1.4, 1.0.52-0ubuntu1.5)
Remove: libcec2:amd64 (2.2.0-2~trusty)
End-Date: 2015-09-08  23:30:27

```

i guess its this:
```
oem-audio-hda-daily-dkms:amd64 (0.201506190242~ubuntu14.04.1, 0.201509081346~ubuntu14.04.1)
```

i tried to force version with synaptic package manager or even download old version manually but haven't found it on the web :(

any help very much appreciated - i can provide any info you need (aplay -l etc, just tell me)
thx

---

### Post by XBNCPRk on 2015-09-10
XBMC (now Kodi) sometimes has issues with resetting the default audio out device, especially with updates like the one I see listed on your log. On its system settings menu, make sure the correct output is selected. 
Also, with the sound config panel from your desktop, are you able to hear anything using the test buttons for each speaker channel?

---

### Post by nuc_buntu on 2015-09-10
no, cant hear anything using the test sound feature... also played music from browser and tried the speaker-test command (but not sure if i used it correctly) but no sound at all - [COLOR=#333333][FONT=Ubuntu Beta]pavucontrol definitely shows activity when playing something, but nothing comes out of the tv-speaker[/FONT][/COLOR]. thank you very much for your reply

---

### Post by Yellow Pasque on 2015-09-10
> i found no .asoundrc nor do i have a ~/.pulse folder

You don't need .asoundrc and .pulse moved to ~/.config/pulse. If you want to try resetting it:
```
rm -r ~/.config/pulse*; pulseaudio -k
```

Also, see if you can get more detailed information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by XBNCPRk on 2015-09-10
I see that grub also updated? When you set up the system originally did you have to add any tags to it (either nomodeset, or radeon.audio=1, etc) to get sound, and if so, are those still there?  

Last, can you grab a set of headphones and shove em in to the jack, just to make sure the system is producing audio correctly, just that its not on the correct output?

---

### Post by nuc_buntu on 2015-09-11
AlsaInfo:
```
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Fri Sep 11 10:17:20 UTC 2015




!!Linux Distribution
!!------------------


Ubuntu 14.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer:
Product Name:
Product Version:
Firmware Version:  WYLPT10H.86A.0028.2014.0814.1906




!!Kernel Information
!!------------------


Kernel release:    3.13.0-63-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.13.0-63-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2




!!Loaded ALSA modules
!!-------------------


snd_hda_intel
snd_hda_intel




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7c34000 irq 63
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7c30000 irq 64




!!PCI Soundcards installed in the system
!!--------------------------------------


00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:03.0 0403: 8086:0a0c (rev 09)
        Subsystem: 8086:2054
--
00:1b.0 0403: 8086:9c20 (rev 04)
        Subsystem: 8086:2054




!!Modprobe options (Sound related)
!!--------------------------------


snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
        align_buffer_size : -1
        bdl_pos_adj : 32,1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
        enable_msi : -1
        id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        power_save : 0
        power_save_controller : Y
        probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        single_cmd : N
        snoop : -1


!!Module: snd_hda_intel
        align_buffer_size : -1
        bdl_pos_adj : 32,1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
        enable_msi : -1
        id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        power_save : 0
        power_save_controller : Y
        probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        single_cmd : N
        snoop : -1




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: Intel ID 2807
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862807
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="ID 2807 Digital", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Codec: Realtek ALC283
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0283
Subsystem Id: 0x80862054
Revision Id: 0x100003
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC283 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC283 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0xbf 0xbf]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00]
  Connection: 1
     0x0d
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x12
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x0c
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a11020: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001373c: IN OUT HP EAPD Detect
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40941905: [N/A] Aux at Ext N/A
    Conn = RCA, Color = Black
    DefAssociation = 0x0, Sequence = 0x5
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=73
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x03211010: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D3, actual=D3
  Connection: 2
     0x0c* 0x0d
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  4 Sep 11 12:13 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  8 Sep 11 12:13 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  3 Sep 11 12:13 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  7 Sep 11 12:13 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  2 Sep 11 12:13 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  6 Sep 11 12:13 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  5 Sep 11 12:13 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  1 Sep 11 12:13 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Sep 11 12:13 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Sep 11 12:13 .
drwxr-xr-x 3 root root 240 Sep 11 12:13 ..
lrwxrwxrwx 1 root root  12 Sep 11 12:13 pci-0000:00:03.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Sep 11 12:13 pci-0000:00:1b.0 -> ../controlC1




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: ID 2807 Digital [ID 2807 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [HDMI]


Card hw:0 'HDMI'/'HDA Intel HDMI at 0xf7c34000 irq 63'
  Mixer name    : 'Intel ID 2807'
  Components    : 'HDA:80862807,80860101,00100000'
  Controls      : 6
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!-------Mixer controls for card 1 [PCH]


Card hw:1 'PCH'/'HDA Intel PCH at 0xf7c30000 irq 64'
  Mixer name    : 'Realtek ALC283'
  Components    : 'HDA:10ec0283,80862054,00100003'
  Controls      : 14
  Simple ctrls  : 6
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 63 [100%] [30.00dB] [off]
  Front Right: Capture 63 [100%] [30.00dB] [off]




!!Alsactl output
!!--------------


--startcollapse--
state.HDMI {
        control.1 {
                iface MIXER
                name 'IEC958 Playback Con Mask'
                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.2 {
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.3 {
                iface MIXER
                name 'IEC958 Playback Default'
                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access 'read write'
                        type IEC958
                        count 1
                }
        }
        control.4 {
                iface MIXER
                name 'IEC958 Playback Switch'
                value true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.5 {
                iface CARD
                name 'HDMI Jack'
                value true
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.6 {
                iface PCM
                device 3
                name 'Playback Channel Map'
                value.0 0
                value.1 0
                comment {
                        access read
                        type INTEGER
                        count 2
                        range '0 - 36'
                }
        }
}
state.PCH {
        control.1 {
                iface MIXER
                name 'Master Playback Volume'
                value.0 87
                value.1 87
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 87'
                        dbmin -6525
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.2 {
                iface MIXER
                name 'Master Playback Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.3 {
                iface MIXER
                name 'Mic Playback Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -3450
                        dbmax 1200
                        dbvalue.0 -3450
                        dbvalue.1 -3450
                }
        }
        control.4 {
                iface MIXER
                name 'Mic Playback Switch'
                value.0 false
                value.1 false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.5 {
                iface MIXER
                name 'Capture Volume'
                value.0 63
                value.1 63
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 63'
                        dbmin -1725
                        dbmax 3000
                        dbvalue.0 3000
                        dbvalue.1 3000
                }
        }
        control.6 {
                iface MIXER
                name 'Capture Switch'
                value.0 false
                value.1 false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.7 {
                iface MIXER
                name 'Mic Boost Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 3'
                        dbmin 0
                        dbmax 3600
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.8 {
                iface CARD
                name 'Mic Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.9 {
                iface CARD
                name 'Headphone Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.10 {
                iface MIXER
                name 'Beep Playback Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -3450
                        dbmax 1200
                        dbvalue.0 -3450
                        dbvalue.1 -3450
                }
        }
        control.11 {
                iface MIXER
                name 'Beep Playback Switch'
                value.0 false
                value.1 false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.12 {
                iface PCM
                name 'Playback Channel Map'
                value.0 0
                value.1 0
                comment {
                        access read
                        type INTEGER
                        count 2
                        range '0 - 36'
                }
        }
        control.13 {
                iface PCM
                name 'Capture Channel Map'
                value.0 0
                value.1 0
                comment {
                        access read
                        type INTEGER
                        count 2
                        range '0 - 36'
                }
        }
        control.14 {
                iface MIXER
                name 'PCM Playback Volume'
                value.0 255
                value.1 255
                comment {
                        access 'read write user'
                        type INTEGER
                        count 2
                        range '0 - 255'
                        tlv '0000000100000008ffffec1400000014'
                        dbmin -5100
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
}
--endcollapse--




!!All Loaded Modules
!!------------------


Module
ses
enclosure
snd_hda_codec_realtek
snd_hda_codec_generic
joydev
hid_generic
snd_hda_intel
snd_hda_codec
snd_hda_core
rfcomm
snd_hwdep
bnep
intel_rapl
bluetooth
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm_intel
kvm
snd_pcm
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
aesni_intel
aes_x86_64
lrw
gf128mul
glue_helper
ablk_helper
snd_page_alloc
cryptd
snd_seq_midi
snd_seq_midi_event
ir_mce_kbd_decoder
ir_lirc_codec
lirc_dev
usb_storage
ir_sanyo_decoder
usbhid
hid
ir_sony_decoder
ir_jvc_decoder
ir_rc6_decoder
snd_rawmidi
ir_nec_decoder
ir_rc5_decoder
nls_iso8859_1
rc_rc6_mce
nuvoton_cir
snd_seq
rc_core
i915
mac_hid
video
drm_kms_helper
snd_seq_device
drm
parport_pc
snd_timer
lpc_ich
i2c_algo_bit
mei_me
snd
ppdev
mei
soundcore
lp
parport
e1000e
ahci
ptp
libahci
pps_core




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010


/sys/class/sound/hwC0D0/driver_pin_configs:


/sys/class/sound/hwC0D0/user_pin_configs:


/sys/class/sound/hwC0D0/init_verbs:


/sys/class/sound/hwC0D0/hints:


/sys/class/sound/hwC1D0/init_pin_configs:
0x12 0x411111f0
0x14 0x40000000
0x17 0x411111f0
0x18 0x411111f0
0x19 0x03a11020
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40941905
0x1e 0x411111f0
0x21 0x03211010


/sys/class/sound/hwC1D0/driver_pin_configs:


/sys/class/sound/hwC1D0/user_pin_configs:


/sys/class/sound/hwC1D0/init_verbs:


/sys/class/sound/hwC1D0/hints:




!!ALSA/HDA dmesg
!!--------------


[    2.983954] Bluetooth: BNEP socket layer initialized
[    2.993728] snd_hda_core: module verification failed: signature and/or  required key missing - tainting kernel
[    3.021497] input: MOSART Semi. 2.4G Keyboard Mouse as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/input/input4
--
[    3.227416] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.227447] snd_hda_intel 0000:00:03.0: Probing card using HDA DKMS, version 0.201509081346~ubuntu14.04.1
[    3.227464] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    3.227795] snd_hda_intel 0000:00:03.0: irq 63 for MSI/MSI-X
[    3.227854] snd_hda_intel 0000:00:1b.0: Probing card using HDA DKMS, version 0.201509081346~ubuntu14.04.1
[    3.227864] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    3.228755] snd_hda_intel 0000:00:1b.0: irq 64 for MSI/MSI-X
[    3.239172] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[    3.241288] type=1400 audit(1441966398.954:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=620 comm="apparmor_parser"
--
[    3.242005] type=1400 audit(1441966398.954:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=620 comm="apparmor_parser"
[    3.249553] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC283: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
[    3.249558] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.249561] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.249562] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    3.249564] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    3.249566] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[    3.250040] snd_hda_codec_hdmi: Unknown symbol snd_hdac_i915_register_notifier (err 0)
[    3.252348] snd_hda_codec_generic hdaudioC0D0: autoconfig for ID 2807: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[    3.252355] snd_hda_codec_generic hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.252359] snd_hda_codec_generic hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.252362] snd_hda_codec_generic hdaudioC0D0:    mono: mono_out=0x0
[    3.252365] snd_hda_codec_generic hdaudioC0D0:    dig-out=0x3/0x0
[    3.252368] snd_hda_codec_generic hdaudioC0D0:    inputs:
[    3.252871] input: HDA Intel HDMI HDMI as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[    3.294051] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[    3.294170] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
[    3.745993] init: samba-ad-dc main process (882) terminated with status 1
```

It's been quite a since i did the setup of my nuc, but i think i didn't change anything in GRUB. I did everthing with online-guides and as i just searched i find no info that such changes may be needed for NUC/Ubuntu.

In the meantime i tried everything suggested on: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

still no sound :(

gonna try headphones and will report back, thx guys!

EDIT: headphones are working!

Here is a Screenshot of AlsaMixer (to me it looks weird, maybe it helps):
[IMG]http://i.imgur.com/Lb5ak5e.jpg[/IMG]

EDIT2:
just downloaded 15.04 on an USB-drive and sound worked out of the box :D:(:confused:

here is the alsa-info from live-os. maybe you can tell what is different/the problem:
```
!!################################!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Fri Sep 11 11:04:49 UTC 2015




!!Linux Distribution
!!------------------


Ubuntu 15.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.04" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"




!!DMI Information
!!---------------


Manufacturer:
Product Name:
Product Version:
Firmware Version:  WYLPT10H.86A.0028.2014.0814.1906




!!Kernel Information
!!------------------


Kernel release:    3.19.0-15-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.19.0-15-generic
Library version:    1.0.28
Utilities version:  1.0.28




!!Loaded ALSA modules
!!-------------------


snd_hda_intel
snd_hda_intel




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7c34000 irq 47
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7c30000 irq 48




!!PCI Soundcards installed in the system
!!--------------------------------------


00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:03.0 0403: 8086:0a0c (rev 09)
        Subsystem: 8086:2054
--
00:1b.0 0403: 8086:9c20 (rev 04)
        Subsystem: 8086:2054




!!Modprobe options (Sound related)
!!--------------------------------


snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
        align_buffer_size : -1
        bdl_pos_adj : 32,1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
        enable_msi : -1
        id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        power_save : 0
        power_save_controller : Y
        probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        single_cmd : N
        snoop : -1


!!Module: snd_hda_intel
        align_buffer_size : -1
        bdl_pos_adj : 32,1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
        enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
        enable_msi : -1
        id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
        position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        power_save : 0
        power_save_controller : Y
        probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
        probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
        single_cmd : N
        snoop : -1




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: Intel Haswell HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862807
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=1, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 3
     0x02* 0x03 0x04
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=7 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560020: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560030: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Realtek ALC283
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0283
Subsystem Id: 0x80862054
Revision Id: 0x100003
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Master Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC283 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3c 0x3c]
  Converter: stream=8, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC283 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x27 0x27]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 5
     0x18 0x19 0x1a 0x1b 0x1d
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x03 0x0b
Node 0x0e [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00]
  Connection: 1
     0x0d
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x97 0x97]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x12 [Pin Complex] wcaps 0x40040b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x03a11020: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001373c: IN OUT HP EAPD Detect
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40941905: [N/A] Aux at Ext N/A
    Conn = RCA, Color = Black
    DefAssociation = 0x0, Sequence = 0x5
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=73
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Master Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001001c: OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x03211010: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x18 0x19 0x1a 0x1b 0x1d 0x0b
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  2 Sep 11 10:50 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  6 Sep 11 10:50 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  5 Sep 11 10:50 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  9 Sep 11 10:50 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  3 Sep 11 10:50 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  4 Sep 11 10:50 /dev/snd/pcmC0D7p
crw-rw----+ 1 root audio 116,  8 Sep 11 10:50 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  7 Sep 11 10:50 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  1 Sep 11 10:50 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Sep 11 10:50 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Sep 11 10:50 .
drwxr-xr-x 3 root root 260 Sep 11 10:50 ..
lrwxrwxrwx 1 root root  12 Sep 11 10:50 pci-0000:00:03.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Sep 11 10:50 pci-0000:00:1b.0 -> ../controlC1




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [HDMI]


Card hw:0 'HDMI'/'HDA Intel HDMI at 0xf7c34000 irq 47'
  Mixer name    : 'Intel Haswell HDMI'
  Components    : 'HDA:80862807,80860101,00100000'
  Controls      : 14
  Simple ctrls  : 2
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!-------Mixer controls for card 1 [PCH]


Card hw:1 'PCH'/'HDA Intel PCH at 0xf7c30000 irq 48'
  Mixer name    : 'Realtek ALC283'
  Components    : 'HDA:10ec0283,80862054,00100003'
  Controls      : 14
  Simple ctrls  : 6
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 60 [69%] [-20.25dB] [on]
  Front Right: Playback 60 [69%] [-20.25dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 39 [62%] [12.00dB] [on]
  Front Right: Capture 39 [62%] [12.00dB] [on]




!!Alsactl output
!!--------------


--startcollapse--
state.HDMI {
        control.1 {
                iface CARD
                name 'HDMI/DP,pcm=3 Jack'
                value true
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.2 {
                iface MIXER
                name 'IEC958 Playback Con Mask'
                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.3 {
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.4 {
                iface MIXER
                name 'IEC958 Playback Default'
                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access 'read write'
                        type IEC958
                        count 1
                }
        }
        control.5 {
                iface MIXER
                name 'IEC958 Playback Switch'
                value true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.6 {
                iface PCM
                device 3
                name ELD
                value '1000070067100001000000000000000020a38842484953454e53450917070000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access 'read volatile'
                        type BYTES
                        count 83
                }
        }
        control.7 {
                iface CARD
                name 'HDMI/DP,pcm=7 Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.8 {
                iface MIXER
                name 'IEC958 Playback Con Mask'
                index 1
                value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.9 {
                iface MIXER
                name 'IEC958 Playback Pro Mask'
                index 1
                value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access read
                        type IEC958
                        count 1
                }
        }
        control.10 {
                iface MIXER
                name 'IEC958 Playback Default'
                index 1
                value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
                comment {
                        access 'read write'
                        type IEC958
                        count 1
                }
        }
        control.11 {
                iface MIXER
                name 'IEC958 Playback Switch'
                index 1
                value true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 1
                }
        }
        control.12 {
                iface PCM
                device 7
                name ELD
                value ''
                comment {
                        access 'read volatile'
                        type BYTES
                        count 0
                }
        }
        control.13 {
                iface PCM
                device 3
                name 'Playback Channel Map'
                value.0 0
                value.1 0
                value.2 0
                value.3 0
                value.4 0
                value.5 0
                value.6 0
                value.7 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 8
                        range '0 - 36'
                }
        }
        control.14 {
                iface PCM
                device 7
                name 'Playback Channel Map'
                value.0 0
                value.1 0
                value.2 0
                value.3 0
                value.4 0
                value.5 0
                value.6 0
                value.7 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 8
                        range '0 - 36'
                }
        }
}
state.PCH {
        control.1 {
                iface MIXER
                name 'Master Playback Volume'
                value.0 60
                value.1 60
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 87'
                        dbmin -6525
                        dbmax 0
                        dbvalue.0 -2025
                        dbvalue.1 -2025
                }
        }
        control.2 {
                iface MIXER
                name 'Master Playback Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.3 {
                iface MIXER
                name 'Mic Playback Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -3450
                        dbmax 1200
                        dbvalue.0 -3450
                        dbvalue.1 -3450
                }
        }
        control.4 {
                iface MIXER
                name 'Mic Playback Switch'
                value.0 false
                value.1 false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.5 {
                iface MIXER
                name 'Capture Volume'
                value.0 39
                value.1 39
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 63'
                        dbmin -1725
                        dbmax 3000
                        dbvalue.0 1200
                        dbvalue.1 1200
                }
        }
        control.6 {
                iface MIXER
                name 'Capture Switch'
                value.0 true
                value.1 true
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.7 {
                iface MIXER
                name 'Mic Boost Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 3'
                        dbmin 0
                        dbmax 3600
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
        control.8 {
                iface CARD
                name 'Mic Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.9 {
                iface CARD
                name 'Headphone Jack'
                value false
                comment {
                        access read
                        type BOOLEAN
                        count 1
                }
        }
        control.10 {
                iface MIXER
                name 'Beep Playback Volume'
                value.0 0
                value.1 0
                comment {
                        access 'read write'
                        type INTEGER
                        count 2
                        range '0 - 31'
                        dbmin -3450
                        dbmax 1200
                        dbvalue.0 -3450
                        dbvalue.1 -3450
                }
        }
        control.11 {
                iface MIXER
                name 'Beep Playback Switch'
                value.0 false
                value.1 false
                comment {
                        access 'read write'
                        type BOOLEAN
                        count 2
                }
        }
        control.12 {
                iface PCM
                name 'Playback Channel Map'
                value.0 0
                value.1 0
                comment {
                        access read
                        type INTEGER
                        count 2
                        range '0 - 36'
                }
        }
        control.13 {
                iface PCM
                name 'Capture Channel Map'
                value.0 0
                value.1 0
                comment {
                        access read
                        type INTEGER
                        count 2
                        range '0 - 36'
                }
        }
        control.14 {
                iface MIXER
                name 'PCM Playback Volume'
                value.0 255
                value.1 255
                comment {
                        access 'read write user'
                        type INTEGER
                        count 2
                        range '0 - 255'
                        tlv '0000000100000008ffffec1400000014'
                        dbmin -5100
                        dbmax 0
                        dbvalue.0 0
                        dbvalue.1 0
                }
        }
}
--endcollapse--




!!All Loaded Modules
!!------------------


Module
cfg80211
intel_rapl
iosf_mbi
x86_pkg_temp_thermal
intel_powerclamp
coretemp
snd_hda_codec_realtek
kvm_intel
snd_hda_codec_generic
kvm
snd_hda_codec_hdmi
snd_hda_intel
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
dm_multipath
snd_hda_controller
aesni_intel
scsi_dh
snd_hda_codec
snd_soc_rt5640
joydev
aes_x86_64
snd_hwdep
snd_seq_midi
snd_seq_midi_event
snd_soc_rl6231
lrw
gf128mul
snd_soc_core
glue_helper
snd_rawmidi
ablk_helper
cryptd
ir_lirc_codec
ir_sony_decoder
lirc_dev
ir_sanyo_decoder
ir_xmp_decoder
ir_rc6_decoder
ir_sharp_decoder
ir_jvc_decoder
ir_rc5_decoder
ir_nec_decoder
ir_mce_kbd_decoder
snd_seq
rc_rc6_mce
snd_compress
nuvoton_cir
snd_pcm_dmaengine
mei_me
rc_core
snd_pcm
i2c_hid
mei
snd_seq_device
lpc_ich
dw_dmac
snd_timer
dw_dmac_core
8250_dw
snd
i2c_designware_platform
i2c_designware_core
spi_pxa2xx_platform
soundcore
snd_soc_sst_acpi
mac_hid
parport_pc
ppdev
lp
parport
autofs4
squashfs
overlay
nls_iso8859_1
dm_mirror
dm_region_hash
dm_log
hid_generic
usbhid
hid
ses
enclosure
i915
uas
i2c_algo_bit
usb_storage
drm_kms_helper
e1000e
drm
ahci
ptp
libahci
pps_core
video
sdhci_acpi
sdhci




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D0/init_pin_configs:
0x05 0x18560010
0x06 0x18560020
0x07 0x58560030


/sys/class/sound/hwC0D0/driver_pin_configs:


/sys/class/sound/hwC0D0/user_pin_configs:


/sys/class/sound/hwC0D0/init_verbs:


/sys/class/sound/hwC0D0/hints:


/sys/class/sound/hwC1D0/init_pin_configs:
0x12 0x411111f0
0x14 0x40000000
0x17 0x411111f0
0x18 0x411111f0
0x19 0x03a11020
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x40941905
0x1e 0x411111f0
0x21 0x03211010


/sys/class/sound/hwC1D0/driver_pin_configs:


/sys/class/sound/hwC1D0/user_pin_configs:


/sys/class/sound/hwC1D0/init_verbs:


/sys/class/sound/hwC1D0/hints:




!!ALSA/HDA dmesg
!!--------------


[   33.725848] device-mapper: multipath: version 1.7.0 loaded
[   33.782147] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[   33.792293] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input8
[   33.821901] sound hdaudioC1D0: autoconfig: line_outs=1 (0x21/0x0/0x0/0x0/0x0) type:hp
[   33.821908] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   33.821913] sound hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   33.821917] sound hdaudioC1D0:    mono: mono_out=0x0
[   33.821919] sound hdaudioC1D0:    inputs:
[   33.821924] sound hdaudioC1D0:      Mic=0x19
[   33.831885] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[   33.832011] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[   33.856451] Adding 4120572k swap on /dev/sda3.  Priority:-1 extents:1 across:4120572k SSFS

```

---

### Post by Erwin_B on 2015-09-11
[COLOR=#000000][FONT=Verdana]I had basically the same issue with my Intel Nuc, also running Ubuntu 14.04 with the same kernel. Audio passthrough stopped working after some package updates yesterday. I also tried just about everything there is to try. Finally decided to boot an older kernel (3.13.0-62-generic) which fixed it.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]There must be something wrong with the Alsa dkms build in combination with the new kernel.[/FONT][/COLOR]

---

### Post by nuc_buntu on 2015-09-11
@erwin_b: now thats some neat info! please give me some detail how and what you did! you would save my weekend :)

---

### Post by Yellow Pasque on 2015-09-11
If the dkms module failed to build, it should have left a log in /var/lib/dkms (probably in a subdirectroy thereof).

As for booting into older -62 kernel (assuming you didn't remove it), see this to bring up the boot menu, which will allow you to boot previous kernels: [https://help.ubuntu.com/community/Grub2#Hidden](https://help.ubuntu.com/community/Grub2#Hidden)

---

### Post by Erwin_B on 2015-09-11
If you've done any package upgrades (apt-get upgrade) lately, and have not removed all of the older kernels, you can simply boot into one from the boot menu at startup.
If the boot menu doesn't appear, or flashes by too quickly, you may have to set the grub timeout in /etc/default/grub. I set it to 20 seconds which gives you ample time to select any of the menu options before the system continues to boot (see below). Don't forget to run *sudo update-grub *after you've updated the config.
Older kernels are under the 'Ubuntu advanced' option. Just select the version older than the current one and hit <enter>.

[COLOR=#111111][FONT=Consolas]# GRUB_HIDDEN_TIMEOUT=0
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]# GRUB_HIDDEN_TIMEOUT_QUIET=true
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]GRUB_TIMEOUT=20[/FONT][/COLOR]

---

### Post by nuc_buntu on 2015-09-13
thanks a ton m8! it worked!

---

### Post by nuc_buntu on 2015-09-15
i just saw there is a new [COLOR=#000000][FONT=Ubuntu Mono]oem-audio-hda-daily-dkms[/FONT][/COLOR] and i thought it would fix the problem with the latest kernel. problem is now sounds not working even with old kernel :( i cant describe how angry/Sad i am i did this damn update :/

Any hero can help me out of misery? any help much appreciated

---

### Post by Erwin_B on 2015-09-15
Bummer :(
I would see if I could get my hands on an older version of the alsa package. Maybe you still have some in your apt cache. Try this to see if you have:

[I]ls /var/cache/apt/archives/ | grep oem-audio

[/I]If you do, you can do: *sudo dpkg -i **/var/cache/apt/archives/*[I]<oem-audio-hda-daily-dkms_0.20150fill_in_the_older_version_you_found_all.deb>
[/I]to rebuild it for the kernel you are running.

Good luck!

---

### Post by nuc_buntu on 2015-09-16
funny things are happening :-k

i found the deb file from 8th sept. uninstalled existing [COLOR=#000000][FONT=Ubuntu Mono]oem-audio-hda-daily-dkms[/FONT][/COLOR]. tried installing the deb from cache - said its missing dmks. did apt-get install dkms and then installed deb from cache. worked but still no sound.

went to [https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages?field.name_filter=oem-&field.status_filter=&field.series_filter=](https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages?field.name_filter=oem-&field.status_filter=&field.series_filter=)

downloaded deb from july. uninstalled existing and installed the july version via ubuntu software gui. now sound is working again. never gonna touch that damn system again, damn those updates :evil:

@erwin_b: cant thank you enough, you are a cool guy! you helping me out is very much appreciated!

---

### Post by Erwin_B on 2015-09-16
Glad to be of help. :)

Since these are all workarounds, I'm wondering if anyone has found the cause of this issue yet.

---

