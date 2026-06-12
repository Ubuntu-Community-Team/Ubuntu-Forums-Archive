---
title: "Monitor flickers"
date: 2015-11-08
forum: General Help
---

### Post by Joaquint on 2015-11-08
Hello! Recently I installed linux on a laptop and this weird graphic glitch occurs, where the screen flickers a bit and some noise bars appear and disappear. Microsoft Windows works fine.    


I don't know what causes this. I've already tried installing drivers, messing with compiz and xrandr (even broke xorg once!). I tried other linux distros (so far Fedora, CentOS 7, Ubuntu and Elementary). it happens on all of them. Also, if I press CTRL+ALT+F2 to show up the console, it still happens. Some websites cause it more than others. 

Also, when booting on safe graphic version, it doesn't happen (but my resolution is limited to 800x600). I think it must be xorg.


Ubuntu version is 14.04. System specs are:      

[INDENT]4GB RAM, i5-5200 @ 2.2 x4, Intel HD 5500 (Broadwell GT2)[/INDENT]




Here is the output of lspci:    




    ```
 00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)  
     00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)  
     00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)  
     00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)  
     00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)  
     00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)  
     00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)   
     00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)  
     00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)   
      00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)  
      00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)   
     00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)   
    00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)   
    02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)   
    03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)   



```Here is the output of xrandr:   
```


    Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767    
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 293mm x 165mm  
1920x1080      60.0*+   59.9     40.0    
1680x1050      60.0     59.9   
1600x1024      60.2  
1400x1050      60.0   
1280x1024      60.0  
1440x900       59.9  
1280x960       60.0  
1360x768       59.8     60.0  
1152x864       60.0  
1024x768       60.0  
800x600        60.3     56.2  
640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


```

I've tried [this]("http://askubuntu.com/questions/469701/weird-partial-screen-flickering-after-upgrade-to-14-04") and [this]("http://(http://askubuntu.com/questions/584212/how-to-resolve-screen-flickering-on-ubuntu-14-04-lts-and-dell-inspiron-15-7000-s") along with a few other workarounds.

Here's a video:  

[https://www.youtube.com/watch?v=PH5AyMFkttk]("http://https://www.youtube.com/watch?v=PH5AyMFkttk")

Pretty obscure but laptop is Bangho Zero G05-i518.


Thank you very much!

---

