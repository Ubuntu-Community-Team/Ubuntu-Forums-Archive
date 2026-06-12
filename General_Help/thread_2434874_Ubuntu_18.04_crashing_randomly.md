---
title: "Ubuntu 18.04 crashing randomly"
date: 2020-01-12
forum: General Help
---

### Post by vamisk on 2020-01-12
Howdy everyone. I recently installed Ubuntu 18.04 to replace Win10 on an older HP laptop i have. Things were fine for a bit but it seems after i installed Google Chrome and youtube-dl i've been getting a random lock up. I'm not sure whether the OS has crashed or the it's just the display has frozen. I checked CPU temps and CPU load and they're not even really working that hard.

I checked Journalctl and "logs" and they're both showing the same problems.

```
Jan12 16:18:46 C-LPC kernel: Couldn'tget size: 0x800000000000000e

amd-disable-c6.service:Main process exited, code=exited, status=1/FAILURE 
Jan12 16:19:07 C-LPC systemd[1]: amd-disable-c6.service:Failed with result 'exit-code'. 
Jan12 16:19:07 C-LPC systemd[1]: Failed to start Service to disable theC6 State on AMD Zen-based (Ryzen, Epyc) processors on boot.

Jan12 16:19:12 C-LPC wpa_supplicant[799]: dbus:wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jan12 16:19:12 C-LPC wpa_supplicant[799]: dbus: Failed to constructsignal

Jan12 16:19:13 C-LPC wpa_supplicant[799]: bgscansimple: Failed to enable signal strength monitoring

Jan12 16:19:30 C-LPC spice-vdagent[1342]: Cannotaccess vdagent virtio channel/dev/virtio-ports/com.redhat.spice.0

Jan12 16:19:39 C-LPC pulseaudio[1372]: [pulseaudio]backend-ofono.c: Failed to register as a handsfree audio agent withofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofonowa
```


There are a few extra errors in logs that journalctl didn't catch but they seem to be for audio software.

Can anyone help me with this? Thanks in advance.

---

### Post by TheFu on 2020-01-12
R U running a hypervisor and trying to use Spice?

---

### Post by vamisk on 2020-01-13
No sir, this was a fresh install of Ubuntu 18.04. I did some digging and i guess it's the C6 state causing the random lockups. I used Zenstates to disable the C6 state and the PC was able to stay running all night so that is seemingly the solution. 

I'm not very versed with Ubuntu so this is still a learning process for me. Trying to set up a Crontab to run the C6 disable at every startup.

---

