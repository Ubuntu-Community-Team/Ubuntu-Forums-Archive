---
title: "Want to enable TTY on ctrl+alt+Fn keys"
date: 2023-07-28
forum: General Help
---

### Post by computer_freak_8 on 2023-07-28
I'm trying to figure out how to enable the [Ctrl] + [Alt] + [F(n)] TTYs on Ubuntu.

I've been using Ubuntu as my primary OS since circa 2008 and have become pretty self-sufficient with finding things along the way - be it posts on Stack Exchange, AskUbuntu, or various Arch documentation - but I can't seem to find the right terms to find what I need now.

Here are my current specs that may be relevant:
Ubuntu 23.04 (dist-upgraded a couple times from 22.04 which was a clean install)
MSI PRO X670-P WIFI motherboard
AMD Ryzen 9 7900X CPU
MSI RTX 4090 GPU
Proprietary driver installed via "Additional Drivers" GUI (nvidia-driver-535)

Currently, this is what happens when I hit [Ctrl] + [Alt] + [F(n)] keys:
[Ctrl] + [Alt] + [F1] = takes me to login screen
[Ctrl] + [Alt] + [F2] = my active desktop; however I left it, locked or unlocked, all programs running
[Ctrl] + [Alt] + [F3] through [Ctrl] + [Alt] + [F12] = some terminal output messages of some sort.
I cannot interact with the screen on the F3-F12 screens. I hit [Enter], [Esc], [Ctrl] + [c], etc... nothing happens.
It looks something like this:

```
[    1.188825] hub 10-0:1.0: config failed, hub doesn't have any ports! (err -19
)
/dev/nvme0n1p2: clean, 489491/60989440 files, 16656040/24394240 blocks
[    7.842083]
[    8.185403] snd_hda_intel 0000:17:00.6: no codecs found!
_

```

How do I get my [Ctrl] + [Alt] + [F(n)] keys to give me login prompts like I'm used to?

---

### Post by MAFoElffen on 2023-07-29
It would really help if we knew what hardware you have, what versio of Ubuntu and which kernel... A lot of that would be answered if you ran the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and posted the URL of where the reports gets uploaded to a pastebin. Also, the mode in vttyX console sessions is closely tied to Grub2 and what Grub itself see's, so if you could get to a Grub Menu > Press key <C> to get to a Grub CLI prompt and type 
```

videoinfo

```
Then take a picture of that output with your phone and post it as an attachment to your post.

---

### Post by computer_freak_8 on 2023-08-02
> **MAFoElffen said:**
> It would really help if we knew what hardware you have, what versio of Ubuntu and which kernel
I did list most of my hardware (all the usual suspects, CPU/GPU/Mobo) as well as my Ubuntu version (23.04).
```
$ uname -a
Linux h7flow 6.2.0-26-generic #26-Ubuntu SMP PREEMPT_DYNAMIC Mon Jul 10 23:39:54 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```
Regardless, attached is sanitized output from the script you provided. I will see if I can capture the grub and either post a picture or recreate in plaintext as I did with the OP.
Thank you.

---

### Post by computer_freak_8 on 2023-08-02
Here's the "videoinfo" parts:
first attempt:

```
grub> videoinfo
error: Secure Boot forbids loading module from (hd1,gpt2)/boot/grub/x86_64-efi/videoinfo.mod.
grub>
```

after disabling Secure Boot:
```
grub> videoinfo
List of supported video modes:
Legend: mask/position=red/green/blue/reserved
Adapter `Bochs PCI Video Driver':
  No info available
Adapter `Cirrus CLGD 5446 PCI Video Driver':
  No info available
Adapter `EFI GOP driver':
  0x000 3840 x 2160 x 32 (15360)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x001  640 x  480 x 32 (2560)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x002  800 x  600 x 32 (3200)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
* 0x003 1024 x  768 x 32 (4096)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x004 1280 x  720 x 32 (5210)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x005 1280 x  800 x 32 (5210)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x006 1280 x 1024 x 32 (5210)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x007 1366 x  768 x 32 (5464)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x008 1440 x  900 x 32 (5760)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x009 1400 x 1050 x 32 (5600)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x00a 1600 x 1200 x 32 (6400)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x00b 1680 x 1050 x 32 (6720)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x00c 1920 x 1080 x 32 (7680)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x00d 1920 x 1200 x 32 (7680)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  0x00e 2048 x 1536 x 32 (8192)  Direct color, mask: 8/8/8/8  pos: 16/8/0/24
  EDID version: 1.4
    Preferred mode: 3840x2160
grub>
```

---

### Post by MAFoElffen on 2023-08-02
Looking over both right now... Very nice & very new hardware.

Okay... I see both nvidia and amdgpu loaded... on an MSI Pro X670-P WiFi board, running Gnome on X11.

Let's see what you have the desktop set at the moment:
```

xdpyinfo | grep -e 'name of display' -e 'dimensions'

```

---

### Post by MAFoElffen on 2023-08-02
As a test, while at the Grub2 Boot Menu...

Press the <E> key. <Arrow-Down to the line that starts with the word "linux". <Arrow-Right> until you get to the words "quiet splash" Delete the word "quiet" and replace with "---" (3 dashes). <Arrow-Right until after "splash"...

Add a <Space> after the word "splash, then type in the text "radeon.modeset=0 amdgpu.modeset=0 video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank " (without the quotes). Then press <Cntrl><X>. See if it boots and test.

If that works, then edit (with privileges) file /etc/default/grub, line that starts with "GRUB_CMDLINE_LINUX_DEFAULT" with the same edits. Like this:
```

GRUB_CMDLINE_LINUX_DEFAULT="--- splash radeon.modeset=0 amdgpu.modeset=0 video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"

```
Then go down more in that file to where "GRUB_GFXMODE" is located and change it to this"
```

GRUB_GFXMODE=1920x1080x32

```
Then save it, and do
```

sudo update-grub

```

---

### Post by computer_freak_8 on 2023-08-03
> **MAFoElffen said:**
> Looking over both right now... Very nice & very new hardware.

Okay... I see both nvidia and amdgpu loaded... on an MSI Pro X670-P WiFi board, running Gnome on X11.

Let's see what you have the desktop set at the moment:
```

xdpyinfo | grep -e 'name of display' -e 'dimensions'

```

```
name of display:    :1
  dimensions:    3840x2160 pixels (602x341 millimeters)
```

I built my last computer 10 years ago so if this one lasts another 10... I figure it's money well spent.
Ahh good catch on both drivers loaded! The AMD stuff has Radeon built-in, but I'm not using it. I may also try (just as a test) to use the Radeon instead of the Nvidia GPU to see if that gives TTYs.
I thought Ubuntu ran Wayland by default for the past few releases? I haven't done anything to intentionally switch to X11 but perhaps the "Additional Drivers" dialog did so when installing the Nvidia driver.
I will fiddle with the Grub stuff, including both what you provided (FHD) and forcing 4k (3840x2160@60Hz) to see if either will make a difference.

---

### Post by computer_freak_8 on 2023-08-06
> **computer_freak_8 said:**
> 
I will fiddle with the Grub stuff, including both what you provided (FHD) and forcing 4k (3840x2160@60Hz) to see if either will make a difference.
No dice so far. Only change I'm noticing is this moves my "active desktop" to F7 instead of F2, and F2 is now the same output as mentioned in OP, minus the snd_hda_intel part.

---

