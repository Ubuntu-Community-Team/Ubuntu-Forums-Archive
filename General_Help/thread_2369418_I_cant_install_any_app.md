---
title: "I cant install any app"
date: 2017-08-22
forum: General Help
---

### Post by wojtekkha on 2017-08-22
Hi when i try install any apps from terminal i have this.
I try install updates, try any commands and try makes "Please install the linux-headers-4.10.0-28-generic package" but not works.
Please help.


```
sudo apt-get install silversearcher-ag
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Nast&#281;puj&#261;ce pakiety zosta&#322;y zainstalowane automatycznie i nie s&#261; ju&#380; wi&#281;cej wymagane:
  linux-image-4.10.0-24-generic linux-image-4.10.0-26-generic
Aby je usun&#261;&#263; nale&#380;y u&#380;y&#263; "sudo apt autoremove".
Nast&#281;puj&#261;ce pakiety zostan&#261; USUNI&#280;TE:
  linux-image-extra-4.10.0-24-generic linux-image-extra-4.10.0-26-generic
  linux-image-extra-4.10.0-28-generic
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
  silversearcher-ag
0 aktualizowanych, 1 nowo instalowanych, 3 usuwanych i 0 nieaktualizowanych.
12 nie w pe&#322;ni zainstalowanych lub usuni&#281;tych.
Konieczne pobranie 0 B/36,8 kB archiwów.
Po tej operacji zostanie zwolnione 466 MB miejsca na dysku.
Kontynuowa&#263;? [T/n] t
(Odczytywanie bazy danych ... 325179 plików i katalogów obecnie zainstalowanych.)
Usuwanie pakietu linux-image-extra-4.10.0-24-generic (4.10.0-24.28) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
Error! Your kernel headers for kernel 4.10.0-24-generic cannot be found.
Please install the linux-headers-4.10.0-24-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: b&#322;&#261;d przetwarzania pakietu linux-image-extra-4.10.0-24-generic (--remove):
 podproces zainstalowany skrypt post-removal zwróci&#322; kod b&#322;&#281;du 1
Usuwanie pakietu linux-image-extra-4.10.0-26-generic (4.10.0-26.30) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
Error! Your kernel headers for kernel 4.10.0-26-generic cannot be found.
Please install the linux-headers-4.10.0-26-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: b&#322;&#261;d przetwarzania pakietu linux-image-extra-4.10.0-26-generic (--remove):
 podproces zainstalowany skrypt post-removal zwróci&#322; kod b&#322;&#281;du 1
Usuwanie pakietu linux-image-extra-4.10.0-28-generic (4.10.0-28.32) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
Error! Your kernel headers for kernel 4.10.0-28-generic cannot be found.
Please install the linux-headers-4.10.0-28-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: b&#322;&#261;d przetwarzania pakietu linux-image-extra-4.10.0-28-generic (--remove):
 podproces zainstalowany skrypt post-removal zwróci&#322; kod b&#322;&#281;du 1
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 linux-image-extra-4.10.0-24-generic
 linux-image-extra-4.10.0-26-generic
 linux-image-extra-4.10.0-28-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by RobGoss on 2017-08-22
Hello and welcome to the forums, what command are you running in your terminal?

---

### Post by Bashing-om on 2017-08-22
wojtekkha; Hello; Welcome to the forum.

Is this a liveDVD(USB) that you are attempting to update ?
A live system is read only and new kernels can not be installed.
> 
Fatal: open /gparted-live/live/vmlinuz: No such file or directory


This is an English Forum and unfortunately English is the only language many if us can converse in.

If this is a actual installed to hard drive system, please post the out puts of terminal commands:
```

LC_ALL=C sudo apt update
LC_ALL=C sudo apt upgrade

```
to get the output in English .

See then what the root is the issue is.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by wojtekkha on 2017-08-23
Ok, sorry and thanks.
I use commands:
-sudo apt-get update 
-sudo apt-get upgrade
-sudo apt-get autoremove
-sudo apt-get clean
-sudo apt-get -f install

@Bashing-om
I cant use usb and cd because my usb ports not work and cd too.

LC_ALL=C sudo apt update:
```
LC_ALL=C sudo apt update[sudo] password for wojtekhyla: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://packages.microsoft.com/repos/vscode stable InRelease             
Hit:3 http://pl.archive.ubuntu.com/ubuntu zesty InRelease                     
Hit:4 http://security.ubuntu.com/ubuntu zesty-security InRelease              
Hit:5 http://ppa.launchpad.net/atareao/telegram/ubuntu zesty InRelease        
Hit:6 http://pl.archive.ubuntu.com/ubuntu zesty-updates InRelease             
Ign:7 http://dl.google.com/linux/talkplugin/deb stable InRelease              
Hit:8 http://dl.google.com/linux/chrome/deb stable Release                    
Hit:9 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu zesty InRelease
Hit:10 https://dl.winehq.org/wine-builds/ubuntu zesty InRelease               
Hit:11 http://dl.google.com/linux/talkplugin/deb stable Release               
Ign:12 http://ppa.launchpad.net/ferramroberto/java/ubuntu zesty InRelease     
Hit:13 http://archive.canonical.com zesty InRelease                           
Hit:14 http://repository.spotify.com stable InRelease                   
Hit:15 http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu zesty InRelease
Hit:16 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu zesty InRelease
Hit:17 https://download.sublimetext.com apt/dev/ InRelease
Hit:18 http://ppa.launchpad.net/kdenlive/kdenlive-stable/ubuntu zesty InRelease
Hit:19 http://ppa.launchpad.net/linrunner/tlp/ubuntu zesty InRelease
Hit:20 http://ppa.launchpad.net/numix/ppa/ubuntu zesty InRelease
Hit:21 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu zesty InRelease
Ign:22 http://ppa.launchpad.net/pgolm/the-silver-searcher/ubuntu zesty InRelease
Hit:23 http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu zesty InRelease
Hit:24 http://ppa.launchpad.net/tista/adapta/ubuntu zesty InRelease
Hit:26 http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu zesty InRelease
Ign:27 http://ppa.launchpad.net/upubuntu-com/icons/ubuntu zesty InRelease
Hit:28 http://ppa.launchpad.net/webupd8team/atom/ubuntu zesty InRelease
Hit:29 http://ppa.launchpad.net/webupd8team/brackets/ubuntu zesty InRelease
Hit:30 http://ppa.launchpad.net/webupd8team/java/ubuntu zesty InRelease
Hit:32 http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu zesty InRelease
Err:33 http://ppa.launchpad.net/ferramroberto/java/ubuntu zesty Release
  404  Not Found
Err:34 http://ppa.launchpad.net/pgolm/the-silver-searcher/ubuntu zesty Release
  404  Not Found
Err:35 http://ppa.launchpad.net/upubuntu-com/icons/ubuntu zesty Release
  404  Not Found
Reading package lists... Done 
E: The repository 'http://ppa.launchpad.net/ferramroberto/java/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/pgolm/the-silver-searcher/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/upubuntu-com/icons/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

LC_ALL=C sudo apt upgrade:
```
LC_ALL=C sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  logrotate ubuntu-drivers-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 85.1 kB/90.2 MB of archives.
After this operation, 4096 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://pl.archive.ubuntu.com/ubuntu zesty-updates/main amd64 ubuntu-drivers-common amd64 1:0.4.22.1 [47.3 kB]
Get:2 http://pl.archive.ubuntu.com/ubuntu zesty-updates/main amd64 logrotate amd64 3.8.7-2ubuntu3.1 [37.8 kB]
Fetched 85.1 kB in 0s (351 kB/s)   
Preconfiguring packages ...
(Reading database ... 325181 files and directories currently installed.)
Preparing to unpack .../ubuntu-drivers-common_1%3a0.4.22.1_amd64.deb ...
Unpacking ubuntu-drivers-common (1:0.4.22.1) over (1:0.4.22) ...
Preparing to unpack .../logrotate_3.8.7-2ubuntu3.1_amd64.deb ...
Unpacking logrotate (3.8.7-2ubuntu3.1) over (3.8.7-2ubuntu3) ...
Setting up linux-image-4.10.0-30-generic (4.10.0-30.34) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-30-generic /boot/vmlinuz-4.10.0-30-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.10.0-30-generic.postinst line 1052.
dpkg: error processing package linux-image-4.10.0-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for ureadahead (0.100.0-19) ...
Setting up linux-image-4.10.0-26-generic (4.10.0-26.30) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.10.0-26.30 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.10.0-26.30 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
Error! Your kernel headers for kernel 4.10.0-26-generic cannot be found.
Please install the linux-headers-4.10.0-26-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-26-generic /boot/vmlinuz-4.10.0-26-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.10.0-26-generic.postinst line 1052.
dpkg: error processing package linux-image-4.10.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-4.10.0-24-generic (4.10.0-24.28) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.10.0-24.28 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.10.0-24.28 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
Error! Your kernel headers for kernel 4.10.0-24-generic cannot be found.
Please install the linux-headers-4.10.0-24-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-24-generic /boot/vmlinuz-4.10.0-24-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.10.0-24-generic.postinst line 1052.
dpkg: error processing package linux-image-4.10.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ubuntu-drivers-common (1:0.4.22.1) ...
Setting up linux-image-4.10.0-32-generic (4.10.0-32.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-32-generic /boot/vmlinuz-4.10.0-32-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-32-generic /boot/vmlinuz-4.10.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-32-generic /boot/vmlinuz-4.10.0-32-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-32-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-32-generic /boot/vmlinuz-4.10.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-32-generic /boot/vmlinuz-4.10.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-32-generic /boot/vmlinuz-4.10.0-32-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.10.0-32-generic.postinst line 1052.
dpkg: error processing package linux-image-4.10.0-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-4.10.0-28-generic (4.10.0-28.32) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
Error! Your kernel headers for kernel 4.10.0-28-generic cannot be found.
Please install the linux-headers-4.10.0-28-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.10.0-28-generic /boot/vmlinuz-4.10.0-28-generic
Added Linux  +  *
Added Linux_Old  +
Fatal: open /gparted-live/live/vmlinuz: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.10.0-28-generic.postinst line 1052.
dpkg: error processing package linux-image-4.10.0-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db (2.7.6.1-2) ...
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.10.0-32-generic; however:
  Package linux-image-4.10.0-32-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up logrotate (3.8.7-2ubuntu3.1) ...
dpkg: dependency problems prevent configuration of linux-image-extra-4.10.0-32-generic:
 linux-image-extra-4.10.0-32-generic depends on linux-image-4.10.0-32-generic; however:
  Package linux-image-4.10.0-32-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.10.0-32-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.10.0-30-generic:
 linux-image-extra-4.10.0-30-generic depends on linux-image-4.10.0-30-generic; however:
  Package linux-image-4.10.0-30-generic is not configured yet.


No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                             dpkg: error processing package linux-image-extra-4.10.0-30-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.10.0.32.32); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-4.10.0-30-generic
 linux-image-4.10.0-26-generic
 linux-image-4.10.0-24-generic
 linux-image-4.10.0-32-generic
 linux-image-4.10.0-28-generic
 linux-image-generic
 linux-image-extra-4.10.0-32-generic
 linux-image-extra-4.10.0-30-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2017-08-23
wojtekkha; OK;

These PPAs:
> 
Err:33 [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu)
Err:34 [http://ppa.launchpad.net/pgolm/the-silver-searcher/ubuntu](http://ppa.launchpad.net/pgolm/the-silver-searcher/ubuntu)
Err:35 [http://ppa.launchpad.net/upubuntu-com/icons/ubuntu](http://ppa.launchpad.net/upubuntu-com/icons/ubuntu)

Have not been updated by the authors and have no support in the zesty release. Disable these sources.

These kernel images:
> 
Errors were encountered while processing:
 linux-image-4.10.0-30-generic
 linux-image-4.10.0-26-generic
 linux-image-4.10.0-24-generic
 linux-image-4.10.0-32-generic
 linux-image-4.10.0-28-generic
 linux-image-generic
 linux-image-extra-4.10.0-32-generic
 linux-image-extra-4.10.0-30-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Will require additional information to isolate the problem.
Post back the outputs of teerminal commands:
```

df -h
df -i
ls -al /boot/
dpkg -l | grep linux-

```

we see then
[INDENT][INDENT]what condition the condition is in
[/INDENT][/INDENT]

---

