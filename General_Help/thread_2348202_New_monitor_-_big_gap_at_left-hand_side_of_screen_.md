---
title: "New monitor - big gap at left-hand side of screen for Lubuntu"
date: 2017-01-01
forum: General Help
---

### Post by DrDvorak on 2017-01-01
In my home 'office', I have 2 desktop PCs. One is a designated 'work' machine, a PC purchased last year with Windows 10 that I added Ubuntu to as a dual-operating system machine. Display output is HDMI. The other PC is an old Dell Dimension running Lubuntu that is for 'personal' use such as personal e-mail, downloading bills and running MoneyManagerEx, etc. Display output is VGA. My single mouse and keyboard are plugged into a USB hub. With this setup I can easily switch between 2 machines, just by changing Source on the single monitor (well, HDMI TV) and switching which USB cable (from the two PCs) that the USB hub is plugged into. I wanted to have a clear separation of work and personal use machines, so that I could set off some long processing (like analysing chess games or downloading and uploading podcasts to my Google Music), and then get some work done on the work machine while the non-work processing chugged away. This is a reason why I went for a 2-machine setup rather than just using separate accounts on 1 PC. I didn't want to do everything under one account either, as I didn't like the idea of customers seeing that chess software, games etc. were installed, when sharing my desktop with them, and I wanted separate Dropbox storage for work and personal files.

This setup worked well for me until I was forced to replace the monitor which was damaged in a household accident. Instead of a like-for-like replacement, I got a good deal on a 24 inch Seiki Smart TV which had VGA and HDMI inputs, to give me a bigger monitor than I had before, which I can also use as a spare telly if I want to watch something different from the Mrs.

On the work machine, both Ubuntu and Windows 10 work fine with the new monitor - they just seemed to detect the screen size and fill it. On the Lubuntu personal machine, the screen is readable, but there is 2-inch black gap at the left-hand side of the screen - I cannot move the mouse pointer into that area. So, some of the screen space is 'wasted', which is a bit naff. The annoying thing is that Ubuntu 'just worked', whereas it seems some kind of manual intervention is needed to make the best use of the screen with Lubuntu. Does anyone know how to do this?

---

### Post by Impavidus on 2017-01-02
The main difference seems to be that one computer uses a HDMI cable, the other VGA. My experience with VGA (which uses a classic analogue cable) is that you often have to experiment a bit with the monitor settings to get things right, in your case adjusting the phase of the horizontal synchronisation. The monitor should have a setting to move or stretch/compress the image on screen.

---

### Post by DrDvorak on 2017-01-03
I have just done 2 more experiments:

1. Windows 7 laptop plugged into the new TV: TV screen filled automatically with no issues.
2. Lubuntu netbook plugged into the new TV: TV screen filled automatically.

So this does not seem to be a VGA issue or that Lubuntu is not compatible with this TV: it's that the Lubuntu desktop needs some sort of manual intervention (unlike my Lubuntu netbook, which 'just worked by itself' for this TV).

---

### Post by DrDvorak on 2017-01-03
**Jere is the output from Ubuntu on the Medion Akoya 'work PC', which is filling all of the screen without any manual intervention having been required along the way:**

paul@office-ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 1366mm x 768mm
    1366x768      59.79*+
    1920x1080     60.00    50.00    59.94    30.00    25.00 24.00    29.97    23.98
    1920x1080i    60.00    50.00    59.94
    1280x960      60.00
    1280x800      59.91
    1152x864      59.97
    1280x768      59.87
    1280x720      60.00    50.00    59.94
    1024x768      60.00
    800x600       60.32
    720x576       50.00
    720x576i      50.00
    720x480       60.00    59.94
    720x480i      60.00    59.94
    640x480       60.00    59.94
    720x400       70.08
paul@office-ubuntu:~$
**The 1366x768 resolution that fills the screen on the work machine is just not available on the personal use machine:**

paul@dell-dimension:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DVI-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
DIN disconnected (normal left inverted right x axis y axis)
DVI-1 disconnected (normal left inverted right x axis y axis)

**I am vaguely aware of gtf and xrandr, and have used them in the past to successfully address slightly different types of screen resolution problems:**



paul@dell-dimension:~$ gtf 1366 768 59.79


  # 1368x768 @ 59.79 Hz (GTF) hsync: 47.53 kHz; pclk: 85.56 MHz
  Modeline "1368x768_59.79"  85.56  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync


paul@dell-dimension:~$ 


**It's interesting that I entered 1366 as input, but got the very slightly different 1368 in the output. Anyhow, I used the output to create a mode line, add it, and switch to it:**


xrandr --newmode "1368x768_59.79"  85.56  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
xrandr --addmode DVI-0 1368x768_59.79
xrandr --output DVI-0 --mode 1368x768_59.79
[B]
This did change the screen resolution - but only within the non-black area. The black gap at the left-hand side of the screen remained in place, unaffected, suggesting that the answer to this might lie outside of gtf/xrandr?

As mentioned above, it was strange how I entered 1366 and got 1368 back. To eliminate that variable, I did a find and replace on the xrandr commands to set it to 1366, consistent with the exact value seen on the computers that aren't affected by the black gap problem. The Dell Dimension accepted the commands as valid, but they did nothing to address the black gap.[/B]


xrandr --newmode "1366x768_59.79"  85.56  1366 1440 1584 1800  768 769 772 795  -HSync +Vsync
xrandr --addmode DVI-0 1366x768_59.79
xrandr --output DVI-0 --mode 1366x768_59.79

---

