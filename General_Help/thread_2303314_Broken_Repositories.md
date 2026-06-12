---
title: "Broken Repositories"
date: 2015-11-17
forum: General Help
---

### Post by cranerja on 2015-11-17
A while back I may have added a ppa to obtain a certain package, and I am know unable to download certain packages from the official ubuntu repositories. I do not remember what the ppa was and I have cleaned my ppas. I am still unable to understand why it won't work.

```
$ sudo apt-get install libreoffice-baseReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gambas3-gb-desktop gambas3-gb-desktop-x11 gambas3-gb-image gambas3-gb-qt4
  linux-image-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libhsqldb1.8.0-java libreoffice-base-drivers libreoffice-java-common
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libservlet3.0-java
Suggested packages:
  libreoffice-gcj libreoffice-report-builder libjtds-java
  libreoffice-mysql-connector libmyodbc libmysql-java
  libreoffice-sdbc-postgresql odbc-postgresql libpg-java libsqliteodbc tdsodbc
  mdbtools
The following NEW packages will be installed:
  libhsqldb1.8.0-java libreoffice-base libreoffice-base-drivers
  libreoffice-java-common libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb
  libservlet3.0-java
0 upgraded, 7 newly installed, 0 to remove and 37 not upgraded.
Need to get 5,283 kB of archives.
After this operation, 15.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  libhsqldb1.8.0-java
Install these packages without verification? [y/N] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libservlet3.0-java all 7.0.52-1ubuntu0.3 [294 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main libhsqldb1.8.0-java all 1.8.0.10+dfsg-3ubuntu1 [895 kB]
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libreoffice-base-drivers amd64 1:4.2.8-0ubuntu2
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libreoffice-base-drivers amd64 1:4.2.8-0ubuntu2
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libreoffice-base amd64 1:4.2.8-0ubuntu2
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libreoffice-java-common all 1:4.2.8-0ubuntu2
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libreoffice-sdbc-firebird amd64 1:4.2.8-0ubuntu2
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libreoffice-sdbc-hsqldb amd64 1:4.2.8-0ubuntu2
  404  Not Found [IP: 91.189.91.24 80]
Fetched 1,189 kB in 34s (34.0 kB/s)                                            
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-base-drivers_4.2.8-0ubuntu2_amd64.deb  404  Not Found [IP: 91.189.91.24 80]


E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-base_4.2.8-0ubuntu2_amd64.deb  404  Not Found [IP: 91.189.91.24 80]


E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-java-common_4.2.8-0ubuntu2_all.deb  404  Not Found [IP: 91.189.91.24 80]


E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-sdbc-firebird_4.2.8-0ubuntu2_amd64.deb  404  Not Found [IP: 91.189.91.24 80]


E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-sdbc-hsqldb_4.2.8-0ubuntu2_amd64.deb  404  Not Found [IP: 91.189.91.24 80]


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



```

I also have that weird authentication warning.
Any ideas?

---

### Post by grahammechanical on 2015-11-17
In cleaning out those PPAs did you also disable some of the Ubuntu repositories?

Regards.

---

### Post by deadflowr on 2015-11-18
Perhaps best to run
```
sudo apt-get update
```
if errors show up, post the full output.

From a casual looksy, the packages listed, such as libreoffice-base, are no longer at the version you are trying to get, but have been updated.
This is usually fixed by running the above command.

---

### Post by cranerja on 2015-11-18
> **deadflowr said:**
> Perhaps best to run
```
sudo apt-get update
```
if errors show up, post the full output.

From a casual looksy, the packages listed, such as libreoffice-base, are no longer at the version you are trying to get, but have been updated.
This is usually fixed by running the above command.

I also ran that, and it gives me:
```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13B00F1FD2C19886

W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32


W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32


W: GPG error: http://us.archive.ubuntu.com trusty-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: https://private-ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E131728675254D99
W: GPG error: http://us.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  


W: Failed to fetch http://repository.spotify.com/dists/stable/InRelease  


W: Some index files failed to download. They have been ignored, or old ones used instead.



```

Ignoring the spotify entry, something is clearly wrong.

And no, I didn't clear out any official ppas.

---

### Post by oldos2er on 2015-11-19
You can get the gpg keys with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the alphanumeric string appearing after 
NO_PUBKEY.

Can you post the output of ```
ls /etc/apt/sources.list.d/
``` please?

---

### Post by cranerja on 2015-11-19
> **oldos2er said:**
> You can get the gpg keys with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is the alphanumeric string appearing after 
NO_PUBKEY.

Can you post the output of ```
ls /etc/apt/sources.list.d/
``` please?

After doing that apt-get update remains the same, and this is the output for one of the codes.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A040830F7FAC5991Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.SZTZqZKTV2 --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/atareao-atareao.gpg --keyring /etc/apt/trusted.gpg.d/fossfreedom-rhythmbox-plugins.gpg --keyring /etc/apt/trusted.gpg.d/fossfreedom-rhythmbox.gpg --keyring /etc/apt/trusted.gpg.d/gambas-team-gambas3.gpg --keyring /etc/apt/trusted.gpg.d/gezakovacs-ppa.gpg --keyring /etc/apt/trusted.gpg.d/glennric-dolphin-emu.gpg --keyring /etc/apt/trusted.gpg.d/graphics-drivers-ppa.gpg --keyring /etc/apt/trusted.gpg.d/grumbel-ppa.gpg --keyring /etc/apt/trusted.gpg.d/i-nex-development-team-daily.gpg --keyring /etc/apt/trusted.gpg.d/i-nex-development-team-stable.gpg --keyring /etc/apt/trusted.gpg.d/jfi-ppa.gpg --keyring /etc/apt/trusted.gpg.d/kirillshkrogalev-ffmpeg-next.gpg --keyring /etc/apt/trusted.gpg.d/maarten-baert-simplescreenrecorder.gpg --keyring /etc/apt/trusted.gpg.d/minecraft-installer-peeps-minecraft-installer.gpg --keyring /etc/apt/trusted.gpg.d/mixxx-mixxx.gpg --keyring /etc/apt/trusted.gpg.d/nilarimogard-webupd8.gpg --keyring /etc/apt/trusted.gpg.d/noobslab-apps.gpg --keyring /etc/apt/trusted.gpg.d/noobslab-icons.gpg --keyring /etc/apt/trusted.gpg.d/noobslab-nitrux-os.gpg --keyring /etc/apt/trusted.gpg.d/noobslab-themes.gpg --keyring /etc/apt/trusted.gpg.d/numix-ppa.gpg --keyring /etc/apt/trusted.gpg.d/obsproject-obs-studio.gpg --keyring /etc/apt/trusted.gpg.d/oibaf-graphics-drivers.gpg --keyring /etc/apt/trusted.gpg.d/openjdk-r-ppa.gpg --keyring /etc/apt/trusted.gpg.d/osmoma-audio-recorder.gpg --keyring /etc/apt/trusted.gpg.d/otto-kesselgulasch-gimp.gpg --keyring /etc/apt/trusted.gpg.d/phablet-team-tools.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/ravefinity-project-ppa.gpg --keyring /etc/apt/trusted.gpg.d/steam.gpg --keyring /etc/apt/trusted.gpg.d/team-xbmc-ppa.gpg --keyring /etc/apt/trusted.gpg.d/teejee2008-ppa.gpg --keyring /etc/apt/trusted.gpg.d/thopiekar-darling.gpg --keyring /etc/apt/trusted.gpg.d/umang-indicator-stickynotes.gpg --keyring /etc/apt/trusted.gpg.d/vokoscreen-dev-vokoscreen.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-java.gpg --keyring /etc/apt/trusted.gpg.d/whatsapp-purple-ppa.gpg --keyring /etc/apt/trusted.gpg.d/xorg-edgers-ppa.gpg --keyring /etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg --keyring /etc/apt/trusted.gpg.d/yktooo-ppa.gpg --keyserver keyserver.ubuntu.com --recv-keys A040830F7FAC5991
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yannubuntu-boot-repair.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/yktooo-ppa.gpg': resource limit
gpg: requesting key 7FAC5991 from hkp server keyserver.ubuntu.com
gpg: key 7FAC5991: "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>" 28 new signatures
gpg: Total number processed: 1
gpg:         new signatures: 28



```

And here is my sources list:

```
ls /etc/apt/sources.list.d/atareao-atareao-trusty.list
atareao-atareao-trusty.list.save
fossfreedom-rhythmbox-plugins-trusty.list
fossfreedom-rhythmbox-plugins-trusty.list.save
fossfreedom-rhythmbox-trusty.list
fossfreedom-rhythmbox-trusty.list.save
gambas-team-gambas3-trusty.list
gambas-team-gambas3-trusty.list.save
gezakovacs-ppa-trusty.list
gezakovacs-ppa-trusty.list.save
glennric-dolphin-emu-trusty.list
glennric-dolphin-emu-trusty.list.save
google-chrome.list
google-chrome.list.save
google-chrome-unstable.list.save
google-earth.list
google-earth.list.save
graphics-drivers-ppa-trusty.list
graphics-drivers-ppa-trusty.list.save
grumbel-ppa-trusty.list
grumbel-ppa-trusty.list.save
i-nex-development-team-daily-trusty.list
i-nex-development-team-daily-trusty.list.save
i-nex-development-team-stable-trusty.list
i-nex-development-team-stable-trusty.list.save
jfi-ppa-trusty.list
jfi-ppa-trusty.list.save
kirillshkrogalev-ffmpeg-next-trusty.list
kirillshkrogalev-ffmpeg-next-trusty.list.save
maarten-baert-simplescreenrecorder-trusty.list
maarten-baert-simplescreenrecorder-trusty.list.save
minecraft-installer-peeps-minecraft-installer-trusty.list
minecraft-installer-peeps-minecraft-installer-trusty.list.save
mixxx-mixxx-trusty.list
mixxx-mixxx-trusty.list.save
nilarimogard-webupd8-trusty.list
nilarimogard-webupd8-trusty.list.save
noobslab-apps-trusty.list
noobslab-apps-trusty.list.save
noobslab-icons-trusty.list
noobslab-icons-trusty.list.save
noobslab-nitrux-os-trusty.list
noobslab-nitrux-os-trusty.list.save
noobslab-themes-trusty.list
noobslab-themes-trusty.list.save
numix-ppa-trusty.list
numix-ppa-trusty.list.save
obsproject-obs-studio-trusty.list
obsproject-obs-studio-trusty.list.save
oibaf-graphics-drivers-trusty.list
oibaf-graphics-drivers-trusty.list.save
openjdk-r-ppa-trusty.list
openjdk-r-ppa-trusty.list.save
osmoma-audio-recorder-trusty.list
osmoma-audio-recorder-trusty.list.save
otto-kesselgulasch-gimp-trusty.list
otto-kesselgulasch-gimp-trusty.list.save
phablet-team-tools-trusty.list
phablet-team-tools-trusty.list.save
pipelight-stable-trusty.list
pipelight-stable-trusty.list.save
playdeb.list
playdeb.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.save
ravefinity-project-ppa-trusty.list
ravefinity-project-ppa-trusty.list.save
steam.list
steam.list.save
team-xbmc-ppa-trusty.list
team-xbmc-ppa-trusty.list.save
teejee2008-ppa-trusty.list
teejee2008-ppa-trusty.list.save
thopiekar-darling-trusty.list
thopiekar-darling-trusty.list.save
umang-indicator-stickynotes-trusty.list
umang-indicator-stickynotes-trusty.list.save
vokoscreen-dev-vokoscreen-trusty.list
vokoscreen-dev-vokoscreen-trusty.list.save
webupd8team-java-trusty.list
webupd8team-java-trusty.list.save
whatsapp-purple-ppa-trusty.list
whatsapp-purple-ppa-trusty.list.save
xorg-edgers-ppa-trusty.list
xorg-edgers-ppa-trusty.list.save
yannubuntu-boot-repair-trusty.list
yannubuntu-boot-repair-trusty.list.save
yktooo-ppa-trusty.list
yktooo-ppa-trusty.list.save



```

---

### Post by oldos2er on 2015-11-19
Wow, that is a lot of PPAs. I thought you said you cleaned them out?

Are you using the main server or a mirror?

---

### Post by cranerja on 2015-11-19
> **oldos2er said:**
> Wow, that is a lot of PPAs. I thought you said you cleaned them out?

Are you using the main server or a mirror?

I did.

And as far as I know, I am using the main server.

---

### Post by sandyd on 2015-11-19
Can you post the output of
```

apt-key list
```
please?

---

### Post by mc4man on 2015-11-20
You've exceeded the limit on gpg key's (40) so remove all the _unused ones_ in  /etc/apt/trusted.gpg.d

---

