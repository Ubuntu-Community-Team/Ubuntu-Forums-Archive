---
title: "Screen Resolution and Bluetooth mouse problems"
date: 2007-09-02
forum: General Help
---

### Post by Jriske on 2007-09-02
I have decided to switch to Ubuntu from using Arch/Fedora/Debian and everything has been going good so far except for two details. I can not get X to use my screen resolution of 1920x1200 for my Dell 2405fpw monitor, nor can I get my MX900 bluetooth mouse to work.


For my monitor, it's the Dell 2405fpw 24 inch widescreen monitor. Link here: [http://www.dell.com/content/products/productdetails.aspx/monitor_2405fpw?c=us&cs=22&l=en&s=dfh](http://www.dell.com/content/products/productdetails.aspx/monitor_2405fpw?c=us&cs=22&l=en&s=dfh)

Horizontal scan range	
30 kHz to 81 kHz (automatic)

Vertical scan range	
56 Hz to 76 Hz, exception 1680 x 1200 & 1920 x 1200 at 60 Hz only

When I edit xorg.conf to have 1920x1200 screen resolution and then restart X it works fine. After I reboot my computer or X again it says "Out of power range, cannot display this video mode. Switch to 1920x1200 at 60hz"


My second problem is I am unable to use my Logitech MX900 bluetooth mouse with Ubuntu, it's been auto detected fine with other distros, but not with Ubuntu.


I am not using Linux right now, when I switch over I will post my xorg.conf file.

---

### Post by Brandon.Viking on 2007-09-02
I have had the exact same problem once I started the NViida Accelerated drivers on my installation. If this applies to you too, then set your X to default refresh of 50Hz (which is terrible I know...) but then setup the screen using the NVidia settings tool (I started it by starting it as gksudo nvidia-settings) 
Once its setup  by nvidia-settings it seems to stick. You may have to manually setup the setttings for the monitor to get the resolution after the settings are complete. (I had to too)

Not sure if it helps but worked for me.

---

### Post by Jriske on 2007-09-02
Thanks, it looked like it worked. I used sudo aticonfig --initial and then I ctrl + alt + backspace and it seemed to work.

Anyone have any ideas on getting my MX900 to work?

---

### Post by Jriske on 2007-09-02
I got my mouse to work. Thanks. :)

---

