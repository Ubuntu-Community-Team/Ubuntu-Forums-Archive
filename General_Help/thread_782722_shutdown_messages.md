---
title: "shutdown messages"
date: 2008-05-05
forum: General Help
---

### Post by kishorebudha on 2008-05-05
When I shutdown ubuntu (Hardy) I get the following message before shutdown.

[INDENT]NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1209984940.809736] nm-print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1209984940.809736] nm-print_open_socks(): Open Sockets List Done:

NetworkManager: <info> Deactivating device eth1

NetworkManager: <info> Deactivating device eth0

NetworkManager: <WARN> nm_hal_deinit(): libha1 shutdown failed - Connection is closed

NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed
NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed
NetworkManager: nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed[/INDENT]

---

### Post by kishorebudha on 2008-05-05
I tried the solution here, which did not work.

[https://answers.launchpad.net/ubuntu/+question/16914](https://answers.launchpad.net/ubuntu/+question/16914)

---

