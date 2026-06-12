---
title: "Nvidia GTX 550 Ti: Installing non–open-source drivers"
date: 2014-11-30
forum: General Help
---

### Post by adriande2 on 2014-11-30
So, my motherboard has some power issues. One thing is that, unless I increase my graphics card's voltage, games that fully utilize my graphics card will crash after a bit.
In Windows, I simply use MSI Afterburner to easily turn up the GPU voltage. On Ubuntu, I couldn't find much in the way of information aside from overclocking options appearing after a certain Nvidia driver version; One such version that's past the open-source drivers that Ubuntu uses.
So, I'm a bit of a Linux newbie. I managed to install version 340.58 via the console but, after I restarted, Ubuntu would crash after the login screen. After an unsuccessful attempt at using the repair tool at startup, I reinstalled Ubuntu.

So, I obviously did something wrong. Can anyone tell me how I could successfully go about this. If not, are there any alternative overclocking solutions?
I'm using Ubuntu 14.10 with a GTX 550 Ti, if that helps.

---

### Post by pqwoerituytrueiwoq on 2014-12-04
just open software sources and go to the driver tab (last one) and install the desired nvidia driver version
you may also just run this command if you prefer
```
sudo apt-get install nvidia-331-updates
```
edit you will want the newest beta nvida driver from the xorg edgers ppa which supports overclocking (overvolting is done via command line w/ nvidia-settings)

you may want to hack your GPU bios and apply a higher voltage to it, either your PSU is a piece of junk or your card is defective
i have done that with a ASUS 550 TI/Galaxy 650 TI Boost, just to get higher clock speeds (need to be done from windows)

---

### Post by adriande2 on 2014-12-04
I don't know how to affect the BIOS on my card as I've never actually looked into it; I understand the risks of flashing something like this and the basic concepts to it but that's about it. Are there any guides that you'd consider helpful that you'd suggest?

Also, it is most likely my motherboard that's the issue. My card was once in another PC with no  problems there and this issue has persisted across a few PSUs as well, I doubt  a Corsair TX850 would have this trouble(it's overkill, I know, mistake  on my part back when I didn't know too much about PSUs and power  consumption). It seems likely since my motherboard has other power  issues besides this as I get quite a similar issue with USB hubs when they start using more power as well.

---

### Post by pqwoerituytrueiwoq on 2014-12-04
there are guides, i THINK i still have everything necessary for a 550 ti on another hdd
but you will need the fermi bios calculator and nibitor
[http://forums.guru3d.com/showthread.php?t=336117](http://forums.guru3d.com/showthread.php?t=336117)
when i sold my 550 TI i included a flash drive with everything needed for flashing (free dos boot) and moding
i think voltage/power via the motherboard and the 6pin are different settings

all you need to do is up hte voltage a little, should not be too hard
the software for my 650Ti boost is better, but not compatible with the 550 ti

sounds like your motherboard is giving your vdrop, make sure the contacts are clean for the gpu

---

### Post by adriande2 on 2014-12-05
Well, I can't find any still-active downloads for Fermi bios calculator.  Also, Fermi bios editor and NiBiTor won't fully work with my GPU BIOS  output by GPU-Z, Fermi bios editor won't read it at all and NiBiTor will  read it but will not give me proper options.

---

### Post by Yellow Pasque on 2014-12-05
You can do it without altering the VBIOS using the Nvidia 346 beta:
[http://www.phoronix.com/scan.php?page=news_item&px=MTg0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTg0MDI)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

Use at your own risk...

---

### Post by pqwoerituytrueiwoq on 2014-12-08
> **adriande2 said:**
> Well, I can't find any still-active downloads for Fermi bios calculator.  Also, Fermi bios editor and NiBiTor won't fully work with my GPU BIOS  output by GPU-Z, Fermi bios editor won't read it at all and NiBiTor will  read it but will not give me proper options.
I don't know about any copyrights on that software, so please delete this post/link if anyone has a problem with this
[http://s000.tinyupload.com/?file_id=78090494676314720705]("http://s000.tinyupload.com/index.php?file_id=78090494676314720705") (Size: ~15.25Mb aka 15,988,814 bytes)
Sum checks
```
md5sum /tmp/GPU_BIOS_EDITING.7z 
e61f0df035e09461fff92d3cdc5dd102  /tmp/GPU_BIOS_EDITING.7z
sha1sum /tmp/GPU_BIOS_EDITING.7z 
24bd5dedc30ebe207c58d37611a4e331e32b1e1c  /tmp/GPU_BIOS_EDITING.7z
```
Here is a list of the file contents
```
GPU_BIOS_EDITING
&#9500;&#9472;&#9472; EDITING
&#9474;   &#9500;&#9472;&#9472; FermibiosCalculator 1.0.0.4
&#9474;   &#9474;   &#9500;&#9472;&#9472; FermibiosCalculator 1.0.0.4.exe
&#9474;   &#9474;   &#9492;&#9472;&#9472; READ ME.txt
&#9474;   &#9500;&#9472;&#9472; FermibiosCalculator 1.0.0.4.exe
&#9474;   &#9500;&#9472;&#9472; FermiBiosEditor.zip
&#9474;   &#9500;&#9472;&#9472; guide.txt
&#9474;   &#9500;&#9472;&#9472; Kepler BIOS Tweaker v1.25.exe
&#9474;   &#9500;&#9472;&#9472; NiBiTor.v6.06
&#9474;   &#9474;   &#9500;&#9472;&#9472; NiBiTor.v6.06
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; nibitor64.sys
&#9474;   &#9474;   &#9474;   &#9500;&#9472;&#9472; NiBiTor.exe
&#9474;   &#9474;   &#9474;   &#9492;&#9472;&#9472; nibitor.sys
&#9474;   &#9474;   &#9500;&#9472;&#9472; NiBiTor.v6.06.exe
&#9474;   &#9474;   &#9492;&#9472;&#9472; NiBiTor.v6.06.txt
&#9474;   &#9492;&#9472;&#9472; NiBiTor.v6.06.zip
&#9492;&#9472;&#9472; FLASHING
    &#9500;&#9472;&#9472; nvflash_windows_5.142
    &#9474;   &#9500;&#9472;&#9472; bios.rom
    &#9474;   &#9500;&#9472;&#9472; GALEXY
    &#9474;   &#9474;   &#9500;&#9472;&#9472; 1097MHz.rom
    &#9474;   &#9474;   &#9500;&#9472;&#9472; 1110MHz.rom
    &#9474;   &#9474;   &#9492;&#9472;&#9472; STOCK.rom
    &#9474;   &#9500;&#9472;&#9472; nvflash.exe
    &#9474;   &#9500;&#9472;&#9472; nvflsh32.sys
    &#9474;   &#9500;&#9472;&#9472; nvflsh64.sys
    &#9474;   &#9492;&#9472;&#9472; save.rom
    &#9500;&#9472;&#9472; nvflash_windows_5.142.zip
    &#9500;&#9472;&#9472; USB flash tool for NVIDIA GPU's +Fermi BIOS guide
    &#9474;   &#9492;&#9472;&#9472; USB flash tool for NVIDIA GPU's +Fermi BIOS guide
    &#9474;       &#9500;&#9472;&#9472; FermiBiosEditor 1.55
    &#9474;       &#9474;   &#9492;&#9472;&#9472; FermiBiosEditor.exe
    &#9474;       &#9500;&#9472;&#9472; FERMI BIOS - NiBiToR - Fermi BIOS Editor guide.pdf
    &#9474;       &#9500;&#9472;&#9472; GUIDE Flashing GPU BIOS.pdf
    &#9474;       &#9500;&#9472;&#9472; HP USB Disk Storage Format Tool
    &#9474;       &#9474;   &#9492;&#9472;&#9472; SP27213.exe
    &#9474;       &#9500;&#9472;&#9472; NiBiTor.v6.03
    &#9474;       &#9474;   &#9500;&#9472;&#9472; nibitor64.sys
    &#9474;       &#9474;   &#9500;&#9472;&#9472; NiBiTor.exe
    &#9474;       &#9474;   &#9492;&#9472;&#9472; nibitor.sys
    &#9474;       &#9500;&#9472;&#9472; nvflash_5.100.0.1
    &#9474;       &#9474;   &#9500;&#9472;&#9472; CWSDPMI.EXE
    &#9474;       &#9474;   &#9500;&#9472;&#9472; nvflash.doc
    &#9474;       &#9474;   &#9492;&#9472;&#9472; nvflash.exe
    &#9474;       &#9500;&#9472;&#9472; THE ULTIMATE Fanspeed IC NiBiTor guide.pdf
    &#9474;       &#9492;&#9472;&#9472; USB image w7
    &#9474;           &#9500;&#9472;&#9472; AUTOEXEC.BAT
    &#9474;           &#9500;&#9472;&#9472; bootfix.bin
    &#9474;           &#9500;&#9472;&#9472; bootmgr
    &#9474;           &#9500;&#9472;&#9472; COMMAND.COM
    &#9474;           &#9500;&#9472;&#9472; CONFIG.SYS
    &#9474;           &#9500;&#9472;&#9472; DISPLAY.SYS
    &#9474;           &#9500;&#9472;&#9472; EGA2.CPI
    &#9474;           &#9500;&#9472;&#9472; EGA3.CPI
    &#9474;           &#9500;&#9472;&#9472; EGA.CPI
    &#9474;           &#9500;&#9472;&#9472; IO.SYS
    &#9474;           &#9500;&#9472;&#9472; KEYB.COM
    &#9474;           &#9500;&#9472;&#9472; KEYBOARD.SYS
    &#9474;           &#9500;&#9472;&#9472; KEYBRD2.SYS
    &#9474;           &#9500;&#9472;&#9472; KEYBRD3.SYS
    &#9474;           &#9500;&#9472;&#9472; KEYBRD4.SYS
    &#9474;           &#9500;&#9472;&#9472; MODE.COM
    &#9474;           &#9492;&#9472;&#9472; MSDOS.SYS
    &#9492;&#9472;&#9472; USB flash tool for NVIDIA GPU's +Fermi BIOS guide.rar

14 directories, 50 files
```

---

