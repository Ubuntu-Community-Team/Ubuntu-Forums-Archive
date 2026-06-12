---
title: "Wifi LED on with iwl3945"
date: 2008-04-18
forum: General Help
---

### Post by luisjorge on 2008-04-18
Hi everyone! I've searched and read a lot of instructions on how to make the Wifi LED stay on with different cards, but nothing with an Intel PRO WIreless 3945, using the iwl3945 driver that comes with Ubuntu Hardy.
Does anyone know how to make this LED work? 

Thanks in advance!

Luis Jorge.

---

### Post by ramjet_1953 on 2008-04-19
Try this:

Create a file[COLOR="Blue"] ipl3945[/COLOR] in[COLOR="Blue"] /etc/modprobe.d[/COLOR]

ie [COLOR="Red"]/etc/modprobe.d/ipl3945[/COLOR]

When you have done this, open the file with a text editor and insert this:

[COLOR="Red"]options ipl3945 led=1[/COLOR]

Save the file

Re-boot

NOTE: The above operations need to be performed in sudo mode.

Good luck!

Regards,
Roger :cool:

---

### Post by luisjorge on 2008-04-19
Hi! Thanks for the quick reply! So I tried creating that file, and it didn't work. I also tried naming it "iwl3945" instead of ipl3945, and it disabled my wireless card on the next reboot, so I erased it and I have wireless again. Is there another way of getting this LED on?

Thanks for the help!

Luis Jorge.

---

### Post by fragos on 2008-04-19
The LED is controlled by the driver. On my Dell Inspiron 1420n the standard pwl driver lights the LED but the iwl driver doesn't. Laptops frequently use some proprietary hardware. Not all laptops will turn an LED on under the control of the same driver.

---

### Post by steveneddy on 2008-04-23
Installing the backports did the trick for me.

In terminal:

```

sudo apt-get install linux-backports-modules-hardy-generic

```

reboot, enjoy.

I am using the Intel 3945 wireless chipset. I don't know if this works for other wireless chipsets.

---

### Post by steveneddy on 2008-04-23
> **ramjet_1953 said:**
> Try this:

Create a file[COLOR="Blue"] ipl3945[/COLOR] in[COLOR="Blue"] /etc/modprobe.d[/COLOR]

ie [COLOR="Red"]/etc/modprobe.d/ipl3945[/COLOR]

When you have done this, open the file with a text editor and insert this:

[COLOR="Red"]options ipl3945 led=1[/COLOR]

Save the file

Re-boot

NOTE: The above operations need to be performed in sudo mode.

Good luck!

Regards,
Roger :cool:

This did not work for me.

---

### Post by techdude3177 on 2008-07-02
I just updated to Hardy from Gutsy and now i am having the same problem with my LED not coming on. However if i use the older kernel of 2.6.22 it works fine.

---

### Post by fragos on 2008-07-02
Check here and use the backport that matches your version. I think -19 is the latest.

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work)

---

### Post by pferpaddy on 2008-07-02
The reason the leds dont work is that wireless support is now supported natively in the kernel and not as a restricted driver as it was in gusty im using intrepid  at the moment and with the new kernel the wireless light is back!

---

### Post by techdude3177 on 2008-07-02
your using what?!

---

### Post by pferpaddy on 2008-07-02
> **techdude3177 said:**
> your using what?!

interpid ibex as in ubuntu 8.10 alpha 1

it comes with the latest kernel so better hardware support

---

### Post by techdude3177 on 2008-07-02
um okay? well i updated to the newest kernel today.
so how do i test it or get to it or whatever i need to do, lol.
i am kinda lost. sorry

N/M i figured it out, thanks for the heads up!

---

### Post by pferpaddy on 2008-07-02
well you prob do not have the latest kernel because im useing the testing version of ubuntu where as your using a stable release if you reallllyyy want the wi-fi light so badly open your terminal and enter sudo gedit 
/etc/apt/sources.list then change any reference to hardy to intrepid
save and close and open synaptic and reload it. search linux- then download the latest kernel then again open the terminal and enter sudo gedit 
/etc/apt/sources.list change everything that you changed to intrepid back to hardy sava and viola youve got the testing kernel but this will prob cause a whole world of problems although you will still be albe to boot from ur pevious kernel from the boot loader. hope this helps

---

### Post by techdude3177 on 2008-07-02
actually there is an easier way.
for anyone else or later reference you can do
From the command prompt:
> update-manager -d
to get the latest kernal.  I didnt know it was in testing at first until i googled it.  Then i did that right away, its still installing everything.  So thanks for the heads up!

---

### Post by pferpaddy on 2008-07-03
well if you want half of the software uv installed to be replaced with default stuff and a very unstable system then go a head but unless you know what ur doing SERIOUS CATION dont upgrade

---

### Post by techdude3177 on 2008-07-03
I understand.  I learn things better by driving right in anyways! so even if its gets too probmatic, its only on my laptop and i have everything backed up on my desktop and ill just roll back if needed to.

---

### Post by pferpaddy on 2008-07-03
in that case go right a head first thing u will need to no is fglrx driver dont work properly and gnome session dont load unless you use the friendly reovery option in boot and just go to normal boot. do not ask me why i havent figured it out yet and the last thing is HAL thts not workin properly yet
good luck

---

### Post by EarloftheWest on 2008-07-16
Ah, to what lengths folks (meaning me) :) will go to get the LED working.

I really want this LED to work. So last night, I tried 4 ways to get the LED functional. 
First try: I downloaded and installed the latest wireless drivers from the compatible wireless project:
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
No joy.
Thinkwiki indicates that the config.mk file needs to be modified so I did just that. Quote:
"You can download a compatible driver which supports WiFi led flicking and build it with modifying the config.mk by adding CONFIG_IWL3945_LEDS=y and CONFIG_IWLWIFI_LEDS=y these two options. For Ubuntu/Debian users, build-essential, linux-source-2.6.24 and linux-headers-generic packages are required."
It wouldn't compile correctly with those additions.
(The insanity continues.) :lolflag:
Second try: I next downloaded and compiled the latest kernel 2.6.26. (The latest kernel has updates and supports the LED.)
It loaded, without binary graphics drivers or wireless support.
Third try: I changed my sources to intrepid and downloaded and installed the 2.6.26 kernel that intrepid uses. Still had video and wireless problems.
Fourth try: I did a distro upgrade to Intrepid.
Success! I can report that using Intrepid will yield you a functional wireless LED. However, it doesn't flicker as fast as the driver Windows uses. (Intrepid is in Alpha state and it wasn't usable for me without going through more configuration - video drivers for example.)

Of the above attempts, the least intrusive way to get the LED working would be to follow the compat-wireless project's instructions if I could figure out how to configure it when it compiles to activate the LED.

I should also mention that a few weeks ago I used ndiswrapper. The LED worked fine but the wireless didn't. I think that I need to somehow unload the iwlwifi driver so that the ndiswrapper doesn't conflict with it. Does anyone know how to do this?

---

