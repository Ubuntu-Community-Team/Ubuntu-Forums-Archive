---
title: "hp pavilion dv6 graphics card -- making it work"
date: 2014-01-09
forum: General Help
---

### Post by merockstar on 2014-01-09
Ubuntu is a dream come to true to me as far as I'm concerned. I love how slick it is, and the UI.

But I'm weird. I MUST feel like I'm doing everything as optimally as possible, or it just drives me nuts.

Last night I tried to set up cgminer so I could mine me some coinyewest.

This made me aware that my graphics card isn't being detected properly.

In several concerted efforts to make this work, I've managed to break 2 different installation attempts today. Installing for a third time in 24 hours as I type this.

So even though I've pretty much given up on mining coinyewest, I'd like to be able to get in on the launch of other p & d coins as they come out. Not to mention, I'd just like to feel like all my hardware is working.

So my computer is an HP Pavilion DV6 (cant figure out the exact model, sticker on bottom doesnt seem to have it).

lspci | grep vga informs me that the graphics card is an AMD Radeon HD 4200 series (I think it's an integrated graphics chipset, which means its supposed to be able to swtich back and forth between a lighter card and a real card, but I haven't figured out anyway to verify this, i've tried tutorials for both assumptions already though, pretty sure its one of those swtichy versions).

The last tutorial I was looking at, that I haven't tried yet, suggests using an older version of AMDs catalyst drivers (12.6, when the newest is 13.1). So I'm probably going to try that now (after install finishes).

I was just wondering if anybody else has a computer like mine and has been in my position? what worked for you? im trying to use 12.04 because upgrading is a pain, id rather just run an os for four years.

3D seems to work after a base install in spite of miners not working, so I think whats happening is its defaulting to the discrete one, and outright ignoring the other (which is why ive been able to run ubuntu all this time without really noticing)

anyways... install finished, need to restart computer and update (again).

hope somebody can shed some light on this...

---

### Post by QIII on 2014-01-09
Hello!

What version of Ubuntu are you running?

---

### Post by merockstar on 2014-01-09
Wow what a quick response!

I'm using 12.04

---

### Post by QIII on 2014-01-09
Which version of 12.04?  ;)

With 12.04 and 12.04.1 you are OK with that card.  

Also, is that the only GPU or does it have an integrated Intel graphics unit?

---

### Post by merockstar on 2014-01-09
ooooh... i always run the updater to the fullest, i believe its 12.04.3 -- although I just did a completely fresh install (that im probably about to break again lol) also i believe there is an integrated intel graphics unit

---

### Post by merockstar on 2014-01-09
alrighty...

every single tutorial on this matter I have attempted to follow has resulted in me getting a blank screen when I go to reboot my computer (and the only way I know to fix it is to outright reinstall the whole OS... this is the fourth time ive done it now).

5 bucks worth of btc to the person who helps me to get this to work... (you know its gonna be worth like 5 grand in a few years...)

---

### Post by merockstar on 2014-01-09
> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12


Thats the error i get from fglrxinfo when trying this tutorial: [http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200)

google it, pick ANY tutorial on the subject, post it, and i can post the error i got.

---

### Post by merockstar on 2014-01-09
it seems this is actually supported now...

found this :[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

also found [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

wondering which would be the better tutorial to follow now... the later is more current by about a month...

but it suggests using "fglrx-experimental-13" instead of just fglrx like the first one does.

I'm wondering, what is the difference?

If i use the experimental one, that means when a new one comes out I'd have to uninstall it and install the next iteration, right?

also the later tutorial recommends installing raring first.

can anyone clarify this for me??? I think i'm close to an answer here... (btw the 5 dollars in bitcoin offer is revoked if this ends up being the solution, since i spent all night digging it up myself :P   )

---

### Post by Mark Phelps on 2014-01-09
Supporting Hybrid Graphics is a very different situation from supporting "legacy" AMD video chipsets.  

AMD dropped Linux support for the HD 2x/3x/4x-series chipsets last summer.  The now-called "legacy" drivers are incompatible with the X-server version that came out starting with Ubuntu 12.04.2.  Just checked on the AMD drivers page and even though it shows supporting Ubuntu 13.10, it still clearly states >  to Xserver 1.12  -- which rules out any Ubuntu version newer than 12.04.1.

Sorry, but you're relegated to the default Radeon drivers for newer Ubuntu versions.

---

### Post by mastablasta on 2014-01-09
it seems to me the method is using repositories. and from what i understand when repository is updated, you pull down the updates as well.

---

### Post by merockstar on 2014-01-09
> **Mark Phelps said:**
> Supporting Hybrid Graphics is a very different situation from supporting "legacy" AMD video chipsets.  

AMD dropped Linux support for the HD 2x/3x/4x-series chipsets last summer.  The now-called "legacy" drivers are incompatible with the X-server version that came out starting with Ubuntu 12.04.2.  Just checked on the AMD drivers page and even though it shows supporting Ubuntu 13.10, it still clearly states  -- which rules out any Ubuntu version newer than 12.04.1.

Sorry, but you're relegated to the default Radeon drivers for newer Ubuntu versions.

So... if I keep using this version of Ubuntu, I don't get to use my (non integrated) video card no matter what because AMD won't support my operating system?

and my ONLY option is to downgrade and force mysel not to hit the "install updates" button? or switch to windows if I want to mine a pump and dump coin on launch (which is about the only time a computer like mine would have any chance of making anything) or play a game?

There is absolutely no way I can make this work with a current Ubuntu version??

---

### Post by SeijiSensei on 2014-01-09
The solution is to disable the Intel card in the BIOS.  I had to do this for a DV6 with a 6770M chip: [http://ubuntuforums.org/showthread.php?t=2117118&p=12685455#post12685455](http://ubuntuforums.org/showthread.php?t=2117118&p=12685455#post12685455)

---

### Post by merockstar on 2014-01-09
SeijiSensei -- that sounds promising. im gonna give this a shot soon. post or pm a btc address to claim my five dollar offer earlier in case this works out, if you want.

---

### Post by Yellow Pasque on 2014-01-09
Hold on a minute...

1. What model DV6 do you have?

2. Please show output of lspci so we actually know what GPU(s) you have:
```
sudo update-pciids
lspci
```

---

### Post by merockstar on 2014-01-09
> **Temüjin said:**
> Hold on a minute...

1. What model DV6 do you have?

2. Please show output of lspci so we actually know what GPU(s) you have:
```
sudo update-pciids
lspci
```

you got it.

```
Downloaded daily snapshot dated 2014-01-09 03:15:01
merockstar@merockstar-HP-Pavilion-dv6-Notebook-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250]
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)

```

As for not having much time to be on here, well, if nothing else, I appreciate you just telling me what to post so people can help me :)

no worries. sorry if i come across as impatient in this thread.

as for what model dv6... ive been trying to figure that out... i have no idea <_< doesnt seem to be on the sticker on the computer itself

---

### Post by Yellow Pasque on 2014-01-10
Okay, so we are not dealing with hybrid or Intel graphics. There is only the 4250. You have two options:

1. Run the open-source driver as is (works out of box)
2. Install Ubuntu 12.04.1 and then install Catalyst legacy driver

---

### Post by merockstar on 2014-01-11
> **Temüjin said:**
> Okay, so we are not dealing with hybrid or Intel graphics. There is only the 4250. You have two options:

1. Run the open-source driver as is (works out of box)
2. Install Ubuntu 12.04.1 and then install Catalyst legacy driver

Oooooh I was completely mistaken then.

The open source drivers have been running fine for me, until I tried to mine coinyewest with it. Wonder why cgminer not picking it up.

---

### Post by QIII on 2014-01-11
Your mining software may depend on features not available in the open source driver.  The open source driver simply does not have everything the proprietary driver does because there is no way for the open source developers to use everything without having the full specifications of the hardware, which ATI does not publish.  

If your mining app requires features specific to the proprietary driver, then the option to install <= 12.04.1 and the proprietary driver is what you need.

I generally tell people to just use the open source driver unless they have a specific need for the proprietary one.  Yours may be just such a case.

---

### Post by merockstar on 2014-01-11
> **QIII said:**
> Your mining software may depend on features not available in the open source driver.  The open source driver simply does not have everything the proprietary driver does because there is no way for the open source developers to use everything without having the full specifications of the hardware, which ATI does not publish.  

If your mining app requires features specific to the proprietary driver, then the option to install <= 12.04.1 and the proprietary driver is what you need.

I generally tell people to just use the open source driver unless they have a specific need for the proprietary one.  Yours may be just such a case.

I appreciate your insight.

The issue I have with downgrading my linux version version is that I also keep crypto on the same machine, making security imperative.

I probably should have a seperate computer just for mining, but I sold most of my btc before the rise (like an idiot), so I figure if I was to get into mining at all, my only shot would be to mine coins as they're just released, then sell them when I think they're at their peak (what I tried to do with coinye).

How much of a security concern would it be if I were to downgrade?

Would I have to stare at all the new possible updates stacking up, while restraining myself from hitting the update button, or is there some way to tell ubuntu that I intentionally don't want to upgrade?

---

### Post by Yellow Pasque on 2014-01-11
If using 12.04.1, you wouldn't have security concerns since the only older components you're using are kernels/Xservers, which are patched for security issues.

---

### Post by merockstar on 2014-01-12
> **Temüjin said:**
> If using 12.04.1, you wouldn't have security concerns since the only older components you're using are kernels/Xservers, which are patched for security issues.

you've been incredibly helpful. thank you.

I appreciate all the comments in this thread.

---

