---
title: "No sound in firefox"
date: 2007-10-26
forum: General Help
---

### Post by quickshade on 2007-10-26
I've tried everything. 6 pages on google, 10 on yahoo and not one of those fixed my problem. Sound is great on my desktop. But in firefox I get nothing on youtube or anything like that. Not a huge deal but would be nice to fix it. I had it working before but then it just stopped. any suggestions would be great. Thanks.

---

### Post by jusmurph on 2007-10-26
Do you know if its just a flash related?

Or any media via firefox?

All so, try this:

>  Originally Posted by Gabriel Pastor
I had the same problem with feisty and solved it.
I have 2 sound cards, and it seems that sometimes the wrong sound card is the default sound device.

$ sudo asoundconf list
Names of available sound cards:
Intel
CA0106

The first one is integrated on the motherboard, and the second one (an audigy) is the one I use.

To solve the problem, I just set the default sound card to the audigy:
$ sudo asoundconf set-default-card CA0106

Then the sound works !
Hope it helps.

---

### Post by Crafty Kisses on 2007-10-26
> **quickshade said:**
> I've tried everything. 6 pages on google, 10 on yahoo and not one of those fixed my problem. Sound is great on my desktop. But in firefox I get nothing on youtube or anything like that. Not a huge deal but would be nice to fix it. I had it working before but then it just stopped. any suggestions would be great. Thanks.

You should post the following output:
```
lspci
```

---

### Post by wayne040576 on 2007-10-28
> **jusmurph said:**
> Do you know if its just a flash related?

Or any media via firefox?
...
All so, try this:

jusmurph, Thanks for that!

 I upgraded yesterday and had spent the last few hours trying to get my sound working, when I came across this thread. I also disabled my motherboard sound device in the bios so hopefully this won't happen again.

---

### Post by quickshade on 2007-10-29
> 00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)

Here's what I know, My sound card has digital out, which I connect to my sound system  via coaxial cable. My sound card is from NVidia but seems to have 2 parts. The regular analog and then the digital. If I disable anything in my bios I do not get any sound at all.  In order to get sound I have to enable digital 1 which is under the recording tab. After which I get sound from all programs except youtube or any other flash based media. I'm at a loss. I really love Linux but sound support is still terrible and isn't improving at all.

EDIT: my only soundcard to choose from as default is nvidia.

---

### Post by quickshade on 2007-10-30
I've tried every site I could imagine and still no luck. I recently (10 minutes ago) saw the post on the soundconfig in the home folder. I have 2 of them. One with barely any text and one with a whole bunch of stuff related to my sound card. Don't know if that helps anyone. Talk about annoying, my system is 99% perfect and fixing this problem is all I have to do.

---

