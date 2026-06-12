---
title: "Delayed NetworkManager Startup"
date: 2008-05-15
forum: General Help
---

### Post by ibuclaw on 2008-05-15
Hi all.

I've been recently been getting really slow Network Manager startups...

ie:
I log in with no internet, and three minutes later, the Network Manager applet starts up and I finally have a connection!
When what should be really happening is that it is already connected by the time I login.

Here is the log message of this command:
```
$ cat /var/log/* | grep NetworkManager | sort >~/nm.log
```
[PHP]
May 15 13:52:19 fredbuntu NetworkManager: <info>  starting... 
May 15 13:52:19 fredbuntu NetworkManager: <info>  starting... 
May 15 13:52:25 fredbuntu NetworkManager: <debug> [1210858225.908840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_DW_Q120A'). 
May 15 13:52:25 fredbuntu NetworkManager: <debug> [1210858225.908840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_DW_Q120A'). 
May 15 13:52:25 fredbuntu NetworkManager: <debug> [1210858225.908840] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_DW_Q120A'). 
May 15 13:52:25 fredbuntu NetworkManager: <info>  ath0: Device is fully-supported using driver 'ath_pci'. 
May 15 13:52:25 fredbuntu NetworkManager: <info>  ath0: Device is fully-supported using driver 'ath_pci'. 
May 15 13:52:25 fredbuntu NetworkManager: <info>  ath0: driver does not support SSID scans (scan_capa 0x00). 
May 15 13:52:25 fredbuntu NetworkManager: <info>  ath0: driver does not support SSID scans (scan_capa 0x00). 
May 15 13:52:25 fredbuntu NetworkManager: <info>  Deactivating device ath0. 
May 15 13:52:25 fredbuntu NetworkManager: <info>  Deactivating device ath0. 
May 15 13:52:25 fredbuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 15 13:52:25 fredbuntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 15 13:52:25 fredbuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 15 13:52:25 fredbuntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 15 13:52:25 fredbuntu NetworkManager: <info>  Now managing wireless (802.11) device 'ath0'. 
May 15 13:52:25 fredbuntu NetworkManager: <info>  Now managing wireless (802.11) device 'ath0'. 
May 15 13:52:26 fredbuntu NetworkManager: <debug> [1210858226.205585] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 15 13:52:26 fredbuntu NetworkManager: <debug> [1210858226.205585] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 15 13:52:26 fredbuntu NetworkManager: <debug> [1210858226.205585] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 15 13:55:09 fredbuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May 15 13:55:09 fredbuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) New wireless user key for network 'HOME USER NET' received. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) New wireless user key for network 'HOME USER NET' received. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'HOME USER NET'. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'HOME USER NET'. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) started... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0) started... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0/wireless): access point 'HOME USER NET' is encrypted, and a key exists.  No new key needed. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0/wireless): access point 'HOME USER NET' is encrypted, and a key exists.  No new key needed. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0/wireless): access point 'HOME USER NET' is encrypted, but NO valid key exists.  New key needed. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Activation (ath0/wireless): access point 'HOME USER NET' is encrypted, but NO valid key exists.  New key needed. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Device ath0 activation scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Device ath0 activation scheduled... 
May 15 13:55:10 fredbuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'ath0'. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  SWITCH: no current connection, found better connection 'ath0'. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Will activate connection 'ath0/HOME USER NET'. 
May 15 13:55:10 fredbuntu NetworkManager: <info>  Will activate connection 'ath0/HOME USER NET'. 
May 15 13:55:11 fredbuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 15 13:55:11 fredbuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May 15 13:55:11 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:11 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:11 fredbuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
May 15 13:55:11 fredbuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant0^I' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
May 15 13:55:12 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was '0' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was '0' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: response was 'OK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 484f4d452055534552204e4554' 
May 15 13:55:12 fredbuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 484f4d452055534552204e4554' 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'HOME USER NET'. 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'HOME USER NET'. 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Supplicant state changed: 1 
May 15 13:55:15 fredbuntu NetworkManager: <info>  Supplicant state changed: 1 
May 15 13:55:16 fredbuntu NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
May 15 13:55:16 fredbuntu NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
May 15 13:55:16 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
May 15 13:55:16 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
May 15 13:55:16 fredbuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0 
May 15 13:55:16 fredbuntu NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0 
May 15 13:55:17 fredbuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath0 
May 15 13:55:17 fredbuntu NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath0 
May 15 13:55:18 fredbuntu NetworkManager: <info>  Old device 'ath0' activating, won't change. 
May 15 13:55:18 fredbuntu NetworkManager: <info>  Old device 'ath0' activating, won't change. 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
May 15 13:55:22 fredbuntu NetworkManager: <info>    address 192.168.1.2 
May 15 13:55:22 fredbuntu NetworkManager: <info>    address 192.168.1.2 
May 15 13:55:22 fredbuntu NetworkManager: <info>    broadcast 192.168.1.255 
May 15 13:55:22 fredbuntu NetworkManager: <info>    broadcast 192.168.1.255 
May 15 13:55:22 fredbuntu NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface ath0 
May 15 13:55:22 fredbuntu NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface ath0 
May 15 13:55:22 fredbuntu NetworkManager: <info>    gateway 192.168.1.1 
May 15 13:55:22 fredbuntu NetworkManager: <info>    gateway 192.168.1.1 
May 15 13:55:22 fredbuntu NetworkManager: <info>    nameserver 208.67.220.220 
May 15 13:55:22 fredbuntu NetworkManager: <info>    nameserver 208.67.220.220 
May 15 13:55:22 fredbuntu NetworkManager: <info>    nameserver 208.67.222.222 
May 15 13:55:22 fredbuntu NetworkManager: <info>    nameserver 208.67.222.222 
May 15 13:55:22 fredbuntu NetworkManager: <info>    netmask 255.255.255.0 
May 15 13:55:22 fredbuntu NetworkManager: <info>    netmask 255.255.255.0 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 15 13:55:22 fredbuntu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Activation (ath0) Finish handler scheduled. 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Activation (ath0) Finish handler scheduled. 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Activation (ath0) successful, device activated. 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Activation (ath0) successful, device activated. 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May 15 13:55:23 fredbuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May 15 13:55:23 fredbuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
[/PHP]
I log in at 13:52, and the NetworkManager applet recognises my atheros card, but it only reacts to connect at 13:55 (Also the time when the applet finally shows up on my desktop bar).

Any help on debugging this would be great.

Regards
Iain

---

### Post by ibuclaw on 2008-05-15
Here is my dhcdbd output:
[PHP]
May 15 13:52:24 fredbuntu dhcdbd: Started up.
May 15 13:52:24 fredbuntu dhcdbd: Started up.
May 15 13:52:24 fredbuntu dhcdbd: Started up.
May 15 13:55:10 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
May 15 13:55:10 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
May 15 13:55:10 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.domain_name
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.domain_name
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.domain_name
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
May 15 13:55:22 fredbuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
[/PHP]

And my avahi-daemon log too:
[PHP]
May 15 13:52:19 fredbuntu avahi-daemon[5111]: avahi-daemon 0.6.22 starting up.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: avahi-daemon 0.6.22 starting up.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Found user 'avahi' (UID 108) and group 'avahi' (GID 119).
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Found user 'avahi' (UID 108) and group 'avahi' (GID 119).
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Network interface enumeration completed.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Network interface enumeration completed.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: No service file found in /etc/avahi/services.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: No service file found in /etc/avahi/services.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Registering HINFO record with values 'I686'/'LINUX'.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Registering HINFO record with values 'I686'/'LINUX'.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Server startup complete. Host name is fredbuntu.local. Local service cookie is 183900224.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Server startup complete. Host name is fredbuntu.local. Local service cookie is 183900224.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Successfully called chroot().
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Successfully called chroot().
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Successfully dropped remaining capabilities.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Successfully dropped remaining capabilities.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Successfully dropped root privileges.
May 15 13:52:19 fredbuntu avahi-daemon[5111]: Successfully dropped root privileges.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Interface ath0.IPv4 no longer relevant for mDNS.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Interface ath0.IPv4 no longer relevant for mDNS.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.2.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.2.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.2.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.2.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.2.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.2.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: New relevant interface ath0.IPv4 for mDNS.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: New relevant interface ath0.IPv4 for mDNS.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: New relevant interface ath0.IPv4 for mDNS.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: New relevant interface ath0.IPv4 for mDNS.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Registering new address record for 192.168.1.2 on ath0.IPv4.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Registering new address record for 192.168.1.2 on ath0.IPv4.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Registering new address record for 192.168.1.2 on ath0.IPv4.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Registering new address record for 192.168.1.2 on ath0.IPv4.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Withdrawing address record for 192.168.1.2 on ath0.
May 15 13:55:22 fredbuntu avahi-daemon[5111]: Withdrawing address record for 192.168.1.2 on ath0.
[/PHP]

---

