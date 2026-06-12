---
title: "Changing to Secure Boot in Bios wiped Network (wireless and eth)"
date: 2019-11-12
forum: General Help
---

### Post by cov on 2019-11-12
[I did see a thread on this from 2017]("https://ubuntuforums.org/showthread.php?t=2349257"), but the OP's solution was to simply reinstall.

I have successfully installed Ubuntu 19.10 on a brand new laptop.```
Machine:   Type: Laptop System: ASUSTeK product: TUF Gaming FX705DT_FX705DT v: 1.0 serial: K6NRCV04M56925A 
           Mobo: ASUSTeK model: FX705DT v: 1.0 serial: K624NRCV007RCCMB UEFI: American Megatrends v: FX705DT.308 
           date: 09/19/2019 
Battery:   ID-1: BAT0 charge: 65.9 Wh condition: 65.9/67.2 Wh (98%) volts: 17.1/16.6 model: FX70542 serial:    
           status: Full 
CPU:       Topology: Quad Core model: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx bits: 64 type: MT MCP arch: Zen+ 
           rev: 1 L1 cache: 384 KiB L2 cache: 2048 KiB L3 cache: 4096 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 36729 
           Speed: 1225 MHz min/max: 1400/2300 MHz Core speeds (MHz): 1: 1223 2: 1255 3: 1224 4: 1232 5: 1224 6: 1224 
           7: 1224 8: 1218 
Graphics:  Device-1: NVIDIA vendor: ASUSTeK driver: N/A bus ID: 01:00.0 chip ID: 10de:1f91 
           Device-2: Advanced Micro Devices [AMD/ATI] Picasso vendor: ASUSTeK driver: N/A bus ID: 05:00.0 
           chip ID: 1002:15d8 
           Display: server: X.org 1.20.4 driver: none unloaded: vesa tty: 120x33 
           Message: Advanced graphics data unavailable in console for root. 
Audio:     Device-1: NVIDIA vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 01:00.1 chip ID: 10de:10fa 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel 
           v: kernel bus ID: 05:00.6 chip ID: 1022:15e3 
           Sound Server: ALSA v: k4.19.0-6-amd64 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK driver: r8169 v: kernel 
           port: e000 bus ID: 02:00.0 chip ID: 10ec:8168 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 04:d4:c4:7a:0f:d4 
           Device-2: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter vendor: AzureWave driver: N/A 
           port: d000 bus ID: 04:00.0 chip ID: 10ec:c821 
```

i then installed Virtualbox, which said it needed Secure Boot to be enabled in the BIOS: [https://appuals.com/fix-amd-v-is-disabled-in-the-bios-verr_svm_disabled/]("https://appuals.com/fix-amd-v-is-disabled-in-the-bios-verr_svm_disabled/")

However, switching on Secure Boot lost both wired and wireless networking.

Switching it off again did not restore it.

Without a network connection, the machine is unusable for the purpose I bought it for.

Please advise!

---

### Post by yancek on 2019-11-12
> i then installed Virtualbox, which said it needed Secure Boot to be enabled in the BIOS:

You have mis-read the post.  It does not say Secure Boot needs to be enabled but that **Secure Virtual Machine Mode** is **Enabled**.  You will need to access your BIOS to find the option bearing in mind that what is shown in the thread may not be the same on your hardware/BIOS firmware but should be similar. 

I'm not sure how turning Secure Boot on or off is going to affect your networking.  Did you make any other changes?

---

