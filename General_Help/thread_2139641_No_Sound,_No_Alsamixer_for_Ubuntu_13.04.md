---
title: "No Sound, No Alsamixer for Ubuntu 13.04"
date: 2013-04-27
forum: General Help
---

### Post by Keinden on 2013-04-27
[I](Just a fair warning, I've only just been using ubuntu 12.10 as a os where I can't fool around like windows (gaming etc) so I don't know much about programming)

[/I]I've only been using Ubuntu 12.10 for my work which was perfectly fine, sound ok everything until I upgraded. At first, the upgrade said it was sucessful but when I decided to go on youtube to listen to some tunes it didn't work (tried with headphones and speakers). I then swapped to Windows 8 to see if something happened to it but it was working there. I did have a look around other sites but for some reason when I type alsamixer in Terminal, it shows no such file or directory.

---

### Post by Keinden on 2013-04-27
Ok, So I did what this guy did after looking around the page (URL : [http://ubuntuforums.org/showthread.php?t=2139589](http://ubuntuforums.org/showthread.php?t=2139589))

For the first 2 codes it went well but when it came to the third code (sudo alsa force-reload) it doesn't seem to finish
```

leo@leo-ubuntu:~$ apt-get remove --purge alsa-base pulseaudio
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
leo@leo-ubuntu:~$ sudo apt-get remove --purge alsa-base pulseaudio
[sudo] password for leo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  efibootmgr
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  alsa-base* indicator-sound* libcanberra-pulse* pulseaudio*
  pulseaudio-esound-compat* pulseaudio-module-bluetooth*
  pulseaudio-module-x11* ubuntu-desktop*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 5,148 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157948 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing alsa-base ...
Purging configuration files for alsa-base ...
Removing indicator-sound ...
Removing libcanberra-pulse:amd64 ...
Purging configuration files for libcanberra-pulse:amd64 ...
Removing pulseaudio-module-x11 ...
Removing pulseaudio-module-bluetooth ...
Removing pulseaudio-esound-compat ...
Removing pulseaudio ...
Purging configuration files for pulseaudio ...
userdel: group pulse not removed because it has other members.
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for ureadahead ...
leo@leo-ubuntu:~$ sudo apt-get install alsa-base pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  efibootmgr
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  pulseaudio-module-x11
Suggested packages:
  apmd alsa-oss oss-compat pavumeter paman paprefs pulseaudio-module-raop
  pulseaudio-esound-compat
The following NEW packages will be installed:
  alsa-base pulseaudio pulseaudio-module-x11
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,023 kB/1,174 kB of archives.
After this operation, 4,120 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main pulseaudio amd64 1:3.0-0ubuntu6 [1,003 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main pulseaudio-module-x11 amd64 1:3.0-0ubuntu6 [19.5 kB]
Fetched 1,023 kB in 22s (46.4 kB/s)                                            
Selecting previously unselected package alsa-base.
(Reading database ... 157704 files and directories currently installed.)
Unpacking alsa-base (from .../alsa-base_1.0.25+dfsg-0ubuntu4_all.deb) ...
Selecting previously unselected package pulseaudio.
Unpacking pulseaudio (from .../pulseaudio_1%3a3.0-0ubuntu6_amd64.deb) ...
Selecting previously unselected package pulseaudio-module-x11.
Unpacking pulseaudio-module-x11 (from .../pulseaudio-module-x11_1%3a3.0-0ubuntu6_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up alsa-base (1.0.25+dfsg-0ubuntu4) ...
Setting up pulseaudio (1:3.0-0ubuntu6) ...
Adding user pulse to group audio
Processing triggers for ureadahead ...
Setting up pulseaudio-module-x11 (1:3.0-0ubuntu6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
leo@leo-ubuntu:~$ alsa force-reload
mkdir: cannot create directory &#8216;/var/run/alsa&#8217;: Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 135: /sbin/alsa: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer.
mkdir: cannot create directory &#8216;/var/run/alsa&#8217;: Permission denied
Loading ALSA sound driver modules: (none to reload).
leo@leo-ubuntu:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer

```
The last line is just hanging there.....

---

### Post by pqwoerituytrueiwoq on 2013-04-27
if you are using HDMI audio it is probably a bug in the 3.8.0-19 kernel
installing the [mainline kernel](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme) solves this

---

### Post by Elfy on 2013-04-27
*Thread moved to **General Help**.*

---

### Post by Keinden on 2013-04-27
Its not the HDMI audio though, its both where you connect your headphone and the speakers inbuilt to my laptop but I will see if your suggestion will help

---

### Post by Keinden on 2013-04-27
It worked! Although the test sounds don't work :/ but thanks!

---

