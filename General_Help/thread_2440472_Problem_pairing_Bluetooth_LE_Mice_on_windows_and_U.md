---
title: "Problem pairing Bluetooth LE Mice on windows and Ubuntu."
date: 2020-04-11
forum: General Help
---

### Post by georgesgiralt on 2020-04-11
Hello !
I didn't know where to put this so I thought General Help could be suitable. If it is not, could someone, please move it to a more appropriate sub forum ? Thanks in advance.
I would like to pair a Chinese Bluetooth LE mouse in Ubuntu (19.10)  and windows on the same machine.
I've followed the information on this page : 
[https://console.systems/2014/09/how-to-pair-low-energy-le-bluetooth.html](https://console.systems/2014/09/how-to-pair-low-energy-le-bluetooth.html)
My Windows registry snippet looks like this (It is a Windows 10 machine with all the updates/upgrades installed) : 
```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\BTHPORT\Parameters\Keys]

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\BTHPORT\Parameters\Keys\a0a4c5ce0f58]
"848edf8aabac"=hex:3d,e1,a1,c6,5e,87,6c,ae,1c,73,d0,1f,5a,7d,6b,cb
"c44567239cfe"=hex:43,74,f2,22,96,ec,b0,3a,a5,b5,9e,30,b8,05,32,15
"MasterIRK"=hex:72,7d,5e,df,ed,66,d8,e0,0f,72,d7,81,c8,11,31,cc

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\BTHPORT\Parameters\Keys\a0a4c5ce0f58\dc7f01789376]
"LTK"=hex:4a,61,c2,f6,30,77,c7,b3,e1,11,eb,71,a7,af,69,bc
"KeyLength"=dword:00000010
"ERand"=hex(b):3d,09,cf,88,38,4c,1e,ee
"EDIV"=dword:00009eb5
"IRK"=hex:74,32,37,32,53,42,20,57,14,81,42,62,67,24,74,97
"Address"=hex(b):76,93,78,01,7f,dc,00,00
"AddressType"=dword:00000001
"MasterIRKStatus"=dword:00000001
"AuthReq"=dword:0000002d

```
And my Ubuntu info file for the Bluetooth mouse looks like : 
```

[General]
Name=Bluetooth4.0Mouse
AddressType=static
SupportedTechnologies=LE;
Trusted=true
Blocked=false
Services=00001800-0000-1000-8000-00805f9b34fb;00001801-0000-1000-8000-00805f9b34fb;0000180a-0000-1000-8000-00805f9b34fb;0000180f-0000-1000-8000-00805f9b34fb;00001812-0000-1000-8000-00805f9b34fb;00010203-0405-0607-0809-0a0b0c0d1912;

[ConnectionParameters]
MinInterval=6
MaxInterval=6
Latency=99
Timeout=400

[IdentityResolvingKey]
Key=97742467624281145720425332373274

[LongTermKey]
Key=205DC72A35B52E727A49703656CC1E66
Authenticated=0
EncSize=16
EDiv=41695
Rand=13152074216847889720

[SlaveLongTermKey]
Key=67472C5ACBB5AD242C5A5333AE8C3D2D
Authenticated=0
EncSize=16
EDiv=13581
Rand=11149546000981995039

[DeviceID]
Source=2
Vendor=9354
Product=33382
Version=1

```
I've no problem inserting LTK, KeyLengh, Erand and EDIV parts into the info file, but CSRK does not exits in the Windows registry ...
I also have this part on the Registry snippet :
```

"IRK"=hex:74,32,37,32,53,42,20,57,14,81,42,62,67,24,74,97
"Address"=hex(b):76,93,78,01,7f,dc,00,00
"AddressType"=dword:00000001
"MasterIRKStatus"=dword:00000001
"AuthReq"=dword:0000002d

```
And this in the info file :
```

[SlaveLongTermKey]
Key=67472C5ACBB5AD242C5A5333AE8C3D2D
Authenticated=0
EncSize=16
EDiv=13581
Rand=11149546000981995039

```
I've tried to insert the extra values (per the instructions on console.systems) from the Windows reg file to the Ubuntu info file, but had no luck whatsoever. The mouse switch fast from paired to not paired and finally fails to connect.
The syslog shows many groups of these messages :
```

bluetoothd[958]: No cache for DC:7F:01:78:93:76
bluetoothd[958]: BATT attribute not found
bluetoothd[958]: batt-profile profile accept failed for DC:7F:01:78:93:76
bluetoothd[958]: GAP attribute not found
bluetoothd[958]: gap-profile profile accept failed for DC:7F:01:78:93:76
bluetoothd[958]: input-hog profile accept failed for DC:7F:01:78:93:76

```
I am lost, here. So all the help I can get will be greatly appreciated.
Many thanks in advance.

---

