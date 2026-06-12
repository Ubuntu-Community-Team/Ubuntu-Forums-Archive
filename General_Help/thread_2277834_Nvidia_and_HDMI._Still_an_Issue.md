---
title: "Nvidia and HDMI. Still an Issue"
date: 2015-05-11
forum: General Help
---

### Post by dawer2 on 2015-05-11
[FONT=arial][SIZE=3]I've been googling for a few days for a solution and I can't find any. I can't connect to my TV via HDMI which is quite the issue. 

I played with some sort of xorg.conf file, downloaded drivers, x-server, reinstalled ubuntu, bios stuff, and a few other things that I won't pretend to understand (just followed guides). Anyone have any idea what to do? In my xrandr there isn't even an hdmi listed. For reference i have an *NVIDIA® GeForce™ GTX 970M (6.0GB) GDDR5 PCI-Express DX11 (Maxwell) *. I also have a *4th Generation Intel® Haswell Core™ i7-4790K.*[/SIZE][/FONT]

here are some commands + results that seemed to be standard in this issue. Please note that this is after a 3rd fresh install of ubuntu 14.04. Also, I should have 1 HDMI port and 2 uhm...other..ports for external monitors. I'm not really sure what the other ones are called but none of them are listed in the xrandr. The HDMI is the only one plugged at the moment (since I don't own any of the other type. whatever it is)

ubuntu@ubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080       0.0* 

ubuntu@ubuntu:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation Device 13d8 (rev a1)

ubuntu@ubuntu:~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff


Any Ideas? I'm totally lost and without support for external displays I'll get stuck going back to windows :\. I'd rather avoid that because programming has been so convenient in ubuntu. Plus windows is honestly just too bulky for me to experiment with different modeling ideas (although. after moving from matlab to octave, I certainly do miss the wonderful matlab gui). I've seriously worked my google-fu to the max and thoguh I've found tons of results, nothing has worked. 

Last Note: The flashdrive I have with ubuntu on it has worked with my other laptops (much older) and connects to the tv without a hitch so I'd be hard-pressed to believe that it is corrupted in any way.

---

### Post by grahammechanical on 2015-05-11
I do not know the answer and I have  a machine with a much lower specification but just so you have something to compare here is what I see when I run those 3 commands.

> 
graham@sdb1-Uplus1:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.1*+   60.0     59.9     50.0     24.0     60.0     50.0  
   1440x480       60.1  
   1280x1024      75.0  
   1280x800       84.9  
   1280x720       60.0     59.9     50.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9     59.9

graham@sdb1-Uplus1:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2)

graham@sdb1-Uplus1:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: GT216 [GeForce GT 220]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:9c00(size=128) memory:fe680000-fe6fffff

A few things come to mind. Blind guesses if you like. What video driver is being used? Does the open source video driver give different results. You are using Ubuntu 14.04 but is it 14.04.2?

Note this Phoronix's test. There should be support for Haswell CPUs In Ubuntu but I wonder what kernel you are installing and whether you have the newest proprietary video drivers.

[http://www.phoronix.com/scan.php?page=article&item=intel_windows7_2014&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_windows7_2014&num=1)

Something is telling me that Haswell also means integrated graphics

> All other currently known i3, i5 and i7 desktop processors include Intel HD 4600 graphics (GT2).

[http://en.wikipedia.org/wiki/Haswell_%28microarchitecture%29](http://en.wikipedia.org/wiki/Haswell_%28microarchitecture%29)

[http://www.cnet.com/uk/news/intels-new-fourth-gen-haswell-processors-what-you-need-to-know-faq/](http://www.cnet.com/uk/news/intels-new-fourth-gen-haswell-processors-what-you-need-to-know-faq/)

Regards.

---

### Post by SeijiSensei on 2015-05-12
Did you install the proprietary NVIDIA driver?  If so, try using the NVIDIA manager application.  You'll find it in the menus.

---

### Post by dawer2 on 2015-05-12
okay things suddenly took a terrible turn for the worse and I haven't even done anything more yet. Yesterday when I messaged you guys I had just fresh-installed ubuntu again. Then today I try using my laptop and it is only in 800x600 res with no other options. I figured I would just need to reboot but then it gave me this [ 3.075228] mmc0: Unknown controller version (3). You make experience problems. and then never started.

Google tells me that mmc0 is just the card reader so I can't see why that would be the issue.

So then I tried booting from my flashdrive and it gives me the same issue whether I click try, install, oem install.

Then I went into my bios to look at it and for some reason my two hard drives are no longer options in the boot priorities section. I imagine some other stuff might be different but I don't know what anything else really means so I couldn't tell you. 

At any rate, my new laptop is pretty much useless right now (I'm using my old one to write this). It's definitely worse than just no hdmi :(

help please

---

### Post by dawer2 on 2015-05-12
All problems solved. 

As far as the mmc0 + no hdd detected etc. well...that just solved itself. By magic probably. Basically after the thousandth restart, it just worked...I would like to know why this happened and how it got better but I have this feeling in the back of my mind that if I ever truly understood how it worked it would stop working. So I'll look into it no further.

HDMI: It seems I didn't really understand how to install the nvidia drivers properly. logging out, ctrl+alt+f1, kill xserver via sudo stop lightdm , sudo init 3, running the file, and then turning xserver back on via sudo start lightdm worked for me. (details here: [http://askubuntu.com/questions/149206/how-to-install-nvidia-run](http://askubuntu.com/questions/149206/how-to-install-nvidia-run)) 

Now I have working HDMI and sound too. 

The only downside is that it takes longer to shutdown and brings up a wonderful giant Terminal-esque thing where it unloads everything. Plus whenever I start the computer it says "Error: No video mode detected" for a couple seconds and then starts up. I tried the fixes I understood like commenting out the grub hidden timeouts but it didn't do anything. Mildly annoying but nothing crucial (as far as I know). All in all, problem solved. Thanks for your help guys!

---

