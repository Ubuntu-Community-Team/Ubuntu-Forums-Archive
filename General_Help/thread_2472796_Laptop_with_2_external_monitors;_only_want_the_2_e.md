---
title: "Laptop with 2 external monitors; only want the 2 externals"
date: 2022-03-12
forum: General Help
---

### Post by goemonburo on 2022-03-12
I have a Dell Inspiron 3511, a docking station D3100, and 2 external monitors.  I do have the slow graphics issues that some folks have noted, but as I'm not gaming or doing high speed video stuff, this is basically fine.

However, what I want is to have ONLY the 2 external monitors on when they're plugged in, and switch to the lone laptop screen if I'm on the road.  However, despite lots of fiddling with the display options, it seems that I'm stuck with having 3.  Which means that sometimes alerts pop up on the laptop, not visible, and I have to open up the clamshell when I finally figure out they're there.  Also, I have to log in on the laptop screen before it switches to the externals.

Does anyone know if I'm stuck with this by virtue of it being the USB docking station and DisplayPort software?  Or can I configure it to shut off the laptop screen if I've got the externals plugged in?  That's been easy in all other systems I've had, but somehow this one is not playing nice.

Thank you!

---

### Post by mIk3_08 on 2022-03-13
Please go to your terminal and run the command below and paste the result here in thread wrap with code. Thanks and regards.
```
hostnamectl status
```

---

### Post by mIk3_08 on 2022-03-14
Hi. the command i gave you will give us a little information about your machine so that people in Ubuntuforum community that are willing to help you may also know what system you have. Thanks and regards.

---

### Post by HermanAB on 2022-03-14
I would try to disable the local onboard video in the BIOS settings. If that is not possible, then I would make a startup script with “xrandr” to configure the video.

---

### Post by mIk3_08 on 2022-03-15
> **goemonburo said:**
> I have a Dell Inspiron 3511, a docking  station D3100, and 2 external monitors.  I do have the slow graphics  issues that some folks have noted, but as I'm not gaming or doing high  speed video stuff, this is basically fine.
However, what I want is to have ONLY the 2 external monitors on when  they're plugged in, and switch to the lone laptop screen if I'm on the  road.  However, despite lots of fiddling with the display options, it  seems that I'm stuck with having 3.  Which means that sometimes alerts  pop up on the laptop, not visible, and I have to open up the clamshell  when I finally figure out they're there.  Also, I have to log in on the  laptop screen before it switches to the externals.
Does anyone know if I'm stuck with this by virtue of it being the USB  docking station and DisplayPort software?  Or can I configure it to shut  off the laptop screen if I've got the externals plugged in?  That's  been easy in all other systems I've had, but somehow this one is not  playing nice.
Thank you!
> **HermanAB said:**
> I would try to disable the local onboard video in the BIOS settings. If that is not possible, then I would make a startup script with “xrandr” to configure the video. I agree with you HermanAB. This is one of the possible way to solve his issue. Regards.

---

### Post by goemonburo on 2022-03-15
Here is the output of `hostnamectl status`:

```
Static hostname: xxxxxxxx
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: xxxxxxx
           Boot ID: xxxxxxx
  Operating System: Ubuntu 20.04.4 LTS
            Kernel: Linux 5.13.0-35-generic
      Architecture: x86-64
```

---

### Post by goemonburo on 2022-03-15
Wouldn't disabling the local onboard video in Bios mean I'd be stuck any time I don't have it hooked up to the external monitors?  That would solve the issue of having 3 but might be a bigger hassle than what I'm currently doing.

Thank you for the suggestions, though.  I appreciate your time.  If it's still useful, I have put the output of that program, too.

---

### Post by #&amp;thj^% on 2022-03-15
This one can be a bit of scare it will disable the chosen monitor, you'll want to have mutiple monitors attached to finish. (Also a TTY session will work)
find your monitor with 
```
xrandr -q
```
mine:
```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080    120.00*+

```
My laptop display is "DP-2 "
So i would use:
```
xrandr --output DP-2 --off

```
I would advise you to have more than one monitor up before doing this.
now when you know your going to travel activate it with:
```
xrandr --output DP-2 --auto

```

---

### Post by goemonburo on 2022-03-15
@1fallen, thanks you for the suggestion.  I will give this a try but given my penchant for forgetfulness, I'm liable to be in the airport turning the computer on before I remember I never did the "xrandr --output DP-2 --auto" and will I be totally stuck at that point until I can hook up a monitor?  Or will using the keyboard display options work?

---

### Post by #&amp;thj^% on 2022-03-15
> **goemonburo said:**
> @1fallen, thanks you for the suggestion.  I will give this a try but given my penchant for forgetfulness, I'm liable to be in the airport turning the computer on before I remember I never did the "xrandr --output DP-2 --auto" and will I be totally stuck at that point until I can hook up a monitor? **_ Or will using the keyboard display options work?_**
Yep, just do a key combo Ctrl + F3, then login, and you will have to rember this:
```
xrandr --output DP-2 --auto
```
Imporant to make sure that "DP-2" is your laptop display. That refernce was mine. use "xrandr -q" to be sure, this is critical.
I'll add an alias if that would help.
BTW: As soon as you add another montior, you can achive the same as I posted in Post #8
EDIT: Easy to rember alias:
run:
```
leafpad .bashrc
```
add these two lines just below where it shows "#aliases"
```
alias dp1="xrandr --output DP-2  --off"
alias dp2="xrandr --output DP-2  --auto"
```
Of course change DP-2 to your screen.
save and close.
fire up your terminal or a TTY and use:
dp1 to turn off and dp2 to regain your monitor. Thats not hard to remember now, hopefully.:)

---

### Post by goemonburo on 2022-03-15
@1fallen, thank you very much.  It looks very useful and I think I'll do the alias method you mention just in case.  Easier to remember like you say!

---

### Post by goemonburo on 2022-03-15
So I've done exactly what you suggested and to my surprise, it works really well overall!  Interestingly, I don't seem to need the "dp2" alias because when the monitors are unplugged and I restart it goes to the laptop screen automatically.  Then when I plug the externals back in I have to again do "dp1" to get the laptop to turn off.

Now the only additional question would be is there any way to do this at boot?  So that if the external monitors are plugged in, it will boot up to those rather than to the laptop?  Am I just asking for the moon?  It's not a showstopper to open the clamshell briefly, log in, close it, open a terminal, type "dp1" and go on from there...but it's just so odd that every other laptop I've ever had does this all automatically.  

Anyway...thank you very much for the help thus far.  I'm willing to leave it at this unless fixing this last issue is pretty simple.

---

### Post by mIk3_08 on 2022-03-16
> **goemonburo said:**
> So I've done exactly what you suggested and to my surprise, it works really well overall!  Interestingly, I don't seem to need the "dp2" alias because when the monitors are unplugged and I restart it goes to the laptop screen automatically. 

 see... I've told you that the people of Ubuntu community forum never failed to support your needs. Now, we have just to wait a little time for your additional concern request. 
It is better if you can open other thread post for this if you can't received any reply to your additional concern request and mark this as solve. Regards 
> **goemonburo said:**
> 
Now the only additional question would be is there any way to do this at  boot?  So that if the external monitors are plugged in, it will boot up  to those rather than to the laptop?  Am I just asking for the moon?   It's not a showstopper to open the clamshell briefly, log in, close it,  open a terminal, type "dp1" and go on from there...but it's just so odd  that every other laptop I've ever had does this all automatically.  
Anyway...thank you very much for the help thus far.  I'm willing to  leave it at this unless fixing this last issue is pretty simple.

---

