---
title: "Clean up of my system"
date: 2013-09-05
forum: General Help
---

### Post by ELMIT on 2013-09-05
I noted some problems with my AMD/64 4 core system with 16G RAM:

1. High load!   6 all the time
dbus-daemon 95% CPU
NetworkManager 73%
wpa_supplicant  55%
CPU temperature 54C (monitor shows red)

2. Since yesterday Firefox does not start (offers me for Safe mode)

3. Nixnotes starts not with the right icon of unity (it uses QT Jumbi instead)

4. friends is not working with a very descriptive message when trying to send a message: "Error occurred"

5. I get Online accounts messages. When I look at it, then nothing to do, but very often it says I need to grant access again.

6. Desktop sharing works, but vino fills up the hard disk with authentication errors (within a few hours 1.5 TB !!! till the box stop working)

7. thunderbird complaints that it cannot login to the calendar, but fetches email fine.

8. very often I get suddenly hard disk read only. How can I fix that without restarting the computer?

9. Thunderbird and Firefox crashed recently very often!

10. Software updater must be started manually, automatic does not work anymore. Often I get a message about xpia-update to report, ... 

11. When I start the computer a program about address collection is very busy, ...

I put all these into one message, because it might be, that some of these are related or depending on each other.

Here are the past 100 lines of syslog, just in case you see something about the current situation:

```
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.9578] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan18): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan18): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.9918] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan5): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan5): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.10238] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan21): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan21): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.10689] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan14): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan14): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.10844] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan10): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan10): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.10982] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan20): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan20): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.11175] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan27): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan27): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.11434] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan24): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan24): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.11679] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan19): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan19): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.11948] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan17): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan17): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.12194] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan2): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan2): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.12535] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan22): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan22): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.12782] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan26): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan26): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.13028] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan12): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan12): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.13274] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan7): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan7): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.13520] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan13): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan13): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.13766] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan18): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan18): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.14014] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan5): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan5): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <error> [1378436150.14265] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan21): error adding interface: The maximum number of pending replies per connection has been reached
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <info> (wlan21): supplicant interface state: starting -> down
Sep  6 10:55:50 ronald-desktop NetworkManager[2874]: <warn> Trying to remove a non-existant call id.
Sep  6 10:55:50 ronald-desktop rsyslogd-2177: imuxsock begins to drop messages from pid 2874 due to rate-limiting
Sep  6 10:55:50 ronald-desktop wpa_supplicant[2952]: Could not set interface wlan11 flags: Input/output error
Sep  6 10:55:50 ronald-desktop wpa_supplicant[2952]: nl80211: Could not set interface 'wlan11' UP
Sep  6 10:55:50 ronald-desktop kernel: [52584.971200] phy11 -> rt2500pci_wait_bbp_ready: Error - BBP register access failed, aborting.
Sep  6 10:55:50 ronald-desktop kernel: [52584.971205] phy11 -> rt2500pci_set_device_state: Error - Device failed to enter state 4 (-5).
Sep  6 10:55:51 ronald-desktop wpa_supplicant[2952]: Could not set interface wlan11 flags: Input/output error
Sep  6 10:55:51 ronald-desktop wpa_supplicant[2952]: WEXT: Could not set interface 'wlan11' UP
Sep  6 10:55:51 ronald-desktop wpa_supplicant[2952]: wlan11: Failed to initialize driver interface
Sep  6 10:55:51 ronald-desktop kernel: [52585.999324] phy11 -> rt2500pci_wait_bbp_ready: Error - BBP register access failed, aborting.
Sep  6 10:55:51 ronald-desktop kernel: [52585.999329] phy11 -> rt2500pci_set_device_state: Error - Device failed to enter state 4 (-5).
Sep  6 10:55:52 ronald-desktop wpa_supplicant[2952]: Could not set interface wlan0 flags: Input/output error
Sep  6 10:55:52 ronald-desktop wpa_supplicant[2952]: nl80211: Could not set interface 'wlan0' UP
Sep  6 10:55:52 ronald-desktop kernel: [52587.015534] phy0 -> rt2500pci_wait_bbp_ready: Error - BBP register access failed, aborting.
Sep  6 10:55:52 ronald-desktop kernel: [52587.015539] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 4 (-5).
Sep  6 10:55:53 ronald-desktop wpa_supplicant[2952]: Could not set interface wlan0 flags: Input/output error
Sep  6 10:55:53 ronald-desktop wpa_supplicant[2952]: WEXT: Could not set interface 'wlan0' UP
Sep  6 10:55:53 ronald-desktop wpa_supplicant[2952]: wlan0: Failed to initialize driver interface
Sep  6 10:55:53 ronald-desktop kernel: [52588.031959] phy0 -> rt2500pci_wait_bbp_ready: Error - BBP register access failed, aborting.
Sep  6 10:55:53 ronald-desktop kernel: [52588.031964] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 4 (-5).
Sep  6 10:55:54 ronald-desktop wpa_supplicant[2952]: Could not set interface wlan8 flags: Input/output error
Sep  6 10:55:54 ronald-desktop wpa_supplicant[2952]: nl80211: Could not set interface 'wlan8' UP
Sep  6 10:55:54 ronald-desktop kernel: [52589.046075] phy8 -> rt2500pci_wait_bbp_ready: Error - BBP register access failed, aborting.
Sep  6 10:55:54 ronald-desktop kernel: [52589.046080] phy8 -> rt2500pci_set_device_state: Error - Device failed to enter state 4 (-5).

```

---

### Post by 3rdalbum on 2013-09-06
If your hard disk suddenly becomes read-only, that indicates a problem that may potentially be catastrophic. It may be causing some or all of the other problems.

First, boot from a live CD and go to the terminal. DO NOT MOUNT YOUR HARD DISK. Determine the device file of the partition by typing:

sudo fdisk -l

(that's a lowercase L)

Let's say the partition is /dev/sda1. Type:

sudo fsck /dev/sda1

Answer yes to everything. Reboot as normal. Hopefully this was just some filesystem damage that has now been repaired. If the hard disk becomes read-only again, check the SMART statistics in Disk Utility and see if there have been more than 10 unrecoverable read or write errors. If there have been, back up the hard disk, throw it out, and buy a new one. Preferably a different brand.

---

### Post by ELMIT on 2013-09-08
I got a little bit better, by opening the Network icon in Settings and disabled wireless, since I don't use it anyway. The load came down from 8 to under 1 and the dbus-daemon, NetworkManager and wpa_supplicant are not anymore in the top list.

---

