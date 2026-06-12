---
title: "Screen Resolution"
date: 2013-04-18
forum: General Help
---

### Post by chimi_12 on 2013-04-18
Hi all, 


I have just installed Lubuntu in an old PC, at first try I used the normal iso installer, but after select the language and hit install, I could not see the installation wizard because of the screen resolution. Well, I could solve this selecting nomodeset (in F6 menu) and typing xforcevesa Then the installation wizard starts without problems but my CD had a problem and then I could not complete the installation.](*,)  Then downloaded the alternate install and the installation completes perfectly, but... once again, I have the screen resolution problem and even can't log in. (see the image attached, there you can see the problem). 

I looked for a solution and I found some threads about xrandr (here: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_XRandR_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_XRandR_changes_persistently) ) but when I type xrandr in terminal (I did Ctrl+Alt+F1 to switch from the graphical mode to terminal) I get the message: "can't open display" also I looked for a xorg.conf file and I didn't found anything. 


So, now I don't know how to solve and how to search for solutions to my problem. 


All the help you can bring me would be really appreciate!! 


Thanks in advance!!

---

### Post by matt_symes on 2013-04-18
Hi

To get xrandr to work at a console you need to set the display environmental in the console.

```
DISPLAY=:0 xrandr
```

Kind regards

---

### Post by chimi_12 on 2013-04-18
Hi matt_symes, 

Thanks for your reply and your time! 

You say, > set the display evironmental in the console so, I will be able to run xrandr in console. But, will this help me to solve the problem of resolution in graphical mode? I mean, I feel that this command ```
DISPLAY=:0 xrandr
``` will make xrandr work but only in console. And my goal is change the resolution in graphical mode, because right now I cant read or see anything. 

Thanks Again.

---

### Post by matt_symes on 2013-04-18
Hi

```
DISPLAY=:0 xrandr
```

The above command will get the display settings (screen resolutions) in the console. 

You can then add modes (resolutions) and change the settings of the existing mode.

This will affect the GUI and it's why you need to pass the DISPLAY parameter so it know which display (X server) to use.

Kind regards

---

### Post by chimi_12 on 2013-04-18
Perfect!! 


Now I understand, thanks so much!! 


Regards

---

### Post by chimi_12 on 2013-04-19
Hi Again matt_symes, :D

I tried the command you said, but now I get another error:

```
No protocol specified
Can't open display :0
```

I search for it, and found some commands like: 
```
export XAUTHORITY=/home.....
```
and some others similar, but I guess that these commands are for graphical environment and I'm just using a tty terminal (CTRL+ALT+F1) so, seems that these  commands will not work for me.

Do you know if I'm doing something wrong or if is there another alternative to solve my problem?

Thanks!!!

---

### Post by matt_symes on 2013-04-19
Hi

Are you logging into the same console with your user name and password ?

Try this in the console.

```

export DISPLAY=:0
xhost +
xrandr
```

The last command will give you a list of screen resolutions. select one with.

```
xrandr -s <screen_mode>
```

You can then also add new modes and set them. 

I think your problem is fixable.

I have been testing these commands on my machine.

Kind regards

---

### Post by chimi_12 on 2013-04-19
Hi, 

Yes I'm logging in with my username and password, I tried what you said me. 

> **matt_symes said:**
> 
Try this in the console.

```

export DISPLAY=:0
xhost +
xrandr
```


But I get the same message :confused: (see the image attached)

Thanks

---

### Post by humpty88 on 2013-04-19
Some tips;
Try the PC on another monitor just to see what happens.
Also have a look at /var/log/Xorg.0.log - will show what happened with the auto-detection.

---

### Post by matt_symes on 2013-04-19
Hi

If, from the console, you type

```
DISPLAY=:0 xauth list $DISPLAY
```

Does that return some along the lines of

```
MIT-MAGIC-COOKIE-1 xxxxxxxxxxxxxxxxxxxxxxxxxxx
```

where xxxxxxxxxxxxxxxxxxxxxxxxxxx is a long alpha numeric number ?

Can you also post the output of

```
ls -l /home/$USER/.Xauthority
```

We may have to try to tackle this another way.

Kind regards

---

### Post by chimi_12 on 2013-04-19
Hi, 

When I ran the command

```
DISPLAY=:0 xauth list $DISPLAY
```

xauth says that the .Xauthority does not exist

```
xauth: file /home/administrador/.Xauthority does not exist
```

I have attached the file Xorg.0.log but I had to cut the file that weighed over 19 kb that allows forum.

Thanks

---

### Post by matt_symes on 2013-04-19
Hi

One more piece of information then we can work out how to tackle this.

From the console again.

```
echo "$XAUTHORITY"
```

You have a savage graphics card and they were problematic at best at times. I take your rig is pretty old :)

It using the vesa driver but selecting an incorrect mode by the looks of it.

If you boot into recovery mode is your display good. Booting into a LiveCD/USB is your display good ?

Kind regards

---

### Post by chimi_12 on 2013-04-20
Hi, 

Hahaha yes I know, it's a kind of old PC hahaha...

Ok, the command:
```
echo $XAUTHORITY
```

returns: 
```
/home/administrador/.Xauthority
```

so, I don't know why the file does not exist...

About booting in live CD, the first menu looks good (where you select language and "Install or try whitout install", memtest, etc...) But once you select the option "Try Lubuntu without installing" once again the screen resolution problem appears. 

I tried another thing... Before select "Try lubuntu...." I hit "F6" and select the option nomodeset. Then I typed: xforcevesa and the LiveCD boots without problem. (See the attached pictures, there you will see what I did)

Thanks!!

---

### Post by matt_symes on 2013-04-20
Hi

Try editing the grub command line with xforcevesa.

At the grub command prompt, select the kernel and press e to edit the line.

Look for the line with *quiet* and *slash* in it and at the end type

```
xforcevesa
```

Press ctrl + x or F10 to continue booting.

How does that pan out ?

BTW: Your issues at the console were because you did not have a magic cookie so could not be authenticated by the xserver. Pretty sure about that.

Kind regards

---

### Post by chimi_12 on 2013-04-20
Hi, 

Tried the grub, edited as you said but didn't work. The screen resolution is still wrong.. The xforcevesa didn't work this time. :sad:

Thanks for your help!!, 

Kind regards

---

### Post by matt_symes on 2013-04-20
Hi

Boot into the LiveCD with xforcevesa set. Open a terminal and type

```
xrandr
```

Make a note of the setting it using.

You see a display like this.

```
matthew-S206:/home/matthew/storage/linux_source/linux-3.8.6 % xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   **1366x768       60.0*+**
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
matthew-S206:/home/matthew/storage/linux_source/linux-3.8.6 %
```

The one with the ***** is the one your currently using. We'll try to boot into your system after and set that as the resolution.

In fact make a note of all the settings.

EDIT: 

Mount your hard drive and navigate to your Desktop directory.

Create a file using gedit containing.

```
xrandr -s <resolution you are using>
```

So for me it would be

```
xrandr -s **1366x768**
```

save the file.

Right click on it and make it executable. This step is important.

Position it in the upper middle of the desktop.

We may be able to use that to change the resolution easier as all you have to do is double click on a bigger target when we try to boot into your system.

Kind regards

---

### Post by chimi_12 on 2013-04-20
Hi matt_symes, 

Right now I'm out of the office (there's the PC), return on Monday, then will do what you are saying. 

Thank you very much!!

---

### Post by chimi_12 on 2013-04-22
Hi, 

Well, I already did what you had indicated. Boots into LiveCD, then excecute xrandr, this is what it returns: 

```

lubuntu@lubuntu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0 

```

Then I did the file following step by step. Then boots with the real system, without seeing clearly tried to logging, once on the desktop I double click the icon of the file but not executed. Then opened a terminal using CTRL+ALT+T and without seeing typed:

```
xrandr -s 1280x1024
```


and although this was the screen resolution used in the LiveCD, did not work. For some reason the screen still looks bad. Also tried changing the rate: 

```
xrandr -s 1280x1024 --rate 70
```

But still not works. See the attachments, the first picture is after changing to 1280x1024 resolution, and the second one is after moving the mouse around. 

Thanks,

---

### Post by matt_symes on 2013-04-23
Hi

Sorry for the delay in getting back to this post. I have been busy over the last day and a half.

Anyway, i think we should try creating a new mode as those last pictures look like a scan line issue.

Open a terminal and type

```
cvt 128 1024
```

You will get a response back that looks something like this (This is from my netbook).

```
matthew-S206:/home/matthew % cvt 128 1024
# 128x1024 58.80 Hz (CVT) hsync: 62.50 kHz; pclk: 10.00 MHz
Modeline **"128x1024_60.00"**   **10.00  128 136 144 160  1024 1027 1037 1063 -hsync +vsync**
matthew-S206:/home/matthew % 
```

It's the info in bold we are interested in as they will be the scan parameters and mode name.

Next create the new mode, so use the parameters returned from the cvt call in the next command (they should be the same but hey, always better to double check these things).

I would type

```
xrandr --newmode "128x1024_60.00"  10.00  128 136 144 160  1024 1027 1037 1063 -hsync +vsync
```

Now we need to associate the mode with an adaptor. I am using LVDS here as an example but i'm not sure if this is the correct one for you. See the end of this post for an explanation.

```
xrandr --addmode LVDS "128x1024_60.00"
```

Finally use the new mode on the adaptor.

```
xrandr --output LVDS --mode "128x1024_60.00"
```

If you can see the terminal well enough when you boot into your install then type the commands there and post back on efficacy.

...if not the boot into a liveCD/USB and add the xrandr commands to that text file from the live environment. Then all you need to do is click that file when you boot into your install.

As i said, I'm not sure if LVDS is the correct adaptor you should be using. 

Here's my adaptor. LVDS is my adaptor.

```
**LVDS** connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
```

Here's yours

```
**default** connected 1280x1024+0+0 0mm x 0mm
```

It suggests your adaptor is called default (i have not come across that before), so for your first attempt it replace uppercase LVDS in the commands above with the word (lowercase) default.

I hope that makes sense.

Kind regards.

---

### Post by chimi_12 on 2013-04-24
Hi, 

Don't care about the time, I figured you were busy. ;)

The command: 

```
cvt 128 1024
``` returns the same as yours:
```
# 128x1024 58.80 Hz (CVT) hsync: 62.50 kHz; pclk: 10.00 MHz
Modeline "128x1024_60.00"   10.00  128 136 144 160  1024 1027 1037 1063 -hsync +vsync
```

Then typed, as you said, this command: 

```
xrandr --newmode "128x1024_60.00" 10.00 128 136 144 160 1024 1027 1037 1063 -hsync +vsync
```

But returns this message (see the attached picture): 

```
failed to get size of gamma for output default
```

Anyway, I continued to type: 

```
xrandr --output default --mode "128x1024_60.00"
```

But this didn't do anything. Don't return anything. I did all this, watching the screen with difficulty, because as you know it is not possible to see everything correctly.

Kind regards!

---

### Post by matt_symes on 2013-04-24
Hi

You typed

```
xrandr --newmode ....
```

Did you then type

```
xrandr --addmode ....
```

before the

```
xrandr --output ...
```

?

It is important that all three steps get typed. Try that first.

BTW: You can check the new mode was added by running the xrandr command again and looking for a line with **1280x1024_60.00** in it. If it's not there then don'tbother with the other two commands as they will not work and just post back.

Anyway, if that fails because it "can't get the gamma",  let's see if we can give it some :)

Add this to the xrandr output command.

```
--gamma 1:1:1
```

so the output command becomes

```
xrandr --output default --gamma 1:1:1 --mode 1280x1024_60
```

It may be that the gamma failure in the first step is ensuring the mode is not getting added in the first place. If that is so then each subsequent step would fail. I'm looking into whether this is the case or not.

BTW: None of this is permanent. We're trying to find what works and then we can make it permanent.

EDIT: One question if forgot to ask. You're not using a KVM switch or sum such between you and the monitor are you ?

Kind regards

---

### Post by chimi_12 on 2013-04-24
Hi, 

Before test the new commands, yes I'm using a KVM switch, I'm sorry, you didn't asked, but I neither specified that detail (a big detail maybe?)

And yes, again, I didn't type the command (sorry): 

```
xrandr --addmode ....
```

I'll test that and comment, and I'll test without the KVM switch. ](*,)

Thanks for your time!!

---

### Post by matt_symes on 2013-04-24
Hi

> Before test the new commands, yes I'm using a KVM switch, I'm sorry, you  didn't asked, but I neither specified that detail (a big detail maybe?)

That could be a very big detail. 

KVM switches can stop Ubuntu getting the EDID information from the monitor so it does not know the monitors correct resolution, scan rate and gamma values.

Connect directly to the monitor, reboot and see how you get on. Don't run the commands just yet. Try that first.

EDIT:

> I didn't type the command (sorry):

There's no need to be sorry. Let's just see if we can get this fixed for you :)

Kind regards

---

### Post by chimi_12 on 2013-04-24
Hi, 

Well, as said, I connected the PC directly to the monitor. The system still boots with wrong screen resolution. 

So, I tried to use the xforcevesa option setting it up with the option "e" at the kernel selection menu (as we did before). But this didn't work either. Then I tried the commands you said:

```
$ cvt 128 1024
# 128x1024 58.80 Hz (CVT) hsync: 62.50 kHz; pclk: 10.00 MHz
Modeline "128x1024_60.00"   10.00  128 136 144 160  1024 1027 1037 1063 -hsync +vsync
```

Still gets the message: "Failed to get size of gamma for output default"

Anyway, I continue: 

```
xrandr --newmode "128x1024_60.00"   10.00  128 136 144 160  1024 1027 1037 1063 -hsync +vsync
```

Once again the message appears "Failed to get size of gamma for output default"
Ten I tried:
```
$ xrandr
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      60.0*    75.0  
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0     56.0     65.0  
   640x480        75.0     73.0     67.0     60.0  
  **128x1024_60.00 (0x1bb)   10.0MHz**
        h: width   128 start  136 end  144 total  160 skew    0 clock   62.5KHz
        v: height 1024 start 1027 end 1037 total 1063           clock   58.8Hz

```

So, I continue with the others commands (again the gamma message appears): 

```
xrandr --addmode default "128x1024_60.00"

```

And: 

```
xrandr --output default --gamma 1:1:1 --mode "128x1024_60.00" 
```

But nothing happens. The screen keeps the resolution problem.

Thanks!!

---

### Post by axept on 2013-04-24
You keep writing ****"**_128_x1024**".... Shouldn't it be **_1280_x1024 ? ;)**

---

### Post by matt_symes on 2013-04-24
Hi

We're not having much luck at the moment :(

> 128x1024_60.00 (0x1bb)   10.0MHz

**128**x1024_60.00 10Mhz.

Your using a value of 128 and not 1280 in cvt.

Reboot your PC to get rid of that xrandr setting and copy and paste this command into the terminal.

```
cvt 1280 1024 60
```

That will force it to use 60MHz in the calculation as well (which it would have used anyway).

Please then rerun those xrandr commands.

Kind regards

---

### Post by chimi_12 on 2013-04-24
Hi, 

I already ran the commands (before your reply) with 1280x1024 (without the 60 at the end) and also ran the xrandr (--newmode, --addmode....) commands, but get the same results. 

Thanks!

---

### Post by matt_symes on 2013-04-24
Hi

I think we need to have a good look at the logs as we are getting nowhere fast here.

Boot into the install. Open a terminal and type

```
sudo apt-get -y install pastebinit
```

Enter your password.

Then type (capital X in Xorg):

```
pastebinit /var/log/Xorg.0.log
```

Post the URL it displays into your next post.

Kind regards

---

### Post by chimi_12 on 2013-04-26
Hi,

Sorry to be slow to respond, yesterday was a busy day at the office.

Well, here is the URL of pastebinit.

[http://paste.ubuntu.com/5604832/](http://paste.ubuntu.com/5604832/)

Thanks.

---

### Post by matt_symes on 2013-04-26
Hi

I will look at your log file tomorrow morning buy in the mean time, i know you have tried at leat one different rate but you mat want to try more.

> 1280x1024      60.0*    75.0   
1024x768       75.0     70.0     60.0  

```
xrandr --output default --mode 1280x1024 --rate 75
```

```
xrandr --output default --mode 1024x768 --rate 75
```

```
xrandr --output default --mode 1024x768 --rate 70
```

```
xrandr --output default --mode 1024x768 --rate 60
```

Do any of these give you a good picture ?

Kind regards

---

### Post by chimi_12 on 2013-04-29
Hi,

Already tried what you say. But we still have no success. Tried every mode and rate, and the screen refreshes every time. But the problem persists. I mean, the screen accepts the modes but for some reason, cannot fix the error. 

So, is still there a way to solve this? or is it better reinstall the system?... I installed the system using lubuntu's CD (and remember that I was using the KVM switch while installing) So I think, maybe I can install using the ubuntu's CD and then install LXDE. What do you  think about it? 

EDIT: Maybe use Xubuntu? 

Kind regards!

---

### Post by matt_symes on 2013-04-30
Hi

To be honest, i'm really not sure what to suggest :(

You could try to set the refresh rate to 80 Hz...

> [    16.282] (**) SAVAGE(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz 
[    16.282] (II) SAVAGE(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz ez)

... but i don't think that would work.

I have no experience with savage cards. 

Maybe a bug in shadowfb now that XAA is deprecated ?

Compare and contrast Xorg.0.log from the LiveCD/USB and the installed version. That's what i would do.

Other versions of Ubuntu/Linux may very well have the same problem.

Kind regards

---

### Post by chimi_12 on 2013-05-03
Hi matt_symes, 

Don't worry, I really appreciate your colaboration to solve this problem, I will look if another distro may work without problems. 

Thank you for your time!! 

PD: Sorry to respond until now, I was out of the office the past few days.

Kind regards.

---

### Post by chimi_12 on 2013-05-03
Hi, 

Just want to comment, I just have installed Xubuntu and everything goes ok.. So, must be something in Lubuntu (I don't know what) that didn't let the system works as we expected. I guess that the KVM switch was the problem, but right now, that the systems is working without problems, I think I will not do testings about that.

Kind Regards

---

### Post by matt_symes on 2013-05-03
Hi

Xubuntu is an excellent choice and is what I'm currently using :D

Maybe installing Lubuntu with the KVM switch in place was what caused the problem then. 

I assume you did not install Xubuntu with the KVM switch attached ?

KVM switches can and do sometimes cause problems as they interfere with the various DDC implementations and stop Linux getting the EDID information from the monitor.

In case your interested:

[http://en.wikipedia.org/wiki/Display_Data_Channel](http://en.wikipedia.org/wiki/Display_Data_Channel)

Kind regards

---

### Post by tormod on 2013-06-24
Your original problem looks like [https://bugs.launchpad.net/bugs/1083032](https://bugs.launchpad.net/bugs/1083032)

I don't see why it works in Xubuntu unless you installed an old version, or you are using the vesa driver instead.

---

