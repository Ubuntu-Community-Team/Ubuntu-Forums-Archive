---
title: "[SOLVED] WL-182 USB network adapter no longer functioning"
date: 2008-06-04
forum: General Help
---

### Post by _sluimers_ on 2008-06-04
after an update that required a restart, my USB adapter stopped working and I no longer have internet.


This is what I get:
```
rogier@dhcppc3:~$ sudo /etc/init.d/networking restart
[sudo] password for rogier: 
 * Reconfiguring network interfaces...                                          
ra0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'ra0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
Failed to disable WPA in the driver.
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ra0: ERROR while getting interface flags: No such device
Failed to bring up ra0.
                                                                         [ OK ]
```

any ideas? :confused:

---

