---
title: "Can't fit desktop to screen for new TV (Samsung hlt5687sx/xaa)"
date: 2013-12-10
forum: General Help
---

### Post by I.Bun.Tu on 2013-12-10
I am running Ubuntu 13.10 and just got a Samsung hlt5687sx/xaa. When I plugged it in via HDMI the desktop was zoomed in (I could barely see the launcher so it was cut off by roughly 30 pixels around each side). I did some trouble-shooting and figured out that the issue is not with Linux but with how the TV is accepting resolutions.

Here's what I discovered (in Windows, and now I'm looking for a solution in Linux; the TV displays the same thing at each resolution regardless of whether Windows or Linux is plugged in, so there is no difference between Windows and Linux but not all the resolutions available in Windows are available to me in Ubuntu):

The TV has 2 similar display settings that could both potentially be usable (ignoring 4:3 and wide stretch, etc.) which are "16:9" and "Just Scan" and there are no zoom settings.

Outputting from the computer 1920x1080, the "Just Scan" setting cuts off only around 10 pixels around each side of the screen and around half of the launcher is visible. Now if I switch the display setting to "16:9" even more of the image is cut off, which makes sense since 1920x1080 is fairly off ratio from 16:9.

Outputting a resolution of 1776x1000 in "Just Scan" makes an image with a 5-10 pixel black boarder around it, slightly smaller than the screen. If I then set the TV display to "16:9" the image fits the screen.

Outputting a resolution of 1600x900 in "Just Scan" gives an image that is slightly smaller than the screen again, and then setting the TV to "16:9" gives a perfect fit. VOILA!

Now from what I gather, the "Just Scan" setting draws a screen size somewhere between 16:9 and 19:11 and as far as I can tell the best solution is to use the "16:9" display setting on the TV and output a resolution of 1600x900 pixels (or higher with the same ratio).

Now the only problem I'm having is that Ubuntu only wants to let me select 1920x1080 or 1280x720 resolution for the Samsung TV. 

I tried following the guide here:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

for adding undetected resolutions. The TV is a 120hz TV and I tried adding the 1600x900 resolution at both 120hz and at 60hz but when I select either of them in Ubuntu the TV screen goes black with a message from the TV saying "Mode Not Supported"

So if anyone knows a better solution, I am all ears. Otherwise I would really appreciate some help setting my output resolution for this TV to 1600x900. I am using an HDMI output from an HIS Radeon HD 4760 AGP 1GB gpu. Thanks.

---

### Post by I.Bun.Tu on 2013-12-12
So the issue was the TV overscanning the input. After spending several hours on the phone with about 4 different technicians from Samsung (who all pretty much knew nothing) I've come to understand that my "Just Scan" size for my TV is supposed to do all the things peoples various other video settings allow them to do to fit the image to the screen. But Samsung wrapped it all up in one setting instead of making it a few different settings that a user could use to tweak to get the right fit for different inputs and whatnot... but it's all wrapped up into one little setting that doesn't work properly, but according to the TV's user manual should allow you to view any HDMI 1080p input without a truncated image (paraphrased verbatim).

Anyways, I fixed the problem using xrandr and then saved the settings in my lightdm.conf file. I will outline a step-by-step guide for anyone else who has issues with a TV overscanning an image (apparently those with nvidia proprietary drivers have an overscan compensation setting in their driver configuration utility and there may be a similar option for ATI, though it is far less discussed on the net; the solution below should work for anyone using Ubuntu and with a slight tweak for other Linux distros to set the script to run before the DE loads):

First open a terminal (ctrl+alt+t in Ubuntu) and type:

```
xrandr -q
```

to list your displays and see the device name for your TV output, should be HDMI-0 or HDMI-1, etc.

Now turn on underscan and adjust the settings to find the correct pixel borders for your TV:

```
xrandr --output HDMI-0 --set underscan on
xrandr --output HDMI-0 --set "underscan hborder" 39 --set "underscan vborder" 21
```

Replace HDMI-0 with HDMI-2 or whatever your device is called. Then keep repeating the last line with different values until you get it to fit your screen exactly. Above are the exact settings I used for my Samsung 56" TV (the model number above) and I also had to adjust the position to center the image on the screen after underscanning.

So assuming I didn't make any typos, you should now have your Ubuntu desktop fitting your TV correctly. The next step is to make this into a script, make the script executable and tell that script to auto-execute before the desktop environment.

So create a new file in a text editor and paste the following:
```

#!/bin/sh
xrandr --output HDMI-0 --set underscan on
xrandr --output HDMI-0 --set "underscan hborder" 39 --set "underscan vborder" 21
```

Replace the last line with the values that give the correct sizing for your TV then save the file as a .sh, make it executable and tell it to auto-execute before your DE starts. This will vary for different distributions of Linux. This is how I did this for Ubuntu 13.10 with the Unity desktop environment (in a terminal):

```
gksu mousepad /usr/bin/samsung56underscan.sh
```

then mousepad opens and I pasted the above 3 lines (you can replace mousepad with gedit or whatever text editor you prefer; don't forget to 'sudo apt-get install gksu' if you do not have it already). I did this as root in order to place the script in /usr/bin because this was where I wanted it. You could easily do this process without root privileges and save the script in your home folder or somewhere else that you have access to it, when we tell Unity to auto-execute the script we will be pointing to the file directly. Now save and close the text editor. Back to the terminal:

```
sudo chmod a+x /usr/bin/samsung56underscan.sh
gksu mousepad /etc/lightdm/lightdm.conf
```

Now add the following line to lightdm.conf when it opens in the text editor (I placed it at the top, right below [SeatDefaults] but I'm sure you can place it anywhere:

```
display-setup-script=/usr/bin/samsung56underscan.sh
```

That should be it. This is what I've done in my setup and it is working great. I hope this helps some other people. It took me a lot longer to write than expected.

---

