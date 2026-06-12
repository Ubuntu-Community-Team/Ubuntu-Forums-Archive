---
title: "Ubuntu boot errors"
date: 2024-03-25
forum: General Help
---

### Post by gybbs on 2024-03-25
Hi! I'm a new Ubuntu user (I'm just starting out), and after spending hours and hours configuring my system, I noticed that my PC was taking much longer to shut down (not even 5 seconds at first, compared with over two minutes now). I asked some AIs, and they advised me to use the following command to list the various errors since my last boot: journalctl -rb 0 -p 0..3
Here's the output I got:
mars 25 20:12:17 gybbs gdm-launch-environment][895]: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
mars 25 20:12:15 gybbs systemd[1396]: Failed to start Application launched by gnome-session-binary.
mars 25 20:12:15 gybbs systemd[1396]: Failed to start Application launched by gnome-session-binary.
mars 25 20:12:15 gybbs systemd[1396]: Failed to start Application launched by gnome-session-binary.
mars 25 20:12:14 gybbs gdm-password][1379]: gkr-pam: unable to locate daemon control file
mars 25 20:10:52 gybbs pulseaudio[948]: Module module-bluetooth-discover not loaded.
mars 25 20:10:52 gybbs pulseaudio[948]: Module module-bluetooth-policy not loaded.
mars 25 20:10:52 gybbs gnome-session-binary[980]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
mars 25 20:10:52 gybbs gnome-session-binary[980]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed

Does anyone know how to fix these problems? And please explain them to me! ^^'

Thanks for your help (and sorry if the topic is in the wrong category)!

---

### Post by QIII on 2024-03-25
Moved from a chat area to General Help.

---

### Post by aug7744 on 2024-03-25
Try edit config using the command below
sudo nano /etc/systemd/system.conf
Remove "#" in begin of "DefaultTimeoutStartSec" and "DefaultTimeoutStopSec" and add the settings
DefaultTimeoutStartSec=20s
DefaultTimeoutStopSec=20s

That control the maximum time the OS will wait when closing services and shutdown.

---

### Post by gybbs on 2024-03-26
Okay, but if I do this, what will actually happen? What am I risking? I mean, if it limits the time for the machine to shut down, does it (the machine, or even the services) risk shutting down incorrectly? Actually, the fact that it takes a long time isn't my biggest problem, I'm more concerned about errors.

---

### Post by aug7744 on 2024-03-26
That setting only limit the maximum time to run for each service or command in startup and shutdown.
I use for an long time an not problem.
That avoid the terrible long time that happen randomly when doing shutdown and show "waiting 2 minutes" for process having an long time to run. In high percentage that behavior is because not was possible run the command so waiting 2 minutes or limiting the time for each process is the same result.
Also in world of computers and system not always an error message is exactly an error message. If not happen problems in your hardware, no damage in filesystem, all softwares run correctly and not any other type of error you need simply ignore that type of error message =)

---

### Post by gybbs on 2024-03-27
Ok, thank you very much for your help!

---

### Post by gybbs on 2024-03-27
I have a question: if I uninstall/reinstall Ubuntu to factory state, my  problems will logically be solved. Because I've been doing a lot of  testing, changing, uninstalling and reinstalling third-party  services/packages in a lot of different ways, and I think that's what's  been causing me all my problems (removing packages that are useful for  the system to work properly, for example?). So I'd like some advice on  the best way to do it (a clean install), and if there's any  software/services I should install/configure for better security  (iptables, ufw/firewalld, clamonacc/OnAccessScan, fail2ban,  rkhunter/chkrootkit, timeshift...)? Thank you very much for your help.

---

### Post by aug7744 on 2024-03-28
Try create partitions on disk using GPT table.
 first partition being 8 MB unformatted and marked being bios_grub
 second partition being 600 MB formating as ext2 or ext4 for /boot
 third partition for /root being btrfs another partition for /home being btrfs
 and the last partition using total free disk space being btrfs.

  Try use 2 browsers ... one for normal browsing and another for banks and shopping.
 File archiver > peazip
 pdf reader > koodo reader
 system cleaner > bleachbit
 firewall > portmaster
  You need try anothers distro ubuntu based .. have distro use less of 500 MB RAM and are faster.
 Good luck.

---

