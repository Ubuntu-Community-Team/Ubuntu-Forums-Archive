---
title: "Nvidia 6600. Linux. Error."
date: 2006-08-06
forum: General Help
---

### Post by Roasted on 2006-08-06
I tried downloading this:

[http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html)

And I get this:

[IMG]http://i2.photobucket.com/albums/y36/Roasted/dafsd34r5.png[/IMG]

---

### Post by Dr. Nick on 2006-08-06
That is because it is not executable, To make it executable right click int and hit properties, then check xecute on the permissions tab. However that package can not be run from within a gui, you must shut down xorg and run it from a command line.

look here for the best ways to install the drivers,

I like method 1

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Roasted on 2006-08-06
What can I type in terminal to make sure the new drivers ARE in and working properly?

---

### Post by Dr. Nick on 2006-08-07
their are a few commands, I cant remember them though.

The way I usually check it is look for the nvidia screen on bootup and then try some opengl screen saveres and see if they playback well.

Also if you look at the file

/etc/X11/xorg.conf

check the device section and the driver line should read "nvidia' not "nv" or "vesa"

I will try to dig the commands up to test.

---

### Post by Dr. Nick on 2006-08-07
I believe this will test it

glxinfo

run from a terminal should say something like this
> 
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4

That may/may not be correct though. My drivers work and that is the output I see.

As I mentioned I just play a opengl game or screensaver and see if I am satasfied with the performance, and if your xorg.conf has "nvidia" in the driver line then the drivers are activated

---

### Post by Roasted on 2006-08-07
Below the part you pasted above, did you get a longgggggggg *** list of... something? 

Also - Your's says client glx, mine says server glx. Why?

How do I find the xorg.conf file to see if nvidia is in it?

---

### Post by Dr. Nick on 2006-08-07
if you look the client is further down, yes I edited out of a long output

run this command

cat /etc/X11/xorg.conf

scroll up some after its done and look for this

Section "Device"
        Identifier      "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"

Your identifier will be different but teh driver line will be the same if its working, if you see anything besides nvidia then look at the link I posted above

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Roasted on 2006-08-07
So wait, just because it says nvidia that means I have the new driver? I was thinking that if I upgraded from driver 8 to 9, that it would say "nvidia 9" there instead. Know what I mean?

---

### Post by Dr. Nick on 2006-08-07
Yeah I understand what youe saying that seems logical, but is not the case. It will always say nvidia when it is working. If it said nvidia 8 or 9 then it would have to be changed every time you update which could be a hassle and a spot for possible errors to arise.

the "nv" driver is a built in driver that will always work on a nvidia card, but just doesnt porvide 3d accerleration

---

### Post by Roasted on 2006-08-07
Hm. Granted, I have a working driver. I'm just having a hard time understanding if I have the new one or if I have the old one still...

---

### Post by Dr. Nick on 2006-08-07
what you can do is open synaptic, system - administration - synaptic

then search for "nvidia" and not the version of nvidia-glx

mine is 1.0.8762+2.6.15.11 so that should be the newest ver


The above will only work if you used nvidia-glx to install the drivers, which is how most people do it

---

### Post by Roasted on 2006-08-07
What do you mean by using nvidia-glx to install it? Is that the Method 1 thing from the link you posted before?

---

### Post by Dr. Nick on 2006-08-07
yeah, method 1 install the nvidia-glx package,

nvidia-glx is the same the driver found on nvidias site, but is just made to install on ubuntu easier then the file from nvidia which is generic to all linux distrobutions.


for that reason the version numbers should match up. I think the 8762 is the newest according to nvidias site so I am not worried.

sometimes a updated nvidia-glx package may take a few extra days to show up after a nvidia update, but its not a big deal

---

### Post by Roasted on 2006-08-07
I was just browsing synaptic and noticed something. If a new driver comes out for my 6600 Nvidia, would it come up in synaptic? I noticed the "latest version" and "installed version" sections in synaptic. Just wondering.

---

### Post by Dr. Nick on 2006-08-07
Yes, the updated drivers still use the same "nvidia-glx" name so synaptic will automatically realize when their is a newer version in the ubuntu repositories and will alert you to that.

---

