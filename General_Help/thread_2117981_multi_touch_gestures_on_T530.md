---
title: "multi touch gestures on T530"
date: 2013-02-19
forum: General Help
---

### Post by curiousgally on 2013-02-19
Hi,

I recently bought a lenovo thinkpad T530 and installed ubuntu 12.10.  Wanted to know if I can get touch gestures to work on my touchpad like 3 fingers swipe etc for changing tracks in music etc. I got the 2 finger scroll to work without a problem. Is the number of gestures a hardware limitation or a software one ?  Any help is appreciated. googling leads me to no-where. 

Thanks.

---

### Post by Melclic on 2013-04-17
Hello curiousgally,

I recently got the three finger swipe to work, after a loooooonnngg time googling. You can see if touchegg works for you: 
[http://code.google.com/p/touchegg/](http://code.google.com/p/touchegg/)
It  enables a lot of configuration of your synaptics touchpad. For me  however it was a dead end. My solution is a little derivative hack from
[http://rickey-nctu.blogspot.co.uk/2011/09/ibm-developer-ubuntugesture-perlubuntu.html](http://rickey-nctu.blogspot.co.uk/2011/09/ibm-developer-ubuntugesture-perlubuntu.html)

First and foremost, you should check if your hardware detects three fingers.

Get your copy the synaptics configuration file and copy it to the following location:
```
sudo cp /usr/share/X11/xorg.conf.d/50-synaptics.conf /etc/X11/xorg.conf
```
Modify the file you have just copied
```
sudo gedit /etc/X11/xorg.conf
```
Find the section enclosed by 'Section "InputClass"' 'EndSection' that contains 'Identifier "touchpad catchall"'

And add the lines 'Option "SHMConfig" "on"' and 'Option "Protocol" "event"' for it to look something like this:
```
Section "InputClass"
   Identifier "touchpad catchall"
   MatchIsTouchpad "on"
   MatchDevicePath "/dev/input/event*"
   Driver "synaptics"
   Option "SHMConfig" "on"
   Option "Protocol" "event"
EndSection
```
Then you have to restart X, or just restart you laptop. After that type in the terminal 
```
synclient -m 100
```
And move your cursor around. There should be a column named "f" and it should return the number of fingers that you are being detected. If that number includes 3 when you press with three finger your touchpad supports three finger swipe. Congrats!

Right; now download the file attached and save it where you want. And to test it:

```
python /path/to/file
```

Try the three finger swipe. I have configured it so to change workspace.

If that works for you and you configured it to your needs, just add it to your start up applications with the command
```
bash -c "python /path/to/file"
```
Basically the file monitors the synclient and detects when three fingers have been activated and returns an appropriate action. You can set the actions yourself and the sensitivity of the swipe movements.

Hope this helps

---

### Post by jpgrms on 2013-04-22
hi thanks for this tutorial... i found my hardware detecting up to 3 fingers... however, upon testing the downloaded script, an error is appearing:

     sh: 1: xdotool: not found

how do i fix this? i also want to be able to shift workspaces using 3-finger swipe as i think it's cool...

---

### Post by Melclic on 2013-04-22
All you need to do is:
```
sudo apt-get install xdotool
```
Remember that the sensibility of the toucpad is different on each laptop, so set your own sensibility by playing with the numbers in the script. For example the line:
```
if diff_y > 800:
```
I would increase and decrease this value and see what works for you.

---

### Post by Subbeh on 2013-04-23
Thanks so much! Works perfectly!

---

### Post by Melclic on 2013-04-23
here is the pastebin of  it [http://pastebin.com/taUP6ei1](http://pastebin.com/taUP6ei1)/

---

### Post by mic585 on 2013-05-03
Hello! i tried this suggestion for multitouch and so far it's working perfectly. However i would like to be able to both bind 3 finger and 4 finger gestures ( i noticed my touchpad supports this, so why not use it ).
I tried the following but it isn't functioning the way i expect. (i just send simple keystrokes for debugging purposes in terminal)

```
import os
import re
import subprocess

if __name__ == "__main__":
    cmd = 'synclient -m 100'

    p = subprocess.Popen(cmd, stdout = subprocess.PIPE, stderr = subprocess.STDOUT, shell = True)
    skip = False
    first = True
    start = False
    start_x = 0
    start_y = 0
    diff_x = 0
    diff_y = 0    
    try:
        while True:
            line = p.stdout.readline()
            if not line:
                break
            try:
                tokens = [x for x in re.split('([^0-9\.])+', line.strip()) if x.strip()]
                x, y, fingers = int(tokens[1]), int(tokens[2]), int(tokens[4])
            if fingers==3:
            if not start:
                start_x = x
                start_y = y
                start = True
        if start and not fingers==3:
            diff_x = x-start_x
            diff_y = y-start_y
            #MODIFY THE NUMBERS BELLOW FOR SENSITIVITY
                        #if diff_y > 300:
                        #        os.system("xdotool key ctrl+Left")
                        #elif diff_y < -300:
                        #        os.system("xdotool key ctrl+Right")
            if diff_x > 100:
                                os.system("xdotool key a")
                        elif diff_x < -100:
                                os.system("xdotool key b")
            start = False
            start_x = 0
            start_y = 0
            diff_y = 0
            diff_x = 0
        if fingers == 4:
            if not start:
                start_x = x
                start_y = y
                start = True
        if start and not fingers == 4:
            diff_x = x-start_x
            diff_y = y-start_y
            if diff_x > 100:
                os.system("xdotool key c")
            elif diff_x < -100:
                os.system("xdotool key d")
            start = False
            start_x = 0
            start_y = 0
            diff_y = 0
            diff_x = 0
            except (IndexError, ValueError):
                pass
    except KeyboardInterrupt:
        pass 
```


Using this script , 3 finger swipes give no output and 4 finger swipes give unlogical data to me.

Another think that i would like to achieve is to be able to bind 3 finger swipe to back and forward. I can for example bind this to alt+Right and alt+Left and have the same shortcut in firefox, however then this will not work in my file explorer. Is it possible to send a back and forward command like the side buttons of a mouse does for example?

---

### Post by Melclic on 2013-05-04
ok the firs thing i would do is monitor the synclient to reproduce the four finger swipe as best as possible. Take care to note the sensibility between the x and y axis

```
synclient -m 100
```

I took the liberty of changing the script above. I think the problem was the gestures conflicting with each other. However I cannot test it since my touchpad does not support 4 fingers. 

[http://pastebin.com/TFHLnVdr](http://pastebin.com/TFHLnVdr)

But let me know if that works for you. Basically I have separated completely the two gestures; where one cannot work while the other is being monitored

As for the application specific gestures I will need to look into that...

If anyone reads this and has any suggestions I would love to hear about them.

---

### Post by kid1994hn on 2013-05-06
It's great! But I want to use 3 finger as back button on my browse and nautilus.. How can I configure it?

---

### Post by mic585 on 2013-05-08
> **Melclic said:**
> ok the firs thing i would do is monitor the synclient to reproduce the four finger swipe as best as possible. Take care to note the sensibility between the x and y axis

```
synclient -m 100
```

I took the liberty of changing the script above. I think the problem was the gestures conflicting with each other. However I cannot test it since my touchpad does not support 4 fingers. 

[http://pastebin.com/TFHLnVdr](http://pastebin.com/TFHLnVdr)

But let me know if that works for you. Basically I have separated completely the two gestures; where one cannot work while the other is being monitored

As for the application specific gestures I will need to look into that...

If anyone reads this and has any suggestions I would love to hear about them.

Would it be possible to include the code in your post? The pastebin link is not working for me.

EDIT : It seems pastebin is not working on the nework i'm currently on (School). I'll try again when i get back home.

---

### Post by marcoordonez on 2013-09-19
Thank you so much, the code works well.

---

### Post by Jonathan_Veersma on 2013-09-20
Works great! How should I edit the script if I want to use "Ctrl + Three finger gesture" as input?

---

### Post by Amit_Kulkarni on 2013-10-18
Thanks a lot! This is the only solution that worked for me. For some time, at least.

I'm facing a problem after upgrading Kubuntu from 13.04 to 13.10. While adding the two lines to xorg.conf, I noticed it's slightly different compared to what it was before.
Here are the contents (after adding the two lines):

[FONT=courier new]# Example xorg.conf.d snippet that assigns the touchpad driver[/FONT]
[FONT=courier new]# to all touchpads. See xorg.conf.d(5) for more information on[/FONT]
[FONT=courier new]# InputClass.[/FONT]
[FONT=courier new]# DO NOT EDIT THIS FILE, your distribution will likely overwrite[/FONT]
[FONT=courier new]# it when updating. Copy (and rename) this file into[/FONT]
[FONT=courier new]# /etc/X11/xorg.conf.d first.[/FONT]
[FONT=courier new]# Additional options may be added in the form of[/FONT]
[FONT=courier new]#   Option "OptionName" "value"[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "touchpad catchall"[/FONT]
[FONT=courier new]        Driver "synaptics"[/FONT]
[FONT=courier new]        MatchIsTouchpad "on"[/FONT]
[FONT=courier new]        Option "SHMConfig" "on"[/FONT]
[FONT=courier new]        Option "Protocol" "event"[/FONT]
[FONT=courier new]# This option is recommend on all Linux systems using evdev, but cannot be[/FONT]
[FONT=courier new]# enabled by default. See the following link for details:[/FONT]
[FONT=courier new]# [http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html](http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html)[/FONT]
[FONT=courier new]      MatchDevicePath "/dev/input/event*"[/FONT]
[FONT=courier new]EndSection[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "touchpad ignore duplicates"[/FONT]
[FONT=courier new]        MatchIsTouchpad "on"[/FONT]
[FONT=courier new]        MatchOS "Linux"[/FONT]
[FONT=courier new]        MatchDevicePath "/dev/input/mouse*"[/FONT]
[FONT=courier new]        Option "Ignore" "on"[/FONT]
[FONT=courier new]EndSection[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# This option enables the bottom right corner to be a right button on[/FONT]
[FONT=courier new]# non-synaptics clickpads.[/FONT]
[FONT=courier new]# This option is only interpreted by clickpads.[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "Default clickpad buttons"[/FONT]
[FONT=courier new]        MatchDriver "synaptics"[/FONT]
[FONT=courier new]        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"[/FONT]
[FONT=courier new]#       To disable the bottom edge area so the buttons only work as buttons,[/FONT]
[FONT=courier new]#       not for movement, set the AreaBottomEdge[/FONT]
[FONT=courier new]#       Option "AreaBottomEdge" "82%"[/FONT]
[FONT=courier new]EndSection[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# This option disables software buttons on Apple touchpads.[/FONT]
[FONT=courier new]# This option is only interpreted by clickpads.[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "Disable clickpad buttons on Apple touchpads"[/FONT]
[FONT=courier new]        MatchProduct "Apple|bcm5974"[/FONT]
[FONT=courier new]        MatchDriver "synaptics"[/FONT]
[FONT=courier new]        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"[/FONT]
[FONT=courier new]EndSection[/FONT]



I tried following the procedure anyway, but the "synclient -m 100" gives this error:

[FONT=courier new]synclient: invalid option -- 'm'
Usage: synclient [-h] [-l] [-V] [-?] [var1=value1 [var2=value2] ...]
  -l List current user settings
  -V Print synclient version string and exit
  -? Show this help message
  var=value  Set user parameter 'var' to 'value'.

[/FONT]Am I doing anything wrong here?

---

### Post by strofo on 2013-11-04
> **Amit_Kulkarni said:**
> Thanks a lot! This is the only solution that worked for me. For some time, at least.

I'm facing a problem after upgrading Kubuntu from 13.04 to 13.10. While adding the two lines to xorg.conf, I noticed it's slightly different compared to what it was before.
Here are the contents (after adding the two lines):

[FONT=courier new]# Example xorg.conf.d snippet that assigns the touchpad driver[/FONT]
[FONT=courier new]# to all touchpads. See xorg.conf.d(5) for more information on[/FONT]
[FONT=courier new]# InputClass.[/FONT]
[FONT=courier new]# DO NOT EDIT THIS FILE, your distribution will likely overwrite[/FONT]
[FONT=courier new]# it when updating. Copy (and rename) this file into[/FONT]
[FONT=courier new]# /etc/X11/xorg.conf.d first.[/FONT]
[FONT=courier new]# Additional options may be added in the form of[/FONT]
[FONT=courier new]#   Option "OptionName" "value"[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "touchpad catchall"[/FONT]
[FONT=courier new]        Driver "synaptics"[/FONT]
[FONT=courier new]        MatchIsTouchpad "on"[/FONT]
[FONT=courier new]        Option "SHMConfig" "on"[/FONT]
[FONT=courier new]        Option "Protocol" "event"[/FONT]
[FONT=courier new]# This option is recommend on all Linux systems using evdev, but cannot be[/FONT]
[FONT=courier new]# enabled by default. See the following link for details:[/FONT]
[FONT=courier new]# [http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html](http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html)[/FONT]
[FONT=courier new]      MatchDevicePath "/dev/input/event*"[/FONT]
[FONT=courier new]EndSection[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "touchpad ignore duplicates"[/FONT]
[FONT=courier new]        MatchIsTouchpad "on"[/FONT]
[FONT=courier new]        MatchOS "Linux"[/FONT]
[FONT=courier new]        MatchDevicePath "/dev/input/mouse*"[/FONT]
[FONT=courier new]        Option "Ignore" "on"[/FONT]
[FONT=courier new]EndSection[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# This option enables the bottom right corner to be a right button on[/FONT]
[FONT=courier new]# non-synaptics clickpads.[/FONT]
[FONT=courier new]# This option is only interpreted by clickpads.[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "Default clickpad buttons"[/FONT]
[FONT=courier new]        MatchDriver "synaptics"[/FONT]
[FONT=courier new]        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"[/FONT]
[FONT=courier new]#       To disable the bottom edge area so the buttons only work as buttons,[/FONT]
[FONT=courier new]#       not for movement, set the AreaBottomEdge[/FONT]
[FONT=courier new]#       Option "AreaBottomEdge" "82%"[/FONT]
[FONT=courier new]EndSection[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]# This option disables software buttons on Apple touchpads.[/FONT]
[FONT=courier new]# This option is only interpreted by clickpads.[/FONT]
[FONT=courier new]Section "InputClass"[/FONT]
[FONT=courier new]        Identifier "Disable clickpad buttons on Apple touchpads"[/FONT]
[FONT=courier new]        MatchProduct "Apple|bcm5974"[/FONT]
[FONT=courier new]        MatchDriver "synaptics"[/FONT]
[FONT=courier new]        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"[/FONT]
[FONT=courier new]EndSection[/FONT]



I tried following the procedure anyway, but the "synclient -m 100" gives this error:

[FONT=courier new]synclient: invalid option -- 'm'
Usage: synclient [-h] [-l] [-V] [-?] [var1=value1 [var2=value2] ...]
  -l List current user settings
  -V Print synclient version string and exit
  -? Show this help message
  var=value  Set user parameter 'var' to 'value'.

[/FONT]Am I doing anything wrong here?

I have a same problem after upgrading to Ubuntu 13.10. It looks like a SHMConfig option doesn't work.

---

### Post by Jonathan_Veersma on 2013-11-10
> **strofo said:**
> I have a same problem after upgrading to Ubuntu 13.10. It looks like a SHMConfig option doesn't work.

[COLOR=#333333][FONT=Helvetica]Upgrading to 13.10 removes the '-m' option.[/FONT][/COLOR]
[https://github.com/iberianpig/xSwipe/issues/4](https://github.com/iberianpig/xSwipe/issues/4)

---

### Post by FireSBurnsmuP on 2013-11-13
[EDIT] Whoops, read twice, ask not.

Pretty slick little script, though. Thanks a mil!

Any chance that there's some way, by modifying this script, to invert the scroll direction of the default-enabled 2-finger scrolling? Because that would just be awesome.

---

### Post by Hyunjae_Park on 2014-02-11
Hi, I'm following you instruction, and i got an error in here.

stevepark@ubuntu:~$ synclient -m 100
synclient: invalid option -- 'm'
Usage: synclient [-h] [-l] [-V] [-?] [var1=value1 [var2=value2] ...]
  -l List current user settings
  -V Print synclient version string and exit
  -? Show this help message
  var=value  Set user parameter 'var' to 'value'.


Can i ask what the problem is???

Thank you!

---

### Post by DanielFerreira on 2014-03-16
Hello!

Same here! Isn't there a way to retrieve the the same data other way? It seems that "-m" flag has been deprecated. :S

Thank you!

---

### Post by Anil3a on 2014-05-05
> **Melclic said:**
> Hello curiousgally,

I recently got the three finger swipe to work, after a loooooonnngg time googling. You can see if touchegg works for you: 
[http://code.google.com/p/touchegg/](http://code.google.com/p/touchegg/)
It  enables a lot of configuration of your synaptics touchpad. For me  however it was a dead end. My solution is a little derivative hack from
[http://rickey-nctu.blogspot.co.uk/2011/09/ibm-developer-ubuntugesture-perlubuntu.html](http://rickey-nctu.blogspot.co.uk/2011/09/ibm-developer-ubuntugesture-perlubuntu.html)

First and foremost, you should check if your hardware detects three fingers.

Get your copy the synaptics configuration file and copy it to the following location:
```
sudo cp /usr/share/X11/xorg.conf.d/50-synaptics.conf /etc/X11/xorg.conf
```
Modify the file you have just copied
```
sudo gedit /etc/X11/xorg.conf
```
Find the section enclosed by 'Section "InputClass"' 'EndSection' that contains 'Identifier "touchpad catchall"'

And add the lines 'Option "SHMConfig" "on"' and 'Option "Protocol" "event"' for it to look something like this:
```
Section "InputClass"
   Identifier "touchpad catchall"
   MatchIsTouchpad "on"
   MatchDevicePath "/dev/input/event*"
   Driver "synaptics"
   Option "SHMConfig" "on"
   Option "Protocol" "event"
EndSection
```
Then you have to restart X, or just restart you laptop. After that type in the terminal 
```
synclient -m 100
```
And move your cursor around. There should be a column named "f" and it should return the number of fingers that you are being detected. If that number includes 3 when you press with three finger your touchpad supports three finger swipe. Congrats!

Right; now download the file attached and save it where you want. And to test it:

```
python /path/to/file
```

Try the three finger swipe. I have configured it so to change workspace.

If that works for you and you configured it to your needs, just add it to your start up applications with the command
```
bash -c "python /path/to/file"
```
Basically the file monitors the synclient and detects when three fingers have been activated and returns an appropriate action. You can set the actions yourself and the sensitivity of the swipe movements.

Hope this helps




Hi
while i run the following code, its gives me error :
```
synclient -m 100
```

```

synclient: invalid option -- 'm'
Usage: synclient [-h] [-l] [-V] [-?] [var1=value1 [var2=value2] ...]
  -l List current user settings
  -V Print synclient version string and exit
  -? Show this help message
  var=value  Set user parameter 'var' to 'value'.

```

I also downloaded the file and tried running the file mTouch.py but no good.

Please help, I am using 14.04 ubuntu in HP Pavilion g7

---

### Post by nikhil4 on 2014-06-30
Hi , i  tried your solution on my laptop runing ubuntu 14.04  and everything worked well till the step synclient -m 100 command  the output i got was -m is not alid option 
synclient: invalid option -- 'm'
Usage: synclient [-h] [-l] [-V] [-?] [var1=value1 [var2=value2] ...]
  -l List current user settings
  -V Print synclient version string and exit
  -? Show this help message
  var=value  Set user parameter 'var' to 'value'.

will your solution work for me ?

---

