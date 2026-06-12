---
title: "Ubuntu 16.04.6 LTS on Thinkpad P52: Black screen on resume"
date: 2019-03-09
forum: General Help
---

### Post by sridhar5 on 2019-03-09
Hello! I've seen several posts on these forums talking about a black screen when the laptop is resumed. I have the same problem, and I'd like to add as much info as I can, hoping for a solution.

This is a brand new Thinkpad P52 on which I installed Ubuntu Mate 16.04.6 this past week, alongside Win10. When I resume the laptop after suspending it, the screen remains black. But I can ssh into it, and I can see the processes running. I have tried several of the alternatives I found on these forums to fix it, but no luck so far (including using nomodeset in the boot command line, switching the BIOS to integrated graphics instead of discrete). I tried the nvidia drivers and found them very unstable, so removed them.

 I have attached to this post a zip file containing the outputs of inxi and lspci commands as well as the kern.log and syslog entries for the time interval right before and after the resume attempt. If there is any other info I can provide to help resolve this, please let me know. Thanks in advance for all your help!

EDIT: Below the output of inxi -Fx - added because the file in the zip file includes escape characters that make it much less readable.
```

System:    Host: ThinkPad-P52 Kernel: 4.15.0-46-generic x86_64 (64 bit gcc: 5.4.0) Console: tty 3
           Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 20M9CTO1WW v: ThinkPad P52
           Mobo: LENOVO model: 20M9CTO1WW v: SDK0Q40104 WIN Bios: LENOVO v: N2CET35W (1.18 ) date: 12/14/2018
CPU:       Hexa core Intel Xeon E-2176M (-HT-MCP-) cache: 12288 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 32544
           clock speeds: max: 4400 MHz 1: 900 MHz 2: 900 MHz 3: 900 MHz 4: 900 MHz 5: 900 MHz 6: 900 MHz
           7: 900 MHz 8: 900 MHz 9: 900 MHz 10: 900 MHz 11: 900 MHz 12: 900 MHz
Graphics:  Card: NVIDIA GP107GLM [Quadro P2000 Mobile] bus-ID: 01:00.0
           Display Server: X.org 1.19.6 drivers: nouveau (unloaded: fbdev,vesa)
           tty size: 160x60 Advanced Data: N/A out of X
Audio:     Card-1 NVIDIA GP107GL High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel Cannon Lake PCH cAVS driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-46-generic
Network:   Card-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi bus-ID: 00:14.3
           IF: wlp0s20f3 state: up mac: 20:79:18:cb:ba:3d
           Card-2: Intel Ethernet Connection (7) I219-LM driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6
           IF: enp0s31f6 state: down mac: e8:6a:64:57:0e:fe
Drives:    HDD Total Size: 500.1GB (2.8% used) ID-1: /dev/nvme0n1 model: N/A size: 256.1GB
           ID-2: /dev/sda model: ST500LM034 size: 500.1GB
Partition: ID-1: / size: 178G used: 6.0G (4%) fs: ext4 dev: /dev/nvme0n1p6
           ID-2: swap-1 size: 8.00GB used: 0.00GB (0%) fs: swap dev: /dev/nvme0n1p5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 264 Uptime: 47 min Memory: 542.7/15722.4MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 

```

---

### Post by sridhar5 on 2019-03-09
Following up on my own post: Seems like it is now fixed. I had to install the nvidia drivers via Administration - Software and Updates - Additional Drivers (I selected the latest version 415), and then I had to switch the BIOS Display setting from Discrete Graphics to Hybrid Graphics. This seems to have resolved all the issues I had, including setting brightness (via the F5 and F6 keys) and setting the display resolution (via System - Preferences - Hardware - Displays). I'm a happy camper now. :p Hope this is of use to someone.

---

