---
title: "Monitor settings in login manager"
date: 2021-02-22
forum: General Help
---

### Post by franekw on 2021-02-22
Hi,

The problem: Ubuntu detects the wrong primary screen.

The primary screen is a 32'' Samsung and the secondary monitor is 27'' Acer. In GRUB, everything is displayed correctly. Then Ubuntu detects Acer as the primary screen. While logged in, I have changed and saved display settings for the desktop, which Ubuntu remebers. However, login screen remains unchanged. I read a couple of posts, usually in AskBuntu, and all sources lead to the same routine:

```

sudo cp ~/.config/monitors.xml ~gdm/.config/monitors.xml
sudo chown gdm:gdm ~gdm/.config/monitors.xml

```

Additionally, a few sources suggest to turn off Wayland. As such, I am supposed to uncomment the line: `WaylandEnable=false`

I have done all of the above and the login settings remain the same. I cannot figure out what else to do in order for Ubuntu to correctly display screens during logging in. Please, can anybody help?

PS. I visited a number of websites but I tried to apply settings based on the those:

[https://askubuntu.com/questions/1255230/ubuntu-20-04-login-screen-doesnt-appear-on-the-primary-screen](https://askubuntu.com/questions/1255230/ubuntu-20-04-login-screen-doesnt-appear-on-the-primary-screen)

[https://askubuntu.com/questions/1195373/how-do-i-apply-settings-for-the-login-screen](https://askubuntu.com/questions/1195373/how-do-i-apply-settings-for-the-login-screen)

---

### Post by mIk3_08 on 2021-02-22
First I would like start with the hardware arrangement to know the order  of your video card output ports and what kind of output ports they are.  For my video card, I have Display Port then next is HDMI and the last  one is the DVI. I don't have the standard VGA port. Then I would like to  know which and where of the video card slot the monitor is plug-in.  What port of video card output is where your 32'' Samsung monitor  plug-in. and the second one is your 27'' Acer monitor where did you plug  it in, what port did you plug it in as I always consider the output  port of your video card. I first start with hardware because maybe we have both experience the same way of difficulty. If we haven't solve the situation then the next step will be the software and it is more complicated in most cases. I hope you get my point and my way of deliberations. The way I deliver my simplifications.

---

### Post by franekw on 2021-02-22
It's Nvidia GeForce 2080Ti OC with 4 outputs: 2 x HDMI, 1 Display Port and 1 USB-C. I installed Ubuntu 20.04 where the problem has started while did not have any issues on 18.04. Monitors are connected to both HDMI ports. This is what `xrandr` gives me:

```

Screen 0: minimum 8 x 8, current 9984 x 3456, maximum 32767 x 32767
HDMI-0 connected 3840x2160+6144+841 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  59.94    50.00  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       59.94    59.93  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 6144x3456+0+0 (normal left inverted right x axis y axis) 697mm x 392mm
   3840x2160     60.00*+  59.94    50.00    30.00    29.97    25.00    23.98    23.98  
   2560x1440     59.95  
   1920x1080     60.00    59.94    50.00    29.97    23.98  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
USB-C-0 disconnected (normal left inverted right x axis y axis)

``` 

This link [https://egpu.io/forums/gpu-monitor-peripherals/nvidia-geforce-rtx-2080-ti-usb-c-port/](https://egpu.io/forums/gpu-monitor-peripherals/nvidia-geforce-rtx-2080-ti-usb-c-port/) shows output configuration. I hope it is all what you have requested. Thanks.

---

### Post by mIk3_08 on 2021-02-23
> **franekw said:**
> It's Nvidia GeForce 2080Ti OC with 4 outputs: 2 x HDMI, 1 Display Port and 1 USB-C. I installed Ubuntu 20.04 where the problem has started while did not have any issues on 18.04. Monitors are connected to both HDMI ports. This is what `xrandr` gives me:

```

Screen 0: minimum 8 x 8, current 9984 x 3456, maximum 32767 x 32767
HDMI-0 connected 3840x2160+6144+841 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+  59.94    50.00  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       59.94    59.93  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 6144x3456+0+0 (normal left inverted right x axis y axis) 697mm x 392mm
   3840x2160     60.00*+  59.94    50.00    30.00    29.97    25.00    23.98    23.98  
   2560x1440     59.95  
   1920x1080     60.00    59.94    50.00    29.97    23.98  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
USB-C-0 disconnected (normal left inverted right x axis y axis)

``` 

This link [https://egpu.io/forums/gpu-monitor-peripherals/nvidia-geforce-rtx-2080-ti-usb-c-port/](https://egpu.io/forums/gpu-monitor-peripherals/nvidia-geforce-rtx-2080-ti-usb-c-port/) shows output configuration. I hope it is all what you have requested. Thanks.



as the link you have given; I assume this is your video card...  

[ATTACH=CONFIG]288000[/ATTACH]

And as what you have said below;

> **franekw said:**
>  Monitors are connected to both HDMI ports? 

How come that you are using two hdmi port where you only have one hdmi video output port. as what I saw in the image you send via link, are you using hub/ or any video output splitter? if so, I think it won't work that way.
can you post an original image of your video card here with all the output port same as the image above; 
I'm asking the image of your video card because I'm so confused. 
Can you post it to this thread?

---

### Post by franekw on 2021-02-25
> **mIk3_08 said:**
> I'm asking the image of your video card because I'm so confused. 
Can you post it to this thread?

Sorry about it. That was the wrong link with the wrong picture. I am definitely not using any splitter!

Here is the proper full name of my video card `Asus GeForce RTX 2080 Ti 11 GB STRIX GAMING OC Video Card`, with the link to it:
[https://rog.asus.com/us/graphics-cards/graphics-cards/rog-strix/rog-strix-rtx2080ti-o11g-gaming-model/](https://rog.asus.com/us/graphics-cards/graphics-cards/rog-strix/rog-strix-rtx2080ti-o11g-gaming-model/)

In the gallery, one of the images shows a layout of the back panel of the card, which is exactly the layout of my card. There you can see the video card has multiple output ports, two of which are HDMI which are in use, and which monitors are connected to.

---

### Post by mIk3_08 on 2021-02-25
Did you try to interchange the two connected male hdmi plug connection of your two monitors? 
Your primary monitor and the your secondary monitor.
Try  to connect your primary monitor which is 32'' Samsung where your 27''  Acer secondary monitor is connected and your 27'' Acer monitor will be  connected to hdmi port where your primary is connected.
Try to  interchange the two hdmi connected monitors the primary monitor will be  on labeled "A" and the secondary will be on labeled "B" then boot your  machine. If it is already its place try vice versa then boot machine.
see image below;

[ATTACH=CONFIG]288009[/ATTACH]

---

### Post by franekw on 2021-02-25
> **mIk3_08 said:**
> Did you try to interchange the two connected male hdmi plug connection of your two monitors? 


Yes, I did; while this could work, everything else will change: UEFI, login screen in Windows 10, another linux distribution, etc. I was hoping for another solution to this problem. Besides, what I found on the internet worked in Ubuntu 18.04 LTS.

---

### Post by mIk3_08 on 2021-02-26
How about using your dp port.  Can you use dp port as a primary for your primary monitor? dp port is best for multi monitors. (Eyefinity) just leave the secondary monitor on hdmi only the primary. Have you tested it on the first DP port one, see image below;

[ATTACH=CONFIG]288010[/ATTACH]


Try to use the DP port. In my case I use the DP as my primary.
But I use Ubuntu 18.04 O.S. I want to use a hub on my dp port but I don't have a budget yet. Maybe next time I will.
My triple monitor machine works very smoothly with my Ubuntu 18.04 O.S.
see image of my port connection below;


[ATTACH=CONFIG]288011[/ATTACH]

---

### Post by mIk3_08 on 2021-03-04
Hello, how are you? just want to show you my triple monitor machine using Ubuntu 18.04. And this is my login view,
see images below;

[URL="https://imgur.com/i0f1hZF"][IMG]http://i.imgur.com/i0f1hZFl.jpg[/IMG]

[/URL][IMG]http://i.imgur.com/xGsPPrpl.jpg[/IMG]

And here is my desktop with wide wallpaper: 
see image below;

[[IMG]http://i.imgur.com/BKlDcXNl.png[/IMG]]("https://imgur.com/BKlDcXN")


And here is my desktop running with web browser:

[[IMG]http://i.imgur.com/T23QLlBl.png[/IMG]]("https://imgur.com/T23QLlB")

---

