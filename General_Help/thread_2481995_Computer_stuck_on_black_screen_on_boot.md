---
title: "Computer stuck on black screen on boot"
date: 2022-12-15
forum: General Help
---

### Post by paulionel on 2022-12-15
Hello, 


I run a dual boot system with windows and Ubuntu. I set this up a couple of years ago and it has been running great. A couple of weeks ago I upgraded from a Nvidia GTX 750-Ti to a Nvidia RTX 3070. Since this upgrade I haven't used the Ubuntu side of my system until I tried yesterday. I used the grub loader as usual, but after selecting Ubuntu, it gets stuck on a black screen with a cursor blinking in the top left corner. I suspect that the upgrade from the 750-Ti to the 3070 is what's causing this, but I'm really not sure, and I'm not sure how to solve this.


I tried following the suggestion in this post:
[https://askubuntu.com/a/111298](https://askubuntu.com/a/111298)
It suggested that I "replace quiet splash with no splash or nomodeset". I tried both. "no splash" results in the same black screen. "nomodeset" results in the following picture:
[IMG]https://imgur.com/a/q5g7Bwv[/IMG]
(I couldn't figure out to actually attach the picture so there is a link)
[https://imgur.com/a/q5g7Bwv](https://imgur.com/a/q5g7Bwv)

Here is the text if you don't want to click the link:
"
         Starting RealtimeKit Scheduling Policy Service...
[ OK ]Starting RealtimeKit Scheduling Policy Service.
         Starting Daemon for power management...
[ OK ]Started Snap Daemon.
                                            Starting Wait until snapd is fully seeded...
                                                       Starting Time & Date Service...
                                                                      [ OK ] Started Time & Date Service.
                                                                                 [ OK ] Finished Wait until snapd is fully seeded.
                                                                                            [ OK ] Started Daemon for po
wer management.
"

I also tried a suggestion from this post:
[https://askubuntu.com/a/162087](https://askubuntu.com/a/162087)
It suggested Boot-Repair. So I followed this link:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I created a live usb of boot-repair and clicked on "Recommended repair**"**. I tried rebooting, but I still had the same problem. This is my pastebin from the boot repair:
[https://pastebin.ubuntu.com/p/s7t3wCdvPZ/](https://pastebin.ubuntu.com/p/s7t3wCdvPZ/)

Finally, I tried just booting Ubuntu from a live USB. I was able to successfully boot into Ubuntu, but the screen was a very bright yellow and I couldn't see anything.


Here's my Hardware:
AMD - Ryzen 7 5800x 4th Gen 8-Core, 16-threads
ASUS - TUF GAMING X570-PLUS (WI-FI) (Socket AM4) USB-C Gen2 AMD Motherboard with LED Lighting
G.SKILL Ripjaws V Series 32GB (2 x 16GB) 288-Pin DDR4 SDRAM DDR4 3200 (PC4 25600) Desktop Memory Model F4-3200C16D-32GVK
Seagate BarraCuda ST2000DM008 2TB 7200 RPM 256MB Cache SATA 6.0Gb/s 3.5" Hard Drive Bare Drive
SAMSUNG 970 EVO M.2 2280 1TB PCIe Gen3. X4, NVMe 1.3 64L V-NAND 3-bit MLC Internal Solid State Drive (SSD) MZ-V7E1T0BW
EVGA GeForce RTX 3070 FTW3 ULTRA GAMING, 08G-P5-3767-RL, 8GB GDDR6, iCX3 Technology, ARGB LED, Metal Backplate, LHR

Thanks in advance for any and all help. If you need any more info from me just let me know.
[COLOR=#FFFFFF][FONT=&amp]https://imgur.com/EsuhO1z[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-12-15
I'll help... I also do NVidia and have supported the Linux Graphics layer since about 2005. LOL My guess is that you need to reload a different graphics driver for your newer NVidia Card.

Have you looked [here]("https://ubuntuforums.org/showthread.php?t=1743535") in the first post of my sticky? About halfway down that post, it has what you already tried, by removing "quiet splash" and replacing with "--- nomodeset". I know the "---" might sound silly and unimportant, but some systems will ignore boot parameters unless they are after those characters. Do'n ask me why or how, but it seems to help on some systems.

If that doesn't work, then remove "quiet splash vt.handoff=7" and replace with " --- 3". What that will do is boot to text console rcmode 3 (multi-user).

From there, login, then
```

sudo ubuntu-drivers devices

```
Check to see that the program 'ubuntu-drivers' is installed, that it ID'es your GPU correctly and shows recommended video drivers for it. If so, then:
```

sudo ubuntu-drivers autoinstall

```
If 'ubuntu-drivers is missing, then install via
```

sudo apt install --yes ubuntu-drivers-extra

```

---

