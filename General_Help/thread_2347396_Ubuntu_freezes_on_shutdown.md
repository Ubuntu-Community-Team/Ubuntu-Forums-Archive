---
title: "Ubuntu freezes on shutdown"
date: 2016-12-24
forum: General Help
---

### Post by lhsm on 2016-12-24
I am running ubuntu 16.10 on a intel i7-5500 laptop with Nvidia 830M hybrid with intel hd graphics 5500.
I've updated the intel graphics driver to the latest using the intel tool. And also updated to nvidia latest from the repository.
However, my ubuntu installation is still freezing on shutdown with the prompt:
[B]Reboot: power off
[/B]
This is my journalctl error log:

```
dez 24 12:40:02 vostro kernel: iwlwifi 0000:07:00.0: Unsupported splx structure
dez 24 12:40:15 vostro systemd[876]: nvidia-persistenced.service: Failed at step EXEC spawning /usr/bin/nvidia-persistenced: No such file or directory
dez 24 12:40:15 vostro systemd[1]: Failed to start NVIDIA Persistence Daemon.
dez 24 12:40:15 vostro bluetoothd[861]: Failed to obtain handles for "Service Changed" characteristic
dez 24 12:40:15 vostro bluetoothd[861]: Failed to set mode: Blocked through rfkill (0x12)
dez 24 12:40:17 vostro systemd[959]: nvidia-persistenced.service: Failed at step EXEC spawning /usr/bin/nvidia-persistenced: No such file or directory
dez 24 12:40:17 vostro systemd[1]: Failed to start NVIDIA Persistence Daemon.
dez 24 12:40:18 vostro NetworkManager[890]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
dez 24 12:40:19 vostro wpa_supplicant[1059]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
dez 24 12:40:19 vostro wpa_supplicant[1059]: dbus: Failed to construct signal
dez 24 12:40:19 vostro wpa_supplicant[1059]: Could not read interface p2p-dev-wlp7s0 flags: No such device
dez 24 12:40:20 vostro lightdm[1102]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
dez 24 12:40:20 vostro lightdm[1102]: PAM adding faulty module: pam_kwallet.so
dez 24 12:40:20 vostro lightdm[1102]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
dez 24 12:40:20 vostro lightdm[1102]: PAM adding faulty module: pam_kwallet5.so
dez 24 12:40:26 vostro pulseaudio[1318]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by 
dez 24 12:40:29 vostro lightdm[1515]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
dez 24 12:40:29 vostro lightdm[1515]: PAM adding faulty module: pam_kwallet.so
dez 24 12:40:29 vostro lightdm[1515]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
dez 24 12:40:29 vostro lightdm[1515]: PAM adding faulty module: pam_kwallet5.so
dez 24 12:40:34 vostro pulseaudio[2014]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by 
dez 24 12:40:34 vostro bluetoothd[861]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)

```

---

### Post by timandjulz on 2016-12-25
I think your warnings/errors can be ignored.  You can get rid of the nvidia-persistenced.service error via:

```
sudo touch /usr/bin/nvidia-persistenced
```

Does shutdown complete if you execute the following from terminal?

```
sudo shutdown now
```

---

