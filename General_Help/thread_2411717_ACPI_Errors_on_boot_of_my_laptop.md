---
title: "ACPI Errors on boot of my laptop"
date: 2019-02-02
forum: General Help
---

### Post by rebellious.ben on 2019-02-02
I am using Ubuntu 18.04.1 LTS only on my machine.  My laptop is a HP 15-db0011ds. Below is a list of errors I am getting in the black screen on reboot or boot of my system & I was hoping someone could help me fix the errors on my machine. The computer is still working fine, I am just wanting to fix the problems.  Thank you for your time.
[[IMG]https://imagizer.imageshack.com/v2/150x100q90/922/CbeUw9.jpg[/IMG]]("https://imageshack.com/i/pmCbeUw9j")

---

### Post by rebellious.ben on 2019-02-03
Only 1 view on my post, I am looking for a little help.  Please & thank you.

---

### Post by CatKiller on 2019-02-03
The view counter has been broken forever.

Those ACPI error messages can safely be ignored.

Running dmesg will give you boot messages as a text output rather than taking a photo of your screen.

---

### Post by rebellious.ben on 2019-02-05
Thank you for your time & response @CatKiller

---

### Post by swangnation on 2019-06-29
Hi guys,

I'm still new to ubuntu and I'm encountering an annoying message shortly after i boot up which says "system problem detected" with the report problem now or cancel.

My bios is current, I'm on an Asus amd64 X55E laptop with ubuntu 18.04 / 4.18.0-21 full encryption.

 When i run systemctl --failed nothing shows up.

When i run systemctl list-unit-files nothing comes up as failed

When i run ```
journalctl -p 3 -b
``` i get the following output
```

-- Logs begin at Mon 2019-06-17 11:46:00 AEST, end at Sun 2019-06-30 10:47:59 AEST. --
Jun 30 10:00:11 praetorian kernel: ACPI BIOS Error (bug): Could not resolve [^^^PB2.VGA.AFN7], AE_NOT_FOUND (20180531/psargs-330)
Jun 30 10:00:11 praetorian kernel: ACPI Error: Method parse/execution failed \_SB.PCI0.VGA.LCDD._BCM, AE_NOT_FOUND (20180531/psparse-516)
Jun 30 10:00:11 praetorian kernel: ACPI Error: Evaluating _BCM failed (20180531/video-364)
Jun 30 10:01:01 praetorian spice-vdagent[1072]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Jun 30 10:01:32 praetorian spice-vdagent[1565]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Jun 30 10:01:52 praetorian pulseaudio[1454]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possib
Jun 30 10:01:55 praetorian wpa_supplicant[772]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jun 30 10:01:55 praetorian wpa_supplicant[772]: dbus: Failed to construct signal
```

I know these may not be the biggest issues but when i got to /var/crash there are no crash reports there, infact the directory is empty so i want to get rid of these annoying messages after boot up. I'm not sure if i am able to somehow add kernel parameters to solve this...in fact i'm not sure how to fix this at all.

Does anyone have any suggestions?

---

### Post by swangnation on 2019-07-01
bump

---

