---
title: "Lubuntu Update - operation failed."
date: 2013-01-17
forum: General Help
---

### Post by TeHana86 on 2013-01-17
Hi,

Definately a beginner level once working below Desktop level.

Installed Lubuntu a month ago and received "operation failed" on updates immediately after. I guessed that this was because the original files did not exist and therefore could not be replaced. Have now decided that there must be a more complicated and important reason why the updates failed. The log is on the attached file.

All advice welcomed.

---

### Post by ibjsb4 on 2013-01-17
Not all of us have a way to open .odt files  :)

How bout posting the output from:

```
sudo apt-get update
```

---

### Post by TeHana86 on 2013-01-20
Sorry for the delay.

Attached is the text as requested (sudo apt-get update) plus the original "Details" of the "operation failed" in .docx format.

---

### Post by mörgæs on 2013-01-20
Please don't attach text. Better to insert relevant sections in the post using CODE tags around.

---

### Post by ibjsb4 on 2013-01-20
code tags

[ATTACH]230387[/ATTACH]

---

### Post by TeHana86 on 2013-01-20
Thanks morgaes, and ibjsb4 for showing how to insert inside CODE tags. I opted for attaching documents because the outputs looked too long to include in a message. 

Output from “Operation failed - Details”

```
installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ...
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 141975 files and directories currently installed.)
Preparing to replace dpkg 1.16.1.2ubuntu7 (using .../dpkg_1.16.1.2ubuntu7.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
Setting up dpkg (1.16.1.2ubuntu7.1) ...
(Reading database ...
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%

(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 141976 files and directories currently installed.)
Preparing to replace chromium-browser-l10n 20.0.1132.47~r144678-0ubuntu0.12.04.1
(using .../chromium-browser-l10n_23.0.1271.97-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement chromium-browser-l10n ...
Preparing to replace libfreetype6 2.4.8-1ubuntu2 (using .../
libfreetype6_2.4.8-1ubuntu2.1_i386.deb) ...
Unpacking replacement libfreetype6 ...
Preparing to replace libnspr4 4.8.9-1ubuntu2.3 (using .../
libnspr4_4.9.4-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libnspr4 ...
Preparing to replace libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu6.1 (using .../
libnss3-1d_3.14.1-0ckbi1.93ubuntu.0.12.04.1_i386.deb) ...
Unpacking replacement libnss3-1d ...
Preparing to replace libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1 (using .../
libnss3_3.14.1-0ckbi1.93ubuntu.0.12.04.1_i386.deb) ...
Unpacking replacement libnss3 ...
Preparing to replace chromium-codecs-ffmpeg 20.0.1132.47~r144678-0ubuntu0.12.04.1
(using .../chromium-codecs-ffmpeg_23.0.1271.97-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement chromium-codecs-ffmpeg ...
Preparing to replace chromium-browser 20.0.1132.47~r144678-0ubuntu0.12.04.1 (using .../
chromium-browser_23.0.1271.97-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement chromium-browser ...
Preparing to replace libpulse0 1:1.1-0ubuntu15.1 (using .../libpulse0_1%%
3a1.1-0ubuntu15.2_i386.deb) ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.1 (using .../libpulse-mainloopglib0_1%%3a1.1-0ubuntu15.2_i386.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.1 (using .../libpulsedsp_1%%
3a1.1-0ubuntu15.2_i386.deb) ...
Unpacking replacement libpulsedsp ...
Preparing to replace libnm-util2 0.9.4.0-0ubuntu4.1 (using .../libnmutil2_0.9.4.0-0ubuntu4.2_i386.deb) ...
Unpacking replacement libnm-util2 ...
Preparing to replace libnm-glib4 0.9.4.0-0ubuntu4.1 (using .../libnmglib4_0.9.4.0-0ubuntu4.2_i386.deb) ...
Unpacking replacement libnm-glib4 ...
Preparing to replace network-manager 0.9.4.0-0ubuntu4.1 (using .../networkmanager_0.9.4.0-0ubuntu4.2_i386.deb) ...
Unpacking replacement network-manager ...
Preparing to replace libnm-glib-vpn1 0.9.4.0-0ubuntu4.1 (using .../libnm-glibvpn1_0.9.4.0-0ubuntu4.2_i386.deb) ...
Unpacking replacement libnm-glib-vpn1 ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.1 (using .../pulseaudio-utils_1%%
3a1.1-0ubuntu15.2_i386.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.1 (using .../pulseaudio_1%%
3a1.1-0ubuntu15.2_i386.deb) ...
Unpacking replacement pulseaudio ...

Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.1 (using .../pulseaudio-modulex11_1%%3a1.1-0ubuntu15.2_i386.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace x11-common 1:7.6+12ubuntu1 (using .../x11-common_1%%3a7.6
+12ubuntu2_all.deb) ...
Unpacking replacement x11-common ...
Preparing to replace xserver-xorg-video-all 1:7.6+12ubuntu1 (using .../xserver-xorg-videoall_1%%3a7.6+12ubuntu2_i386.deb) ...
Unpacking replacement xserver-xorg-video-all ...
Preparing to replace xserver-xorg-input-all 1:7.6+12ubuntu1 (using .../xserver-xorg-inputall_1%%3a7.6+12ubuntu2_i386.deb) ...
Unpacking replacement xserver-xorg-input-all ...
Preparing to replace xserver-xorg 1:7.6+12ubuntu1 (using .../xserver-xorg_1%%3a7.6
+12ubuntu2_i386.deb) ...
Unpacking replacement xserver-xorg ...
Preparing to replace xorg 1:7.6+12ubuntu1 (using .../xorg_1%%3a7.6
+12ubuntu2_i386.deb) ...
Unpacking replacement xorg ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up hplip-data (3.12.2-1ubuntu3.1) ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing hplip-data (--configure):
subprocess installed post-installation script returned error exit status 101
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of hplip:
hplip depends on hplip-data (= 3.12.2-1ubuntu3.1); however:
Package hplip-data is not configured yet.
dpkg: error processing hplip (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
printer-driver-postscript-hp depends on hplip (>= 3.12.2-1ubuntu3.1); however:
Package hplip is not configured yet.
dpkg: error processing printer-driver-postscript-hp (--configure):
dependency problems - leaving unconfigured
Setting up libfreetype6 (2.4.8-1ubuntu2.1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up libnspr4 (4.9.4-0ubuntu0.12.04.1) ...
Setting up libnss3 (3.14.1-0ckbi1.93ubuntu.0.12.04.1) ...
Setting up libnss3-1d (3.14.1-0ckbi1.93ubuntu.0.12.04.1) ...
Setting up libpulse0 (1:1.1-0ubuntu15.2) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.2) ...
Setting up libpulsedsp (1:1.1-0ubuntu15.2) ...
Setting up libnm-util2 (0.9.4.0-0ubuntu4.2) ...
Setting up libnm-glib4 (0.9.4.0-0ubuntu4.2) ...
Setting up network-manager (0.9.4.0-0ubuntu4.2) ...
Setting up libnm-glib-vpn1 (0.9.4.0-0ubuntu4.2) ...
Setting up pulseaudio-utils (1:1.1-0ubuntu15.2) ...

Setting up pulseaudio (1:1.1-0ubuntu15.2) ...
Setting up pulseaudio-module-x11 (1:1.1-0ubuntu15.2) ...
Setting up x11-common (1:7.6+12ubuntu2) ...
Setting up xserver-xorg-video-all (1:7.6+12ubuntu2) ...
Setting up xserver-xorg-input-all (1:7.6+12ubuntu2) ...
Setting up xserver-xorg (1:7.6+12ubuntu2) ...
Setting up xorg (1:7.6+12ubuntu2) ...
Setting up chromium-codecs-ffmpeg (23.0.1271.97-0ubuntu0.12.04.1) ...
Setting up chromium-browser (23.0.1271.97-0ubuntu0.12.04.1) ...
Setting up chromium-browser-l10n (23.0.1271.97-0ubuntu0.12.04.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
hplip-data
hplip
printer-driver-postscript-hp
Error in function:
Setting up hplip-data (3.12.2-1ubuntu3.1) ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing hplip-data (--configure):
subprocess installed post-installation script returned error exit status 101
dpkg: dependency problems prevent configuration of hplip:
hplip depends on hplip-data (= 3.12.2-1ubuntu3.1); however:
Package hplip-data is not configured yet.
dpkg: error processing hplip (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
printer-driver-postscript-hp depends on hplip (>= 3.12.2-1ubuntu3.1); however:
Package hplip is not configured yet.
dpkg: error processing printer-driver-postscript-hp (--configure):
dependency problems - leaving unconfigured

```
......................

Output from sudo get-apt update
 
```
Ign http://nz.archive.ubuntu.com precise InRelease
Ign http://nz.archive.ubuntu.com precise-updates InRelease
Ign http://nz.archive.ubuntu.com precise-backports InRelease
Hit http://nz.archive.ubuntu.com precise Release.gpg
Hit http://nz.archive.ubuntu.com precise-updates Release.gpg
Hit http://nz.archive.ubuntu.com precise-backports Release.gpg
Hit http://nz.archive.ubuntu.com precise Release
Hit http://nz.archive.ubuntu.com precise-updates Release
Hit http://nz.archive.ubuntu.com precise-backports Release
Ign http://extras.ubuntu.com precise InRelease
Ign http://security.ubuntu.com precise-security InRelease
Hit http://nz.archive.ubuntu.com precise/main Sources
Hit http://nz.archive.ubuntu.com precise/restricted Sources
Hit http://nz.archive.ubuntu.com precise/universe Sources
Hit http://nz.archive.ubuntu.com precise/multiverse Sources
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://nz.archive.ubuntu.com precise/main i386 Packages
Hit http://nz.archive.ubuntu.com precise/restricted i386 Packages
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://nz.archive.ubuntu.com precise/universe i386 Packages
Hit http://nz.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://nz.archive.ubuntu.com precise/main TranslationIndex
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]
Hit http://nz.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://nz.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://nz.archive.ubuntu.com precise/universe TranslationIndex
Hit http://nz.archive.ubuntu.com precise-updates/main Sources
Hit http://nz.archive.ubuntu.com precise-updates/restricted Sources
Hit http://extras.ubuntu.com precise Release
Hit http://nz.archive.ubuntu.com precise-updates/universe Sources
Hit http://nz.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://nz.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://nz.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://nz.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://nz.archive.ubuntu.com precise-updates/multiverse i386 Packages
Get:3 http://security.ubuntu.com precise-security/main Sources [61.0 kB]
Hit http://nz.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://nz.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://nz.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://extras.ubuntu.com precise/main Sources
Hit http://nz.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://nz.archive.ubuntu.com precise-backports/main Sources
Hit http://nz.archive.ubuntu.com precise-backports/restricted Sources
Hit http://nz.archive.ubuntu.com precise-backports/universe Sources
Hit http://nz.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://nz.archive.ubuntu.com precise-backports/main i386 Packages
Get:4 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Hit http://nz.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://nz.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages

Hit http://nz.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://nz.archive.ubuntu.com precise-backports/main TranslationIndex
Get:5 http://security.ubuntu.com precise-security/universe Sources [20.0 kB]
Hit http://nz.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://nz.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://nz.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://nz.archive.ubuntu.com precise/main Translation-en
Get:6 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B]
Hit http://nz.archive.ubuntu.com precise/multiverse Translation-en
Hit http://nz.archive.ubuntu.com precise/restricted Translation-en
Hit http://nz.archive.ubuntu.com precise/universe Translation-en
Get:7 http://security.ubuntu.com precise-security/main i386 Packages [227 kB]
Hit http://nz.archive.ubuntu.com precise-updates/main Translation-en
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://nz.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://nz.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://nz.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://nz.archive.ubuntu.com precise-backports/main Translation-en
Hit http://nz.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://nz.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://nz.archive.ubuntu.com precise-backports/universe Translation-en
Get:8 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:9 http://security.ubuntu.com precise-security/universe i386 Packages [63.1 kB]
Get:10 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,366 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en_NZ
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 431 kB in 8s (49.9 kB/s)
Reading package lists... Done
```

Thanks


---

### Post by ibjsb4 on 2013-01-21
Try reinstalling hplip.

```
sudo apt-get remove --autoremove hplip && sudo apt-get install hplip
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

You do have an HP printer, right?

---

### Post by TeHana86 on 2013-06-21
Thanks for the advice.
The delay in replying was due to a decline of the PC and eventually one day it would not boot - tried all sorts of ideas. And so after 12 years, had to say goodbye to that one.

Now on a 2003 HP (Del) nx9000 laptop (508Mb RAM). It was frustratingly slow on XP, taking 10 mins to load the AVG anti-virus updater each day. It took 4 months of much trial and error to trick the laptop to install Lubuntu 12.10 via Virtual CloneDrive  (other wouldn't work) and then persuade it to load from the CD - it all happened fast one afternoon and I couldn't remember what latest trick I tried.

BUT NOW - It runs 12.10 wonderfully. I found a thread on getting and installing hplip to solve the "scanner not found" problem and the little old laptop runs like a real computer. Lubuntu takes little room from the 40Gb hard drive. It has all the speed I need and except for not being able to play video clips yet, I take back all the ill thoughts I've had about it.

:KS

---

### Post by mörgæs on 2013-06-22
Good. If you can get a little more RAM you will see a big difference in speed.

---

