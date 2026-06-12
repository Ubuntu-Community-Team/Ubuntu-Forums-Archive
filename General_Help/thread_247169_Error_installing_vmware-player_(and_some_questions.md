---
title: "Error installing vmware-player (and some questions)"
date: 2006-08-30
forum: General Help
---

### Post by KenSentMe on 2006-08-30
When i try to install vmware-player on my system i get an error. Everytime install something with apt, i tries to solve it, but it wont work.

The error:

```

jeroen@homer:~$ sudo apt-get install vmware-player
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.15-23
Aanbevolen pakketten:
  linux-image-2.6.15-23-386
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  vmware-player vmware-player-kernel-modules
  vmware-player-kernel-modules-2.6.15-23
0 pakketten opgewaardeerd, 3 nieuwe pakketten geïnstalleerd, 0 verwijderen en 0 niet opgewaardeerd.
Er moeten 12,0MB aan archieven opgehaald worden.
Na het uitpakken zal er 32,5MB extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? j
Ophalen:1 http://archive.ubuntu.com dapper/multiverse vmware-player-kernel-modules-2.6.15-23 2.6.15.10-6 [165kB]
Ophalen:2 http://archive.ubuntu.com dapper/multiverse vmware-player-kernel-modules 2.6.15.10-6 [6762B]
Ophalen:3 http://archive.ubuntu.com dapper/multiverse vmware-player 1.0.1-4 [11,8MB]
12,0MB opgehaald in 37s (324kB/s)
Voorconfigureren van pakketten...
Selecteren van voorheen niet geselecteerd pakket vmware-player-kernel-modules-2.6.15-23.
(Database inlezen ... 155498 bestanden en mappen geïnstalleerd.)
Uitpakken van vmware-player-kernel-modules-2.6.15-23 (uit .../vmware-player-kernel-modules-2.6.15-23_2.6.15.10-6_i386.deb) ...
Selecteren van voorheen niet geselecteerd pakket vmware-player-kernel-modules.
Uitpakken van vmware-player-kernel-modules (uit .../vmware-player-kernel-modules_2.6.15.10-6_all.deb) ...
Selecteren van voorheen niet geselecteerd pakket vmware-player.
Uitpakken van vmware-player (uit .../vmware-player_1.0.1-4_i386.deb) ...
Instellen van vmware-player-kernel-modules-2.6.15-23 (2.6.15.10-6) ...

Instellen van vmware-player-kernel-modules (2.6.15.10-6) ...
Instellen van vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.5.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.112.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: fout bij afhandelen van vmware-player (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also i have two questions:

1. On the wiki it says that i can use easyvmx.com to create vmx files for free. However, the website seems to be down. Are there any alternatives?

2. Do i need to completely reinstall Windows XP in VMware to run it. I have a ghost image of an installation that runs on this same pc. Can i use that?

---

### Post by KenSentMe on 2006-09-01
Nobody?

It seems like the module isn't loaded, because vmware-player-kernel-modules-2.6.15-23 is installed and i have 2.6.15-26-686. 

Should i install linux-image-2.6.15.-23-386 to make this work, and will this affect my system on some other way? 

Or maybe there is a workaround?

---

### Post by KenSentMe on 2006-09-01
Ok. I've got vmware-player running now. The problem was that the security updates of multiverse weren't in my sources.list.

Now i got a problem running Windows. I've used this wiki: [https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO) . But i can't get the vmware-player to run the iso or my hardware cd-rom. It both says that there's no OS installed.

Any suggestions?

---

