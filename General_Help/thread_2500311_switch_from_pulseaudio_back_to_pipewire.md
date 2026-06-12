---
title: "switch from pulseaudio back to pipewire"
date: 2024-08-29
forum: General Help
---

### Post by drew1121 on 2024-08-29
I somehow have pulseaudio installed instead of pipewire. How would I go about switching back to it?

---

### Post by julian552 on 2024-09-02
You must first uninstall PulseAudio and its associated components.



[RIGHT][[COLOR=#a9a9a9][SIZE=1]Mini Militia[/SIZE][/COLOR]]("https://www.minimilitia.mobi/") [[COLOR=#a9a9a9][SIZE=1]App Lock[/SIZE][/COLOR]]("https://www.applock.ooo/")[/RIGHT]

---

### Post by paulparker2 on 2024-09-21
My VERSION="24.04.1 LTS (Noble Numbat)" 
with GNOME with Wayland



Those wanting pipewire need remove which of pulseaudio   ? 


Those wanting pulseaudio need remove which pipewire  ? 




These what self found today:   

> 
paulparker@7400K-hxi52:~$ apt search pulseaudio | grep -i installed

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libao-common/noble,now 1.2.2+20180113-1.1ubuntu4 all [installed,automatic]
libao4/noble,now 1.2.2+20180113-1.1ubuntu4 amd64 [installed,automatic]
libcanberra-pulse/noble,now 0.30-10ubuntu10 amd64 [installed,automatic]
libpcaudio0/noble,now 1.2-2build3 amd64 [installed,automatic]
libpulse-mainloop-glib0/noble,now 1:16.1+dfsg1-2ubuntu10 amd64 [installed,automatic]
libpulse0/noble,now 1:16.1+dfsg1-2ubuntu10 amd64 [installed,automatic]
pipewire-pulse/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
paulparker@7400K-hxi52:~$ 
paulparker@7400K-hxi52:~$ 
paulparker@7400K-hxi52:~$ 
paulparker@7400K-hxi52:~$ apt search pipewire  | grep -i installed

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

gnome-remote-desktop/noble-updates,now 46.3-0ubuntu1 amd64 [installed,automatic]
gstreamer1.0-pipewire/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
libpipewire-0.3-0t64/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
libpipewire-0.3-common/noble-updates,now 1.0.5-1ubuntu1 all [installed,automatic]
libpipewire-0.3-modules/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
libspa-0.2-bluetooth/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
libspa-0.2-modules/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
libwireplumber-0.4-0/noble,now 0.4.17-1ubuntu4 amd64 [installed,automatic]
pipewire/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
pipewire-alsa/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
pipewire-audio/noble-updates,now 1.0.5-1ubuntu1 all [installed,automatic]
pipewire-bin/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
pipewire-pulse/noble-updates,now 1.0.5-1ubuntu1 amd64 [installed,automatic]
wireplumber/noble,now 0.4.17-1ubuntu4 amd64 [installed,automatic]
paulparker@7400K-hxi52:~$ 



---

