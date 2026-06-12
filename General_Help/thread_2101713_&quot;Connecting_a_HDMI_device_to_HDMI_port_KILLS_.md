---
title: "&quot;Connecting a HDMI device to HDMI port KILLS sound output&quot;"
date: 2013-01-05
forum: General Help
---

### Post by blackdalek on 2013-01-05
Can anyone in here help?, sound was working fine this morning. I plugged in a HDMI cable and sound worked fine through the TV. I unplugged it and sound never returned. Even after a reboot. It won't come back. Here is result of aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and here is result of lspci

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
```

and this is what is in output devices [http://imagebin.org/241799](http://imagebin.org/241799)

---

### Post by blackdalek on 2013-01-05
Additional info -

1. I hear the "log in" sound when the computer starts, then sound goes dead once the unity desktop is loaded.

2. Sound comes back sometimes if I start certain games such as Tuxkart, but not always, then sound works system-wide. Until next reboot -then all sound goes dead again.

3. In any situation, the sound device NEVER shows up in the output sound devices list EVER...

---

### Post by blackdalek on 2013-01-06
Apparently this problem is insolvable,

Ran out of time to find a solution, did a re-install from the CD. Got sound back, but the sound output devices list is still blank in sound settings.




Now how to I tag this thread as "insolvable"? ;)

---

### Post by blackdalek on 2013-01-11
Yep. As soon as I plug the HDMI lead into the HDMI port of my Dell Inspiron 3520, built-in speaker sound goes utterly dead.... but ONLY for the current logged in user.

Have spent days researching this and problem seems to be specific to this laptop model (i.e. I could not find anyone else with this problem)

The ONLY way I can get sound back for my logged in user is to do a complete re-install of Ubuntu.

Once the built-in sound output has been rendered DEAD by the insertion of a HDMI cable, there is no way to get sound back for that user. It does NOT return when the HDMI cable is removed (as you would expect it to).
If you log in as a different user or guest user then built-in sound returns to normal... however, plug in a HDMI during that user's session and bingo! - sound output is killed stone dead again.

Another thing which is probably related - no sound output devices EVER appear in the sound settings output list window EXCEPT when a HDMI cable is plugged in. Then it is empty again when it is removed.


The laptop in question is running ubuntu 12.10.

If you think it will make any difference, I can humour you by providing any terminal command output or screenshot you ask for in relation to this system. Just ask and I will post.
Although I doubt anyone will be able to shed any light. Spent over 24 hours on this already on forums, google and #ubuntu irc... All fruitless endeavours...

---

### Post by blackdalek on 2013-01-11
made a new discovery - 

Insert a plug into the headphones socket at side of laptop.
Remove plug from headphones socket.
Audio automagically comes back alive again.

Freaking moronic solution, but works faster than a full re-install of Ubuntu which was my only other means of fixing this issue until now.

---

### Post by blackdalek on 2013-01-12
Lookk what I found! - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1076840](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1076840)

This looks like it is precisely what is happening with my Inspiron 3520, and my issue with the HDMI port is a direct side effect of this bug.

So I wan't dreaming it after all. I hope a fix is released soon ;)

---

