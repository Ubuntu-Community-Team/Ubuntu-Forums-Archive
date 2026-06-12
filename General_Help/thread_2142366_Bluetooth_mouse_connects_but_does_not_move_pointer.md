---
title: "Bluetooth mouse connects but does not move pointer."
date: 2013-05-05
forum: General Help
---

### Post by sona1111 on 2013-05-05
I have am IBM t60 laptop with the "official" thinkpad bluetooth laser mouse. When I connected it at first it was fine, and it also works about 70% of the time - usually a restart will fix it. The problem is that it connects but does not work further then that. I can tell this because the thinkpad has a bluetooth light which blinks whenever their is activity - for example if I move the mouse or click it, the light will blink, which means the bluetooth is connected and the mouse works. However the pointer will not move as a result. 

Any ideas?

(ubuntu 12.10)

---

### Post by sona1111 on 2013-05-05
oh and here is cat proc/bus/input/devices

```
I: Bus=0019 Vendor=0000 Product=0005 Version=0000N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0


I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input5
U: Uniq=
H: Handlers=rfkill kbd event5 
B: PROP=0
B: EV=33
B: KEY=18040000 0 0 100000 0 0 0 101501b 102004 80000000 1104000 e0000 0 0 0
B: MSC=10
B: SW=8


I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=1
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=11000003


I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=synaptics-pt/serio0/input0
S: Sysfs=/devices/platform/i8042/serio1/serio2/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3


I: Bus=0005 Vendor=17ef Product=6002 Version=0245
N: Name="ThinkPad Bluetooth Laser Mouse"
P: Phys=00:16:CF:DD:D5:2E
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:11/input19
U: Uniq=00:02:76:35:11:76
H: Handlers=mouse2 event8 
B: PROP=0
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

```

---

### Post by sona1111 on 2013-05-07
This is still a problem.

---

### Post by KFoder on 2013-05-10
Hi 

I have the same problem, and have had ever since i upgraded from 12.04 to 12.10, I had hoped an upgrade to 13.04 would solve the problem, but it didn't.

I'm using KUbuntu, and can see my mouse as connected in the panel widget, but the desktop does not react to movement or clicks.

If I disconnects the mouse via the panel, a couple of times, the mouse suddenly becomes active on the desktop .... for some time then it stops working again, and this time it require a reboot and a coupe of disconnects to become active again.

Bluetooth works great when I'm connecting to my phone or my stereo headset, and was working with my mouse until 12.10.

Please help, it's becomming rather anoying.

Kim

---

### Post by varunendra on 2013-05-11
I may not be able to offer any precise help but you need to identify the drivers in use, then keep an eye on the drivers and device states (in dmesg, syslog and lsmod) whenever a change occurs.

We can identify the device with 'xinput' command. Then we can identify the driver with 'usb-devices' command (since the bluetooth adapters are internally connected via usb).

Accordingly, please post outputs of -
```
xinput
usb-devices
lsmod
```

As soon as the problem occurs, also run -
```
dmesg | tail -20
cat /var/log/syslog | tail -20
```
and see if there are any clues. The command 'tail -20' will limit the output to last 20 lines. You may increase the value if needed.

---

### Post by sona1111 on 2013-05-26
ok, well it happened again and I remembered to come back here...

(all of these were output during the time the problem was occurring)

xinput:
```

paul@paul-ThinkPad-T60p:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ThinkPad Bluetooth Laser Mouse          	id=14	[slave  pointer  (2)]
&#9116;   &#8627; ThinkPad Bluetooth Laser Mouse          	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]
```

usb devices:
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=b6d2 Rev=94.12
S:  Manufacturer=SanDisk
S:  Product=SDAD-111
S:  SerialNumber=080321001897
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=cd12 ProdID=ef18 Rev=01.00
S:  Manufacturer=USB     
S:  Product=Flash Disk      
S:  SerialNumber=3F389B3B05CC131F
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=2110 Rev=01.00
S:  Manufacturer=Broadcom Corp
S:  Product=BCM2045B
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)


T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0483 ProdID=2016 Rev=00.01
S:  Manufacturer=STMicroelectronics
S:  Product=Biometric Coprocessor
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

```

lsmod
```

Module                  Size  Used by
nls_iso8859_1          12618  1 
hid_generic            12485  0 
hidp                   21826  1 
hid                    82179  2 hid_generic,hidp
3c59x                  41500  0 
joydev                 17162  0 
coretemp               13169  0 
kvm_intel             126746  0 
kvm                   357807  1 kvm_intel
pcmcia                 39545  0 
microcode              18210  0 
snd_hda_codec_analog    75060  1 
snd_hda_intel          32516  2 
snd_hda_codec         111548  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
psmouse                84878  0 
serio_raw              13032  0 
i2c_i801               17145  0 
pcspkr                 12631  0 
thinkpad_acpi          69338  0 
snd_seq_midi           13133  0 
yenta_socket           27096  0 
pcmcia_rsrc            18192  1 yenta_socket
lpc_ich                16926  0 
nvram                  13987  1 thinkpad_acpi
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_rawmidi            25383  1 snd_seq_midi
irda                  184930  0 
arc4                   12474  2 
crc_ccitt              12628  1 irda
tpm_tis                18209  0 
btusb                  17987  0 
snd_seq_midi_event     14476  1 snd_seq_midi
video                  18895  0 
radeon                825498  3 
bnep                   17708  2 
rfcomm                 37277  16 
bluetooth             183270  27 hidp,btusb,bnep,rfcomm
iwl3945                63696  0 
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
parport_pc             31969  0 
iwlegacy               87811  1 iwl3945
ppdev                  12818  0 
ttm                    75535  1 radeon
drm_kms_helper         47304  1 radeon
mac80211              461261  2 iwl3945,iwlegacy
evbug                  12582  0 
mac_hid                13038  0 
snd_timer              24412  2 snd_pcm,snd_seq
drm                   238811  5 radeon,ttm,drm_kms_helper
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17261  1 
cfg80211              175574  3 iwl3945,iwlegacy,mac80211
i2c_algo_bit           13198  1 radeon
snd                    62146  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
usb_storage            39346  1 
ahci                   25497  2 
libahci                25938  1 ahci
e1000e                178876  0 

```





dmesg:

```
[163747.139171] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1[163747.139187] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163747.168833] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
[163747.168851] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163747.199270] evbug: Event. Dev: input8, Type: 2, Code: 1, Value: -1
[163747.199287] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163747.203156] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 200
[163747.203167] evbug: Event. Dev: input3, Type: 1, Code: 103, Value: 0
[163747.203179] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163747.222416] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
[163747.222431] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163747.379121] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
[163747.379142] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163747.569956] evbug: Event. Dev: input8, Type: 2, Code: 1, Value: -1
[163747.569972] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163747.579981] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
[163747.579996] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163747.747505] evbug: Event. Dev: input8, Type: 2, Code: 1, Value: -1
[163747.747523] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
[163748.238765] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163748.238776] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[163748.238788] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163748.294372] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163748.294382] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[163748.294394] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163748.388993] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163748.389003] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[163748.389016] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163748.460239] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163748.460249] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[163748.460264] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163748.843406] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163748.843443] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[163748.843481] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163748.946897] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163748.946907] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[163748.946921] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163749.958262] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 2
[163749.958272] evbug: Event. Dev: input3, Type: 1, Code: 2, Value: 1
[163749.958287] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163750.016636] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163750.016646] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 1
[163750.016658] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163750.036853] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 2
[163750.036863] evbug: Event. Dev: input3, Type: 1, Code: 2, Value: 0
[163750.036875] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163750.063153] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163750.063163] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 0
[163750.063175] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163750.149874] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163750.149884] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 1
[163750.149897] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163750.205444] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163750.205454] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 0
[163750.205467] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163750.902047] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163750.902319] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[163750.902446] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163750.948985] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163750.948995] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[163750.949004] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.050993] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163751.051004] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[163751.051016] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.098699] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163751.098710] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[163751.098721] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.185589] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163751.185600] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 1
[163751.185611] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.256832] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 14
[163751.256842] evbug: Event. Dev: input3, Type: 1, Code: 14, Value: 0
[163751.256852] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.399115] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 12
[163751.399126] evbug: Event. Dev: input3, Type: 1, Code: 12, Value: 1
[163751.399137] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.494380] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 12
[163751.494391] evbug: Event. Dev: input3, Type: 1, Code: 12, Value: 0
[163751.494402] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.561542] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 2
[163751.561552] evbug: Event. Dev: input3, Type: 1, Code: 2, Value: 1
[163751.561566] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.633041] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 2
[163751.633052] evbug: Event. Dev: input3, Type: 1, Code: 2, Value: 0
[163751.633064] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.658923] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163751.658932] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 1
[163751.658945] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.714804] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163751.714813] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 0
[163751.714825] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.809240] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163751.809251] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 1
[163751.809264] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.864926] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 11
[163751.864937] evbug: Event. Dev: input3, Type: 1, Code: 11, Value: 0
[163751.864951] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[163751.999776] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 28
[163751.999787] evbug: Event. Dev: input3, Type: 1, Code: 28, Value: 1
[163751.999800] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
```

syslog:
```
May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.284961] evbug: Event. Dev: input3, Type: 1, Code: 29, Value: 0May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.284973] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.792348] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 28
May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.792422] evbug: Event. Dev: input3, Type: 1, Code: 28, Value: 1
May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.792497] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.863912] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 28
May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.863923] evbug: Event. Dev: input3, Type: 1, Code: 28, Value: 0
May 26 12:01:50 paul-ThinkPad-T60p kernel: [163836.863935] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
May 26 12:01:51 paul-ThinkPad-T60p kernel: [163836.973192] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
May 26 12:01:51 paul-ThinkPad-T60p kernel: [163836.973214] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
May 26 12:01:51 paul-ThinkPad-T60p kernel: [163837.121584] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
May 26 12:01:51 paul-ThinkPad-T60p kernel: [163837.121604] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163844.950121] evbug: Event. Dev: input8, Type: 2, Code: 1, Value: -1
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163844.950144] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163845.059471] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163845.059485] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163845.200527] evbug: Event. Dev: input8, Type: 2, Code: 1, Value: -1
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163845.200549] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163845.259294] evbug: Event. Dev: input8, Type: 2, Code: 0, Value: 1
May 26 12:01:59 paul-ThinkPad-T60p kernel: [163845.259310] evbug: Event. Dev: input8, Type: 0, Code: 0, Value: 0

```

---

### Post by varunendra on 2013-05-27
Ok, I was wrong about its appearance in usb-devices, but I experimented with my mobile phone by attaching it as a bluetooth input device (like a BT mouse), and it seems it is controlled by **btusb**. That, and based on some personal experience and some observations from your outputs, here are a few workarounds that *should* work, but I can't guarantee the success of any of these (they do work for me).

Things on which I am basing these workarounds (so that others can adapt the variables as per their outputs) -
> **sona1111 said:**
> ..here is cat proc/bus/input/devices
```

I: **[COLOR="#FF0000"]Bus=05[/COLOR]** Vendor=17ef Product=6002 Version=0245
N: Name=**"ThinkPad Bluetooth Laser Mouse"**
P: Phys=00:16:CF:DD:D5:2E
S: Sysfs=/devices/**[COLOR="#FF0000"]pci0000:00/0000:00:1d.3[/COLOR]/[COLOR="#0000CD"]usb5/5-1[/COLOR]/[COLOR="#800000"]5-1:1.0[/COLOR]**/bluetooth/hci0/hci0:11/input19
U: Uniq=00:02:76:35:11:76

```

> **sona1111 said:**
> 
usb devices:
```

T:  **[COLOR="#FF0000"]Bus=05[/COLOR]** Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic **[COLOR="#FF0000"]uhci_hcd[/COLOR]**
S:  Product=UHCI Host Controller
S:  SerialNumber=**[COLOR="#FF0000"]0000:00:1d.3[/COLOR]**
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  **[COLOR="#FF0000"]Bus=05[/COLOR]** Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=2110 Rev=01.00
S:  Manufacturer=Broadcom Corp
S: ** Product=BCM2045B**
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=**[COLOR="#800000"]btusb[/COLOR]**
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=**[COLOR="#800000"]btusb[/COLOR]**
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)


T:  **[COLOR="#FF0000"]Bus=05[/COLOR]** Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0483 ProdID=2016 Rev=00.01
S:  Manufacturer=STMicroelectronics
S:  **[COLOR="#FF0000"]Product=Biometric Coprocessor[/COLOR]**
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

```
**[SIZE=3]Some Info :[/SIZE]**

[INDENT]**[COLOR="#800000"](A) 5-1:1.0[/COLOR]** is the device id of your bluetooth adapter that *should* be under control of **[COLOR="#800000"]btusb[/COLOR]** driver

**[COLOR="#0000CD"](B) usb5/5-1[/COLOR]** is the (internal) usb port id on which the above bluetooth adapter is located. It *should* be under control of driver "**usb**" (based on observation in my laptop)

**[COLOR="#FF0000"](C) pci0000:00/0000:00:1d.3[/COLOR]** is the pci bus id on which the usb hub **[COLOR="#FF0000"]Bus=05[/COLOR]** is located. This hub is apparently controlled by **[COLOR="#FF0000"]uhci_hcd[/COLOR]** driver.[/INDENT]

Now since a restart in your case fixes the problem, I am assuming that simulating a Bluetooth disconnect <--> reconnect cycle *should* be able to reset it.

In my laptop, bluetooth often gets unresponsive (won't turn on, although the BT applet shows it as "On"), and the only way to bring it back to life was a restart. The following fix (bind/unbind the hub driver) works 100% of the time for me now. So, here's what I think should work for you too (use any one of the three) -

**[SIZE=3][COLOR="#800000"]Workaround 1 (reset only BT adapter) :[/COLOR][/SIZE]**
To unbind --> re-bind the **btusb** driver with the bluetooth adapter -
```
echo -n "5-1:1.0" | sudo tee /sys/bus/usb/drivers/btusb/unbind
```
**This will disable the bluetooth adapter only**. To re-enable it, bind the btusb driver again (preferably after 4 to 6 seconds) -
```
echo -n "5-1:1.0" | sudo tee /sys/bus/usb/drivers/btusb/bind
```


**[SIZE=3][COLOR="#800000"]Workaround 2 (reset usb port) :[/COLOR][/SIZE]**
To unbind --> re-bind the **usb** driver with the usb port on which the BT adapter is located -
```
echo -n "5-1" | sudo tee /sys/bus/usb/drivers/usb/unbind
```
**This will disable the internal usb port on which the BT adapter is located**. To re-enable it, bind the usb driver again (preferably after 4 to 6 seconds) -
```
echo -n "5-1" | sudo tee /sys/bus/usb/drivers/usb/bind
```
[COLOR="#FF0000"]*[**NOTE :** This method sometimes leaves the BT adapter in a confused state (on, but not working), so not recommended.]*[/COLOR]


**[SIZE=3][COLOR="#800000"]Workaround 3 (reset usb hub) :[/COLOR][/SIZE]**
To unbind --> re-bind the **uhci_hcd** driver with the usb-hub on which the above usb port is located -
```
echo -n "0000:00:1d.3" | sudo tee /sys/bus/pci/drivers/uhci_hcd/unbind
```
**This will disable the entire hub on which the BT adapter and its holding port is located**. To re-enable it, bind the uhci_hcd driver again (preferably after 4 to 6 seconds) -
```
echo -n "0000:00:1d.3" | sudo tee /sys/bus/pci/drivers/uhci_hcd/bind
```
*[**[COLOR="#FF0000"]CAUTION :[/COLOR]** Please note that as per your outputs, the **[COLOR="#FF0000"]Biometric Coprocessor[/COLOR]** device (finger print reader) is also located on the same hub. So it will also get disconnected during this process. Although it *should* get functional again after re-binding the driver, you should test it to be sure.]*


The last one (disable --> re-enable the entire hub) is what I am using for months, with 100% success rate. The only draw back - it also disables the other devices that are on the same hub. In your case, it is only the finger print reader.

If this works for you, you can create an automated script and add it to your sudoers.d directory so that you don't have to type your password when you need to run it. I have set mine so that I only have to type "u2" in terminal to run it.

Sorry for the scary post, but I hope it may help some.


**PS:**
The exact drivers (usb, btusb, ehci_hcd, uchi_hcd, xhci_hcd), device/bus IDs and the relevant locations of the bind/unbind files may differ for others. Identify the bus id and associated driver as explained above, and locate the relevant driver folder with bind/unbind file within /sys/bus/ directory. USB drivers are located in /sys/bus/usb/ directory, and hub drivers (ehci_hcd, uchi_hcd, xhci_hcd) are located in /sys/bus/pci/ directory.

---

### Post by sona1111 on 2013-05-27
wow! thank you for making such a comprehensive post! I have restarted from when It happened but I will post back the results as soon as I get a chance to try your fixes!

---

### Post by varunendra on 2013-05-27
> **sona1111 said:**
> wow! thank you for making such a comprehensive post! I have restarted from when It happened but I will post back the results as soon as I get a chance to try your fixes!

You're welcome! :)

These internally connected devices are often a source of frustration for many users (I know because I suffered for weeks before trying hard to find a fix), so I thought to present it in a way so that it can help others too, who may have different hardware, different drivers, but similar issues with internally connected devices.

---

### Post by sona1111 on 2013-06-01
Well, bad news...

I tried all three separately, no luck whatsoever.

---

### Post by varunendra on 2013-06-01
> **sona1111 said:**
> Well, bad news...

I tried all three separately, no luck whatsoever.

If it is a bluetooth mouse, it should have an on/off switch. How about toggling it on/off (with a gap of, say, 8-10 seconds) after trying the 3rd method (resetting hub)?

Eventually, it is a matter of a stuck driver, I just can't guess which one and removing individual ones maybe tricky when it comes to bluetooth (I tried once and it turned out to be a bunch of them that are mutually dependent, so I needed to remove them all in a particular sequence, then reload them in reverse sequence).

Also, some of the IDs I used in the commands are based on guess. So you should make sure they exist (like you can simply browse to "/sys/bus/pci/drivers/uhci_hcd/" directory and see if a 'folder' named exactly "0000:00:1d.3" exists there.

And after running the command to unbind the driver, run 'usb-devices' and 'cat proc/bus/input/devices' again to confirm the bluetooth hub and the mouse are actually removed (don't appear in the outputs).

Similarly, after running the 2nd part of the command to re-bind the driver, run both usb-devices and 'cat proc/bus/input/devices' again to confirm they are back in the outputs.

If any of these tests fails it means we are not doing it correctly, most probably a wrong or non-existing entity in the bind/unbind command.

However, there does exist a situation with complex devices that does not let them completely reset until there is a power cycle as well (not just driver unbind/re-bind). But I don't think the inbuilt Bluetooth adapter can be such a 'complex' device.

But then again, all I can do is make guesses and say 'Good Luck'! :)

---

### Post by sona1111 on 2013-06-03
OK, thank you again. I will return here once the problem occurs and I can try all of the checks again.

---

### Post by sona1111 on 2013-06-03
unbind and rebind on/off combination still has no effect. 

The folder "0000:00:1d.3" does indeed exist, but their are other folders there as well. I am not very versed in this linux hardware representation. How can I check which one is the right folder?

It looks to me like the deice was removed:

```
0000:00:1d.3paul@paul-ThinkPad-T60p:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=b6d2 Rev=94.12
S:  Manufacturer=SanDisk
S:  Product=SDAD-111
S:  SerialNumber=080321001897
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=cd12 ProdID=ef18 Rev=01.00
S:  Manufacturer=USB     
S:  Product=Flash Disk      
S:  SerialNumber=3F389B3B11CC131F
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

and cat/proc
```

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 evbug 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 evbug 
B: PROP=0
B: EV=3
B: KEY=4000 0 0 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 evbug 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 evbug 
B: PROP=0
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input4
U: Uniq=
H: Handlers=kbd event4 evbug 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0


I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 evbug 
B: PROP=0
B: EV=40001
B: SND=6


I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input6
U: Uniq=
H: Handlers=rfkill kbd event6 evbug 
B: PROP=0
B: EV=33
B: KEY=18040000 0 0 100000 0 0 0 101501b 102004 80000000 1104000 e0000 0 0 0
B: MSC=10
B: SW=8


I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse0 event7 evbug 
B: PROP=1
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=11000003


I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=synaptics-pt/serio0/input0
S: Sysfs=/devices/platform/i8042/serio1/serio2/input/input8
U: Uniq=
H: Handlers=mouse1 event8 evbug 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```


and after rebinding:
```

0000:00:1d.3paul@paul-Thinkusb-devices


T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=b6d2 Rev=94.12
S:  Manufacturer=SanDisk
S:  Product=SDAD-111
S:  SerialNumber=080321001897
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=cd12 ProdID=ef18 Rev=01.00
S:  Manufacturer=USB     
S:  Product=Flash Disk      
S:  SerialNumber=3F389B3B11CC131F
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.05
S:  Manufacturer=Linux 3.5.0-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=2110 Rev=01.00
S:  Manufacturer=Broadcom Corp
S:  Product=BCM2045B
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)


T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0483 ProdID=2016 Rev=00.01
S:  Manufacturer=STMicroelectronics
S:  Product=Biometric Coprocessor
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)

```

```

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 evbug 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 evbug 
B: PROP=0
B: EV=3
B: KEY=4000 0 0 0 0


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 evbug 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 evbug 
B: PROP=0
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input4
U: Uniq=
H: Handlers=kbd event4 evbug 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0


I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 evbug 
B: PROP=0
B: EV=40001
B: SND=6


I: Bus=0019 Vendor=17aa Product=5054 Version=4101
N: Name="ThinkPad Extra Buttons"
P: Phys=thinkpad_acpi/input0
S: Sysfs=/devices/platform/thinkpad_acpi/input/input6
U: Uniq=
H: Handlers=rfkill kbd event6 evbug 
B: PROP=0
B: EV=33
B: KEY=18040000 0 0 100000 0 0 0 101501b 102004 80000000 1104000 e0000 0 0 0
B: MSC=10
B: SW=8


I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse0 event7 evbug 
B: PROP=1
B: EV=b
B: KEY=6420 0 30000 0 0 0 0 0 0 0 0
B: ABS=11000003


I: Bus=0011 Vendor=0002 Product=000a Version=0000
N: Name="TPPS/2 IBM TrackPoint"
P: Phys=synaptics-pt/serio0/input0
S: Sysfs=/devices/platform/i8042/serio1/serio2/input/input8
U: Uniq=
H: Handlers=mouse1 event8 evbug 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

---

### Post by varunendra on 2013-06-03
As per above outputs, the USB hub was indeed removed, then reconnected as expected. But the BT mouse, as you can see, wasn't (removed, but not reconnected, which is also what I expected). So, does this mouse have a power on/off switch?

Bluetooth devices need to establish a fresh connection once an established one is interrupted, like I had to do manually when I was experimenting with my mobile phone. Assuming the required communication is done automatically between the mouse and the laptop, a power cycle on the mouse after this step should do the job (like it does in an iMac).

---

### Post by sona1111 on 2013-06-19
A small update for developers:

Restarting X with ctrl+alt+backspace works to reconnect the mouse when this occurs.

In the end, I just reinstalled 12.04 and the problem has not popped up since

---

### Post by varunendra on 2013-06-20
> **sona1111 said:**
> A small update for developers:

User feedback is always a very important and appreciated part of open source software development. Glad to see you are willing to contribute that way.

Unfortunately, developers don't look into these forums for such feedbacks or bug reports. In fact they look nowhere else other than specific bug reporting systems, and even ignore feedbacks/bug-reports even if they do see them in places like this. Partly because there is already so much pressure with the officially reported bugs, and partly because fixing them needs a systematic try-and-feedback type collaboration system.

So if the problem reoccurs, you may use launchpad to file an official bug report or add yourself to an existing bug-report : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

By doing so (if the time allows, and you care enough), you may be possibly helping a lot of others like you. :)

---

