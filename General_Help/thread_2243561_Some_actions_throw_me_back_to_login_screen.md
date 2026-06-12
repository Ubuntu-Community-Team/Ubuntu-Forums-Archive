---
title: "Some actions throw me back to login screen"
date: 2014-09-09
forum: General Help
---

### Post by albertredneck on 2014-09-09
Hi guys!

I have a big deal of a problem here. Ubuntu desktop 14.04 throws me back to loging screen pseudorandomly. I'm saying pseudorandomly because it happens ALWAYS when I double click the "terminator" scrollbar to maximize it, or usually while mousewheel-scrolling in my browser. A pattern here is that after some time loged in, the next action (a click somewhere, for example) is more likely to cause the error.

Black screen, and back to login.

I've looked for errors in my system and xorg logs and I can see no errors except for:
Sep  9 22:54:36 albert-N56VZ gnome-session[19624]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012

This may be the cause and I've seen somewhere that a rollback to the previous kernel may fix the problem. I have other options? I'll provide any other info if that may help!

How can I safely rollback the kernel version if that's the last option?

Thank you all.

---

### Post by albertredneck on 2014-09-09
That's in my system log in the last "reset to log screen". The -33 error and GLib-CRITICAL are recurrent and show up every time it happens.

Sep  9 23:21:05 albert-N56VZ pulseaudio[27299]: [pulseaudio] pid.c: Daemon already running.
Sep  9 23:21:05 albert-N56VZ colord: Device added: xrandr-Seiko Epson Corporation
Sep  9 23:21:05 albert-N56VZ colord: Automatic metadata add icc-ed9d19f328b896364af34c8d584422f5 to xrandr-Seiko Epson Corporation
Sep  9 23:21:05 albert-N56VZ colord: Profile added: icc-ed9d19f328b896364af34c8d584422f5
Sep  9 23:21:36 albert-N56VZ gnome-session[27085]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Sep  9 23:22:26 albert-N56VZ wpa_supplicant[1251]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep  9 23:22:28 albert-N56VZ wpa_supplicant[1251]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Sep  9 23:22:54 albert-N56VZ gnome-session[27085]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Sep  9 23:22:54 albert-N56VZ colord: device removed: xrandr-Seiko Epson Corporation
Sep  9 23:22:54 albert-N56VZ colord: Profile removed: icc-ed9d19f328b896364af34c8d584422f5

---

### Post by albertredneck on 2014-09-09
I've started ubuntu via grub with the previous kernel 3.13.0-34, and I've even loged in with a guest account and it keeps happening! :(

I've just to double click the terminator top bar to reproduce it.

Any help will be highly appreciated.

---

### Post by nrobinson on 2014-09-10
I am having the same problem. Running 14.04 with the latest kernel.

I have a NVIDIA optimus card. The error occurs with the NVIDIA drivers installed and without.

The problem started when I installed updates yesterday. Now it occurs randomly when I play videos in either Chrome or Firefox. When I make an application fullscreen, or sometimes just when the machine is sitting idle.

ep 10 16:17:01 nathan-msi-laptop CRON[6365]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 10 16:21:31 nathan-msi-laptop colord: device removed: xrandr-Chi Mei Optoelectronics corp.
Sep 10 16:21:31 nathan-msi-laptop colord: Profile removed: icc-9019bc52308aa3f83080006a53183acf
Sep 10 16:21:31 nathan-msi-laptop colord: Profile removed: icc-d2c2534b08bcf9849cba381f47ff4d2c
Sep 10 16:21:31 nathan-msi-laptop colord: Profile removed: icc-a083381465503fc0a3f138d507c072d2
Sep 10 16:21:31 nathan-msi-laptop gnome-session[3477]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Sep 10 16:21:31 nathan-msi-laptop bluetoothd[1567]: Endpoint unregistered: sender=:1.65 path=/MediaEndpoint/HFPAG
Sep 10 16:21:31 nathan-msi-laptop bluetoothd[1567]: Endpoint unregistered: sender=:1.65 path=/MediaEndpoint/HFPHS
Sep 10 16:21:31 nathan-msi-laptop bluetoothd[1567]: Endpoint unregistered: sender=:1.65 path=/MediaEndpoint/A2DPSource
Sep 10 16:21:31 nathan-msi-laptop bluetoothd[1567]: Endpoint unregistered: sender=:1.65 path=/MediaEndpoint/A2DPSink
Sep 10 16:21:31 nathan-msi-laptop bluetoothd[1567]: hci0: Remove UUID (0x0011) failed: Busy (0x0a)
Sep 10 16:21:31 nathan-msi-laptop acpid: client connected from 6398[0:0]
Sep 10 16:21:31 nathan-msi-laptop acpid: 1 client rule loaded

---

### Post by podestm2 on 2014-09-10
I am also having this problem with 14.04 on a lenovo Y580 laptop (intel + NVIDIA cards).
I initially thought it was due to the Intel drivers I recently installed but they have been purged and the issue persists. I'm using the NVIDIA 343.13 drivers (but have tried reverting). It also happns during a guest session.
It appears to happen randomly with some ui actions, such as resizing windows, but opening a content rich page on firefox (such as facebook) reproducibly causes a return to the login screen.

The problem started following an update yesterday.

#edit : I appear to have resolved my problem by reconfiguring or reinstalling lightdm. I didn't check if only reconfiguring was sufficient. 
apt-get install --reinstall lightdm
dpkg-reconfigure lightdm

---

### Post by albertredneck on 2014-09-10
I've tried the podestm2 solution with no luck :( it keeps happening.

---

### Post by albertredneck on 2014-09-11
I've managed to fix it. Just reinstall ubuntu-desktop and unity:

sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install --reinstall unity

---

