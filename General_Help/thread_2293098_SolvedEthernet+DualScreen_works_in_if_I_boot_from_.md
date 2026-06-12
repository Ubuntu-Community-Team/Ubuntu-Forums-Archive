---
title: "Solved:Ethernet+DualScreen works in if I boot from USB but doesn't if I boot from SSD"
date: 2015-09-02
forum: General Help
---

### Post by mueller.pascal on 2015-09-02
Solved: After noticing that PXE is that "remote booting" Utility I kind of though that there could be something wrong in my UEFI BIOS. From what I remember, I only activated virtualization support when I first had windows, so my VM were more performant, also, I changed boot order. [B]Anyway, I just reseted BIOS settings and reinstalled Kubuntu 15.04 and now it works again.
[/B]


hi,

I have kubuntu installed, the new version. 15.04

If I run it via USB flash drive my pro dock works nice. The internet connects via wire and both screens work. If I install it then the wired internet works too but it doesn't recognize the external screen if I plug it in. so I restart, after the restart, the external screen works until I'm logged in, then it doesn't receive any signal, also, the ethernet breaks and can't connect. Wlan can connect.

[B]So basically: Ethernet + Dual Screen works in if I boot from USB but doesn't if I boot from SSD. Why's that?

[/B]I think dual screen worked before (I think it was kubuntu 14.03 LTS) but maybe it was 15.03 as well. I reinstalled after it kind of crashed after using the spin script from above. (I chose a mode and the screen went black with the cursor and I had no clue what to do) but I dont think this has any affects right now, I just wanted to point out that the script above doesn't take care of dual screen.

If I boot I get some weird ethernet loading screen I have no idea what it is for:

Intel UNDI, PXE-2.1 (build 083)
Realtek RTL8153 USB ethernet connection (Im not sure about the word connection)
XHCI v.073
client MAC ADDR: bla GUID: bla
DHCP .../ (here, the / rotates and some . are added. after 1 minute I get the following msg=

PXE-???: no boot file name received
PXE-M0F: existing PXE Rom

Please note, that there might be some writing mistakes. What's that?

Update: I noticed that the second screen kind of was disabled so it worked but now i have this problem: I log in, it loads 80%, stucks. If I unplug the dock, the desktop appears. If I plug it in again, the login screen with 80% shows up again. If I unplug again, desktops shows up again. etc... o.O

---

