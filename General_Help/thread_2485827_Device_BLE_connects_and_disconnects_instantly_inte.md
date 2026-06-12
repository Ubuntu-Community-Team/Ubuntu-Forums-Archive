---
title: "Device BLE connects and disconnects instantly intel NUC 11, ubuntu 20.04"
date: 2023-04-11
forum: General Help
---

### Post by mathieusollier on 2023-04-11
**context**: I'm trying to connect a blood pressure monitor via BLE on my intel NUC 11. I have another pc, dell xps 15 where I can connect without problem (using the script below).


**config **(my two pcs have the same configs, see below) : 


 - OS : ubuntu 20.04
 - kernel version : 5.13.0-40-generic
 - bluez version : 5.53


Here is the script I am using:


```
import gatt
 
address = 'EC:21:E5:F0:81:C7'
 
types = {
    '00002a2b-0000-1000-8000-00805f9b34fb': "Current_Time",
}
 
manager = gatt.DeviceManager(adapter_name='hci0')
 
class AnyDevice(gatt.Device):
    def connect_succeeded(self):
        super().connect_succeeded()
        print("[%s] Connected" % (self.mac_address))
 
    def connect_failed(self, error):
        super().connect_failed(error)
        print("[%s] Connection failed: %s" % (self.mac_address, str(error)))
 
    def disconnect_succeeded(self):
        super().disconnect_succeeded()
        print("[%s] Disconnected" % (self.mac_address))
 
    def services_resolved(self):
        super().services_resolved()
 
        print("[%s] Resolved services" % (self.mac_address))
        for service in self.services:
            print("[%s]  Service [%s]" % (self.mac_address, service.uuid))
            for characteristic in service.characteristics:
                print("[%s]    Characteristic [%s]" % (self.mac_address, characteristic.uuid))
                characteristic.enable_notifications()
   
    def characteristic_value_updated(self, characteristic: gatt.Characteristic, value: bytes):
        try:
            value = value.decode()
        except UnicodeDecodeError:
            pass
        print(f"[{characteristic.uuid}] updated: {value}")
 
        print("\t", value.hex())
        print("\t", int(value.hex(), 16))
        print("\t", types.get(characteristic.uuid, '?'))
 
 
device = AnyDevice(mac_address=address.capitalize(), manager=manager)
print("Starting...")
device.connect()
print("Connected")
 
manager.run()
print("end")
```


I can show you the output of **/etc/bluetooth/main.conf** :
```
[General]


# Default adaper name
# Defaults to 'BlueZ X.YZ'
#Name = BlueZ


# Default device class. Only the major and minor device class bits are
# considered. Defaults to '0x000000'.
#Class = 0x000100


# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
#DiscoverableTimeout = 0


# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
#PairableTimeout = 0


# Automatic connection for bonded devices driven by platform/user events.
# If a platform plugin uses this mechanism, automatic connections will be
# enabled during the interval defined below. Initially, this feature
# intends to be used to establish connections to ATT channels. Default is 60.
#AutoConnectTimeout = 60


# Use vendor id source (assigner), vendor, product and version information for
# DID profile support. The values are separated by ":" and assigner, VID, PID
# and version.
# Possible vendor id source values: bluetooth, usb (defaults to usb)
#DeviceID = bluetooth:1234:5678:abcd


# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to 'true'.
#ReverseServiceDiscovery = true


# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
#NameResolving = true


# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
#DebugKeys = false


# Restricts all controllers to the specified transport. Default value
# is "dual", i.e. both BR/EDR and LE enabled (when supported by the HW).
# Possible values: "dual", "bredr", "le"
#ControllerMode = dual


# Enables Multi Profile Specification support. This allows to specify if
# system supports only Multiple Profiles Single Device (MPSD) configuration
# or both Multiple Profiles Single Device (MPSD) and Multiple Profiles Multiple
# Devices (MPMD) configurations.
# Possible values: "off", "single", "multiple"
#MultiProfile = off


# Permanently enables the Fast Connectable setting for adapters that
# support it. When enabled other devices can connect faster to us,
# however the tradeoff is increased power consumptions. This feature
# will fully work only on kernel version 4.1 and newer. Defaults to
# 'false'.
#FastConnectable = false


[Policy]


# The ReconnectUUIDs defines the set of remote services that should try
# to be reconnected to in case of a link loss (link supervision
# timeout). The policy plugin should contain a sane set of values by
# default, but this list can be overridden here. By setting the list to
# empty the reconnection feature gets disabled.
#ReconnectUUIDs=00001112-0000-1000-8000-00805f9b34fb, 0000111f-0000-1000-8000-00805f9b34fb, 0000110a-0000-1000-8000-00805f9b34fb


# ReconnectAttempts define the number of attempts to reconnect after a link
# lost. Setting the value to 0 disables reconnecting feature.
#ReconnectAttempts=7


# ReconnectIntervals define the set of intervals in seconds to use in between
# attempts.
# If the number of attempts defined in ReconnectAttempts is bigger than the
# set of intervals the last interval is repeated until the last attempt.
#ReconnectIntervals=1, 2, 4, 8, 16, 32, 64


# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
AutoEnable=true
```
I also tried to follow this link : [archlinux]([https://wiki.archlinux.org/title/Bluetooth#Problems_with_all_BLE_devices_on_kernel_5.9+](https://wiki.archlinux.org/title/Bluetooth#Problems_with_all_BLE_devices_on_kernel_5.9+))


So here is the output of **/var/lib/bluetooth/adapter_mac/device_mac/info** :
```
[General]
Name=BLESmart_0000021FEC21E5F081C7
AddressType=public
SupportedTechnologies=LE;
Trusted=true
Blocked=false
Services=00001800-0000-1000-8000-00805f9b34fb;00001801-0000-1000-8000-00805f9b34fb;00001805-0000-1000-8000-00805f9b34fb;0000180a-0000-1000-8000-00805f9b34fb;0000180f-0000-1000-8000-00805f9b34fb;00001810>
Appearance=0x0381


[IdentityResolvingKey]
Key=1767A79A37E3DB5897ADEDA275157730


[LongTermKey]
Key=3A75C66423E740B1A9BCD220DBBC9BA3
Authenticated=0
EncSize=16
EDiv=51131
Rand=1639348934062904132


[SlaveLongTermKey]
Key=B39C1351E3E2A6C0658D31E08D789A98
Authenticated=0
EncSize=16
EDiv=36670
Rand=11762431942953384779


[ConnectionParameters]
MinInterval=16
MaxInterval=24
Latency=0
Timeout=200


[ServiceChanged]
CCC_LE=2
```
I can show you the output of **dmesg | grep -i bluetooth** :
```
[    3.341466] Bluetooth: Core ver 2.22
[    3.341483] Bluetooth: HCI device and connection manager initialized
[    3.341487] Bluetooth: HCI socket layer initialized
[    3.341488] Bluetooth: L2CAP socket layer initialized
[    3.341491] Bluetooth: SCO socket layer initialized
[    3.387698] Bluetooth: hci0: Bootloader revision 0.4 build 0 week 30 2018
[    3.388688] Bluetooth: hci0: Device revision is 2
[    3.388691] Bluetooth: hci0: Secure boot is enabled
[    3.388692] Bluetooth: hci0: OTP lock is enabled
[    3.388692] Bluetooth: hci0: API lock is enabled
[    3.388693] Bluetooth: hci0: Debug lock is disabled
[    3.388694] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    3.391193] Bluetooth: hci0: Found device firmware: intel/ibt-19-0-4.sfi
[    4.050862] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.050865] Bluetooth: BNEP filters: protocol multicast
[    4.050869] Bluetooth: BNEP socket layer initialized
[    5.322193] Bluetooth: hci0: Waiting for firmware download to complete
[    5.322662] Bluetooth: hci0: Firmware loaded in 1886199 usecs
[    5.322733] Bluetooth: hci0: Waiting for device to boot
[    5.337676] Bluetooth: hci0: Device booted in 14621 usecs
[    5.337836] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-19-0-4.ddc
[    5.339695] Bluetooth: hci0: Applying Intel DDC parameters completed
[    5.342693] Bluetooth: hci0: Firmware revision 0.0 build 121 week 36 2020
[    5.402687] Bluetooth: hci0: MSFT filter_enable is already on
[    6.833805] Bluetooth: RFCOMM TTY layer initialized
[    6.833825] Bluetooth: RFCOMM socket layer initialized
[    6.833833] Bluetooth: RFCOMM ver 1.11
[  585.818696] Bluetooth: hci0: MSFT filter_enable is already on
[  611.683669] Bluetooth: hci0: MSFT filter_enable is already on
[  619.445687] Bluetooth: hci0: MSFT filter_enable is already on
[ 5572.493698] Bluetooth: hci0: MSFT filter_enable is already on
```


when I run sudo btmon while my script is running I obtain :


This is my target device :
```
HCI Event: LE Meta Event (0x3e) plen 54                    #4 [hci0] 0.640965
      LE Extended Advertising Report (0x0d)
        Num reports: 1
        Entry 0
          Event type: 0x0013
            Props: 0x0013
              Connectable
              Scannable
              Use legacy advertising PDUs
            Data status: [0;32mComplete[0m
          Legacy PDU Type: ADV_IND (0x0013)
          Address type: Public (0x00)
          Address: EC:21:E5:F0:81:C7 (Toshiba)
          Primary PHY: LE 1M
          Secondary PHY: No packets
          SID: no ADI field (0xff)
          TX power: 127 dBm
          RSSI: -58 dBm (0xc6)
          Periodic advertising invteral: 0.00 msec (0x0000)
          Direct address type: Public (0x00)
          Direct address: 00:00:00:00:00:00 (OUI 00-00-00)
          Data length: 0x1c
        02 01 06 11 06 1b c5 d5 a5 02 00 bd b1 e1 11 a2  ................
        c9 80 39 be ec 02 0a 00 03 02 10 18              ..9......... 
```
   
But mostly I get this error:


```
@ MGMT Event: Device Disconnected (0x000c) plen 8      {0x000f} [hci0] 2.338903
        LE Address: EC:21:E5:F0:81:C7 (Toshiba)
        Reason: Connection terminated due to authentication failure (0x04)
```


Does anyone have any ideas to resolve this issue?
Thanks in advance

---

### Post by barbex on 2023-06-12
One idea is in this thread, installing firmware: [https://ubuntuforums.org/showthread.php?t=2486421&p=14142312#post14142312]("https://ubuntuforums.org/showthread.php?t=2486421&p=14142312#post14142312")

The solution that worked for me came from here [https://mephisto.cc/en/tech/airpods_pro2/]("https://mephisto.cc/en/tech/airpods_pro2/") -- installing **libspa-0.2-bluetooth** for pipewire via Synaptic.

Hope this helps.

---

