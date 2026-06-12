---
title: "Colours wrong in videos made on system or downloaded"
date: 2013-02-18
forum: General Help
---

### Post by rapattack1 on 2013-02-18
I have videos *.flv and cheese videos. The colours are wrong and i was able to change something in VLC which brought it back to normal in VLC only. Something about hardware acceleration i think. I have experienced this before on a previous install. Btw i am in Australia and Colour is correct spelling :0)
I suspect this is a problem with the monitor/setting or something. XFCE? The settings say this is a CRT monitor and it is not. Its LCD. I have a nvidia pcie video card and when i changed the monitor which doesn't have a dvi port i put an adapter at the video card end as it has two dvi ports and no vga...the monitor only has vga and hdmi. So after i installed ubuntustudio a few days ago i changed monitors. Could this be the issue?

---

### Post by fuorviatos on 2013-02-18
Does your problem affect only .flv videos or also standard formats, like .avi ?
If it occurs with avi as well, I'd try to check what video output is being used by your VLC and change it to something else to see if this solves your problem.

---

### Post by rapattack1 on 2013-02-18
Yes avi is affected too. I have that format on my camera and there is only one file i have made since installing this system. I think also an mp4. No VLC is showing videos correctly now since i changed something. The other programs don't like xine amd movie player

---

### Post by fuorviatos on 2013-02-18
> **rapattack1 said:**
> Yes avi is affected too. I have that format on my camera and there is only one file i have made since installing this system. I think also an mp4. No VLC is showing videos correctly now since i changed something. The other programs don't like xine amd movie player
Ok, so try to switch the video output in your video player.

---

### Post by gordintoronto on 2013-02-18
A DVI to VGA adapter can be a source of problems.

Did you install the Nvidia driver?

What brand and model of video adapter and display?

---

### Post by rapattack1 on 2013-02-20
> **fuorviatos said:**
> Ok, so try to switch the video output in your video player.
Ummmmm can you give me more info as i don't know what that is....where is the option/setting? Never seen anything like that

---

### Post by rapattack1 on 2013-02-20
> **gordintoronto said:**
> A DVI to VGA adapter can be a source of problems.

Did you install the Nvidia driver?

What brand and model of video adapter and display?

Yes i had installed the nvidia driver before the change. Yeah i think i tried an adapter before and it didn't work. Different machine and card.
I was trying to find in UBuntustudio where it tells you the hardware and i can't find it. I can't remember what video card i have. Display? As in monitor? Or resolution?

---

### Post by gordintoronto on 2013-02-20
Open terminal and enter the command: lspci
One of the output lines will include "VGA", and that's your video adapter.

Yes, the brand and model of your monitor. If you run NVIDIA X Server Settings it should tell you, unless the DVI to VGA adapter is blocking the information. Oh, it will probably tell you about the video adapter as well.

---

### Post by fuorviatos on 2013-02-21
> **rapattack1 said:**
> Ummmmm can you give me more info as i don't know what that is....where is the option/setting? Never seen anything like that
Sure :) The video output is the way of indicating your video client the source to show the screen image.
On normal Ubuntu and Linux box it is usually set to "XV" as default, but let's assume you have 3rd acceleration enabled. In such case  by "going trough" XV, you won't be using acceleration from your video card to watch movies for example.

So, try these steps:

> **Qt Interface **

 
[LIST]
[*] Go to tools -> preferences (or press Ctrl+P)
[*] Select the Video tab
[*] Select another video output module by changing the "Output" combo-box
[*] Stop any playback
[*] Launch the playback again
[/LIST]


Personally, I'd go for something like "gl" or "gl2". There may be a specific output for nvidia as well,
so take it into consideration.

---

### Post by rapattack1 on 2013-02-22
> **gordintoronto said:**
> Open terminal and enter the command: lspci
One of the output lines will include "VGA", and that's your video adapter.

Yes, the brand and model of your monitor. If you run NVIDIA X Server Settings it should tell you, unless the DVI to VGA adapter is blocking the information. Oh, it will probably tell you about the video adapter as well.

```
lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GTS] (rev a1)

```
The monitor is also a TV. Its a Samsung LA22a450C1 ;)

---

### Post by fuorviatos on 2013-02-22
Have you tried the trick with the video ouput yet?

---

### Post by rapattack1 on 2013-02-22
> **fuorviatos said:**
> Sure :) The video output is the way of indicating your video client the source to show the screen image.
On normal Ubuntu and Linux box it is usually set to "XV" as default, but let's assume you have 3rd acceleration enabled. In such case  by "going trough" XV, you won't be using acceleration from your video card to watch movies for example.

So, try these steps:



Personally, I'd go for something like "gl" or "gl2". There may be a specific output for nvidia as well,
so take it into consideration.

Thanks so much. I chose gl ;)
So i should do the same in whatever other media player if i can. I like vlc the best anyway. Will make that the default player :0)

Hmmmmm can't seem to find where i set the default movie player and picture viewer. I can see where i set the internet stuff like brower and mail client though

---

