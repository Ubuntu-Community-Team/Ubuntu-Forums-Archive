---
title: "permission denied in GUII application."
date: 2023-04-29
forum: General Help
---

### Post by ulao3 on 2023-04-29
I'm trying to use a application called dolphin, no, not the file browser. I need to configure a location for files it will use. I have my files in the media directory but Dolphin can't access them? Every directory out side my home directory says Permission denied. Is there any way to fix that? I run the app via a short cut I made on the desktop, was hoping to add a sudo to it but that is outside my knowledge.

---

### Post by deadflowr on 2023-04-30
Do you mean the emulator dolphin?
From Ubuntu's Software Store?

---

### Post by The Cog on 2023-04-30
Is this Dolphin app installed as a snap package? I guess so. In which case no, there is no way to fix that other than uninstall the Dolphin snap and install a different type of package - look to see if you can get a .deb package file to install instead. If you can find one, just double-clicking the .deb file should launch an installer.
If you really are stuck with a snap package then you will have to copy the files from your media directory to your home directory, work on them there, and then copy them back to the media directory when you are finished.

EDIT:
It seems that it is now possible to tell snaps to allow access to removable media: See posts #12, #13.

---

### Post by yancek on 2023-04-30
>  Every directory out side my home directory says Permission denied.

I'm not familiar with this application but what you describe is standard/expected behavior on any Linux system.  Most anything outside a user /home directory will need root (sudo) permissions.

The media directory is generally used for external devices.  Is this program on an external drive or are you just trying to mount it there?  What do you mean by configure a location for files it will use?  Are these the dolphin configuration files or files the application will be working on/with?

---

### Post by ulao3 on 2023-04-30
Dolphin just reads from a selected dir for its so called "games". I mount a few network drives to that location that it needs to load. Nothing needs to write to it. 
I do see a deb  package. I can try that.

---

### Post by ulao3 on 2023-04-30
Had to learn about snap, but yeah that got it... Installs ok with deb.

I also see the version is old but was able to find the latest version, when doing this the dpkg says errors were encountered while processing how do I check these?

---

### Post by Holger_Gehrke on 2023-04-30
Did you uninstall the snap version before installing the .deb ? Depending on the PATH environment variable the snap might have higher priority and get called even after you've installed the .deb.

Holger

---

### Post by #&amp;thj^% on 2023-04-30
> **ulao3 said:**
> when doing this the dpkg says errors were encountered while processing how do I check these?

Try this```
dpkg --audit 
```

---

### Post by ulao3 on 2023-04-30
yea the audit tells me to configure the dolphin app. Configuring them gives my the error above. I could not figure out how to remove the  snap version how is that done?
snap remove says its not installed but its still int he snap folder ((oh it has another name then the deb )) ok removed it.
but still cant configure
```

sudo dpkg -i dolphin-emu_5.0-17995-1_amd64.deb
[sudo] password for ulao:
Selecting previously unselected package dolphin-emu.
(Reading database ... 268185 files and directories currently installed.)
Preparing to unpack dolphin-emu_5.0-17995-1_amd64.deb ...
Unpacking dolphin-emu (5.0-17995-1) ...
dpkg: dependency problems prevent configuration of dolphin-emu:
 dolphin-emu depends on libavcodec59 (>= 7:5.0); however:
  Package libavcodec59 is not installed.
 dolphin-emu depends on libavformat59 (>= 7:5.0); however:
  Package libavformat59 is not installed.
 dolphin-emu depends on libavutil57 (>= 7:5.0); however:
  Package libavutil57 is not installed.
 dolphin-emu depends on libc6 (>= 2.34); however:
  Version of libc6:amd64 on system is 2.31-0ubuntu9.2.
 dolphin-emu depends on libcubeb0 (>= 0.0~git20210801.6ce9596); however:
  Package libcubeb0 is not installed.
 dolphin-emu depends on libenet7; however:
  Package libenet7 is not installed.
 dolphin-emu depends on libfmt9 (>= 9.1.0+ds1); however:
  Package libfmt9 is not installed.
 dolphin-emu depends on libhidapi-hidraw0 (>= 0.8.0~rc1+git20140201.3a66d4e+dfsg); however:
  Package libhidapi-hidraw0 is not installed.
 dolphin-emu depends on libmbedcrypto7 (>= 2.28.0); however:
  Package libmbedcrypto7 is not installed.
 dolphin-emu depends on libmbedtls14 (>= 2.28.0); however:
  Package libmbedtls14 is not installed.
 dolphin-emu depends on libmbedx509-1 (>= 2.28.0); however:
  Package libmbedx509-1 is not installed.
 dolphin-emu depends on libmgba0.10 (>= 0.10.1+dfsg); however:
  Package libmgba0.10 is not installed.
 dolphin-emu depends on libopengl0; however:
  Package libopengl0 is not installed.
 dolphin-emu depends on libqt6core6 (>= 6.4.0); however:
  Package libqt6core6 is not installed.
 dolphin-emu depends on libqt6gui6 (>= 6.4.0); however:
  Package libqt6gui6 is not installed.
 dolphin-emu depends on libqt6widgets6 (>= 6.3.0); however:
  Package libqt6widgets6 is not installed.
 dolphin-emu depends on libsfml-network2.5; however:
  Package libsfml-network2.5 is not installed.
 dolphin-emu depends on libsfml-system2.5; however:
  Package libsfml-system2.5 is not installed.
 dolphin-emu depends on libstdc++6 (>= 12); however:
  Version of libstdc++6:amd64 on system is 10.3.0-1ubuntu1~20.04.
 dolphin-emu depends on libswscale6 (>= 7:5.0); however:
  Package libswscale6 is not installed.
 dolphin-emu depends on libxxhash0 (>= 0.6.5); however:
  Package libxxhash0 is not installed.
 dolphin-emu depends on libzstd1 (>= 1.5.2); however:
  Version of libzstd1:amd64 on system is 1.4.4+dfsg-3ubuntu0.1.
 dolphin-emu depends on dolphin-emu-data (= 5.0-17995-1); however:
  Package dolphin-emu-data is not installed.

dpkg: error processing package dolphin-emu (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for man-db (2.9.1-1) ...
Errors were encountered while processing:
 dolphin-emu

```
```

sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 dolphin-emu          Gamecube and Wii emulator




```

---

### Post by ulao3 on 2023-04-30
this maybe my issue..

"Do not use Debian packages on Ubuntu. While Ubuntu is derived from Debian, the dependencies are different and they won't work."

maybe I need the right configured package ? I wnt to install the latest build not latest stable because the latest stable of dolphin is way too old. can apt install get a dev build?

EDIT:: I think I found the hidden page with details.
[URL="https://wiki.dolphin-emu.org/index.php?title=Installing_Dolphin#Ubuntu"]https://wiki.dolphin-emu.org/index.php?title=Installing_Dolphin#Ubuntu


[COLOR=#000000]but this just gives me:

sudo apt-add-repository ppa:dolphin-emu/ppa
Cannot add PPA: 'ppa:~dolphin-emu/ubuntu/ppa'.
ERROR: '~dolphin-emu' user or team does not exist.
[/COLOR]


this works
[/URL]sudo apt-add-repository ppa:ubuntu-toolchain-r/test

but I'm not sure what this means
You don't need to update all GCC packages, just upgrade libstdc++6,  gcc-4.9-base and eventual dependencies in Synaptic, and disable the PPA.


Someone else with my issues got this reply. 

  
          
                       Don't use the PPA. Use the snap package instead.
 sudo snap install dolphin-emulator --edge
 or alternatively to install the stable version of Dolphin Emulator:
 sudo snap install dolphin-emulator
     
Well snap gives me my initial issue, and stable is years old. Solution is to compile from source, FUN! or find a way to make snap work but I think it was concluded you can't

---

### Post by Holger_Gehrke on 2023-04-30
Where did you get that .deb file ? It has at least one dependency that is hard to meet on your system (listdc++6). What version of Ubuntu are you using (looks like 20.04, from the version of libstdc++6) ? The official homepage for dolphin doesn't offer any downloads for Linux, only for Windows, Mac, and Android. The wiki at [https://wiki.dolphin-emu.org/index.php?title=Installing_Dolphin](https://wiki.dolphin-emu.org/index.php?title=Installing_Dolphin) gives a PPA for Ubuntu, but since they are also talking about Ubuntu 14.04 and the PPA doesn't exist anymore I assume this information is out of date. Looking at packages.ubuntu.com I find that dolphin used to be part of the LTS releases except for 22.04. It is in the repositories for 20.04 and 23.04, though. A search for a PPA on launchpad gives ppa:ghostplant/flashback as a source for dolphin-emu for 22.04.

Holger

---

### Post by Holger_Gehrke on 2023-04-30
Regarding access by snaps to removable media auto-mounted through udisks in /media/$USER/: snaps are able to access these file systems, if they have the requisite "plug". To make that connection you use 'snap connect <snap-name>:<plug-name> <snap-name>:<slot-name>' in this case ```
snap connect dolphin-emulator:removable-media
``` You don't need the '<snap-name>:<slot-name>' part because removable-media is in the core snap.

Holger

---

### Post by ulao3 on 2023-04-30
Yes it is dolphin-emu, will try a few of these suggestions.


"snap connect dolphin-emulator:removable-media"

worked

---

