---
title: "Can't get to GUI login screen on previously working system."
date: 2018-06-16
forum: General Help
---

### Post by 0c-bill on 2018-06-16
[B]OS: Ubuntu 18.04 desktop (with standard issue Gnome desktop)
GPU: nVidia GeForce GTX 770[/B]

Background:
   Installed Ubuntu 18.04 with full-disk encryption and LVM. Installed nVidia proprietary drivers. Everything appeared to work fine for over two weeks after this clean install. This included installing and playing Steam games like Kerbal Space Program, Rocket League, and From the Depths; all ran fine and with excellent performance. Then yesterday, Friday June 15, 2018, the machine stopped showing the GUI login screen for GDM. Machine boots fine, just hangs in tty1 with no graphical shell. I can log in and perform many functions in the other virtual terminals, even SSH in from another machine.


[U]Some hopefully useful details:

[/U]**sudo cat /proc/cmdline **yields:
BOOT_IMAGE=/vmlinuz-4.15.0-23-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=1

**sudo cat Xorg.0.log | grep EE **yields:
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    37.745] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[    37.745] (EE) open /dev/dri/card0: No such file or directory
[    37.745] (EE) open /dev/dri/card0: No such file or directory
[    37.746] (EE) Screen 0 deleted because of no matching config section.
[    37.752] (EE) AIGLX: reverting to software rendering


I haven't opened a bug report on launchpad yet, because I am not sure how to classify it yet...

Any ideas how to proceed in troubleshooting/diagnosing this would be greatly appreciated.

---

### Post by 0c-bill on 2018-06-17
I think I am closer to finding the main issue. Using **systemctl status** after booting my machine, shows that gdm service is up. But one of the log entries it displays indicates that the child process it spawned to show the desktop died shrotly after it was spawned. Stopping the gdm service and checking the status appears to indicate an issue with some encrypted/authenticated session. Going back to look at the status for when gdm service is running leads me to believe that a PAM module is being shutdown while it is still needed?

I any case if someone could take a look at this and tell me if it makes sense that I would think that gdm3 is being held-back from displaying due to a PAM-related issue? If my hunch is correct, I should be able to prove it by regressing the version of one or more of the recently updated packages on my system, question is - which package?

I have highlighted the interesting bits for the sake of convenience:

[SIZE=3][FONT=courier new]sudo systemctl status gdm[/FONT][/SIZE][SIZE=3][FONT=courier new][sudo] password for william: [/FONT][/SIZE]
[SIZE=3][FONT=courier new]&#9679; gdm.service - GNOME Display Manager[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   Active: active (running) since Sun 2018-06-17 17:46:51 EDT; 2h 30min ago[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  Process: 1331 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)[/FONT][/SIZE]
[SIZE=3][FONT=courier new] Main PID: 1340 (gdm3)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    Tasks: 3 (limit: 4915)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   CGroup: /system.slice/gdm.service[/FONT][/SIZE]
[SIZE=3][FONT=courier new]           &#9492;&#9472;1340 /usr/sbin/gdm3[/FONT][/SIZE]
[SIZE=3][FONT=courier new]
[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:51 little-black-box systemd[1]: Starting GNOME Display Manager...[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:51 little-black-box systemd[1]: Started GNOME Display Manager.[/FONT][/SIZE]
[B][I][COLOR=#008000][SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm-launch-environment][1355]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm-launch-environment][1355]: pam_unix(gdm-launch-environment:session): session closed for user gdm[/FONT][/SIZE][/COLOR]
[COLOR=#ff0000][SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: GdmDisplay: display lasted 0.396631 seconds[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: Child process -1376 was already dead.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: Child process 1355 was already dead.[/FONT][/SIZE][/COLOR][/I][/B]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: Unable to kill session worker process[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm-launch-environment][1438]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]william@little-black-box:~$ sudo systemctl stop gdm[/FONT][/SIZE]
[SIZE=3][FONT=courier new]william@little-black-box:~$ sudo systemctl status gdm[/FONT][/SIZE]
[SIZE=3][FONT=courier new]&#9679; gdm.service - GNOME Display Manager[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   Active: inactive (dead) since Sun 2018-06-17 20:17:33 EDT; 2s ago[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  Process: 1340 ExecStart=/usr/sbin/gdm3 (code=exited, status=0/SUCCESS)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  Process: 1331 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)[/FONT][/SIZE]
[SIZE=3][FONT=courier new] Main PID: 1340 (code=exited, status=0/SUCCESS)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]
[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm-launch-environment][1355]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm-launch-environment][1355]: pam_unix(gdm-launch-environment:session): session closed for user gdm[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: GdmDisplay: display lasted 0.396631 seconds[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: Child process -1376 was already dead.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: Child process 1355 was already dead.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm3[1340]: Unable to kill session worker process[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 17:46:52 little-black-box gdm-launch-environment][1438]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:33 little-black-box systemd[1]: Stopping GNOME Display Manager...[/FONT][/SIZE]
***[COLOR=#ff0000][SIZE=3][FONT=courier new]Jun 17 20:17:33 little-black-box gdm3[1340]: GLib: g_hash_table_find: assertion 'version == hash_table->version' failed[/FONT][/SIZE][/COLOR]***
[SIZE=3][FONT=courier new]Jun 17 20:17:33 little-black-box systemd[1]: Stopped GNOME Display Manager.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]william@little-black-box:~$ sudo systemctl start gdm[/FONT][/SIZE]
[SIZE=3][FONT=courier new]william@little-black-box:~$ sudo systemctl status gdm[/FONT][/SIZE]
[SIZE=3][FONT=courier new]&#9679; gdm.service - GNOME Display Manager[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   Active: active (running) since Sun 2018-06-17 20:17:51 EDT; 2s ago[/FONT][/SIZE]
[SIZE=3][FONT=courier new]  Process: 2865 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)[/FONT][/SIZE]
[SIZE=3][FONT=courier new] Main PID: 2867 (gdm3)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]    Tasks: 4 (limit: 4915)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]   CGroup: /system.slice/gdm.service[/FONT][/SIZE]
[SIZE=3][FONT=courier new]           &#9492;&#9472;2867 /usr/sbin/gdm3[/FONT][/SIZE]
[SIZE=3][FONT=courier new]
[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box systemd[1]: Starting GNOME Display Manager...[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box systemd[1]: Started GNOME Display Manager.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box gdm-launch-environment][2871]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box gdm-launch-environment][2871]: pam_unix(gdm-launch-environment:session): session closed for user gdm[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box gdm3[2867]: GdmDisplay: display lasted 0.217362 seconds[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box gdm3[2867]: Child process -2888 was already dead.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box gdm3[2867]: Child process 2871 was already dead.[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box gdm3[2867]: Unable to kill session worker process[/FONT][/SIZE]
[SIZE=3][FONT=courier new]Jun 17 20:17:51 little-black-box gdm-launch-environment][2914]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)

[/FONT][/SIZE]

---

### Post by 0c-bill on 2018-07-01
[SIZE=4]*SOLVED*[/SIZE]

[SIZE=3]Found a file left over from an attempt fix the ubiquitous screen-tearing problem. It had a nomodeset entry.
Lesson learned: some changes made can lurk around through many restarts and only cause an issue if a specific update is initiated.[/SIZE]

---

### Post by wipeonair on 2018-07-04
I have exactly the same issue.  Could you please explain what you have done so solve this problem? Thanks in advance!

---

