---
title: "Graphic Problems"
date: 2012-10-26
forum: General Help
---

### Post by Sparrow40k on 2012-10-26
Hey every one, I'm Blake.
I'm new to Ubuntu - How new? I just installed Ubuntu 12.10 (64bit) on my PC but since installing it both my monitors were mirrored, to fix this was easy and in the display area of the control panel. But my problem now is when text is scrolling or pictures loading or anything I get these distorted broken weird looking lines and blockiness covering where the text was loading. Then I just scroll down and back up and it is fix. I'm not sure if this is a big problem or I am going to have to just ignore this. The other problem is both my monitors are running at 1440X900 when they are meant to be running at 1920X1080.

Any help would be awesome. I just installed Ubuntu trying for the first time and I’m not to happy so far...

---

### Post by Sparrow40k on 2012-10-26
I don't what just happened but I was on facebook then both of my screens went all black and then white text came up saying something like "GPU lockup" and had like channel1,2,3 trying to fix or something...

Sorry I am new to this and don't know anything Linux. I'm pretty advanced in Windows though lol

---

### Post by danielbauwens on 2012-10-26
Hello blake, Welcome :)

Can you tell me what for graphics card you have?

---

### Post by Sparrow40k on 2012-10-26
I found this, which I think explains most of my problem: [http://ubuntuforums.org/showthread.php?t=2076002](http://ubuntuforums.org/showthread.php?t=2076002)

My graphics card I was trying trying to find out before I had to restart because just now the computer froze. It is some sort of low profile card. My card has no brand, labels or anything on it because I got it from a friend but it looks similar to this one but with 2 fans;
[IMG]http://images.geeksimages.com/imageshare/G/300x300/GT320-PCIE-1024-2-PB-unit.jpg[/IMG]
I'll post again if I find out the actual card

---

### Post by Sparrow40k on 2012-10-26
I found it!! This is my card:  

GIGABYTE GeForce GT 430
[IMG]http://www.getprice.com.au/images/uploadimg/BimgGigabyte%20GeForce%20GT%20430%20GV-N430OC-1GL.jpg[/IMG]

---

### Post by danielbauwens on 2012-10-26
To find out what your graphics card is type this in your terminal:
```

lspci
lspci -v
lspci -v | grep -i vga
lspci -v | less

```

Look for "VGA compatible controller: xxxxxxxxxxxxxxxxxxxx"
The xxxxx indicates your graphics card.
To go out of the terminal, just type "q"

Daniel

EDIT: I checked your graphics card and it's powered by nvidia.
It's possible you need a driver for that.
Type in your terminal:
```
sudo apt-get install nvidia-current

```

---

### Post by dino99 on 2012-10-26
Please post , from a terminal, the output of:

```
sudo lshw -c  video
```

---

### Post by Sparrow40k on 2012-10-26
> **dino99 said:**
> Please post , from a terminal, the output of:

```
sudo lshw -c  video
```

I did it and got this

"
  *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 430]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e8000000-efffffff memory:e6000000-e7ffffff ioport:dc00(size=128) memory:fea00000-fea7ffff
"

---

### Post by danielbauwens on 2012-10-26
Did you install the driver?

---

### Post by dino99 on 2012-10-26
ok now we are sure about your card.

So you need either:
- xserver-xorg-video-nouveau  (generic video driver)
- nvidia-current

so use jockey-gtk to know if the video driver is used and activated:

```
sudo jockey-gtk
```

as it seems that actually "nouveau" is used, install also nvidia driver:

```
sudo apt-get install nvidia-current
```

now reboot

---

### Post by Sparrow40k on 2012-10-26
> **danielbauwens said:**
> Did you install the driver?

Just finished, it took a while because I had to download 200Mb for it. I'm guessing I should restart now?

---

### Post by dino99 on 2012-10-26
> **Sparrow40k said:**
> Just finished, it took a while because I had to download 200Mb for it. I'm guessing I should restart now?

Explained in previous post #10

---

### Post by danielbauwens on 2012-10-26
Yes you should reboot.
Thank you dino for explaining a big part :)

Daniel

---

### Post by Sparrow40k on 2012-10-26
Okay, now I have a much worse problem.
After rebooting everything was fine up to the login screen. I entered my password (all fine), but after it begins to login the cursor disappear and I am left with just a wallpaper and that is it with the other screen just black the whole time showing nothing. I have left it for ages and nothing happens. I am currently on my laptop because my computer is kinda unusable now...

EDIT

It's been about an hour and a have a cursor again.

---

### Post by Sparrow40k on 2012-10-27
I have just formatted my computer again back to start and it is like when I posted the first post. the glitzed images/text and all.

---

### Post by Sparrow40k on 2012-10-27
I just tried this code now:

```
sudo jockey-gtk
```

And I got the result: "sudo: jockey-gtk: command not found"

---

### Post by Sparrow40k on 2012-10-27
I just found this thread and before doing anything I wanted to see if it was the right thing to do. I kinda don't want to have to format again...

[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

---

### Post by Sparrow40k on 2012-10-27
bump

---

### Post by naelphin on 2012-10-27
The non-OS drivers don't work with 12.10 because xorg was upgraded to 1.13 and the amd/nv drivers don't support it. The beta versions may work off their webpages, but then you'll get scrolling corruption when you enable vsync.

You'll need to wait until Nvidia releases a new version of their driver before you can enable vsync, and live with the tearing.

---

