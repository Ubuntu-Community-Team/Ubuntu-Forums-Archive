---
title: "Is mkdir.... and pluma ~/.config.... supposed to work in Ubuntu?"
date: 2017-05-13
forum: General Help
---

### Post by happydog500 on 2017-05-13
OK, here is the background. I love Ubuntu Mate. I had to stop using it because with two monitors hooked up, the default stops at the "ubuntu" screen (secondary is blank). In Mint 18.1, it worked, so I had to switch to it. 
 After a few months, it doesn't work anymore. It will boot up, have to go into "Display" it's all set up the way it's supposed to. I have to click "Apply" and it works until next boot up, where I have to click "Apply" again. 

 Ubuntu Mate will work after I go into "Display" but I have to boot without monitor hooked up first so was really hoping it would work here. So far, I've had to use Mint because it at least boots up with both monitors. 


 I was told in order to make the Display stick after bootup, was to do this;

 >  1. Open Terminal and run xrandr command
2. Make a startup application file
mkdir -p ~/.config/autostart
pluma ~/.config/autostart/primarymonitor.desktop
… the contents:
[Desktop Entry]
Type=Application
Name=Monitor
Comment=Set the default monitor
Exec= xrandr –output VGA1 –primary

… save and quit

PS. Use your own xrandr info for primarymonitor.desktop file.


 I was so excited I found the fix, but in Mint, it didn't work. So far, that's the only help I've gotten. I thought this might be a "Linux" command and not just a Mint Command. I tried it in my Ubuntu test machine, but it didn't work in Ubuntu either. 

 I was wondering if the commands where *supposed* to work in Ubuntu, or if it has a different command? 


 Thank you,
 Chris.

---

### Post by oldos2er on 2017-05-13
What exactly didn't work?

---

### Post by Habitual on 2017-05-13
Hey Chris:

It's 2 steps, so let's run 'em down?

Step1
Open your terminal and issue:
```
mkdir -p .config/autostart/ 
```
It may actually exist but this is ok to run,
You can "see" if it does exist using
```
ls -al ~/.config/autostart/
``` in the terminal before the above mkdir -p action.

So, after either
```
mkdir -p .config/autostart/ 
```or you've verified it already exists,

Step2
[Pluma]("https://en.wikipedia.org/wiki/Pluma_(editor)") is a graphical editor and the command
```
pluma ~/.config/autostart/primarymonitor.desktop
``` creates the file needed by autostart for your startup item

Run 
```
pluma ~/.config/autostart/primarymonitor.desktop
``` and add everything from
```
[Desktop Entry]
Type=Application
Name=Monitor
Comment=Set the default monitor
Exec= xrandr –output VGA1 –primary
...

```

Exit pluma editor and save the file.
When you restart, it should go off like it should.

Pluma could be any editor on your system you are comfortable with. No requirement on editing text. :)

Hope that helps.

---

### Post by happydog500 on 2017-05-14
I read my post and it's quite confusing even for me. Very sorry I could not write it more clearly. 

  Been using Mint and was given the instructions for Mint. I tried it in Mint, but it didn't work. I thought if I could do it in Ubuntu, and it worked, I could switch back to Ubuntu.    

 **What exactly didn't work?** Ubuntu will not boot up with two monitors. When it gets to the ubuntu screen (just before your desktop set up comes up) it stops. Still can use mouse. If I boot up with only one monitor, it will boot up. Hook up the second monitor, it will work after I go into display (doesn't stay that way next time). 

I was hoping I could use what didn't work in Mint, and use it to make ubuntu work. I tried it, but it didn't work, it still won't boot with both monitors working. 

Habitual, I did the original instructions in Ubuntu. Everything went fine, except when I rebooted, it would not boot with both monitors. 

Here is what I did. On the line; >  –output VGA1 –primary I replaced it with; > -output DVI-0 -primary since that's my default monitor. Saved it, rebooted and it didn't boot up.

 I could not write in a day how much of a problem this has caused. Please, Please help me get this solved. I thought if you do the commands, it would work. Why would it not? What can we do to get it to boot to the log in screen? 

 Thank you for the help so far,
  Chris.

---

### Post by oldos2er on 2017-05-14
Can you please tell us the make and model of your video card and monitors?

---

### Post by happydog500 on 2017-05-14
> **oldos2er said:**
> Can you please tell us the make and model of your video card and monitors?

 My video is AMD Radeon HD 6410D. My default desktop monitor is a acer X223w (DVI-0) and my secondary monitor is a Vizio M420SL (VGA-1).

 Thank you,
 Chris.

---

### Post by Hadaka on 2017-05-14
Hi, this is an older post,but i think it will help you.
[https://ubuntuforums.org/showthread.php?t=1982974](https://ubuntuforums.org/showthread.php?t=1982974)
good luck and please let us know the results.
thanks.

---

### Post by happydog500 on 2017-05-14
Pluma is a pretty interesting thing. Been trying all kinds of different information but they don't work. Right now I have;

> [Desktop Entry]
Type=Application
Name=Monitor
Comment=Set the default monitor
Exec= xrandr –output VGA-0 connected 1920x1080+1680+0 (normal left inverted right x axis y axis) DVI-0 connected –primary

I guess as we approach Ubuntu 18.04, I could use Ubuntu 14.04. :(  If I remember right, Ubuntu 14 doesn't even have Mate Tweaks? I want to use Ubuntu, but if it's a choice between Ubuntu 14 or Mint 17.3, I can't use Ubuntu. 

 It is really discouraging for me to see Ubuntu is trying to be a Windows replacement, and it can't even boot with a monitor and a TV hooked up. Man this is discouraging. I love the ubuntu community.

When I just had **DVI-0 -primary** it wouldn't even boot to the log in screen. 

Before I give up, is there anything else we can try? Maybe we just need the right words in Pluma?

Thank you,
 Chris.

---

### Post by happydog500 on 2017-05-14
Tried;

> [Desktop Entry]
Type=Application
Name=Monitor
Comment=Set the default monitor
Exec= xrandr –output DVI-0 -left of VGA-0

Didn't change a thing. 

 Chris.

---

### Post by Habitual on 2017-05-15
> **happydog500 said:**
> Tried;



Didn't change a thing. 

 Chris.

Chris:
It would be helpful if you gave us the link or site where this information is coming from for this autostart entry.

Thanks!

---

### Post by vasa1 on 2017-05-15
I'm just wondering whether "Is mkdir.... and pluma ~/.config.... supposed to work in Ubuntu?" is an apt title for this thread :???:

"Ubuntu will not boot up with two monitors" from OP's [post #4]("https://ubuntuforums.org/showthread.php?t=2361205&p=13644954#post13644954") would be more like it.

---

### Post by happydog500 on 2017-05-15
> **Habitual said:**
> Chris:
It would be helpful if you gave us the link or site where this information is coming from for this autostart entry.

Thanks!


  Link; [http://puolanka.info/goto/how-to-set-external-monitor-as-primary-monitor/]("http://puolanka.info/goto/how-to-set-external-monitor-as-primary-monitor/")

---

### Post by happydog500 on 2017-05-15
> **vasa1 said:**
> I'm just wondering whether "Is mkdir.... and pluma ~/.config.... supposed to work in Ubuntu?" is an apt title for this thread :???:

"Ubuntu will not boot up with two monitors" from OP's [post #4]("https://ubuntuforums.org/showthread.php?t=2361205&p=13644954#post13644954") would be more like it.

 Thank you. Actually, at the time, the title is apt. 

Used ubuntu but could not get the monitor to work right. Had to switch to Mint. When I switched to Mint, I wanted to use "ucaresystem-core" but **NO!! don't use that in Mint**. I was told it does not work in Mint. ubuntu and Mint are not the same, it will not work. 

 Both monitors worked in Mint, but then stopped working after a few months. I was told to do Pluma stuff and saw that it changed the way the monitors worked. Since ucaresystem-core works in one, but not the other, I was wondering if editing the start up monitors with Pluma was the same in ubuntu as it is in Mint. 

I posted the question, to see if it was just a Mint thing. If the same thing works in ubuntu, I could switch back to ubuntu and try the Pluma stuff to get both monitors to work. 

You do make a good point, maybe I should post the question now that I got an answer. Although I did see a post where they say putting two monitors in ubuntu is "past the scope of the operating system." Which I take as it just can't do it. 

Just seems weird that in ubuntu, when you put something in start up, it doesn't start up.  

 Thanks for the reply,
 Chris.

---

### Post by mc4man on 2017-05-15
Maybe it's just me or how you type or c&p but this would be more appropriate for .desktop... (assumes DVI-0 as posted later.
```
Exec=xrandr --output DVI-0 --primary 
```

(i.e., no space between Exec= & the command, use -- instead of –

---

### Post by oldos2er on 2017-05-15
> Although I did see a post where they say putting two monitors in ubuntu  is "past the scope of the operating system." Which I take as it just  can't do it. There are many of us using two or more monitors, me among them. Getting multiple monitors to work depends on your video card's and drivers capabilities, which is why I asked you about that earlier. I'm using an Nvidia card; I have no experience running AMD cards on Linux, but plenty of others do.

---

### Post by happydog500 on 2017-05-16
> **oldos2er said:**
>  I have no experience running AMD cards on Linux, but plenty of others do.

Exactly, there are plenty of people on all kinds of Linux forms, Debian, Mint, openSUSE, that can't get AMD video working in Linux. Why? Because it's beyond the scope of the Operating system. 
 
 Drivers? The distors come with drivers. Can't get them to work. Why? It's beyond the scope of the operating system to get them to work. 

 I am so glad that you got yours to work. That's excellent!! Way to go!! Good job. 

 I can try putting the -- in where I have - to see if that does anything. Wonder if Mint is - and ubuntu is --? 

 I will keep trying a few more things before I give up.

 I wanted ubuntu to work so bad, I posted here offering to pay someone to help, but moderator edited it out because it is a volunteer forum. 

 Very good you got yours to work. Still holding out that I can get the commands or start up words right and get it to work so I can stick with ubuntu. 

 Thank you,
 Chris.

---

### Post by happydog500 on 2017-05-16
Lets try one last thing before I give up and have to go back to the other system. Here is xrandr from my systrem;

```
 xrandr
Screen 0: minimum 320 x 200, current 3600 x 1080, maximum 8192 x 8192
VGA-0 connected 1920x1080+1680+0 (normal left inverted right x axis y axis) 930mm x 523mm
   1920x1080     59.93*+
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.08    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    60.00  
   720x400       70.08  
DVI-0 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050     59.88*+
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1440x900      74.98    59.90  
   1280x960      60.00  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    60.00  
   720x400       70.08  
```

 Based on this, how would you formulate what to put to be saved to start up?

 Thank you,
 Chris.

---

### Post by vasa1 on 2017-05-16
> **mc4man said:**
> ...
i.e., no space between Exec= & the command, use -- instead of –
That illustrates one of the hazards of copy/pasting :(
Another is smart quotes.

---

### Post by happydog500 on 2017-05-21
> **vasa1 said:**
> That illustrates one of the hazards of copy/pasting :(
Another is smart quotes.

 Thank you for the reply.

 Did not work. Had to give up on ubuntu because it doesn't work with my hardware. Went to Mint. Ubuntu Mate 14.04 "Tweaks" doesn't have "Cupertino" like 16.04 does. That's the one that makes it like Apple. Can "Cupertino" be added to 14.04? 
 Read where 14 is not updated very much now (understandable), all the focus is on going foreword. 


  Chris.

---

### Post by vasa1 on 2017-05-21
> **happydog500 said:**
> Thank you for the reply.

 Did not work. Had to give up on ubuntu because it doesn't work with my hardware. Went to Mint. Ubuntu Mate 14.04 "Tweaks" doesn't have "Cupertino" like 16.04 does. That's the one that makes it like Apple. Can "Cupertino" be added to 14.04? 
 Read where 14 is not updated very much now (understandable), all the focus is on going foreword. 


  Chris.
Please open a new thread for each new question with an appropriate title in an appropriate subforum. Please and thanks!

---

### Post by lisati on 2017-05-21
And with that, thread closed.

---

