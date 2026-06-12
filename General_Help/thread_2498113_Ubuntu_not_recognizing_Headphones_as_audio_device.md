---
title: "Ubuntu not recognizing Headphones as audio device"
date: 2024-05-31
forum: General Help
---

### Post by markovian-baller on 2024-05-31
Hello
I use ubuntu i3. I have a desktop pc with and amd ryzen 5 and an msi nvidia geforce 1660. I use dual boot on a 512gb ssd with windows and linux.

I have a problem with my sony wh-1000mx5 headphones. I am unable to connect them to my Ubuntu system. The headphones were running fine and I could always connect the via bluetoothcl connect {Mac Address}.

Yesterday, I booted on windows and connected the headphones there via bluetooth. I then rebooted to linux and I would always get

[bluetooth]# connect CC:0A:65:1C:6D:59
Device CC:0A:65:1C:6D:59 not available
The headphones are no longer showing up in bluetoothctl scan on. I can no longer connect to them. This seems to be a very specific problem, because my headphones are still able to connect to any other device and my linux pc is still able to connect to any other bluetooth headphones such as my old wh-1000mx3 with full functionality. Thus it seems to not really be a bluetooth problem. I did a wide variety of steps to solve this problem, which I am going to list in the end to not disturb the reading flow. The ONLY thing that led to some results is that I looked into the logs of btmon during bluetoothctl scan. There, I found that my headphones were actually listed:

@ MGMT Event: Device Found (0x0012) plen 34 {0x0002} [hci0] 31.049217 LE Address: CC:0A:65:1C:6D:57 (Static) RSSI: -51 dBm (0xcd) Flags: 0x00000000 Data length: 20 16-bit Service UUIDs (complete): 1 entry Unknown (0xfe03) Name (complete): LE_WH-1000XM5
So my Ubuntu pc was actually finding something. It just couldnt connect to it and only had the "LE Address". I thus did this:

inside bluetoothctl calling the following sequence

menu scan
transport le
back
scan on
Then my headphones appeared and I could connect to them. The headphones did not make their connection sound however and It was also not possible for me to see them in pavucontrol. They did not play any sound either. The only thing that changed is that bluetoothctl would display the name... They are seemingly not recognized as a real device or audio output. I am very helpless at this point and would appreciate any help.

(Logs at the end)

Here is a list of all the things I already tried:

Reboot
Shut down, unplug, wait 5 minutes, plug back in and boot
Reset Headphones
Reinstall bluez
Reset usb:hciconfig hci0 downrmmod btusbmodprobe btusbhciconfig hci0 up
Reset usb like this:sudo rmmod xhci_pci; sudo rmmod xhci_hcd; sudo modprobe xhci_pci xhci_hcd
check rfkill (nothing is blocked)
Restart pulsaudio (by killing and restarting process)
Download a script that claims to fix this:
curl "https://gist.githubusercontent.com/pylover/d68be364adac5f946887b85e6ed6e7ae/raw/install.sh" | sh

fails because it cannot find the bluetooth device, despite bluetoothctl claiming that it is connected
10. check bluetoothctl agent

power on
 agent on 
default-agent 
scan on 
pairable on 
discoverable on
11. Removed, repaired and trusted the device in bluetoothctl

12. Did a software update with the software updater

13. Restarted bluetooth:

systemctl stop bluetooth.service
systemctl enable bluetooth.service
systemctl start bluetooth.service
systemctl restart bluetooth.service
14. Used a usb dongle for bluetooth instead and redid all the steps -> same results

15. Tried connecting over the name, and not the Mac address

15. tried connecting over gnome UI in non-i3 ubuntu -> Headphones disappear as soon as I click on them in the bluetooth panel

16. removed the headphones as device from windows bluetooth

17. Tried adding AutoConnect=true to main.conf of bluetooth

18. Made sure no other devices are connected to the headphones

Because they might be relevant here are my:

sudo systemctl status bluetooth

bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2024-05-31 10:38:30 CEST; 54min ago
       Docs: man:bluetoothd(8)
   Main PID: 1407 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18792)
     Memory: 1.9M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1407 /usr/lib/bluetooth/bluetoothd

Mai 31 10:38:29 blendaddict-MS-7B86 systemd[1]: Starting Bluetooth service...
Mai 31 10:38:29 blendaddict-MS-7B86 bluetoothd[1407]: Bluetooth daemon 5.53
Mai 31 10:38:29 blendaddict-MS-7B86 bluetoothd[1407]: Unknown key AutoConnect for group General in /etc/bluetooth/main.conf
Mai 31 10:38:30 blendaddict-MS-7B86 systemd[1]: Started Bluetooth service.
Mai 31 10:38:30 blendaddict-MS-7B86 bluetoothd[1407]: Starting SDP server
Mai 31 10:38:30 blendaddict-MS-7B86 bluetoothd[1407]: Bluetooth management interface 1.21 initialized

note from me: (autoconnect warning stems from a fix I tried)
This is what bluetoothctl looks like after connecting to the headphones:

[CHG] Device CC:0A:65:1C:6D:59 UUIDs: 5b833e0a-6bc7-4802-8e9a-723ceca4bd8f
[CHG] Device CC:0A:65:1C:6D:59 UUIDs: dc405470-a351-4a59-97d8-2e2e3b207fbb
[CHG] Device CC:0A:65:1C:6D:59 UUIDs: f76acb00-7cab-495f-bb1a-e664598fd77f
[CHG] Device CC:0A:65:1C:6D:59 ServicesResolved: yes
[CHG] Device CC:0A:65:1C:6D:59 Name: LE_WH-1000XM5
[CHG] Device CC:0A:65:1C:6D:59 Alias: LE_WH-1000XM5
[CHG] Device 78:61:67:B2:02:06 RSSI: -70
[CHG] Device 63:BD:2A:54:E2:B3 RSSI: -76
[CHG] Device D0:C0:9D:03:EA:25 RSSI: -84
[CHG] Device FB:CD:3A:83:5F:11 RSSI: -50
[CC-0A-65-1C-6D-59]# 
Sometimes it also says the name of the headphones in the squared brackets.

this is bluetoothctl devices:

[CC-0A-65-1C-6D-59]# devices
Device 94:DB:56:F6:D7:27 LE_WH-1000XM3
Device 78:61:67:B2:02:06 78-61-67-B2-02-06
Device 8C:79:F5:1F:9F:A4 [TV] Samsung 7 Series (43)
Device 40:A4:C1:19:59:EC 40-A4-C1-19-59-EC
Device 63:BD:2A:54:E2:B3 63-BD-2A-54-E2-B3
Device F0:B3:EC:7D:23:FB F0-B3-EC-7D-23-FB
Device 3A:29:4A:5B:E0:82 3A-29-4A-5B-E0-82
Device 4F:E8:0E:A6:2F:8D 4F-E8-0E-A6-2F-8D
Device D0:C0:9D:03:EA:25 D0-C0-9D-03-EA-25
Device CC:0A:65:1C:6D:59 LE_WH-1000XM5
Device 6F:00:70:41:74:E4 6F-00-70-41-74-E4
Device FB:CD:3A:83:5F:11 FB-CD-3A-83-5F-11
Device F2:57:BA:E5:95:79 F2-57-BA-E5-95-79
Device CC:0A:65:1C:6D:57 LE_WH-1000XM5
Device C1:2E:A7:D2:79:29 C1-2E-A7-D2-79-29
Device DF:B1:98:A1:73:71 DF-B1-98-A1-73-71
Device 45:9A:55:64:C6:23 45-9A-55-64-C6-23
Device 6F:2E:C0:58:D9:DB 6F-2E-C0-58-D9-DB
Device DE:6E:07:B1:46:55 DE-6E-07-B1-46-55
And this is my

pactl list short sinks

0alsa_output.pci-0000_29_00.1.hdmi-stereomodule-alsa-card.cs16le 2ch 44100HzSUSPENDED
1alsa_output.pci-0000_2b_00.4.analog-stereomodule-alsa-card.cs16le 2ch 44100HzSUSPENDED
As mentioned, any help is greatly appreciated :)

---

### Post by currentshaft on 2024-05-31
Do you see any thing in "sudo dmesg -wHT" output while you attempt to connect them?

---

### Post by markovian-baller on 2024-05-31
[Fr Mai 31 22:47:08 2024] audit: type=1326 audit(1717188428.916:104): auid=1000 uid=1000 gid=1000 ses=2 subj=snap.spotify.spotify pid=4220 comm="spotify" exe="/snap/spotify/75/usr/share/spotify/spotify" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7f365038922b code=0x50000
[Fr Mai 31 22:47:08 2024] audit: type=1326 audit(1717188428.916:105): auid=1000 uid=1000 gid=1000 ses=2 subj=snap.spotify.spotify pid=4221 comm="spotify" exe="/snap/spotify/75/usr/share/spotify/spotify" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7efc39e4822b code=0x50000
[Fr Mai 31 22:47:09 2024] audit: type=1400 audit(1717188429.820:106): apparmor="DENIED" operation="open" profile="snap.spotify.spotify" name="/etc/vulkan/implicit_layer.d/" pid=4245 comm="spotify" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[Fr Mai 31 22:47:09 2024] audit: type=1400 audit(1717188429.820:107): apparmor="DENIED" operation="open" profile="snap.spotify.spotify" name="/etc/vulkan/implicit_layer.d/" pid=4245 comm="spotify" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[Fr Mai 31 22:47:09 2024] audit: type=1400 audit(1717188429.820:108): apparmor="DENIED" operation="open" profile="snap.spotify.spotify" name="/etc/vulkan/icd.d/" pid=4245 comm="spotify" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[Fr Mai 31 22:47:09 2024] audit: type=1400 audit(1717188429.820:109): apparmor="DENIED" operation="open" profile="snap.spotify.spotify" name="/etc/vulkan/icd.d/" pid=4245 comm="spotify" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[Fr Mai 31 22:47:09 2024] audit: type=1400 audit(1717188429.820:110): apparmor="DENIED" operation="open" profile="snap.spotify.spotify" name="/etc/vulkan/implicit_layer.d/" pid=4245 comm="spotify" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[Fr Mai 31 22:47:09 2024] audit: type=1400 audit(1717188429.820:111): apparmor="DENIED" operation="open" profile="snap.spotify.spotify" name="/etc/vulkan/implicit_layer.d/" pid=4245 comm="spotify" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[Fr Mai 31 22:47:09 2024] audit: type=1400 audit(1717188429.820:112): apparmor="DENIED" operation="open" profile="snap.spotify.spotify" name="/etc/vulkan/icd.d/" pid=4245 comm="spotify" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[Fr Mai 31 22:47:52 2024] usb 1-8.3: reset full-speed USB device number 6 using xhci_hcd
[Fr Mai 31 22:47:59 2024] kauditd_printk_skb: 14 callbacks suppressed
[Fr Mai 31 22:47:59 2024] audit: type=1326 audit(1717188479.653:127): auid=1000 uid=1000 gid=1000 ses=2 subj=snap.spotify.spotify pid=4866 comm="spotify" exe="/snap/spotify/75/usr/share/spotify/spotify" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7f00a8ea122b code=0x50000
[Fr Mai 31 22:47:59 2024] audit: type=1326 audit(1717188479.653:128): auid=1000 uid=1000 gid=1000 ses=2 subj=snap.spotify.spotify pid=4865 comm="spotify" exe="/snap/spotify/75/usr/share/spotify/spotify" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fdb8ed5022b code=0x50000
[Fr Mai 31 22:48:05 2024] usb 1-8.3: reset full-speed USB device number 6 using xhci_hcd
[Fr Mai 31 22:48:43 2024] usb 1-8.3: reset full-speed USB device number 6 using xhci_hcd


[Fr Mai 31 22:47:52 2024] is when I did bluetoothctl connect 

logs of bluetootctl connect
[bluetooth]# connect CC:0A:65:1C:6D:59
Attempting to connect to CC:0A:65:1C:6D:59
[CHG] Device CC:0A:65:1C:6D:59 Connected: yes
Connection successful
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0011
	00001801-0000-1000-8000-00805f9b34fb
	Generic Attribute Profile
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0011/char0012
	00002a05-0000-1000-8000-00805f9b34fb
	Service Changed
[NEW] Descriptor (Handle 0x10d4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0011/char0012/desc0014
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Descriptor (Handle 0x17e4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0011/char0012/desc0015
	00002903-0000-1000-8000-00805f9b34fb
	Server Characteristic Configuration
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0030
	5b833e05-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0030/char0031
	5b833c11-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Characteristic (Handle 0x3a8d)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0030/char0033
	5b833c13-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Descriptor (Handle 0x23c4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0030/char0033/desc0035
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0030/char0036
	5b833c14-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0040
	5b833e06-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0040/char0041
	5b833c10-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0040/char0043
	5b833c12-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Descriptor (Handle 0x3294)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0040/char0043/desc0045
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0046
	5b833e0a-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0046/char0047
	5b833c10-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0046/char0049
	5b833c12-6bc7-4802-8e9a-723ceca4bd8f
	Vendor specific
[NEW] Descriptor (Handle 0x42e4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0046/char0049/desc004b
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0051
	dc405470-a351-4a59-97d8-2e2e3b207fbb
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0051/char0052
	bfd869fa-a3f2-4c2f-bcff-3eb1ec80cead
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0051/char0054
	2a6b6575-faf6-418c-923f-ccd63a56d955
	Vendor specific
[NEW] Descriptor (Handle 0x5524)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0051/char0054/desc0056
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060
	f76acb00-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0061
	f76acb01-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0063
	f76acb02-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Descriptor (Handle 0x6134)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0063/desc0065
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0066
	f76acb03-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Descriptor (Handle 0x6754)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0066/desc0068
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0069
	f76acb04-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char006b
	f76acb05-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Descriptor (Handle 0x14b4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char006b/desc006d
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char006e
	f76acb06-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Descriptor (Handle 0x7f94)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char006e/desc0070
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0071
	f76acb07-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0073
	f76acb08-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Descriptor (Handle 0x88d4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0073/desc0075
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0076
	f76acb09-7cab-495f-bb1a-e664598fd77f
	Vendor specific
[NEW] Descriptor (Handle 0x8ef4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0060/char0076/desc0078
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00d0
	0000fe03-0000-1000-8000-00805f9b34fb
	Unknown
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00d0/char00d1
	f04eb177-3005-43a7-ac61-a390ddf83076
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00d0/char00d3
	2beea05b-1879-4bb4-8a2f-72641f82420b
	Vendor specific
[NEW] Descriptor (Handle 0x9ae4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00d0/char00d3/desc00d5
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00e0
	45c93e07-d90d-4b93-a9db-91e5dd734e35
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00e0/char00e1
	45c93c15-d90d-4b93-a9db-91e5dd734e35
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00e0/char00e3
	45c93c16-d90d-4b93-a9db-91e5dd734e35
	Vendor specific
[NEW] Descriptor (Handle 0x7474)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00e0/char00e3/desc00e5
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00e0/char00e6
	45c93c17-d90d-4b93-a9db-91e5dd734e35
	Vendor specific
[NEW] Descriptor (Handle 0xb304)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service00e0/char00e6/desc00e8
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Primary Service (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100
	0000fe2c-0000-1000-8000-00805f9b34fb
	Google Inc.
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char0101
	fe2c1233-8366-4814-8eb0-01de32100bea
	Vendor specific
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char0103
	fe2c1234-8366-4814-8eb0-01de32100bea
	Vendor specific
[NEW] Descriptor (Handle 0xbef4)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char0103/desc0105
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char0106
	fe2c1235-8366-4814-8eb0-01de32100bea
	Vendor specific
[NEW] Descriptor (Handle 0xc524)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char0106/desc0108
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char0109
	fe2c1236-8366-4814-8eb0-01de32100bea
	Vendor specific
[NEW] Descriptor (Handle 0xd724)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char0109/desc010b
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3461)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char010c
	fe2c1237-8366-4814-8eb0-01de32100bea
	Vendor specific
[NEW] Descriptor (Handle 0xdd54)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char010c/desc010e
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration
[NEW] Characteristic (Handle 0x3a8d)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char010f
	fe2c1238-8366-4814-8eb0-01de32100bea
	Vendor specific
[NEW] Descriptor (Handle 0xe384)
	/org/bluez/hci0/dev_CC_0A_65_1C_6D_59/service0100/char010f/desc0111
	00002902-0000-1000-8000-00805f9b34fb
	Client Characteristic Configuration

It connects but still no sound.

---

