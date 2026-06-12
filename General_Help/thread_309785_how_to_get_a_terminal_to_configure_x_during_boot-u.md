---
title: "how to get a terminal to configure x during boot-up?"
date: 2006-11-30
forum: General Help
---

### Post by jclmusic on 2006-11-30
i want to get a terminal during bootup to configure x, as it seems to need a driver change, because when x should start i just get a blank screen  with "_" at the top. 

how would i do this?

---

### Post by an.echte.trilingue on 2006-11-30
When the ubuntu boot first starts, hit the esc key to get into the GRUB menu, then select single user (recovery) mode, which should be the second option.  Then configure X with sudo dpkg-reconfigure xserver-xorg.

Good Luck!
-mat

---

### Post by xabbott on 2006-11-30
Can also try ctrl+alt+F2 after the error/lock up

---

### Post by jclmusic on 2006-11-30
thanks, managed to get into the x config thingy.

vesa driver doesn't work. any suggestions for a driver for a nvidia card in a hp pheonix motherboard?

edit:
vesa returns a blank screen
vga returns a 'fatal server error: no screens found'
nv returns a 'fatal server error: no screens found'

---

### Post by CatKiller on 2006-11-30
> **jclmusic said:**
> edit:
vesa returns a blank screen
vga returns a 'fatal server error: no screens found'
nv returns a 'fatal server error: no screens found'

You could check the log to see what's wrong with your configuration with ```
less /var/log/Xorg.0.log
``` (Page Up/Down to scroll through, Q to quit)

---

### Post by xabbott on 2006-11-30
Does the live cd work? You could boot that and see what it uses. Then you'd also be able to mount your harddrive install and copy/compare the xorg files.

---

### Post by jclmusic on 2006-11-30
> **xabbott said:**
> Does the live cd work? You could boot that and see what it uses. Then you'd also be able to mount your harddrive install and copy/compare the xorg files.

the livd cd doesn't boot. i installed ubuntu using the network install cd

---

### Post by jclmusic on 2006-11-30
> **CatKiller said:**
> You could check the log to see what's wrong with your configuration with ```
less /var/log/Xorg.0.log
``` (Page Up/Down to scroll through, Q to quit)

lol it's huge! i'm afraid i really don't know what i'm looking for.

---

### Post by an.echte.trilingue on 2006-11-30
you need to add the universe/multiverse repositories following the [instructions here]("https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0") and install the propietary nvidia driver and use it following the [instructions here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").  That should take care of you.

---

### Post by jclmusic on 2006-11-30
> **an.echte.trilingue said:**
> you need to add the universe/multiverse repositories following the [instructions here]("https://help.ubuntu.com/community/Repositories/CommandLine#head-e1a24b1b2037f68b5a95f54388582b58ea4c9bd0") and install the propietary nvidia driver and use it following the [instructions here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").  That should take care of you.

how do i edit sources.list when i can't get x to start?

edit: found the 'nano' code.

---

### Post by CatKiller on 2006-11-30
> **jclmusic said:**
> lol it's huge! i'm afraid i really don't know what i'm looking for.

Fair enough. There's sometimes some fairly obvious ones - like all the resolutions being discounted for one reason or another, or messages about devices having the wrong name or whatever.

Installing the proprietary nVidia driver might help, though.

---

### Post by jclmusic on 2006-11-30
ok none of what those pages say are making any sense to me :( ](*,) 

can u just tell me what commands to type, please?

putting "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse" at the end of sources.list is about the limit of my knowledge with this kinda stuff.

i'm so confused!!!!!! ](*,) :-? :(

---

### Post by CatKiller on 2006-11-30
> **jclmusic said:**
> can u just tell me what commands to type, please?

It depends on what card you've got. If it's an old one, you'll need (after you've enabled the extra repositories)

```
sudo aptitude update
sudo aptitude install nvidia-glx-legacy
```

Otherwise you'll need

```
sudo aptitude update
sudo aptitude install nvidia-glx
```

Then you'll need ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
``` and change the Driver line in the Device section to "nvidia".

Then either reboot or restart X.

---

### Post by jclmusic on 2006-11-30
same result!

aaaaaaaaaaaaaaaaaaah!!!!!!!!!!!! *pulls hair out* lol

---

### Post by christhemonkey on 2006-11-30
Could you post here the output of ```
cat /var/log/Xorg.0.log | less
```

---

### Post by jclmusic on 2006-11-30
```

ServerLayout: "Default Screen" (0)
|    |-->Monitor "Generic Monitor"
|    |-->Device "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
|-->Input Device "Generic Keyboard"
|-->Input Device "Configured Mouse"
|-->Input Device "stylus"

```

lol what is a stylus?

---

### Post by christhemonkey on 2006-11-30
Are you sure your using your nvidia card?!

As that output shows that your using an Intel builtin video card...
The output of that command would be very useful. (cat /var/log/Xorg.0.log | less)


And a stylus is like one of those pens that you can use as a mouse.
Like this one:
[http://image.bizrate.com/resize?sq=400&uid=322963025](http://image.bizrate.com/resize?sq=400&uid=322963025)

---

### Post by jclmusic on 2006-11-30
> **christhemonkey said:**
> Are you sure your using your nvidia card?!

As that output shows that your using an Intel builtin video card...
The output of that command would be very useful. (cat /var/log/Xorg.0.log | less)


And a stylus is like one of those pens that you can use as a mouse.
Like this one:
[http://image.bizrate.com/resize?sq=400&uid=322963025](http://image.bizrate.com/resize?sq=400&uid=322963025)

is the fact i don't have 1 and yet it's in there a problem?

i have a built-in one, and a graphics card plugged in to 1 of the slots. which gives me an idea! i'm gonna try it without the card and see if i get an output from the built-in .

---

### Post by christhemonkey on 2006-11-30
Thats a good idea!
Try it and let us know.

Also, this sentence makes no sense to me :confused:
> is the fact i don't have 1 and yet it's in there a problem? 

---

### Post by jclmusic on 2006-11-30
same result with vesa, nvidia and what it autodetected (i808 or something).

---

### Post by jclmusic on 2006-11-30
lol sorry, i was reffering to the stylus line up there ^^

---

### Post by CatKiller on 2006-11-30
> **jclmusic said:**
> same result with vesa, nvidia and what it autodetected (i808 or something).

The fact that it's autodetected a graphics card and assigned an Intel driver implies that that is the device it is trying to use. That would be the kind of thing that you might have noticed in the log yourself earlier, since you've seen it and actually know that you have an Intel device in there.

If you aren't planning on using both, you should probably disable the onboard graphics in your motherboard's BIOS, and then run **sudo dpkg-reconfigure xserver-xorg** again. Otherwise, you can use **sudo nano /etc/X11/xorg.conf** to tell X which graphics device you want it to use. You do that by specifying the BusID of the device in the Device section. An AGP slot is often PCI:1:0:0, but I don't know how to find the bus address of the other slots.

---

### Post by jclmusic on 2006-11-30
ok i'm trying what u suggested now.

sorry for not realising it was using the other one. this is the first motherboard i've ever used ubutnu on without it auto-detecting it properly.

---

### Post by CatKiller on 2006-11-30
> **jclmusic said:**
> what would the adress of the built-in thing be?

```
lspci | grep VGA
``` should tell you the addresses of both of them in hexadecimal format (xorg.conf wants it in decimal). You'll need to do some conversion - lspci gives **0000:00:0b.0** as the address of one of my cards, but xorg.conf has that as **PCI:0:11:0**. Since X is trying to use the onboard thing, the address of the onboard device is probably the one that's already listed in your xorg.conf.

> sorry for not realising it was using the other one.

No worries. I was only saying that you were the only one who could have known that, not telling you off for not doing so.

>  this is the first motherboard i've ever used ubutnu on without it auto-detecting it properly.

Makes sense. Disabling the onboard is probably the easiest approach though. Then it should autodetect the card you want it to, properly.

---

### Post by jclmusic on 2006-11-30
how do i disable the onboard?

---

### Post by CatKiller on 2006-11-30
> **jclmusic said:**
> how do i disable the onboard?

It depends.

You'll have a key that you press shortly after you turn on the computer to enter the BIOS setup. Often this is the Del key, although it may be one of the F keys. This varies by the BIOS type. Usually it will say at the bottom of the screen at the point you can press it what the button is, but some computer manufacturers insist on covering that up with their own splash screen. In which case, you need to read the documentation or search the Internet.

That will take you into a menu system. Again, what it looks like and what the options are called varies by manufacturer. The page you want might be called "Integrated Peripherals", or it might be called something else. The option that you want to set to "Disable" might be called Onboard VGA, or it might be called something else.

Then you need to save the changes you've made and exit the BIOS setup program. The key to do this might be F10, but then again might be something else.

---

### Post by jclmusic on 2006-11-30
> **CatKiller said:**
> It depends.

You'll have a key that you press shortly after you turn on the computer to enter the BIOS setup. Often this is the Del key, although it may be one of the F keys. This varies by the BIOS type. Usually it will say at the bottom of the screen at the point you can press it what the button is, but some computer manufacturers insist on covering that up with their own splash screen. In which case, you need to read the documentation or search the Internet.

That will take you into a menu system. Again, what it looks like and what the options are called varies by manufacturer. The page you want might be called "Integrated Peripherals", or it might be called something else. The option that you want to set to "Disable" might be called Onboard VGA, or it might be called something else.

Then you need to save the changes you've made and exit the BIOS setup program. The key to do this might be F10, but then again might be something else.

ah it's in the bios settings! cool.

---

### Post by jclmusic on 2006-11-30
it'll only let me change the amount of memory reserved for the onboard vga (512kb/1mb) it won't let me turn it off :-k

---

### Post by CatKiller on 2006-11-30
> **jclmusic said:**
> it'll only let me change the amount of memory reserved for the onboard vga (512kb/1mb) it won't let me turn it off :-k

Looks like you're doing it manually, then, unless your manual says there's a jumper to do it. Or unless changing which device initialises first is possible with that motherboard.

You might be able to give a **BusID** value while you're doing **sudo dpkg-reconfigure xserver-xorg** and have it autodetect the rest, but I've not tried it.

Otherwise **lspci** will tell you the **BusID** (don't forget to change it to the decimal form) and what the card thinks that it's called. Put this information in the **Device** section of your xorg.conf. If you change the **Identifier** line, you'll need to change the **Device** line of the **Screen** section to match (otherwise you'll get the no Screens found error message).

For reference, my Device section looks like this:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
EndSection
```

There may still be an easier way, but I don't know what it is.

---

### Post by jclmusic on 2006-11-30
i don't effing beleive it!
the bloody thing has randomly decided to stop turning on again for the 3rd time this week. i've been trying for 3 weeks to get this motherboard 2 work, and this is the final straw lol. watch out below my window :p
i'm gonna put the old 1 back in, this just takes the piss.

---

