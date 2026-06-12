---
title: "usplash resolution problem"
date: 2008-06-22
forum: General Help
---

### Post by melat0nin on 2008-06-22
Hi all

I recently replaced my Radeon 9800 Pro which was dying with an nVidia 6200.  It is installed and working fine with the nVidia 169.12 driver.

One thing that changed with the change of gfx card was the usplash resolution -- before when I booted the usplash would be at native resolution (1440x900) whereas now it is at 640x480, which looks a lot less nice on my widescreen monitor.

So I read about StartUp-Manager and installed that.  Changed the resolution to the closest match (1024x768 - there were no 16:10 resolutions available in the list) and saved.

Booting up the resolution is fine, but shutting down the usplash screen has got weird colours, it is pinky and looks distorted.  I presume that is something to do with StartUp-Manager altering it with imagemagick?

I tried clicking 'Restore to Original Settings' and putting the resolution back to 640x480, but now the shutdown usplash just displays small in the top left of my screen, and still has the dodgy colours.

Can anyone help me restore my usplash to how it should be?  And is there a way I can force it to work at native resolution?

Cheers

-mel

---

### Post by housam on 2008-06-22
try the following :


```
sudo nano /etc/usplash.conf
```

you will got something like that 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.
  


add the required resolution 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1440[/COLOR]
yres=[COLOR="red"]900 [/COLOR]
 
or the settings you want
then reboot and type :


```
sudo dpkg-reconfigure usplash
```

then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by melat0nin on 2008-06-22
> **housam said:**
> try the following :


```
sudo nano /etc/usplash.conf
```

you will got something like that 


  


add the required resolution 



 
or the settings you want
then reboot and type :


```
sudo dpkg-reconfigure usplash
```

then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________


Thanks for you help!

That got the shutdown usplash to work properly in terms of colours, but they are both still running at a low resolution and look very big on my screen.

It's not of crucial importance since my desktop resolution works perfectly, but it is mildly irritating because the usplashes used to look so 'crisp' when I was booting up/shutting down.

I suspect the issue may be with the nVidia driver.  I notice that I don't see the nVidia logo at any point during bootup, even though I have it installed correctly (I've got the control panel and 3D works).

---

### Post by housam on 2008-06-22
Yes, it could be the drivers. try to reinstall them again.

---

### Post by melat0nin on 2008-06-22
> **housam said:**
> Yes, it could be the drivers. try to reinstall them again.

The way i 'installed' them was using the Hardware Drivers applet in System.. I didn't install them from the nVidia site.

How would I go about reinstalling them?  Is it likely to fix this problem, since 3D works otherwise?

---

### Post by exploder on 2008-06-22
Set your x and y resolutions for usplash and then run,

sudo  update-initramfs -u

You may have try different resolution. For example, my 17" flat panel works with 800x600 but the screen resolution is 1280x1024.You should be able to fix this with a couple of tries!

---

### Post by housam on 2008-06-22
> **melat0nin said:**
> The way i 'installed' them was using the Hardware Drivers applet in System.. I didn't install them from the nVidia site.

How would I go about reinstalling them?  Is it likely to fix this problem, since 3D works otherwise?

Use this guide for installing : [[COLOR="Red"]_http://www.psychocats.net/ubuntu/nvidia_[/COLOR]]("http://www.psychocats.net/ubuntu/nvidia")

or download / install from [COLOR="Red"]_Nvidia site_[/COLOR] according to your specs

---

### Post by emperortux on 2008-07-11
I have the same problem.
I have a 19" widescreen on 1440X900, with a nvidia 6150 LE card
I tried the suggestions above, and the colors corrected themselves, but now it is extremely large (i.e. the ubuntu logo taking up a quarter of the screen.)

---

### Post by emperortux on 2008-07-12
i fixed it. try changing the resolution in startup manager to 1280X1024.
The image is stretched, but other than that there's no problem.
:)

---

### Post by Kevrox on 2008-11-28
I had this issue as well... I have been trawling the net looking for answers and posted a question on launchpad.net.

When I did a hardy to intrepid upgrade... my nice clean crisp boot and shut down splash screen followed. The I decided to do a clean install... big fat chunky boot splash and loading bar.

reloaded hardy and nice again.. ( all on it's own mind you no tweaking of startupmanager) then upgraded again and was still nice. The redid a clean install and yuk again.
The new install was dome with the alternate iso, not sure if that has anything to do with it.
 Found this tread and used startupmanager to get the res right ( 1280x1024)... boot splash is nice now but the shutdown one is like a negative of what it should be... all strange colours. not sure what to try next..
any ideas???
Thanks Kev

---

### Post by Kevrox on 2008-11-29
just for anyone that has the funny colours when they shut down..
I changed my colour bit rate from 8 to 24 in startupmanager and now have nice crisp correct colour on shutdown...
So for me Smooth usplash works great... thanks...

---

