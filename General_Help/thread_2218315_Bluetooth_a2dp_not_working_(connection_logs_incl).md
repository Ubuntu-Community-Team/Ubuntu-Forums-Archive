---
title: "Bluetooth a2dp not working (connection logs incl)"
date: 2014-04-20
forum: General Help
---

### Post by anthony30 on 2014-04-20
I'm having heaps of problems getting bluez working on 14.04, I had similar problems before but got it working eventually.

I think it was something with permissions last time.

Basically I can pair and use a BT mouse just fine, and I can pair a bluetooth speaker, but after connecting it disconnects pretty much instantly.

Any Help is much appreciated!


This is what I get if I stop the bluetoothd service and restart it as root with -d -n flags this is what is shown:-

```

bluetoothd[3632]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[3632]: plugins/mgmtops.c:mgmt_event() Received 40 bytes from management socket
bluetoothd[3632]: plugins/mgmtops.c:mgmt_device_connected() hci0 device 54:53:ED:A3:D1:85 connected eir_len 21
bluetoothd[3632]: src/adapter.c:adapter_get_device() 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avdtp.c:avdtp_confirm_cb() AVDTP: incoming connect from 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/sink.c:sink_set_state() State changed /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85: SINK_STATE_DISCONNECTED -> SINK_STATE_CONNECTING
bluetoothd[3632]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected signaling channel to 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avdtp.c:avdtp_connect_cb() AVDTP imtu=672, omtu=895
bluetoothd[3632]: audio/avdtp.c:session_cb() 
bluetoothd[3632]: audio/avdtp.c:avdtp_parse_cmd() Received DISCOVER_CMD
bluetoothd[3632]: audio/avctp.c:avctp_confirm_cb() AVCTP: incoming connect from 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avctp.c:avctp_set_state() AVCTP Connecting
bluetoothd[3632]: audio/avctp.c:avctp_connect_cb() AVCTP: connected to 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avctp.c:init_uinput() AVRCP: uinput initialized for 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avctp.c:avctp_set_state() AVCTP Connected
bluetoothd[3632]: audio/avctp.c:session_cb() Got 13 bytes of data for AVCTP session 0x7f770454a200
bluetoothd[3632]: audio/avctp.c:session_cb() AVCTP transaction 3, packet type 0, C/R 0, IPID 0, PID 0x110E
bluetoothd[3632]: audio/avctp.c:session_cb() AV/C command 0x1, subunit_type 0x09, subunit_id 0x0, opcode 0x00, 7 operands
bluetoothd[3632]: audio/avctp.c:session_cb() handler not found for 0x00
bluetoothd[3632]: audio/avrcp.c:avrcp_handle_vendor_reject() rejecting AVRCP PDU 0x30, company 0x001958 len 0x0100
bluetoothd[3632]: audio/avdtp.c:connection_lost() Disconnected from 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/sink.c:sink_set_state() State changed /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85: SINK_STATE_CONNECTING -> SINK_STATE_DISCONNECTED
bluetoothd[3632]: audio/avctp.c:avctp_set_state() AVCTP Disconnected
bluetoothd[3632]: audio/avctp.c:avctp_disconnected() AVCTP: closing uinput for 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avdtp.c:avdtp_unref() 0x7f7704535c10: ref=0
bluetoothd[3632]: audio/avdtp.c:avdtp_unref() 0x7f7704535c10: freeing session and removing from list
bluetoothd[3632]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[3632]: plugins/mgmtops.c:mgmt_event() Received 14 bytes from management socket
bluetoothd[3632]: plugins/mgmtops.c:mgmt_device_disconnected() hci0 device 54:53:ED:A3:D1:85 disconnected
bluetoothd[3632]: src/event.c:btd_event_disconn_complete() 
bluetoothd[3632]: src/adapter.c:adapter_remove_connection() 



```

if I run bluez-test-audio connect [addr here]
I get this:-

```

.DBusException: org.bluez.Error.InProgress: In Progress
root@phobos:~# bluez-test-audio connect 54:53:ED:A3:D1:85
Traceback (most recent call last):
  File "/usr/bin/bluez-test-audio", line 42, in <module>
    audio.Connect()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.bluez.Error.Failed: Connect Failed

```

---

### Post by anthony30 on 2014-04-20
Actually I'm almost certain it's a permission thing, after starting pulse as root and running the bluez-test-audio connect command as root it all worked:-

any pointers would be great!

```

bluetoothd[3632]: audio/avdtp.c:avdtp_ref() 0x7f7704547130: ref=2
bluetoothd[3632]: audio/avdtp.c:avdtp_ref() 0x7f7704547130: ref=3
bluetoothd[3632]: audio/sink.c:sink_set_state() State changed /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85: SINK_STATE_DISCONNECTED -> SINK_STATE_CONNECTING
bluetoothd[3632]: audio/avdtp.c:avdtp_unref() 0x7f7704547130: ref=2
bluetoothd[3632]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[3632]: plugins/mgmtops.c:mgmt_event() Received 35 bytes from management socket
bluetoothd[3632]: plugins/mgmtops.c:mgmt_device_connected() hci0 device 54:53:ED:A3:D1:85 connected eir_len 16
bluetoothd[3632]: src/adapter.c:adapter_get_device() 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected signaling channel to 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avdtp.c:avdtp_connect_cb() AVDTP imtu=672, omtu=895
bluetoothd[3632]: audio/avctp.c:avctp_set_state() AVCTP Connecting
bluetoothd[3632]: audio/avdtp.c:session_cb() 
bluetoothd[3632]: audio/avdtp.c:avdtp_parse_resp() DISCOVER request succeeded
bluetoothd[3632]: audio/avdtp.c:avdtp_discover_resp() seid 1 type 1 media 0 in use 0
bluetoothd[3632]: audio/avdtp.c:session_cb() 
bluetoothd[3632]: audio/avdtp.c:avdtp_parse_resp() GET_CAPABILITIES request succeeded
bluetoothd[3632]: audio/avdtp.c:avdtp_get_capabilities_resp() seid 1 type 1 media 0
bluetoothd[3632]: audio/sink.c:discovery_complete() Discovery complete
bluetoothd[3632]: audio/avdtp.c:avdtp_ref() 0x7f7704547130: ref=3
bluetoothd[3632]: audio/a2dp.c:setup_ref() 0x7f770453ec30: ref=1
bluetoothd[3632]: audio/media.c:media_endpoint_async_call() Calling SelectConfiguration: name = :1.115 path = /MediaEndpoint/A2DPSource
bluetoothd[3632]: audio/a2dp.c:a2dp_config() a2dp_config: selected SEP 0x7f7704530fb0
bluetoothd[3632]: audio/a2dp.c:setup_ref() 0x7f770453ec30: ref=2
bluetoothd[3632]: audio/avdtp.c:avdtp_set_configuration() 0x7f7704547130: int_seid=1, acp_seid=1
bluetoothd[3632]: audio/a2dp.c:setup_unref() 0x7f770453ec30: ref=1
bluetoothd[3632]: audio/avctp.c:avctp_connect_cb() AVCTP: connected to 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avctp.c:init_uinput() AVRCP: uinput initialized for 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avctp.c:avctp_set_state() AVCTP Connected
bluetoothd[3632]: audio/avdtp.c:session_cb() 
bluetoothd[3632]: audio/avdtp.c:avdtp_parse_resp() SET_CONFIGURATION request succeeded
bluetoothd[3632]: audio/a2dp.c:setconf_cfm() Source 0x7f7704530fb0: Set_Configuration_Cfm
bluetoothd[3632]: audio/media.c:media_endpoint_async_call() Calling SetConfiguration: name = :1.115 path = /MediaEndpoint/A2DPSource
bluetoothd[3632]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: IDLE -> CONFIGURED
bluetoothd[3632]: audio/avdtp.c:session_cb() 
bluetoothd[3632]: audio/avdtp.c:avdtp_parse_resp() OPEN request succeeded
bluetoothd[3632]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected transport channel to 54:53:ED:A3:D1:85
bluetoothd[3632]: audio/avdtp.c:handle_transport_connect() Flushable packets enabled
bluetoothd[3632]: audio/avdtp.c:handle_transport_connect() sk 28, omtu 895, send buffer size 106496
bluetoothd[3632]: audio/a2dp.c:open_cfm() Source 0x7f7704530fb0: Open_Cfm
bluetoothd[3632]: audio/sink.c:stream_setup_complete() Stream successfully created
bluetoothd[3632]: audio/a2dp.c:setup_unref() 0x7f770453ec30: ref=0
bluetoothd[3632]: audio/a2dp.c:setup_free() 0x7f770453ec30
bluetoothd[3632]: audio/avdtp.c:avdtp_unref() 0x7f7704547130: ref=2
bluetoothd[3632]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: CONFIGURED -> OPEN
bluetoothd[3632]: audio/sink.c:sink_set_state() State changed /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85: SINK_STATE_CONNECTING -> SINK_STATE_CONNECTED
bluetoothd[3632]: audio/transport.c:media_transport_acquire() Transport /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85/fd2: read lock acquired
bluetoothd[3632]: audio/transport.c:media_transport_acquire() Transport /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85/fd2: write lock acquired
bluetoothd[3632]: audio/transport.c:media_owner_create() Owner created: sender=:1.115 accesstype=rw
bluetoothd[3632]: audio/avdtp.c:avdtp_ref() 0x7f7704547130: ref=3
bluetoothd[3632]: audio/a2dp.c:a2dp_sep_lock() SEP 0x7f7704530fb0 locked
bluetoothd[3632]: audio/avdtp.c:avdtp_ref() 0x7f7704547130: ref=4
bluetoothd[3632]: audio/a2dp.c:setup_ref() 0x7f7704546260: ref=1
bluetoothd[3632]: audio/transport.c:media_request_create() Request created: method=Acquire id=9
bluetoothd[3632]: audio/transport.c:media_owner_add() Owner :1.115 Request Acquire
bluetoothd[3632]: audio/transport.c:media_transport_add() Transport /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85/fd2 Owner :1.115
bluetoothd[3632]: audio/avdtp.c:session_cb() 
bluetoothd[3632]: audio/avdtp.c:avdtp_parse_resp() START request succeeded
bluetoothd[3632]: audio/a2dp.c:start_cfm() Source 0x7f7704530fb0: Start_Cfm
bluetoothd[3632]: /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85/fd2: fd(28) ready
bluetoothd[3632]: audio/transport.c:media_owner_remove() Owner :1.115 Request Acquire
bluetoothd[3632]: audio/a2dp.c:setup_unref() 0x7f7704546260: ref=0
bluetoothd[3632]: audio/a2dp.c:setup_free() 0x7f7704546260
bluetoothd[3632]: audio/avdtp.c:avdtp_unref() 0x7f7704547130: ref=3
bluetoothd[3632]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: OPEN -> STREAMING
bluetoothd[3632]: audio/sink.c:sink_set_state() State changed /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85: SINK_STATE_CONNECTED -> SINK_STATE_PLAYING
bluetoothd[3632]: audio/avctp.c:session_cb() Got 13 bytes of data for AVCTP session 0x7f770453f290
bluetoothd[3632]: audio/avctp.c:session_cb() AVCTP transaction 3, packet type 0, C/R 0, IPID 0, PID 0x110E
bluetoothd[3632]: audio/avctp.c:session_cb() AV/C command 0x1, subunit_type 0x09, subunit_id 0x0, opcode 0x00, 7 operands
bluetoothd[3632]: audio/avctp.c:session_cb() handler not found for 0x00
bluetoothd[3632]: audio/avrcp.c:avrcp_handle_vendor_reject() rejecting AVRCP PDU 0x30, company 0x001958 len 0x0100
bluetoothd[3632]: audio/avdtp.c:avdtp_ref() 0x7f7704547130: ref=4
bluetoothd[3632]: audio/a2dp.c:setup_ref() 0x7f77045476e0: ref=1
bluetoothd[3632]: audio/transport.c:media_request_create() Request created: method=Release id=10
bluetoothd[3632]: audio/transport.c:media_owner_add() Owner :1.115 Request Release
bluetoothd[3632]: audio/avdtp.c:session_cb() 
bluetoothd[3632]: audio/avdtp.c:avdtp_parse_resp() SUSPEND request succeeded
bluetoothd[3632]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: STREAMING -> OPEN
bluetoothd[3632]: audio/sink.c:sink_set_state() State changed /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85: SINK_STATE_PLAYING -> SINK_STATE_CONNECTED
bluetoothd[3632]: audio/a2dp.c:suspend_cfm() Source 0x7f7704530fb0: Suspend_Cfm
bluetoothd[3632]: audio/transport.c:media_request_reply() Request Release Reply Success
bluetoothd[3632]: audio/transport.c:media_owner_remove() Owner :1.115 Request Release
bluetoothd[3632]: audio/a2dp.c:a2dp_sep_unlock() SEP 0x7f7704530fb0 unlocked
bluetoothd[3632]: audio/transport.c:media_transport_remove() Transport /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85/fd2 Owner :1.115
bluetoothd[3632]: audio/transport.c:media_transport_release() Transport /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85/fd2: read lock released
bluetoothd[3632]: audio/transport.c:media_transport_release() Transport /org/bluez/3632/hci0/dev_54_53_ED_A3_D1_85/fd2: write lock released
bluetoothd[3632]: audio/transport.c:media_owner_free() Owner :1.115
bluetoothd[3632]: audio/a2dp.c:setup_unref() 0x7f77045476e0: ref=0
bluetoothd[3632]: audio/a2dp.c:setup_free() 0x7f77045476e0
bluetoothd[3632]: audio/avdtp.c:avdtp_unref() 0x7f7704547130: ref=3



```

---

### Post by QDR06VV9 on 2014-04-20
Not mentioned in the wiki is that you can enable all the Bluetooth audio services by using the following:
```
Enable=Source,Sink,Headset,Gateway,Control,Socket,Media
```
Here's a debugging tip if you're feeling very adventurous. Stop the bluetooth daemon (***/etc/rc.d/bluetooth stop***),  then fire up a terminal and start it again from the command line (with  root authority) while also sending all (debug) text input/output to a  file:
```

# script /tmp/bluetooth.txt
# bluetoothd -d -n
```
A ton of stuff will be displayed/written, but  pay special attention (using the text file if need be) to the lines  containing mostly capital letters. Those are some of the main stages in  bringing up/down a Bluetooth device and will perhaps provide some clue  about what's going on "under the covers".


Press *Ctrl- c* to stop the bluetooth daemon.
Press *Ctrl- d* to exit the *script* utility.
Also,.. check out the files in the */var/lib/bluetooth/<baddr>* directory for fun and amusement. Hopefully there's a *pincodes* file containing the PIN code for your headset... along with a bunch of other files.
Good luck.

---

### Post by anthony30 on 2014-04-20
it works if you stop pulseaudio and run it as root.

Almost certainly a permission thing of my regular user


I'm in these groups:-
anthony adm cdrom sudo audio dip plugdev lpadmin bluetooth pulse pulse-access sambashare libvirtd rvm

am I missing something that would cause dbus or bluetooth access issues?

---

### Post by QDR06VV9 on 2014-04-20
I'm no bluetooth guru
But can you show me what As Root (sudo su)
```

# script /tmp/bluetooth.txt
# bluetoothd -d -n

```
Returns, paste with quotetags

---

### Post by anthony30 on 2014-04-20
I'm pretty sure that it's a permission issue for my user the pulseaudio daemon runs as the current user, as soon as I start pulseaudio as root, I can connect to that device. I'm guessing pulse creates a socket or something that bluez uses to connect to and can't do it with the permissions of my current user.


Here you go: 

```

root@phobos:/tmp# bluetoothd -d -n
bluetoothd[5300]: Bluetooth daemon 4.101
bluetoothd[5300]: src/main.c:parse_config() parsing main.conf
bluetoothd[5300]: src/main.c:parse_config() discovto=0
bluetoothd[5300]: src/main.c:parse_config() pairto=0
bluetoothd[5300]: src/main.c:parse_config() pageto=8192
bluetoothd[5300]: src/main.c:parse_config() auto_to=60
bluetoothd[5300]: src/main.c:parse_config() name=%h-%d
bluetoothd[5300]: src/main.c:parse_config() class=0x000100
bluetoothd[5300]: src/main.c:parse_config() Key file does not have key 'DeviceID'
bluetoothd[5300]: Starting SDP server
bluetoothd[5300]: src/plugin.c:plugin_init() Loading builtin plugins
bluetoothd[5300]: src/plugin.c:add_plugin() Loading audio plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading sap plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading input plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading serial plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading network plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading service plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading health plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading thermometer plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading alert plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading time plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading gatt_example plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading proximity plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading deviceinfo plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading hciops plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading mgmtops plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading formfactor plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading storage plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading adaptername plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading wiimote plugin
bluetoothd[5300]: src/plugin.c:add_plugin() Loading dbusoob plugin
bluetoothd[5300]: src/plugin.c:plugin_init() Loading plugins /usr/lib/x86_64-linux-gnu/bluetooth/plugins
bluetoothd[5300]: plugins/service.c:register_interface() path /org/bluez/5300/any
bluetoothd[5300]: plugins/service.c:register_interface() Registered interface org.bluez.Service on path /org/bluez/5300/any
bluetoothd[5300]: plugins/dbusoob.c:dbusoob_init() Setup dbusoob plugin
bluetoothd[5300]: DIS cannot start: GATT is disabled
bluetoothd[5300]: Failed to init deviceinfo plugin
bluetoothd[5300]: proximity/main.c:proximity_init() GATT is disabled
bluetoothd[5300]: Failed to init proximity plugin
bluetoothd[5300]: time/main.c:time_init() GATT is disabled
bluetoothd[5300]: Failed to init time plugin
bluetoothd[5300]: alert/main.c:alert_init() GATT is disabled
bluetoothd[5300]: Failed to init alert plugin
bluetoothd[5300]: thermometer/main.c:thermometer_init() GATT is disabled
bluetoothd[5300]: Failed to init thermometer plugin
bluetoothd[5300]: health/hdp.c:hdp_manager_start() Starting Health manager
bluetoothd[5300]: network/manager.c:read_config() /etc/bluetooth/network.conf: Key file does not have key 'DisableSecurity'
bluetoothd[5300]: network/manager.c:read_config() Config options: Security=true
bluetoothd[5300]: input/manager.c:input_manager_init() input.conf: Key file does not have key 'IdleTimeout'
bluetoothd[5300]: audio/manager.c:audio_manager_init() audio.conf: Key file does not have key 'AutoConnect'
bluetoothd[5300]: plugins/hciops.c:hciops_init() 
bluetoothd[5300]: plugins/gatt-example.c:gatt_example_init() GATT is disabled
bluetoothd[5300]: Failed to init gatt_example plugin
bluetoothd[5300]: Bluetooth Management interface initialized
bluetoothd[5300]: src/main.c:main() Entering main loop
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:read_version_complete() version 1 revision 4
bluetoothd[5300]: src/rfkill.c:rfkill_event() RFKILL event idx 0 type 2 op 0 soft 0 hard 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 13 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:add_controller() Added controller 0
bluetoothd[5300]: src/rfkill.c:rfkill_event() RFKILL event idx 1 type 1 op 0 soft 0 hard 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 289 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:read_info_complete() hci0 addr 7C:7A:91:98:EA:7B version 6 manufacturer 2 class 0x740100
bluetoothd[5300]: plugins/mgmtops.c:read_info_complete() hci0 settings
bluetoothd[5300]: plugins/mgmtops.c:read_info_complete() hci0 name ubuntu-gnome-0
bluetoothd[5300]: plugins/mgmtops.c:read_info_complete() hci0 short name 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_remove_uuid() index 0
bluetoothd[5300]: src/adapter.c:btd_adapter_ref() 0x7fc8dcd82150: ref=1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_read_bdaddr() index 0 addr 7C:7A:91:98:EA:7B
bluetoothd[5300]: src/sdpd-database.c:sdp_init_services_list() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/service.c:register_interface() path /org/bluez/5300/hci0
bluetoothd[5300]: plugins/service.c:register_interface() Registered interface org.bluez.Service on path /org/bluez/5300/hci0
bluetoothd[5300]: src/adapter.c:btd_adapter_ref() 0x7fc8dcd82150: ref=2
bluetoothd[5300]: network/manager.c:network_server_probe() path /org/bluez/5300/hci0
bluetoothd[5300]: src/adapter.c:btd_adapter_ref() 0x7fc8dcd82150: ref=3
bluetoothd[5300]: network/server.c:server_register() Registered interface org.bluez.NetworkServer on path /org/bluez/5300/hci0
bluetoothd[5300]: serial/manager.c:proxy_probe() path /org/bluez/5300/hci0
bluetoothd[5300]: src/adapter.c:btd_adapter_ref() 0x7fc8dcd82150: ref=4
bluetoothd[5300]: serial/proxy.c:proxy_register() Registered interface org.bluez.SerialProxyManager on path /org/bluez/5300/hci0
bluetoothd[5300]: src/adapter.c:btd_adapter_ref() 0x7fc8dcd82150: ref=5
bluetoothd[5300]: sap/manager.c:sap_server_probe() path /org/bluez/5300/hci0
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Adding record with handle 0x10000
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000003-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 0000112d-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001204-0000-1000-8000-00805f9
bluetoothd[5300]: sap/server.c:sap_server_register() Listen socket 0x11
bluetoothd[5300]: audio/manager.c:media_server_probe() path /org/bluez/5300/hci0
bluetoothd[5300]: src/adapter.c:btd_adapter_ref() 0x7fc8dcd82150: ref=6
bluetoothd[5300]: audio/manager.c:audio_adapter_ref() 0x7fc8dcd84710: ref=1
bluetoothd[5300]: audio/manager.c:headset_server_probe() path /org/bluez/5300/hci0
bluetoothd[5300]: audio/manager.c:audio_adapter_ref() 0x7fc8dcd84710: ref=2
bluetoothd[5300]: audio/manager.c:headset_server_init() audio.conf: Key file does not have key 'Master'
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Adding record with handle 0x10001
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000003-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001108-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001112-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001203-0000-1000-8000-00805f9
bluetoothd[5300]: audio/headset.c:headset_config_init() audio.conf: Key file does not have key 'SCORouting'
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Adding record with handle 0x10002
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000003-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 0000111e-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 0000111f-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001203-0000-1000-8000-00805f9
bluetoothd[5300]: audio/manager.c:audio_adapter_ref() 0x7fc8dcd84710: ref=3
bluetoothd[5300]: audio/manager.c:gateway_server_init() audio.conf: Key file does not have key 'Master'
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Adding record with handle 0x10003
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000003-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 0000111e-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001203-0000-1000-8000-00805f9
bluetoothd[5300]: audio/manager.c:a2dp_server_probe() path /org/bluez/5300/hci0
bluetoothd[5300]: audio/manager.c:audio_adapter_ref() 0x7fc8dcd84710: ref=4
bluetoothd[5300]: audio/a2dp.c:a2dp_register() audio.conf: Key file does not have key 'Enable'
bluetoothd[5300]: audio/avdtp.c:avdtp_init() audio.conf: Key file does not have key 'Master'
bluetoothd[5300]: audio/manager.c:avrcp_server_probe() path /org/bluez/5300/hci0
bluetoothd[5300]: audio/manager.c:audio_adapter_ref() 0x7fc8dcd84710: ref=5
bluetoothd[5300]: audio/avrcp.c:avrcp_register() audio.conf: Key file does not have key 'Master'
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Adding record with handle 0x10004
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000017-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 0000110c-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 0000110e-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Adding record with handle 0x10005
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000017-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[5300]: src/sdpd-service.c:add_record_to_server() Record pattern UUID 0000110e-0000-1000-8000-00805f9
bluetoothd[5300]: plugins/adaptername.c:adaptername_probe() Setting name 'ubuntu-gnome-0' for device 'hci0'
bluetoothd[5300]: plugins/mgmtops.c:mgmt_set_name() index 0, name ubuntu-gnome-0
bluetoothd[5300]: plugins/formfactor.c:formfactor_probe() Setting 0x00010c for major/minor device class
bluetoothd[5300]: plugins/mgmtops.c:mgmt_set_dev_class() index 0 major 1 minor 12
bluetoothd[5300]: plugins/mgmtops.c:mgmt_unblock_device() index 0 addr 00:00:00:00:00:00
bluetoothd[5300]: src/device.c:device_create() Creating device /org/bluez/5300/hci0/dev_20_73_13_05_0E_8E
bluetoothd[5300]: src/device.c:btd_device_ref() 0x7fc8dcd87a50: ref=1
bluetoothd[5300]: src/device.c:device_set_temporary() temporary 0
bluetoothd[5300]: src/device.c:device_probe_drivers() Probing drivers for 20:73:13:05:0E:8E
bluetoothd[5300]: input/manager.c:hid_device_probe() path /org/bluez/5300/hci0/dev_20_73_13_05_0E_8E
bluetoothd[5300]: src/device.c:btd_device_ref() 0x7fc8dcd87a50: ref=2
bluetoothd[5300]: input/device.c:input_device_new() Registered interface org.bluez.Input on path /org/bluez/5300/hci0/dev_20_73_13_05_0E_8E
bluetoothd[5300]: src/device.c:device_create() Creating device /org/bluez/5300/hci0/dev_54_53_ED_A3_D1_85
bluetoothd[5300]: src/device.c:device_set_bonded() bonded 1
bluetoothd[5300]: src/device.c:btd_device_ref() 0x7fc8dcd8a350: ref=1
bluetoothd[5300]: src/device.c:device_set_temporary() temporary 0
bluetoothd[5300]: src/device.c:device_probe_drivers() Probing drivers for 54:53:ED:A3:D1:85
bluetoothd[5300]: src/adapter.c:adapter_get_device() 54:53:ED:A3:D1:85
bluetoothd[5300]: src/device.c:btd_device_ref() 0x7fc8dcd8a350: ref=2
bluetoothd[5300]: audio/device.c:audio_device_register() Registered interface org.bluez.Audio on path /org/bluez/5300/hci0/dev_54_53_ED_A3_D1_85
bluetoothd[5300]: audio/manager.c:handle_uuid() Found Audio Sink
bluetoothd[5300]: audio/sink.c:sink_init() Registered interface org.bluez.AudioSink on path /org/bluez/5300/hci0/dev_54_53_ED_A3_D1_85
bluetoothd[5300]: audio/manager.c:handle_uuid() Found AV Target
bluetoothd[5300]: audio/control.c:control_init() Registered interface org.bluez.Control on path /org/bluez/5300/hci0/dev_54_53_ED_A3_D1_85
bluetoothd[5300]: audio/manager.c:handle_uuid() Found AV Remote
bluetoothd[5300]: plugins/mgmtops.c:mgmt_load_link_keys() index 0 keys 1 debug_keys 0
bluetoothd[5300]: plugins/mgmtops.c:mgmtops_load_ltks() index 0 keys 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_get_conn_list() index 0
bluetoothd[5300]: src/manager.c:btd_manager_register_adapter() Adapter /org/bluez/5300/hci0 registered
bluetoothd[5300]: src/adapter.c:btd_adapter_ref() 0x7fc8dcd82150: ref=7
bluetoothd[5300]: plugins/mgmtops.c:update_settings() new settings 2d3
bluetoothd[5300]: src/adapter.c:adapter_mode_changed() old 0x00 new 0x02
bluetoothd[5300]: src/adapter.c:set_mode_complete() 
bluetoothd[5300]: plugins/mgmtops.c:read_info_complete() mgmtops setting name (null)
bluetoothd[5300]: plugins/mgmtops.c:mgmt_set_dev_class() index 0 major 1 minor 0
bluetoothd[5300]: audio/manager.c:state_changed() /org/bluez/5300/hci0 powered on
bluetoothd[5300]: audio/telephony.c:telephony_init() telephony_init() successfully
bluetoothd[5300]: audio/headset.c:telephony_ready_ind() Telephony plugin initialized
bluetoothd[5300]: audio/headset.c:print_ag_features() HFP AG features: "Three-way calling" "EC and/or NR function" "In-band ring tone capability" "Ability to reject a call" "Enhanced call status" "Enhanced call control" "Extended Error Result Codes" 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_disable_cod_cache() index 0
bluetoothd[5300]: Adapter /org/bluez/5300/hci0 has been enabled
bluetoothd[5300]: src/adapter.c:btd_adapter_unref() 0x7fc8dcd82150: ref=6
bluetoothd[5300]: src/rfkill.c:rfkill_event() RFKILL event idx 2 type 2 op 0 soft 0 hard 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() remove_uuid complete
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 269 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:set_local_name_complete() hci0 name ubuntu-gnome-0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 16 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() unblock_device complete
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 9 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() load_link_keys complete
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 9 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: Unknown command complete for opcode 19
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 11 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_set_dev_class() index 0 major 1 minor 0
bluetoothd[5300]: src/adapter.c:register_agent() Agent registered for hci0 at :1.63:/org/bluez/agent/hci0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_set_io_capability() hci0 io_capability 0x01
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 9 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() set_io_capability complete
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 9 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_busy() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 9 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cod_changed() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() set_dev_class complete
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 9 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cod_changed() index 0
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[5300]: plugins/mgmtops.c:mgmt_event() Received 12 bytes from management socket
bluetoothd[5300]: plugins/mgmtops.c:mgmt_cmd_complete() 
bluetoothd[5300]: plugins/mgmtops.c:mgmt_add_uuid_complete() index 0
bluetoothd[5300]: plugins/mgmtops.c:handle_pending_uuids() index 0



```

---

### Post by QDR06VV9 on 2014-04-20
It doesn't look like blueman is doing the right thing for you, If you have to dive this deep into config files, it's doing more harm than good. I would recommend dumping it and sanitizing your bluez stack e.g. apt-get remove, dpkg --purge, and apt-get install. Then, starting from the bluez docs, configure and pair your device for auto-pairing at startup.

---

### Post by anthony30 on 2014-04-20
I don't have blueman.

The system works fine, if I log in as root, I've narrowed it down to the pulseaudio service not having the permissions it needs for something but trying logging in as my regular user and running each part of the system as root (pulseaudio, bluez, the command I use to test the device).

when the _ONLY_ change to my setup (which is basically a fresh install) is that pulseaudio (the new ALSA I guess) is running as root then it can connect.

---

### Post by anthony30 on 2014-04-20
usermod -a -G bluetooth pulse

That should be done by default!!!

---

### Post by anthony30 on 2014-04-20
Ok, I've purged and reinstalled all the pulse stuff... ignore my previous post, I think I happened to do a few things at once and got it working by fluke however I can confirm a reliable work-around about the issue:-

```
pactl load-module module-bluetooth-discover 
```

after executing that I can connect to my bluetooth speakers. 

This confuses me since /etc/pulse/default.pa contains this:-

```

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-policy.so
load-module module-bluetooth-policy
.endif


.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif



```

Any suggestions why it wouldn't load this?

---

### Post by anthony30 on 2014-04-20
apparently it _IS_ loading it, then unloading it... I have no clue why though...

see the line "I: [pulseaudio] module.c: Unloading "module-bluetooth-discover" (index: #19)."

Any ideas would be appreciated.

```

anthony@phobos:~$ /usr/bin/pulseaudio  -vvvvvv
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 4.0
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux x86_64 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimised build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is df6e8fbd098de2ec354a6f36534735cd.
I: [pulseaudio] main.c: Session ID is c2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/anthony/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
I: [pulseaudio] main.c: Fresh high-resolution timers available! Enjoy ol' chap!
D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
D: [pulseaudio] database-tdb.c: Opened TDB database '/home/anthony/.config/pulse/df6e8fbd098de2ec354a6f36534735cd-device-volumes.tdb'
I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/anthony/.config/pulse/df6e8fbd098de2ec354a6f36534735cd-device-volumes'.
I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: [pulseaudio] database-tdb.c: Opened TDB database '/home/anthony/.config/pulse/df6e8fbd098de2ec354a6f36534735cd-stream-volumes.tdb'
I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/anthony/.config/pulse/df6e8fbd098de2ec354a6f36534735cd-stream-volumes'.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry1
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry2
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry3
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry4
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry5
I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: [pulseaudio] database-tdb.c: Opened TDB database '/home/anthony/.config/pulse/df6e8fbd098de2ec354a6f36534735cd-card-database.tdb'
I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/anthony/.config/pulse/df6e8fbd098de2ec354a6f36534735cd-card-database'.
I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #4; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-udev-detect.so': success
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:03.0/sound/card0 is busy: no
D: [pulseaudio] module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_03.0" card_name="alsa_card.pci-0000_00_03.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"'
D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus session bus 5f9605b6f93fc2a03b6e2ab953541bdd as :1.170
D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
I: [pulseaudio] (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/HDA Intel HDMI/HDA Intel HDMI.conf
I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card HDA Intel HDMI
I: [pulseaudio] (alsa-lib)main.c: error: failed to import HDA Intel HDMI use case configuration -2
I: [pulseaudio] alsa-ucm.c: UCM not available for card HDA Intel HDMI
D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for recording on Analogue Mono (analog-mono)
D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for recording on Analogue Stereo (analog-stereo)
D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Mono (analog-mono)
D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:analog-mono - will not be able to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:analog-stereo - will not be able to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:iec958-stereo - will not be able to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Stereo (analog-stereo)
D: [pulseaudio] alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device front:0: No such file or directory
D: [pulseaudio] alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hw:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-stereo+input:analog-mono - will not be able to open output:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-stereo+input:analog-stereo - will not be able to open output:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-stereo+input:iec958-stereo - will not be able to open output:analog-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 4.0 (analog-surround-40)
D: [pulseaudio] alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-mono - will not be able to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-stereo - will not be able to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:iec958-stereo - will not be able to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 4.1 (analog-surround-41)
D: [pulseaudio] alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-mono - will not be able to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-stereo - will not be able to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:iec958-stereo - will not be able to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 5.0 (analog-surround-50)
D: [pulseaudio] alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-mono - will not be able to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-stereo - will not be able to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:iec958-stereo - will not be able to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 5.1 (analog-surround-51)
D: [pulseaudio] alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-mono - will not be able to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-stereo - will not be able to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:iec958-stereo - will not be able to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: [pulseaudio] alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-mono - will not be able to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-stereo - will not be able to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:iec958-stereo - will not be able to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-mono - will not be able to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-stereo - will not be able to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:iec958-stereo - will not be able to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-mono - will not be able to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-stereo - will not be able to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: [pulseaudio] alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-mono - will not be able to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-stereo - will not be able to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
D: [pulseaudio] alsa-util.c: Trying dca:0 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-mono - will not be able to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-stereo - will not be able to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:iec958-stereo - will not be able to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo supported.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] alsa-mixer.c: Probing path 'hdmi-output-0'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'HDMI/DP,pcm=3 Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
D: [pulseaudio] alsa-mixer.c: Path Set 0x14dd680, direction=1
D: [pulseaudio] alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-mono - will not be able to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-stereo - will not be able to open input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:iec958-stereo - will not be able to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying hdmi:0 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hdmi:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hdmi:0 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hdmi:0
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hdmi:0: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-mono - will not be able to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-stereo - will not be able to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:iec958-stereo - will not be able to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0,1
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo-extra1 supported.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0,1
I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0,1: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] alsa-mixer.c: Probing path 'hdmi-output-1'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'HDMI/DP,pcm=7 Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
D: [pulseaudio] alsa-mixer.c: Path Set 0x1501ed0, direction=1
D: [pulseaudio] alsa-mixer.c: Path hdmi-output-1 (HDMI / DisplayPort 2), direction=1, priority=58, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=7, alsa_name='HDMI/DP,pcm=7 Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-mono - will not be able to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-stereo - will not be able to open input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:iec958-stereo - will not be able to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0,1
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 123 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-surround-extra1 supported.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0,1
I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0,1: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
D: [pulseaudio] alsa-mixer.c: Path Set 0x1502b00, direction=1
D: [pulseaudio] alsa-mixer.c: Path hdmi-output-1 (HDMI / DisplayPort 2), direction=1, priority=58, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=7, alsa_name='HDMI/DP,pcm=7 Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-mono - will not be able to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-stereo - will not be able to open input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:iec958-stereo - will not be able to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0,2
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo-extra2 supported.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0,2
I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0,2: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] alsa-mixer.c: Probing path 'hdmi-output-2'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'HDMI/DP,pcm=8 Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
D: [pulseaudio] alsa-mixer.c: Path Set 0x1503bc0, direction=1
D: [pulseaudio] alsa-mixer.c: Path hdmi-output-2 (HDMI / DisplayPort 3), direction=1, priority=57, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=8, alsa_name='HDMI/DP,pcm=8 Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-mono - will not be able to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-stereo - will not be able to open input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:iec958-stereo - will not be able to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra2
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0,2
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 123 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-surround-extra2 supported.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0,2
I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0,2: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
D: [pulseaudio] alsa-mixer.c: Path Set 0x1503b40, direction=1
D: [pulseaudio] alsa-mixer.c: Path hdmi-output-2 (HDMI / DisplayPort 3), direction=1, priority=57, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=8, alsa_name='HDMI/DP,pcm=8 Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-mono - will not be able to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-stereo - will not be able to open input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:iec958-stereo - will not be able to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-mono - will not be able to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-stereo - will not be able to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-mono - will not be able to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-stereo - will not be able to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:iec958-stereo - will not be able to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Profile set 0x146e1f0, auto_profiles=yes, probed=yes, n_mappings=5, n_profiles=5, n_decibel_fixes=0
D: [pulseaudio] alsa-mixer.c: Mapping hdmi-stereo (Digital Stereo (HDMI)), priority=54, channel_map=front-left,front-right, supported=yes, direction=1
D: [pulseaudio] alsa-mixer.c: Mapping hdmi-stereo-extra1 (Digital Stereo (HDMI)), priority=52, channel_map=front-left,front-right, supported=yes, direction=1
D: [pulseaudio] alsa-mixer.c: Mapping hdmi-surround-extra1 (Digital Surround 5.1 (HDMI)), priority=1, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe, supported=yes, direction=1
D: [pulseaudio] alsa-mixer.c: Mapping hdmi-stereo-extra2 (Digital Stereo (HDMI)), priority=52, channel_map=front-left,front-right, supported=yes, direction=1
D: [pulseaudio] alsa-mixer.c: Mapping hdmi-surround-extra2 (Digital Surround 5.1 (HDMI)), priority=1, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe, supported=yes, direction=1
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo (Digital Stereo (HDMI) Output), priority=5400, supported=yes n_input_mappings=0, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Output hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo-extra1 (Digital Stereo (HDMI) Output), priority=5200, supported=yes n_input_mappings=0, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Output hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-surround-extra1 (Digital Surround 5.1 (HDMI) Output), priority=100, supported=yes n_input_mappings=0, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Output hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-stereo-extra2 (Digital Stereo (HDMI) Output), priority=5200, supported=yes n_input_mappings=0, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Output hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Profile output:hdmi-surround-extra2 (Digital Surround 5.1 (HDMI) Output), priority=100, supported=yes n_input_mappings=0, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Output hdmi-surround-extra2
I: [pulseaudio] module-card-restore.c: Restoring port latency offsets for card alsa_card.pci-0000_00_03.0.
I: [pulseaudio] card.c: Created 0 "alsa_card.pci-0000_00_03.0"
D: [pulseaudio] module-alsa-card.c: Found 3 jacks.
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] module-alsa-card.c: Jack 'HDMI/DP,pcm=3 Jack' is now plugged in
D: [pulseaudio] device-port.c: Setting port hdmi-output-0 to status yes
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] module-switch-on-port-available.c: finding port hdmi-output-0
D: [pulseaudio] module-alsa-card.c: Jack 'HDMI/DP,pcm=7 Jack' is now unplugged
D: [pulseaudio] device-port.c: Setting port hdmi-output-1 to status no
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] module-switch-on-port-available.c: finding port hdmi-output-1
D: [pulseaudio] module-alsa-card.c: Jack 'HDMI/DP,pcm=8 Jack' is now unplugged
D: [pulseaudio] device-port.c: Setting port hdmi-output-2 to status no
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] module-switch-on-port-available.c: finding port hdmi-output-2
D: [pulseaudio] alsa-extcon.c: Cannot open '/sys/class/switch/h2w/state'. Skipping.
D: [pulseaudio] reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
D: [pulseaudio] alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hdmi:0
I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
I: [pulseaudio] alsa-sink.c: Successfully opened device hdmi:0.
I: [pulseaudio] alsa-sink.c: Selected mapping 'Digital Stereo (HDMI)' (hdmi-stereo).
I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL hdmi:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
D: [pulseaudio] alsa-mixer.c: Added 1 ports
I: [pulseaudio] module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_03.0.hdmi-stereo.
I: [pulseaudio] sink.c: Created sink 0 "alsa_output.pci-0000_00_03.0.hdmi-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
I: [pulseaudio] sink.c:     device.api = "alsa"
I: [pulseaudio] sink.c:     device.class = "sound"
I: [pulseaudio] sink.c:     alsa.class = "generic"
I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] sink.c:     alsa.name = "HDMI 0"
I: [pulseaudio] sink.c:     alsa.id = "HDMI 0"
I: [pulseaudio] sink.c:     alsa.subdevice = "0"
I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] sink.c:     alsa.device = "3"
I: [pulseaudio] sink.c:     alsa.card = "0"
I: [pulseaudio] sink.c:     alsa.card_name = "HDA Intel HDMI"
I: [pulseaudio] sink.c:     alsa.long_card_name = "HDA Intel HDMI at 0xf0510000 irq 46"
I: [pulseaudio] sink.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:00:03.0"
I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
I: [pulseaudio] sink.c:     device.bus = "pci"
I: [pulseaudio] sink.c:     device.vendor.id = "8086"
I: [pulseaudio] sink.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] sink.c:     device.product.id = "0c0c"
I: [pulseaudio] sink.c:     device.product.name = "Haswell HD Audio Controller"
I: [pulseaudio] sink.c:     device.form_factor = "internal"
I: [pulseaudio] sink.c:     device.string = "hdmi:0"
I: [pulseaudio] sink.c:     device.buffering.buffer_size = "65536"
I: [pulseaudio] sink.c:     device.buffering.fragment_size = "32768"
I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer"
I: [pulseaudio] sink.c:     device.profile.name = "hdmi-stereo"
I: [pulseaudio] sink.c:     device.profile.description = "Digital Stereo (HDMI)"
I: [pulseaudio] sink.c:     device.description = "Built-in Audio Digital Stereo (HDMI)"
I: [pulseaudio] sink.c:     alsa.mixer_name = "Intel Haswell HDMI"
I: [pulseaudio] sink.c:     alsa.components = "HDA:80862807,80860101,00100000"
I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] source.c: Created source 0 "alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of Built-in Audio Digital Stereo (HDMI)"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     alsa.card = "0"
I: [pulseaudio] source.c:     alsa.card_name = "HDA Intel HDMI"
I: [pulseaudio] source.c:     alsa.long_card_name = "HDA Intel HDMI at 0xf0510000 irq 46"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:03.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "8086"
I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] source.c:     device.product.id = "0c0c"
I: [pulseaudio] source.c:     device.product.name = "Haswell HD Audio Controller"
I: [pulseaudio] source.c:     device.form_factor = "internal"
I: [pulseaudio] source.c:     device.string = "0"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-sink.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20.00ms
D: [pulseaudio] alsa-sink.c: hwbuf_unused=0
D: [pulseaudio] alsa-sink.c: setting avail_min=15502
D: [pulseaudio] alsa-mixer.c: Activating path hdmi-output-0
D: [pulseaudio] alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
D: [pulseaudio] alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
I: [pulseaudio] alsa-sink.c: Driver does not support hardware volume control, falling back to software volume control.
I: [pulseaudio] alsa-sink.c: Driver does not support hardware mute control, falling back to software mute control.
D: [pulseaudio] alsa-util.c: snd_pcm_dump():
D: [pulseaudio] alsa-util.c: Hooks PCM
D: [pulseaudio] alsa-util.c: Its setup is:
D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
D: [pulseaudio] alsa-util.c:   format       : S16_LE
D: [pulseaudio] alsa-util.c:   subformat    : STD
D: [pulseaudio] alsa-util.c:   channels     : 2
D: [pulseaudio] alsa-util.c:   rate         : 44100
D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
D: [pulseaudio] alsa-util.c:   msbits       : 16
D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
D: [pulseaudio] alsa-util.c:   period_size  : 8192
D: [pulseaudio] alsa-util.c:   period_time  : 185759
D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
D: [pulseaudio] alsa-util.c:   period_step  : 1
D: [pulseaudio] alsa-util.c:   avail_min    : 15502
D: [pulseaudio] alsa-util.c:   period_event : 0
D: [pulseaudio] alsa-util.c:   start_threshold  : -1
D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
D: [pulseaudio] alsa-util.c:   silence_threshold: 0
D: [pulseaudio] alsa-util.c:   silence_size : 0
D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
D: [pulseaudio] alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel HDMI' device 3 subdevice 0
D: [pulseaudio] alsa-util.c: Its setup is:
D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
D: [pulseaudio] alsa-util.c:   format       : S16_LE
D: [pulseaudio] alsa-util.c:   subformat    : STD
D: [pulseaudio] alsa-util.c:   channels     : 2
D: [pulseaudio] alsa-util.c:   rate         : 44100
D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
D: [pulseaudio] alsa-util.c:   msbits       : 16
D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
D: [pulseaudio] alsa-util.c:   period_size  : 8192
D: [pulseaudio] alsa-util.c:   period_time  : 185759
D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
D: [pulseaudio] alsa-util.c:   period_step  : 1
D: [pulseaudio] alsa-util.c:   avail_min    : 15502
D: [pulseaudio] alsa-util.c:   period_event : 0
D: [pulseaudio] alsa-util.c:   start_threshold  : -1
D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
D: [pulseaudio] alsa-util.c:   silence_threshold: 0
D: [pulseaudio] alsa-util.c:   silence_size : 0
D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
D: [alsa-sink-HDMI 0] alsa-sink.c: Thread starting up
D: [alsa-sink-HDMI 0] core-util.c: RealtimeKit worked.
I: [alsa-sink-HDMI 0] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-sink-HDMI 0] alsa-sink.c: Starting playback.
D: [alsa-sink-HDMI 0] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink-HDMI 0] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] alsa-util.c: Monitor name in ELD info is 'BenQ GW2260' (for device=3)
D: [pulseaudio] alsa-util.c: ELD info empty (for device=7)
D: [pulseaudio] alsa-util.c: ELD info empty (for device=8)
I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_03.0" card_name="alsa_card.pci-0000_00_03.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"").
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:03.0/sound/card0 (alsa_card.pci-0000_00_03.0) module loaded.
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card1 is busy: no
D: [pulseaudio] module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="1" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"'
D: [pulseaudio] reserve-wrap.c: Successfully acquired reservation lock on device 'Audio1'
I: [pulseaudio] (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/HDA Intel PCH/HDA Intel PCH.conf
I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card HDA Intel PCH
I: [pulseaudio] (alsa-lib)main.c: error: failed to import HDA Intel PCH use case configuration -2
I: [pulseaudio] alsa-ucm.c: UCM not available for card HDA Intel PCH
D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for recording on Analogue Mono (analog-mono)
D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Looking at profile input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for recording on Analogue Stereo (analog-stereo)
D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open front:1
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo supported.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-front'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-front', none of required-any elements preset.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-rear'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-rear', none of required-any elements preset.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-internal'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Internal Mic Phantom Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=1, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-dock'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Dock Mic Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-dock', none of required-any elements preset.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Int Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' failed.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Mic Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=1, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Select' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost (+20dB)' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-linein'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-linein', none of required-any elements preset.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' failed.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-video'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' failed.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-video'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' failed.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-radio'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' failed.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' failed.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Auto-Mute Mode' succeeded (volume=0, switch=0, enumeration=1).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone', none of required-any elements preset.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-input-microphone-headset'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headset Mic Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Skipping path 'analog-input-microphone-headset', none of required-any elements preset.
D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
D: [pulseaudio] alsa-mixer.c: Path Set 0x14b90e0, direction=2
D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone-internal (Internal Microphone), direction=2, priority=89, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=3, min_dB=-17.25, max_dB=66
D: [pulseaudio] alsa-mixer.c: Element Internal Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Jack Dock Mic, alsa_name='Dock Mic Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Front Mic, alsa_name='Front Mic Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Rear Mic, alsa_name='Rear Mic Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Internal Mic Phantom, alsa_name='Internal Mic Phantom Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone (Microphone), direction=2, priority=87, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=3, min_dB=-17.25, max_dB=60
D: [pulseaudio] alsa-mixer.c: Element Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Internal Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Jack Mic Phantom, alsa_name='Mic Phantom Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Looking at profile input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1c' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-mono
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Mono (analog-mono)
D: [pulseaudio] alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:hw:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:analog-mono - will not be able to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:analog-stereo - will not be able to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-mono+input:iec958-stereo - will not be able to open output:analog-mono
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Stereo (analog-stereo)
D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open front:1
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo supported.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Out Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Line Out Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=2, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'CLFE' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-speaker'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Speaker Phantom Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Center Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'CLFE' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-speaker'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=2, switch=2, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-headphones'
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Front Headphone Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (found!)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Phantom Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headset' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=2, switch=2, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Front' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Surround' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Center' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'LFE' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probing path 'analog-output-headphones'
D: [pulseaudio] alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
D: [pulseaudio] alsa-mixer.c: Probe of element 'Headphone2' failed.
D: [pulseaudio] alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-speaker'.
D: [pulseaudio] alsa-mixer.c: Available mixer paths (after tidying):
D: [pulseaudio] alsa-mixer.c: Path Set 0x14a40d0, direction=1
D: [pulseaudio] alsa-mixer.c: Path analog-output-speaker (Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=87, min_dB=-181.5, max_dB=0
D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Speaker Phantom, alsa_name='Speaker Phantom Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Path analog-output-headphones (Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=87, min_dB=-181.5, max_dB=0
D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Speaker, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Front Headphone Phantom, alsa_name='Front Headphone Phantom Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Jack Headphone Phantom, alsa_name='Headphone Phantom Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Headphone Mic, alsa_name='Headphone Mic Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-stereo+input:analog-mono - will not be able to open input:analog-mono
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
D: [pulseaudio] alsa-mixer.c: Checking for recording on Analogue Stereo (analog-stereo)
D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open front:1
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-stereo+input:iec958-stereo - will not be able to open input:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 4.0 (analog-surround-40)
D: [pulseaudio] alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround40:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround40:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround40:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround40:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround40:1: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-mono - will not be able to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-stereo - will not be able to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-40+input:iec958-stereo - will not be able to open output:analog-surround-40
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 4.1 (analog-surround-41)
D: [pulseaudio] alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround41:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround41:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround41:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround41:1
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround41:1: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-mono - will not be able to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-stereo - will not be able to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-41+input:iec958-stereo - will not be able to open output:analog-surround-41
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 5.0 (analog-surround-50)
D: [pulseaudio] alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround50:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround50:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround50:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround50:1
I: [pulseaudio] (alsa-lib)pcm_params.c: Slave PCM not usable
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_any() failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround50:1: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-mono - will not be able to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-stereo - will not be able to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-50+input:iec958-stereo - will not be able to open output:analog-surround-50
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analogue Surround 5.1 (analog-surround-51)
D: [pulseaudio] alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround51:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround51:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround51:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround51:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(6) failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround51:1: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-mono - will not be able to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-stereo - will not be able to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-51+input:iec958-stereo - will not be able to open output:analog-surround-51
D: [pulseaudio] alsa-mixer.c: Looking at profile output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
D: [pulseaudio] alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround71:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open surround71:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
D: [pulseaudio] alsa-util.c: Trying plug:surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open plug:surround71:1
D: [pulseaudio] alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:surround71:1: Invalid argument
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-mono - will not be able to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-stereo - will not be able to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Skipping profile output:analog-surround-71+input:iec958-stereo - will not be able to open output:analog-surround-71
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
D: [pulseaudio] alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-mono - will not be able to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-stereo - will not be able to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-stereo+input:iec958-stereo - will not be able to open output:iec958-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-mono - will not be able to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-stereo - will not be able to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-40
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
D: [pulseaudio] alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:1
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-mono - will not be able to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-stereo - will not be able to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-51
D: [pulseaudio] alsa-mixer.c: Looking at profile output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
D: [pulseaudio] alsa-util.c: Trying dca:1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:1
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-mono - will not be able to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-stereo - will not be able to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:iec958-stereo - will not be able to open output:iec958-dts-surround-51
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
D: [pulseaudio] alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-mono - will not be able to open output:hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-stereo - will not be able to open output:hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo+input:iec958-stereo - will not be able to open output:hdmi-stereo
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
D: [pulseaudio] alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-mono - will not be able to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-stereo - will not be able to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround+input:iec958-stereo - will not be able to open output:hdmi-surround
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:1,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D7p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-mono - will not be able to open output:hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-stereo - will not be able to open output:hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra1
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra1)
D: [pulseaudio] alsa-util.c: Trying hdmi:1,1 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D7p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1,1: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-mono - will not be able to open output:hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-stereo - will not be able to open output:hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:iec958-stereo - will not be able to open output:hdmi-surround-extra1
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:1,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D8p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-mono - will not be able to open output:hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-stereo - will not be able to open output:hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra2
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra2
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra2)
D: [pulseaudio] alsa-util.c: Trying hdmi:1,2 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D8p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1,2: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround-extra2
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-mono - will not be able to open output:hdmi-surround-extra2
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-stereo - will not be able to open output:hdmi-surround-extra2
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:iec958-stereo - will not be able to open output:hdmi-surround-extra2
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:1,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D9p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-mono - will not be able to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-stereo - will not be able to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra3
D: [pulseaudio] alsa-mixer.c: Looking at profile output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround-extra3)
D: [pulseaudio] alsa-util.c: Trying hdmi:1,3 with SND_PCM_NO_AUTO_FORMAT ...
I: [pulseaudio] (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D9p' failed (-2)
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:1,3: No such file or directory
D: [pulseaudio] alsa-mixer.c: Caching failure to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-mono - will not be able to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-stereo - will not be able to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:iec958-stereo - will not be able to open output:hdmi-surround-extra3
D: [pulseaudio] alsa-mixer.c: Profile set 0x1497f00, auto_profiles=yes, probed=yes, n_mappings=1, n_profiles=3, n_decibel_fixes=0
D: [pulseaudio] alsa-mixer.c: Mapping analog-stereo (Analogue Stereo), priority=60, channel_map=front-left,front-right, supported=yes, direction=0
D: [pulseaudio] alsa-mixer.c: Profile input:analog-stereo (Analogue Stereo Input), priority=60, supported=yes n_input_mappings=1, n_output_mappings=0
D: [pulseaudio] alsa-mixer.c: Input analog-stereo
D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo (Analogue Stereo Output), priority=6000, supported=yes n_input_mappings=0, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Output analog-stereo
D: [pulseaudio] alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo (Analogue Stereo Duplex), priority=6060, supported=yes n_input_mappings=1, n_output_mappings=1
D: [pulseaudio] alsa-mixer.c: Input analog-stereo
D: [pulseaudio] alsa-mixer.c: Output analog-stereo
I: [pulseaudio] module-card-restore.c: Restoring port latency offsets for card alsa_card.pci-0000_00_1b.0.
I: [pulseaudio] card.c: Created 1 "alsa_card.pci-0000_00_1b.0"
D: [pulseaudio] module-alsa-card.c: Found 6 jacks.
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
D: [pulseaudio] module-alsa-card.c: Jack 'Headphone Jack' is now unplugged
D: [pulseaudio] module-alsa-card.c: Jack 'Speaker Phantom Jack' is now plugged in
D: [pulseaudio] module-alsa-card.c: Jack 'Headphone Jack' is now unplugged
D: [pulseaudio] device-port.c: Setting port analog-output-headphones to status no
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] module-switch-on-port-available.c: finding port analog-output-headphones
D: [pulseaudio] module-alsa-card.c: Jack 'Mic Jack' is now unplugged
D: [pulseaudio] module-alsa-card.c: Jack 'Internal Mic Phantom Jack' is now plugged in
D: [pulseaudio] module-alsa-card.c: Jack 'Mic Jack' is now unplugged
D: [pulseaudio] device-port.c: Setting port analog-input-microphone to status no
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] module-switch-on-port-available.c: finding port analog-input-microphone
D: [pulseaudio] alsa-extcon.c: Cannot open '/sys/class/switch/h2w/state'. Skipping.
D: [pulseaudio] reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio1'
D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open front:1
I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
I: [pulseaudio] alsa-sink.c: Successfully opened device front:1.
I: [pulseaudio] alsa-sink.c: Selected mapping 'Analogue Stereo' (analog-stereo).
I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
I: [pulseaudio] alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
D: [pulseaudio] alsa-mixer.c: Added 2 ports
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_1b.0.analog-stereo.
I: [pulseaudio] sink.c: Created sink 1 "alsa_output.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
I: [pulseaudio] sink.c:     device.api = "alsa"
I: [pulseaudio] sink.c:     device.class = "sound"
I: [pulseaudio] sink.c:     alsa.class = "generic"
I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] sink.c:     alsa.name = "ALC292 Analog"
I: [pulseaudio] sink.c:     alsa.id = "ALC292 Analog"
I: [pulseaudio] sink.c:     alsa.subdevice = "0"
I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] sink.c:     alsa.device = "0"
I: [pulseaudio] sink.c:     alsa.card = "1"
I: [pulseaudio] sink.c:     alsa.card_name = "HDA Intel PCH"
I: [pulseaudio] sink.c:     alsa.long_card_name = "HDA Intel PCH at 0xf0514000 irq 45"
I: [pulseaudio] sink.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
I: [pulseaudio] sink.c:     device.bus = "pci"
I: [pulseaudio] sink.c:     device.vendor.id = "8086"
I: [pulseaudio] sink.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] sink.c:     device.product.id = "8c20"
I: [pulseaudio] sink.c:     device.product.name = "Lynx Point High Definition Audio Controller"
I: [pulseaudio] sink.c:     device.form_factor = "internal"
I: [pulseaudio] sink.c:     device.string = "front:1"
I: [pulseaudio] sink.c:     device.buffering.buffer_size = "65536"
I: [pulseaudio] sink.c:     device.buffering.fragment_size = "32768"
I: [pulseaudio] sink.c:     device.access_mode = "mmap+timer"
I: [pulseaudio] sink.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] sink.c:     device.profile.description = "Analogue Stereo"
I: [pulseaudio] sink.c:     device.description = "Built-in Audio Analogue Stereo"
I: [pulseaudio] sink.c:     alsa.mixer_name = "Realtek ALC292"
I: [pulseaudio] sink.c:     alsa.components = "HDA:10ec0292,17aa501f,00100001"
I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] source.c: Created source 1 "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of Built-in Audio Analogue Stereo"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     alsa.card = "1"
I: [pulseaudio] source.c:     alsa.card_name = "HDA Intel PCH"
I: [pulseaudio] source.c:     alsa.long_card_name = "HDA Intel PCH at 0xf0514000 irq 45"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "8086"
I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] source.c:     device.product.id = "8c20"
I: [pulseaudio] source.c:     device.product.name = "Lynx Point High Definition Audio Controller"
I: [pulseaudio] source.c:     device.form_factor = "internal"
I: [pulseaudio] source.c:     device.string = "1"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-sink.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
I: [pulseaudio] alsa-sink.c: Time scheduling watermark is 20.00ms
D: [pulseaudio] alsa-sink.c: hwbuf_unused=0
D: [pulseaudio] alsa-sink.c: setting avail_min=15502
D: [pulseaudio] alsa-mixer.c: Activating path analog-output-speaker
D: [pulseaudio] alsa-mixer.c: Path analog-output-speaker (Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=87, min_dB=-181.5, max_dB=0
D: [pulseaudio] alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Speaker Phantom, alsa_name='Speaker Phantom Jack', detection possible
I: [pulseaudio] alsa-sink.c: Successfully enabled deferred volume.
I: [pulseaudio] alsa-sink.c: Hardware volume ranges from -181.50 dB to 0.00 dB.
I: [pulseaudio] alsa-sink.c: Fixing base volume to 0.00 dB
I: [pulseaudio] alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-sink.c: Using hardware mute control.
D: [pulseaudio] alsa-util.c: snd_pcm_dump():
D: [pulseaudio] alsa-util.c: Soft volume PCM
D: [pulseaudio] alsa-util.c: Control: PCM Playback Volume
D: [pulseaudio] alsa-util.c: min_dB: -51
D: [pulseaudio] alsa-util.c: max_dB: 0
D: [pulseaudio] alsa-util.c: resolution: 256
D: [pulseaudio] alsa-util.c: Its setup is:
D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
D: [pulseaudio] alsa-util.c:   format       : S16_LE
D: [pulseaudio] alsa-util.c:   subformat    : STD
D: [pulseaudio] alsa-util.c:   channels     : 2
D: [pulseaudio] alsa-util.c:   rate         : 44100
D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
D: [pulseaudio] alsa-util.c:   msbits       : 16
D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
D: [pulseaudio] alsa-util.c:   period_size  : 8192
D: [pulseaudio] alsa-util.c:   period_time  : 185759
D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
D: [pulseaudio] alsa-util.c:   period_step  : 1
D: [pulseaudio] alsa-util.c:   avail_min    : 15502
D: [pulseaudio] alsa-util.c:   period_event : 0
D: [pulseaudio] alsa-util.c:   start_threshold  : -1
D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
D: [pulseaudio] alsa-util.c:   silence_threshold: 0
D: [pulseaudio] alsa-util.c:   silence_size : 0
D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
D: [pulseaudio] alsa-util.c: Slave: Hardware PCM card 1 'HDA Intel PCH' device 0 subdevice 0
D: [pulseaudio] alsa-util.c: Its setup is:
D: [pulseaudio] alsa-util.c:   stream       : PLAYBACK
D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
D: [pulseaudio] alsa-util.c:   format       : S16_LE
D: [pulseaudio] alsa-util.c:   subformat    : STD
D: [pulseaudio] alsa-util.c:   channels     : 2
D: [pulseaudio] alsa-util.c:   rate         : 44100
D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
D: [pulseaudio] alsa-util.c:   msbits       : 16
D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
D: [pulseaudio] alsa-util.c:   period_size  : 8192
D: [pulseaudio] alsa-util.c:   period_time  : 185759
D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
D: [pulseaudio] alsa-util.c:   period_step  : 1
D: [pulseaudio] alsa-util.c:   avail_min    : 15502
D: [pulseaudio] alsa-util.c:   period_event : 0
D: [pulseaudio] alsa-util.c:   start_threshold  : -1
D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
D: [pulseaudio] alsa-util.c:   silence_threshold: 0
D: [pulseaudio] alsa-util.c:   silence_size : 0
D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
D: [alsa-sink-ALC292 Analog] alsa-sink.c: Thread starting up
D: [pulseaudio] alsa-sink.c: Read hardware volume: 0:  38% 1:   6%
D: [pulseaudio] alsa-sink.c:                in dB: 0: -24.95 dB 1: -71.25 dB
D: [alsa-sink-ALC292 Analog] core-util.c: RealtimeKit worked.
I: [alsa-sink-ALC292 Analog] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-sink-ALC292 Analog] alsa-sink.c: Starting playback.
D: [alsa-sink-ALC292 Analog] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [alsa-sink-ALC292 Analog] alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: [pulseaudio] module-device-restore.c: Could not set format on sink alsa_output.pci-0000_00_1b.0.analog-stereo
D: [pulseaudio] alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
D: [pulseaudio] alsa-util.c: Managed to open front:1
I: [pulseaudio] alsa-util.c: Trying to disable ALSA period wakeups, using timers only
D: [pulseaudio] alsa-util.c: Maximum hw buffer size is 371 ms
D: [pulseaudio] alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: [pulseaudio] alsa-util.c: ALSA period wakeups disabled
I: [pulseaudio] alsa-source.c: Successfully opened device front:1.
I: [pulseaudio] alsa-source.c: Selected mapping 'Analogue Stereo' (analog-stereo).
I: [pulseaudio] alsa-source.c: Successfully enabled mmap() mode.
I: [pulseaudio] alsa-source.c: Successfully enabled timer-based scheduling mode.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:1
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:1'
D: [pulseaudio] alsa-mixer.c: Added 2 ports
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module-device-restore.c: Restoring port for source source:alsa_input.pci-0000_00_1b.0.analog-stereo.
I: [pulseaudio] source.c: Created source 2 "alsa_input.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     alsa.resolution_bits = "16"
I: [pulseaudio] source.c:     device.api = "alsa"
I: [pulseaudio] source.c:     device.class = "sound"
I: [pulseaudio] source.c:     alsa.class = "generic"
I: [pulseaudio] source.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] source.c:     alsa.name = "ALC292 Analog"
I: [pulseaudio] source.c:     alsa.id = "ALC292 Analog"
I: [pulseaudio] source.c:     alsa.subdevice = "0"
I: [pulseaudio] source.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] source.c:     alsa.device = "0"
I: [pulseaudio] source.c:     alsa.card = "1"
I: [pulseaudio] source.c:     alsa.card_name = "HDA Intel PCH"
I: [pulseaudio] source.c:     alsa.long_card_name = "HDA Intel PCH at 0xf0514000 irq 45"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_hda_intel"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:00:1b.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "8086"
I: [pulseaudio] source.c:     device.vendor.name = "Intel Corporation"
I: [pulseaudio] source.c:     device.product.id = "8c20"
I: [pulseaudio] source.c:     device.product.name = "Lynx Point High Definition Audio Controller"
I: [pulseaudio] source.c:     device.form_factor = "internal"
I: [pulseaudio] source.c:     device.string = "front:1"
I: [pulseaudio] source.c:     device.buffering.buffer_size = "65536"
I: [pulseaudio] source.c:     device.buffering.fragment_size = "32768"
I: [pulseaudio] source.c:     device.access_mode = "mmap+timer"
I: [pulseaudio] source.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] source.c:     device.profile.description = "Analogue Stereo"
I: [pulseaudio] source.c:     device.description = "Built-in Audio Analogue Stereo"
I: [pulseaudio] source.c:     alsa.mixer_name = "Realtek ALC292"
I: [pulseaudio] source.c:     alsa.components = "HDA:10ec0292,17aa501f,00100001"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-source.c: Using 2.0 fragments of size 32768 bytes (185.76ms), buffer size is 65536 bytes (371.52ms)
I: [pulseaudio] alsa-source.c: Time scheduling watermark is 20.00ms
D: [pulseaudio] alsa-source.c: hwbuf_unused=0
D: [pulseaudio] alsa-source.c: setting avail_min=15502
D: [pulseaudio] alsa-mixer.c: Activating path analog-input-microphone-internal
D: [pulseaudio] alsa-mixer.c: Path analog-input-microphone-internal (Internal Microphone), direction=2, priority=89, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=3, min_dB=-17.25, max_dB=66
D: [pulseaudio] alsa-mixer.c: Element Internal Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: [pulseaudio] alsa-mixer.c: Element Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: [pulseaudio] alsa-mixer.c: Jack Mic, alsa_name='Mic Jack', detection possible
D: [pulseaudio] alsa-mixer.c: Jack Dock Mic, alsa_name='Dock Mic Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Front Mic, alsa_name='Front Mic Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Rear Mic, alsa_name='Rear Mic Jack', detection unavailable
D: [pulseaudio] alsa-mixer.c: Jack Internal Mic Phantom, alsa_name='Internal Mic Phantom Jack', detection possible
I: [pulseaudio] alsa-source.c: Successfully enabled deferred volume.
I: [pulseaudio] alsa-source.c: Hardware volume ranges from -17.25 dB to 66.00 dB.
I: [pulseaudio] alsa-source.c: Fixing base volume to -66.00 dB
I: [pulseaudio] alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-source.c: Using hardware mute control.
D: [pulseaudio] alsa-util.c: snd_pcm_dump():
D: [pulseaudio] alsa-util.c: Hardware PCM card 1 'HDA Intel PCH' device 0 subdevice 0
D: [pulseaudio] alsa-util.c: Its setup is:
D: [pulseaudio] alsa-util.c:   stream       : CAPTURE
D: [pulseaudio] alsa-util.c:   access       : MMAP_INTERLEAVED
D: [pulseaudio] alsa-util.c:   format       : S16_LE
D: [pulseaudio] alsa-util.c:   subformat    : STD
D: [pulseaudio] alsa-util.c:   channels     : 2
D: [pulseaudio] alsa-util.c:   rate         : 44100
D: [pulseaudio] alsa-util.c:   exact rate   : 44100 (44100/1)
D: [pulseaudio] alsa-util.c:   msbits       : 16
D: [pulseaudio] alsa-util.c:   buffer_size  : 16384
D: [pulseaudio] alsa-util.c:   period_size  : 8192
D: [pulseaudio] alsa-util.c:   period_time  : 185759
D: [pulseaudio] alsa-util.c:   tstamp_mode  : ENABLE
D: [pulseaudio] alsa-util.c:   period_step  : 1
D: [pulseaudio] alsa-util.c:   avail_min    : 15502
D: [pulseaudio] alsa-util.c:   period_event : 0
D: [pulseaudio] alsa-util.c:   start_threshold  : -1
D: [pulseaudio] alsa-util.c:   stop_threshold   : 4611686018427387904
D: [pulseaudio] alsa-util.c:   silence_threshold: 0
D: [pulseaudio] alsa-util.c:   silence_size : 0
D: [pulseaudio] alsa-util.c:   boundary     : 4611686018427387904
D: [pulseaudio] alsa-util.c:   appl_ptr     : 0
D: [pulseaudio] alsa-util.c:   hw_ptr       : 0
D: [pulseaudio] alsa-source.c: Read hardware volume: 0:  13% 1:  13%
D: [pulseaudio] alsa-source.c:                in dB: 0: -52.50 dB 1: -52.50 dB
D: [alsa-source-ALC292 Analog] alsa-source.c: Thread starting up
D: [alsa-source-ALC292 Analog] core-util.c: RealtimeKit worked.
I: [alsa-source-ALC292 Analog] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-source-ALC292 Analog] alsa-source.c: Starting capture.
I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #6; argument: "device_id="1" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"").
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card1 (alsa_card.pci-0000_00_1b.0) module loaded.
D: [pulseaudio] module-udev-detect.c: Ignoring /devices/platform/thinkpad_acpi/sound/card29, because marked so.
I: [pulseaudio] module-udev-detect.c: Found 2 cards.
I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #7; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-android-audio-hal.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-jackdbus-detect.so': failure
I: [pulseaudio] module.c: Loaded "module-bluetooth-policy" (index: #8; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-bluetooth-discover-potato.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-esound-protocol-unix.so': failure
I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #9; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-gconf.so': failure
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_03.0.hdmi-stereo'.
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
I: [pulseaudio] module-default-device-restore.c: Restored default source 'alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor'.
I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #10; argument: "").
I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #11; argument: "").
I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #13; argument: "").
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_03.0.hdmi-stereo becomes idle, timeout in 5 seconds.
D: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
D: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-console-kit.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-systemd-login.so': success
I: [pulseaudio] client.c: Created 0 "Login Session c2"
D: [pulseaudio] module-systemd-login.c: Added new session c2
I: [pulseaudio] module.c: Loaded "module-systemd-login" (index: #15; argument: "").
I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #16; argument: "").
I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #17; argument: "").
I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #18; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-4.0/modules/module-bluetooth-discover.so': success
D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus system bus 0cccbbbfb06013cf7e965b2353541bc5 as :1.206
I: [pulseaudio] module.c: Loaded "module-bluetooth-discover" (index: #19; argument: "").
D: [pulseaudio] main.c: Got org.PulseAudio1!
D: [pulseaudio] main.c: Got org.pulseaudio.Server!
I: [pulseaudio] main.c: Daemon startup complete.
D: [pulseaudio] bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_03.0.
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1b.0.
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/HFPAG on adapter /org/bluez/772/hci0.
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/HFPHS on adapter /org/bluez/772/hci0.
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/A2DPSource on adapter /org/bluez/772/hci0.
D: [pulseaudio] bluetooth-util.c: Registering /MediaEndpoint/A2DPSink on adapter /org/bluez/772/hci0.
D: [pulseaudio] bluetooth-util.c: Device /org/bluez/772/hci0/dev_54_53_ED_A3_D1_85 interface org.bluez.AudioSink property 'State' changed to value 'disconnected'
D: [pulseaudio] bluetooth-util.c: Device /org/bluez/772/hci0/dev_54_53_ED_A3_D1_85 interface org.bluez.Audio property 'State' changed to value 'disconnected'
I: [alsa-sink-HDMI 0] alsa-sink.c: Underrun!
I: [alsa-sink-HDMI 0] alsa-sink.c: Increasing wakeup watermark to 30.00 ms
I: [alsa-sink-HDMI 0] alsa-sink.c: Underrun!
I: [alsa-sink-HDMI 0] alsa-sink.c: Increasing wakeup watermark to 40.00 ms
I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
I: [pulseaudio] client.c: Created 2 "Native client (UNIX socket client)"
D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for gnome-shell
D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/gnome-shell.desktop.
I: [pulseaudio] client.c: Created 3 "Native client (UNIX socket client)"
D: [pulseaudio] protocol-native.c: Protocol version: remote 28, local 28
I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: [pulseaudio] protocol-native.c: SHM possible: yes
D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for python2.7
D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/python2.7.desktop.
I: [pulseaudio] module.c: Unloading "module-bluetooth-discover" (index: #19).
I: [pulseaudio] module.c: Unloaded "module-bluetooth-discover" (index: #19).
I: [pulseaudio] module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] source.c: Suspend cause of source alsa_input.pci-0000_00_1b.0.analog-stereo is 0x0004, suspending
I: [alsa-source-ALC292 Analog] alsa-source.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_1b.0.analog-stereo is 0x0004, suspending
I: [alsa-sink-ALC292 Analog] alsa-sink.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
I: [pulseaudio] module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_03.0.hdmi-stereo idle for too long, suspending ...
D: [pulseaudio] sink.c: Suspend cause of sink alsa_output.pci-0000_00_03.0.hdmi-stereo is 0x0004, suspending
I: [alsa-sink-HDMI 0] alsa-sink.c: Device suspended...
D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_03.0.
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: [pulseaudio] module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1b.0.



```

---

### Post by QDR06VV9 on 2014-04-20
Just wondering if you have tried pulseaudio-volume-manager and under the configuration tab,
Your output shows me at least, analog-mono see if there is another option to try maybe start
with Analog Stereo Duplex or others if available.

---

### Post by nmyrick on 2014-06-27
I had the same issue, until I installed an application from the software center called 'Sound', which as a recall now, I had installed this app on 13.10 and my bluetooth audio was working before the upgrade. I already had blueman applet installed on my 14.04, and my bluetooth speaker was being detected but I was not able to play anything and when I would select a2dp, pulse audio would crash.

Now that I have installed 'Sound', I have not had any issue and I am able to connect my bluetooth with a2dp Hi Fidelity using the Sound application.  Here are the screenshots of the software center page for Sound.

Hope this helps. Also, don't worry that it says GNome, it works perfectly in the Unity Desktop.

[ATTACH=CONFIG]254293[/ATTACH][ATTACH=CONFIG]254294[/ATTACH]

---

### Post by nmyrick on 2014-06-27
When installing 'Sound', among other packages, it also installs the following two packages which I believe are what actually fixes the issue. Sound also puts a nice front-end to the processes.

PulseAudio backend for libcanberra (libcanberra-pulse)

GStreamer plugin for PulseAudio (gstreamer0.10-pulseaudio)

---

