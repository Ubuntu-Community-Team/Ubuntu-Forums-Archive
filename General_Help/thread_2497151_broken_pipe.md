---
title: "broken pipe"
date: 2024-04-25
forum: General Help
---

### Post by adolife on 2024-04-25
Hi, 

after installing a vanilla install of ubuntu 22.04.4, and installing the following packages: apt install wget git curl speedtest-cli snapd / snapd install fast

And installing docker with the docker get script, and installing apt install python3-pip python3, I restarted the computer and did this;

```
Welcome to Ubuntu 22.04.4 LTS (GNU/Linux 5.15.0-105-generic x86_64)


 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/pro](https://ubuntu.com/pro)


  System information as of do 25 apr 2024  5:48:31 UTC


  System load:              0.2392578125
  Usage of /:               0.2% of 3.58TB
  Memory usage:             5%
  Swap usage:               0%


  Temperature:              30.0 C
  Processes:                132
  Users logged in:          0
  IPv4 address for docker0: 172.17.0.1


  IPv4 address for enp2s0:  192.168.178.62
  IPv6 address for enp2s0:  2a02:a212:a1be:6d80:ea9c:25ff:fe7d:6eb4




Expanded Security Maintenance for Applications is not enabled.


0 updates kunnen onmiddelijk worden toegepast.


Enable ESM Apps to receive additional future security updates.
See [https://ubuntu.com/esm](https://ubuntu.com/esm) or run: sudo pro status




Last login: Wed Apr 24 09:05:00 2024


root@n100:~# ls


snap
root@n100:~# ls
snap
root@n100:~# ls


snap
root@n100:~# ls
snap
root@n100:~# nano /boot/grub
root@n100:~# cd /boot/grub
root@n100:/boot/grub# ls
fonts  grub.cfg  grubenv  locale  unicode.pf2  x86_64-efi
root@n100:/boot/grub# nano grub.cfg
root@n100:/boot/grub# cd ..
root@n100:/boot# ls
config-5.15.0-105-generic  initrd.img                     System.map-5.15.0-105-generic  vmlinuz.old
efi                        initrd.img-5.15.0-105-generic  vmlinuz
grub                       initrd.img.old                 vmlinuz-5.15.0-105-generic
root@n100:/boot# cd /sys
root@n100:/sys# ls
block  bus  class  dev  devices  firmware  fs  hypervisor  kernel  module  power
root@n100:/sys# cd ..
root@n100:/# ls
bin   cdrom  etc   lib    lib64   lost+found  mnt  proc  run   snap  swap.img  tmp  var
boot  dev    home  lib32  libx32  media       opt  root  sbin  srv   sys       usr
root@n100:/# nano /etc/default/grub
root@n100:/# nano /etc/default/grub
root@n100:/# ls
apt install linux-nvidia-tools-common            # version 5.15.0-1040.40
apt install linux-tools-common                   # version 5.15.0-88.98
apt install linux-nvidia-5.19-tools-common       # version 5.19.0-1014.14
apt install linux-nvidia-tegra-igx-tools-common  # version 5.15.0-1005.5
apt install linux-nvidia-tegra-tools-common      # version 5.15.0-1018.18
apt install linux-xilinx-zynqmp-tools-common     # version 5.15.0-1023.27
root@n100:/# apt install linux-intel-iotg-tools-common
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  linux-intel-iotg-tools-common
0 opgewaardeerd, 1 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
Er moeten 293 kB aan archieven opgehaald worden.
Na deze bewerking zal er 1.020 kB extra schijfruimte gebruikt worden.
Ophalen:1 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-intel-iotg-tools-common all 5.15.0-1055.61 [293 kB]
293 kB opgehaald in 0s (1.186 kB/s)
Voorheen niet geselecteerd pakket linux-intel-iotg-tools-common wordt geselecteerd.
(Database wordt ingelezen ... 81911 bestanden en mappen momenteel geïnstalleerd.)
Uitpakken van .../linux-intel-iotg-tools-common_5.15.0-1055.61_all.deb wordt voorbereid...
Bezig met uitpakken van linux-intel-iotg-tools-common (5.15.0-1055.61) ...
Instellen van linux-intel-iotg-tools-common (5.15.0-1055.61) ...
Bezig met afhandelen van triggers voor man-db (2.10.2-1) ...
Scanning processes...
Scanning processor microcode...
Scanning linux images...


Running kernel seems to be up-to-date.


The processor microcode seems to be up-to-date.


No services need to be restarted.


No containers need to be restarted.


No user sessions are running outdated binaries.


No VM guests are running outdated hypervisor (qemu) binaries on this host.
root@n100:/# turbostat -S --debug sleep 10
WARNING: turbostat not found for kernel 5.15.0-105


  You may need to install the following packages for this specific kernel:
    linux-tools-5.15.0-105-generic
    linux-cloud-tools-5.15.0-105-generic


  You may also want to install one of the following packages to keep up to date:
    linux-tools-generic
    linux-cloud-tools-generic
root@n100:/# apt install linux-tools-5.15.0-105-generic linux-cloud-tools-5.15.0-105-generic linux-tools-generic linux-cloud-tools-generic linux-generic
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
linux-generic is reeds de nieuwste versie (5.15.0.105.102).
De volgende extra pakketten zullen geïnstalleerd worden:
  hwdata linux-cloud-tools-5.15.0-105 linux-cloud-tools-common linux-tools-5.15.0-105 linux-tools-common
Voorheen niet geselecteerd pakket linux-cloud-tools-5.15.0-105-generic wordt geselecteerd.
Uitpakken van .../3-linux-cloud-tools-5.15.0-105-generic_5.15.0-105.115_amd64.deb wordt voorbereid...
Bezig met uitpakken van linux-cloud-tools-5.15.0-105-generic (5.15.0-105.115) ...
Voorheen niet geselecteerd pakket linux-cloud-tools-generic wordt geselecteerd.
Uitpakken van .../4-linux-cloud-tools-generic_5.15.0.105.102_amd64.deb wordt voorbereid...
Bezig met uitpakken van linux-cloud-tools-generic (5.15.0.105.102) ...
Voorheen niet geselecteerd pakket linux-tools-common wordt geselecteerd.
Uitpakken van .../5-linux-tools-common_5.15.0-105.115_all.deb wordt voorbereid...
Bezig met uitpakken van linux-tools-common (5.15.0-105.115) ...
dpkg: fout bij verwerken van archief /tmp/apt-dpkg-install-srUZlc/5-linux-tools-common_5.15.0-105.115_all.deb (--unpack):
 poging tot overschrijven van '/usr/bin/acpidbg', wat ook in pakket linux-intel-iotg-tools-common 5.15.0-1055.61 zit
dpkg-deb: fout: subproces plakken werd gedood door signaal (Broken pipe)
Voorheen niet geselecteerd pakket linux-tools-5.15.0-105 wordt geselecteerd.
Uitpakken van .../6-linux-tools-5.15.0-105_5.15.0-105.115_amd64.deb wordt voorbereid...
Bezig met uitpakken van linux-tools-5.15.0-105 (5.15.0-105.115) ...
Voorheen niet geselecteerd pakket linux-tools-5.15.0-105-generic wordt geselecteerd.
Uitpakken van .../7-linux-tools-5.15.0-105-generic_5.15.0-105.115_amd64.deb wordt voorbereid...
Bezig met uitpakken van linux-tools-5.15.0-105-generic (5.15.0-105.115) ...
Voorheen niet geselecteerd pakket linux-tools-generic wordt geselecteerd.
Uitpakken van .../8-linux-tools-generic_5.15.0.105.102_amd64.deb wordt voorbereid...
Bezig met uitpakken van linux-tools-generic (5.15.0.105.102) ...
Fouten gevonden tijdens verwerken van:
 /tmp/apt-dpkg-install-srUZlc/5-linux-tools-common_5.15.0-105.115_all.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@n100:/# apt update
Geraakt:1 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy InRelease
Ophalen:2 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]
Ophalen:3 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-backports InRelease [109 kB]
Ophalen:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Ophalen:5 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [1.610 kB]
Ophalen:6 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages [1.070 kB]
Ophalen:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 Packages [1.394 kB]
Ophalen:8 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-backports/main amd64 Packages [90,8 kB]
Ophalen:9 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) jammy InRelease [48,8 kB]
Ophalen:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main Translation-en [243 kB]
Ophalen:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/restricted amd64 Packages [1.773 kB]
Ophalen:12 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-backports/universe amd64 Packages [29,8 kB]
Ophalen:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/restricted Translation-en [300 kB]
Ophalen:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 Packages [848 kB]
7.745 kB opgehaald in 1s (6.353 kB/s)
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
2 pakketten kunnen opgewaardeerd worden. Voer 'apt list --upgradable' uit om ze te zien.
root@n100:/# apt upgrade -y
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105 : Vereisten: linux-tools-common maar het is niet geïnstalleerd
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# lspci -v |grep -A8 VGA
00:02.0 VGA compatible controller: Intel Corporation Device 46d1 (prog-if 00 [VGA controller])
        DeviceName: Onboard IGD
        Subsystem: ASUSTeK Computer Inc. Device 8694
        Flags: bus master, fast devsel, latency 0, IRQ 255
        Memory at 71000000 (64-bit, non-prefetchable) [size=16M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=64]
        Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
        Capabilities: [40] Vendor Specific Information: Len=0c <?>
root@n100:/# apt-get install -y gpg-agent wget
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# apt --fix-broken install
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
Vereisten worden gecorrigeerd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  linux-tools-common
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  linux-tools-common
0 opgewaardeerd, 1 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
8 niet volledig geïnstalleerd of verwijderd.
Er moeten 0 B/300 kB aan archieven opgehaald worden.
Na deze bewerking zal er 999 kB extra schijfruimte gebruikt worden.
Wilt u doorgaan? [J/n] J
(Database wordt ingelezen ... 82061 bestanden en mappen momenteel geïnstalleerd.)
root@n100:/# apt -f
E: Commandoregel-optie 'f' [van -f] wordt niet begrepen in combinatie met de andere opties.
root@n100:/# apt install -f
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
Vereisten worden gecorrigeerd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  linux-tools-common
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  linux-tools-common
0 opgewaardeerd, 1 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
8 niet volledig geïnstalleerd of verwijderd.
Er moeten 0 B/300 kB aan archieven opgehaald worden.
Na deze bewerking zal er 999 kB extra schijfruimte gebruikt worden.
Wilt u doorgaan? [J/n] J
(Database wordt ingelezen ... 82061 bestanden en mappen momenteel geïnstalleerd.)
Uitpakken van .../linux-tools-common_5.15.0-105.115_all.deb wordt voorbereid...
Bezig met uitpakken van linux-tools-common (5.15.0-105.115) ...
dpkg: fout bij verwerken van archief /var/cache/apt/archives/linux-tools-common_5.15.0-105.115_all.deb (--unpack):
 poging tot overschrijven van '/usr/bin/acpidbg', wat ook in pakket linux-intel-iotg-tools-common 5.15.0-1055.61 zit
dpkg-deb: fout: subproces plakken werd gedood door signaal (Broken pipe)
Fouten gevonden tijdens verwerken van:
 /var/cache/apt/archives/linux-tools-common_5.15.0-105.115_all.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@n100:/# apt -r linux-tools-common_5.15.0-105.115_all
E: Commandoregel-optie 'r' [van -r] wordt niet begrepen in combinatie met de andere opties.
root@n100:/# apt --remove linux-tools-common_5.15.0-105.115_all
E: Ongeldige bewerking linux-tools-common_5.15.0-105.115_all
root@n100:/# apt uninstall linux-tools-common_5.15.0-105.115_all
E: Ongeldige bewerking uninstall
root@n100:/# apt remove linux-tools-common_5.15.0-105.115_all
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
E: Kan pakket linux-tools-common_5.15.0-105.115_all niet vinden
root@n100:/# apt remove linux-tools-common_5.15.0-105.115
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
E: Kan pakket linux-tools-common_5.15.0-105.115 niet vinden
root@n100:/# apt remove linux-tools-common_5.15.0-105
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
E: Kan pakket linux-tools-common_5.15.0-105 niet vinden
root@n100:/# apt remove linux-tools-common_5.15.0-105.115
Pakketlijsten worden ingelezen... Klaar
gpg-agent staat ingesteld op handmatig geïnstalleerd.
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105 : Vereisten: linux-tools-common maar het zal niet geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# apt install linux-tools-common
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  linux-tools-common
0 opgewaardeerd, 1 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
8 niet volledig geïnstalleerd of verwijderd.
Er moeten 0 B/300 kB aan archieven opgehaald worden.
Na deze bewerking zal er 999 kB extra schijfruimte gebruikt worden.
(Database wordt ingelezen ... 82061 bestanden en mappen momenteel geïnstalleerd.)
Uitpakken van .../linux-tools-common_5.15.0-105.115_all.deb wordt voorbereid...
Bezig met uitpakken van linux-tools-common (5.15.0-105.115) ...
dpkg: fout bij verwerken van archief /var/cache/apt/archives/linux-tools-common_5.15.0-105.115_all.deb (--unpack):
 poging tot overschrijven van '/usr/bin/acpidbg', wat ook in pakket linux-intel-iotg-tools-common 5.15.0-1055.61 zit
dpkg-deb: fout: subproces plakken werd gedood door signaal (Broken pipe)
Fouten gevonden tijdens verwerken van:
 /var/cache/apt/archives/linux-tools-common_5.15.0-105.115_all.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@n100:/# apt remove linux-tools-common
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
Pakket 'linux-tools-common' is niet geïnstalleerd, en wordt dus niet verwijderd
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105 : Vereisten: linux-tools-common maar het zal niet geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# apt --fix-broken install
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
Vereisten worden gecorrigeerd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  linux-tools-common
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  linux-tools-common
0 opgewaardeerd, 1 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
8 niet volledig geïnstalleerd of verwijderd.
Er moeten 0 B/300 kB aan archieven opgehaald worden.
Na deze bewerking zal er 999 kB extra schijfruimte gebruikt worden.
Wilt u doorgaan? [J/n] J
(Database wordt ingelezen ... 82061 bestanden en mappen momenteel geïnstalleerd.)
Uitpakken van .../linux-tools-common_5.15.0-105.115_all.deb wordt voorbereid...
Bezig met uitpakken van linux-tools-common (5.15.0-105.115) ...
dpkg: fout bij verwerken van archief /var/cache/apt/archives/linux-tools-common_5.15.0-105.115_all.deb (--unpack):
 poging tot overschrijven van '/usr/bin/acpidbg', wat ook in pakket linux-intel-iotg-tools-common 5.15.0-1055.61 zit
dpkg-deb: fout: subproces plakken werd gedood door signaal (Broken pipe)
Fouten gevonden tijdens verwerken van:
 /var/cache/apt/archives/linux-tools-common_5.15.0-105.115_all.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@n100:/# rm -f /var/cache/apt/archives/linux-tools-common_5.15.0-105.115_all.deb
root@n100:/# ls
bin   cdrom  etc   lib    lib64   lost+found  mnt  proc  run   snap  swap.img  tmp  var
boot  dev    home  lib32  libx32  media       opt  root  sbin  srv   sys       usr
root@n100:/# apt update
Geraakt:1 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) jammy InRelease
Geraakt:2 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy InRelease
Geraakt:3 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Geraakt:4 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Geraakt:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
2 pakketten kunnen opgewaardeerd worden. Voer 'apt list --upgradable' uit om ze te zien.
root@n100:/# apt upgrade -y
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105 : Vereisten: linux-tools-common maar het is niet geïnstalleerd
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# apt --fix-broken install
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
Vereisten worden gecorrigeerd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  linux-tools-common
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  linux-tools-common
0 opgewaardeerd, 1 nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
8 niet volledig geïnstalleerd of verwijderd.
Er moeten 300 kB aan archieven opgehaald worden.
Na deze bewerking zal er 999 kB extra schijfruimte gebruikt worden.
Wilt u doorgaan? [J/n] n
Afbreken.
root@n100:/# apt remove linux-tools-5.15.0-105
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105-generic : Vereisten: linux-tools-5.15.0-105 maar het zal niet geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# apt remove linux-tools-5.15.0-105-generic
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105 : Vereisten: linux-tools-common maar het zal niet geïnstalleerd worden
 linux-tools-generic : Vereisten: linux-tools-5.15.0-105-generic maar het zal niet geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# apt remove linux-tools-5.15.0-105 linux-tools-generic
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105-generic : Vereisten: linux-tools-5.15.0-105 maar het zal niet geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
root@n100:/# apt remove linux-generic
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar
U kunt 'apt --fix-broken install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-tools-5.15.0-105 : Vereisten: linux-tools-common maar het zal niet geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt --fix-broken install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
```

How can I even install anything if I keep getting the message fix broken install? How do I restore or even uninstall these packages? 

Awaiting anyone's response,

Joannes Wyckmans

---

