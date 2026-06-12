---
title: "Ubuntu Software (snap-store) won't work when starting PC."
date: 2022-10-13
forum: General Help
---

### Post by luncaaa on 2022-10-13
Hello o/

Whenever I restart / turn on my PC and click on the "Ubuntu Software" app, it won't launch unless I run **sudo snap remove snap-store **and then install it with **s****udo snap install snap-store**

Why is this happening?

---

### Post by TheFu on 2022-10-16
Often, if you run the program from a terminal, instead of the menu, any errors will be displayed there, providing a hint to what might be the issue.  Try that.

I've never used the snap-store GUI program. On my systems, snaps are avoided as much as possible.

Also, it would be good to always say the release and DE being used, since that could be important for any GUI issues.

---

### Post by luncaaa on 2022-10-20
Sorry for replying so late

When I run **snap-store** in the terminal, this appears: /snap/snap-store/599/usr/bin/snap-store: error while loading shared libraries: libappstream.so.4: cannot open shared object file: No such file or directory
It says that that file or directory does not exist although I did not touch anything and the command works after uninstalling and reinstalling snap-store.

Where can I check the release and DE being used?
Running **sudo snap install snap-store** says "Installed snap-store 41.3-64-g512c0ff by Canonical"

---

### Post by Dennis N on 2022-10-20
> Where can I check the release and DE being used?
In Ubuntu, open **Settings > About** to see basic system information.
There are also utilities that provide information, some more than others. A basic one is **neofetch**.
------------ 
neofetch output:
```
[COLOR="#FF0000"]OS: Ubuntu 22.04.1 LTS x86_64[/COLOR] 
Host: KVM/QEMU (Standard PC (Q35 + ICH9, 2009) pc-q35-6.2) 
Kernel: 5.15.0-50-generic 
Uptime: 9 mins 
Packages: 1630 (dpkg), 25 (flatpak), 9 (snap) 
Shell: bash 5.1.16 
Resolution: 1920x1080 
[COLOR="#FF0000"]DE: GNOME 42.4 [/COLOR]
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru-bark-dark [GTK2/3] 
Icons: Papirus-Brown-Dark [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i3-8100 (2) @ 3.599GHz 
GPU: 00:01.0 Red Hat, Inc. Virtio GPU 
Memory: 1870MiB / 3923MiB 

```

---

### Post by luncaaa on 2022-10-23
My output is this:

OS: Ubuntu 22.04.1 LTS x86_64 
Host: Satellite Pro R50-B PSSG0E-003 
Kernel: 5.15.0-52-generic 
Uptime: 9 mins 
Packages: 1559 (dpkg), 11 (snap) 
hell: bash 5.1.16 
Resolution: 1360x768 
DE: GNOME 42.4 
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
 Icons: Yaru [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i3-4005U (4) @ 1.700GHz 
GPU: Intel Haswell-ULT 
Memory: 1784MiB / 11884MiB

-- All the packages are up-to-date --

---

### Post by Dennis N on 2022-10-23
The error message indicates a missing library libappstream.so.4

Run this in the terminal to get the missing library:

```
sudo apt install libappstream4
```

Restart, and see if Ubuntu Software works. Don't use sudo if you start from the terminal. You don't need it.

---

### Post by stephenandmindi on 2022-10-25
> **luncaaa said:**
> Sorry for replying so late

When I run **snap-store** in the terminal, this appears: /snap/snap-store/599/usr/bin/snap-store: error while loading shared libraries: libappstream.so.4: cannot open shared object file: No such file or directory
It says that that file or directory does not exist although I did not touch anything and the command works after uninstalling and reinstalling snap-store.


I have not had this one, but in the last week several snaps stopped working, all due to strangely missing shared libraries. Removing and reinstalling them fixed it for me.  I listed all snaps 'snap list' then ran them one by one.
Ones that failed for me included vlc, zoom-client and spotify.

I suspect it was a patch update that came through recently, but haven't spent the energy to figure that part out.

---

