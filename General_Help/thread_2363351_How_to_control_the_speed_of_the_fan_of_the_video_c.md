---
title: "How to control the speed of the fan of the video card ???"
date: 2017-06-09
forum: General Help
---

### Post by offir on 2017-06-09
i have ubuntu 16.04
and GeForce GTX 650 video card
the fan of the card Does not always work
Should work when it reaches a certain temperature
I want to configure the fan
So that it will work permanently

I tried what was written in this link

[http://www.upubuntu.com/2015/05/how-to-controladjust-gpu-fan-speed-for.html]("http://www.upubuntu.com/2015/05/how-to-controladjust-gpu-fan-speed-for.html")

but without success
The option was added to the other options
But when I raise the speed to 80 or any other number
It does not save
It goes down to 10 back


so i try Method 2
```
sudo apt-get install nvclock
nvclock -f -F 70 
```
i get this message

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvclock

```

So how can I change the speed of the fan???

---

### Post by offir on 2017-06-10
No one ever came across it?

---

### Post by Bucky Ball on 2017-06-10
Do you have a driver installed for that from 'Additional Drivers'? If so, you should have the NVIDIA configuration tool in your apps menu. Have a look for 'nvidia' in your dash or apps and you should find it. You can adjust fans/temps and all sorts with it.

---

### Post by offir on 2017-06-10
> Do you have a driver installed for that from 'Additional Drivers'? If so, you should have the NVIDIA configuration tool in your apps menu. Have a look for 'nvidia' in your dash or apps and you should find it. You can adjust fans/temps and all sorts with it

Yes Just like you see at the link I gave 
I'm using Nvidia's driver
As I wrote in the first post
I tried this option
But it is not saved
I click apply
And it returns back to 10
And if I close And I reopen the v gone from the rubrics

---

### Post by efflandt on 2017-06-10
Which nvidia driver package version are you using and who made the GTX 650 card? I believe that you need nvidia-331 or newer with coolbits properly enabled to change GPU speed, memory, and/or fan settings. And from the available checkbox for fan speed it looks like you do, but note that fan speed says "Unsupported" in the graphic you included.

How hot is your graphic card getting that you are concerned (and have you vacuumed lint from it)? I have seen some people bent out of shape if their fan(s) do not increase when their Nvidia card is 50 degrees C, but that is not even warm. The single fan on my EVGA GTX 550 Ti would not even begin to speed up from its 33% minimum unless it got up to 63-64C. The newer GTX 750 Ti uses so little power that the MSI Twin Frozr Gaming GTX 750 Ti OC (silent 33% minimum fans) was impossible to overheat, peaking at 53-54C in graphic benchmarks even if OC'd to the max, limited by 60 watt hardware regulated max. And my Asus Dual GTX 1060 silently barely bumps its fans a few % from 33% minimum in graphic benchmarks somewhere in the 60C range.

The GTX 650 is rated for 98C max and only uses 65 watts, so unless you are going past 80C's into the 90's why worry? Although, 10% minimum fan speed seems unusual because all Nvidia cards I have had recently start at 33%. But some high end Nvidia cards do not run their fan(s) at all until the GPU gets warm.

---

### Post by offir on 2017-06-11
> Which nvidia driver package version are you using and who made the GTX 650 card?
i am using nvidia driver package version 375.66
this is my graphic card (According to what is written on it) [https://www.newegg.com/Product/Product.aspx?Item=N82E16814187201]("https://www.newegg.com/Product/Product.aspx?Item=N82E16814187201")

> but note that fan speed says "Unsupported" in the graphic you included
What does that mean?
On this specific graphics card the fan can not be controlled ?

> 
How hot is your graphic card getting that you are concerned (and have you vacuumed lint from it)?
it go up to 50c 
I clean the computer once a month With air pressure

---

### Post by Bucky Ball on 2017-06-11
You know that temperature is nothing to be concerned about? Prob why fan not kicking in.

---

### Post by offir on 2017-06-11
> You know that temperature is nothing to be concerned about? Prob why fan not kicking in. 

Yeah I know
But I prefer not to play with fire (Wait for damage)
And set the fan to work

---

### Post by pqwoerituytrueiwoq on 2017-06-11
If you really want to be paranoid about the GPU temp IIRC you can set the min fan speed using [KeplerBiosTweker]("https://www.techpowerup.com/download/kepler-bios-tweaker/") from a windows install, that is what i used to OC my 650 TI Boost (Software OCing on linux was not supported at the time)
I was able to get to 1097Mhz stable if anyone is wondering, i cant OC higher without hard-moding the card to get more power to the chip, well within safe temps

---

### Post by Bucky Ball on 2017-06-11
[QUOTE=offir]But I prefer not to play with fire (Wait for damage)[/QUOTE]

From the NVidia page on that card.

> Thermal and Power Specs:
98 C Maximum GPU Tempurature (in C)

I'd be paranoid if the fan *was* kicking in at 50C. Waste of electricity. ;)

I have the GTX 970 and the only time the fans come on is when I'm rendering HD video. If I put my hand on the back of the box, there is cool air coming out the fan hole. Can you feel hot air coming out the back of the computer? You clean it often, so I'm doubting it. If you are, it may have nothing whatsoever to do with the GPU. There are other component in the box that get hot. Are you sure they are all getting adequately cooled? If not, one hot component will bring up the temps of the others.

You have adequate cooling for *everything* you have in the box?

Anyhow, leave you to it and good luck. :)

---

### Post by Kris_M on 2017-06-11
In windows there were separate programs that adjusted all that stuff.

I have heard that the defaults on most cards are fine, a few are not.

I looked at that link and see
sudo nvidia-xconfig 
sudo nvidia-xconfig --cool-bits=4

I don't see that you did anything with that. ?


I will experiment after I clonezilla my build. Later.

As a standard practice I monitor it with psensors. Sits at 34-36 unless I'm playing a game. Graph will show me what it was after I end game.

Nope, no nvidia-xconfig - I do seem to recall that being deleted.

---

### Post by efflandt on 2017-06-11
As long as you are in the [COLOR=#00ff00]green[/COLOR] zone in NVIDIA X Server Settings > Thermal Settings, or even into the [COLOR=#ffa500]yellow[/COLOR] zone, heat should not be a concern. Cards can fail for other reasons, especially if not a major brand. Years ago I had a Galaxy GT 430 that began failing shortly after its 1 year warranty expired, not due to heat, but just cheaply made. Eventually it was not responding immediately during boot. I have had no problems at all with GTX cards from EVGA, MSI, or Asus since then. I never heard of Sparkle brand, but as I said earlier only, using only 65 watts it is probably impossible to overheat that chip and 50C is not even warm for a graphics chip. Maybe it simply has an efficient cooling system and fan and more fan speed is not necessary.

---

### Post by pqwoerituytrueiwoq on 2017-06-11
> **efflandt said:**
> As long as you are in the [COLOR=#00ff00]green[/COLOR] zone in NVIDIA X Server Settings > Thermal Settings, or even into the [COLOR=#ffa500]yellow[/COLOR] zone, heat should not be a concern. Cards can fail for other reasons, especially if not a major brand. Years ago I had a Galaxy GT 430 that began failing shortly after its 1 year warranty expired, not due to heat, but just cheaply made. Eventually it was not responding immediately during boot. I have had no problems at all with GTX cards from EVGA, MSI, or Asus since then. I never heard of Sparkle brand, but as I said earlier only, using only 65 watts it is probably impossible to overheat that chip and 50C is not even warm for a graphics chip. Maybe it simply has an efficient cooling system and fan and more fan speed is not necessary.
I have a Galaxy GT 430 since April 2011 that is still kicking 
I also have a Galaxy GTX 650 TI Boost i got in November of 2013 that i RMAed in February of 2014 cause the fan was not sounding right after i had it running extra fast (a speed that under normal operation would never happen) to be safe as it was under a heavy load for a long period of time
this card is in use on my current system right now, for this chip they were the only manufacture who actually has a heat sync on a the voltage regulators which should allow for a higher OC (surprisingly the only manuf. shipping them with a stock clock configuration)
as for the OCing on that card, see post #9 in this thread

---

### Post by offir on 2017-06-12
> **Kris_M said:**
> In windows there were separate programs that adjusted all that stuff.

I have heard that the defaults on most cards are fine, a few are not.

I looked at that link and see
sudo nvidia-xconfig 
sudo nvidia-xconfig --cool-bits=4

I don't see that you did anything with that. ?


I will experiment after I clonezilla my build. Later.

As a standard practice I monitor it with psensors. Sits at 34-36 unless I'm playing a game. Graph will show me what it was after I end game.

Nope, no nvidia-xconfig - I do seem to recall that being deleted.


I wrote these lines in the terminal
And it has indeed added the possibility to change fan speed
in the options of the graphics card driver

but
When I click on Appley
It does not save
It resets back to 10
And the  v is deleted from the rubrics

---

### Post by KillerKelvUK on 2017-06-12
So if your card supports having the fan speed manually set you need to ensure your xorg.conf file includes the cool bits setting to allow this, have a read here on the how-to ([http://z-issue.com/wp/nvidia-linux-drivers-powermizer-coolbits-performance-levels-and-gpu-fan-setting](http://z-issue.com/wp/nvidia-linux-drivers-powermizer-coolbits-performance-levels-and-gpu-fan-setting)).  For the 375 drivers this is what you need to set "When "4" (Bit 2) is set in the "Coolbits" option value, the nvidia-settings Thermal Monitor page will allow configuration of GPU fan speed, on graphics boards with programmable fan capability." (/usr/share/doc/nvidia-375/html/xconfigoptions.html)

Just bear in mind that your desire not to play with fire could actually be what burns you if you set the speed too low and then tax the GPU beyond the thermal threshold your manual setting covers, easy to forget about and not realise it's happening unitl its too late.  My GTX 970 seems to idle at 50 degrees and no fan is employed, at 100% utilisation whilst mining ethereum it reaches 70 degrees and only spins the fan upto 40%.  Obviously, a lot of variables here so would caution you to consider whether you can track, account and react to all of them as well as your card can.

Hope you get this sorted.

---

