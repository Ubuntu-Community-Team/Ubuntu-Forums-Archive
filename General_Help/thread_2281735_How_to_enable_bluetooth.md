---
title: "How to enable bluetooth"
date: 2015-06-09
forum: General Help
---

### Post by houmingc on 2015-06-09
I can't start bluetooth and use it to syn my Sony Phone

rfkill list


1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

i did below, but still can't activate bluetooth
sudo rfkill unblock bluetooth

root@ubuntu-UX32VD:/home/ubuntu# dmesg | grep -i blue
[   23.181362] Bluetooth: Core ver 2.17
[   23.181382] Bluetooth: HCI device and connection manager initialized
[   23.181390] Bluetooth: HCI socket layer initialized
[   23.181393] Bluetooth: L2CAP socket layer initialized
[   23.181398] Bluetooth: SCO socket layer initialized
[   25.805682] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.805686] Bluetooth: BNEP filters: protocol multicast
[   25.805693] Bluetooth: BNEP socket layer initialized
[   25.811682] Bluetooth: RFCOMM TTY layer initialized
[   25.811693] Bluetooth: RFCOMM socket layer initialized
[   25.811698] Bluetooth: RFCOMM ver 1.11

---

### Post by Bucky Ball on 2015-06-09
*Thread moved to **General Help**.*

You mention nothing about which release/flavour of Ubuntu you are using. Have you installed Bluez (should already be there) and had a look at what results you get from that? What is currently telling you that bluetooth is not actually started? I see no errors in your output. How are you testing your theory? 

Have you got a physical button to switch bluetooth on as your output is saying it is soft-blocked. That may be the only hiccup. 

PS: Please see last link in my signature for using [code] tags when posting code. Thanks.

---

