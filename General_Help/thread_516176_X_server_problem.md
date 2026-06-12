---
title: "X server problem?"
date: 2007-08-02
forum: General Help
---

### Post by legendman212 on 2007-08-02
I'm new to wubi, but i have run Ubuntu on a virtual machine, however the main reason i wanted it was to install beryl, which was not possible on my virtual machine....anywho

i got through the whole install process (after a painful 4 hours of download times 20kbps-300kbps...) but on first reboot i got the "activate swap" error where the system hangs there for 30 minutes, and after comming onto the forums, i fixed that, but now, i get to "Running locak boot scripts (/ect/rc.local), and that takes about 3 minutes, then it takes me to this screen with all these weird characters, and says, "Failed to start X server, would you like to see the details of the error (or something like that).  it showed me where the log was of the error "/var/log/Xorg.0.log"  and under it was this "/ect/X11/Xorg.conf"

now i pressed CTRL+ALT+2, and tried to log in as root, and failed (what is the password for root?)  and it denied me permission to view "/var/log/Xorg.0.log" 

could anyone help me please?  This Wubi installer seems quite amazing, and i really want to check it out.

I'm running a Dell Inspiron E1705 with Intel core duo T2500 @ 2GHZ each
ATI mobility radeon X1400
2.5 GHZ ram

Thanks in advance

---

### Post by ago on 2007-08-03
You login as usual and run individual commands as root by using the "sudo" command. You cannot login as root.

You probably need to install the correct driver for your video card (make sure internet is working). The command is going to be something like:

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel

---

### Post by legendman212 on 2007-08-03
how do i connect to the internet?

---

### Post by tuxcantfly on 2007-08-03
> how do i connect to the internet?

I'm assuming you're using a wireless internet connection, those tend to be the most problematic (wired connection usually just works out of the box with Ubuntu). For now, use a wired (ethernet) connection, and if you need any help with setting up your wireless go to the networking/wireless forum at [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136) and post the manufacturer and model of your chipset/card, they'll probably be able to help better.

---

### Post by legendman212 on 2007-08-03
after connecting to the internet, and doing those commands, I restarted, and i had the same problems, but the updates did install....so i don't know whats wrong

---

### Post by Diabolis on 2007-08-03
Configuring Xserver can be tricky. I had that problem and it took me a LOT of trys to get it working. You could start by typing this:

```
sudo dpkg-reconfigure xserver-xorg
```

You can play around with it until you find the right configuration for your machine. If I were you I would go directly to my xorg.conf file by typing this:

```
sudo nano /etc/X11/xorg.conf
```

The xorg.conf file will open, look for a section called "device". There you'll find the driver you are using, chances are that it's value will be VESA, I changed it for i810 and works fine for me. I think you'll use ATI.

Either of those ways will get your x server working, both edit xorg.conf file, so just use the one you like the most.

---

