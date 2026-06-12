---
title: "Using external monitor as ONLY monitor for laptop"
date: 2014-04-13
forum: General Help
---

### Post by Quevvy on 2014-04-13
I have an old laptop (Vista originally) with 64-bit 13.10 on it. Everything works for the most part except the screen. The screen is extremely dim, but it is readable in the right lighting conditions for short periods of time. I didn't think it'd be worth it to fix the screen issue, so I'm using it as a media player hooked up to my TV via VGA. Whenever I turn on the computer, it tries to extend the display and then all the main icons, etc. are on the laptop display, which is not useful.

Also, it doesn't natively support 720p as a resolution, so whenever I turn it on, I manually add 1280x720 (see code) and then select it, also turning off the laptop's display. In some reading I did earlier, it sounded like persistent changes were easier in earlier versions of Ubuntu, but now I can't find the methods to do that. If I have set the 720p resolution and then restart the computer, it tries to do 720p, but then can't and shows an error message. When I click "OK" on the error message, my screen goes black and then resets to the previous default (not sure why it has to go to black and then reset?).

Basically, I would like to permanently set the default display settings to using the external monitor with 1280x720 (not typically on the display settings menu) resolution and the laptop's display off. How do I do this?

Current code I use to add the 1280x720 resolution:
```

xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --addmode VGA-0 "1280x720_60.00"

```

---

### Post by germanix on 2014-04-13
Go to system-settings, then to screen display. You should now see both of the displays in the window. Click on the laptop display and with the buttons below set the laptop display to "off" and the launcher placement to the external monitor. Then click on the external monitor and and choose the display settings (1280x720), then hit the "apply" button. On my hardware the display setting 1280x720 is available for choosing. (I run Ubuntu 14.04) This works on my system, hope it works on yours.

---

### Post by Quevvy on 2014-04-13
Yes, I know how to do that. My question is pertaining to how to keep those display settings across a reboot. As of now, when I reboot, it defaults to extending the display and the (broken) laptop display as the primary.

---

### Post by 23dornot23d on 2014-04-13
I have had similar problems as the backlight went a long time back on one laptop I have .........

I get around the problem by using arandr and leaving a script on the desktop to click .....

But this can also be put in .config/autostart if you only have one setting ..........

Which desktop are you using ? unity - gnome-shell - xfce4 - lxde ?


Also another way is the (xorg.conf if you are running a nvidia driver) I have managed this
with Nvidia-settings and setting it up when going into the desktop.

But non seem to stick ..... someone mentioned using the config files for lightdm
[http://ubuntuforums.org/showthread.php?t=2214380](http://ubuntuforums.org/showthread.php?t=2214380)

and there is a thread in the latest version explaining it - the latest version is
taking more care over how the graphics is handled too ........ as with lightdm now
the User input flicks to the screen with the mouse on it ...........

---

### Post by Quevvy on 2014-04-13
I am using Unity. I have an ATI card, but fglrx and amdcccle just make everything crash, so I've decided to just try to handle the display issues through Ubuntu itself.

I tried modifying the lightdm file, but it made the display crash similar to what fglrx and amdcccle did to my system. I restored to the backup if the lightdm file, and everything is back to before, but my original issue still persists.

Maybe I should just wait until 14.04 officially comes out? Or get the final beta?

---

### Post by 23dornot23d on 2014-04-14
> 
Maybe I should just wait until 14.04 officially comes out? Or get the final beta? 				


Check here to see what is still causing problems .......... [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

People tend to be better off with a clean install alongside their own OSs ....... should they decide to try it out

But it still is in beta for a few more days .......

As I say I use Nvidia - so am not sure what issues you may come across with these ATI card, but fglrx and amdcccle

17th april is the official release date.

---

### Post by HermanAB on 2014-04-14
BTW, it is usually quite easy to replace the screen backlight tube of a Laptop PC.

---

### Post by 23dornot23d on 2014-04-14
Cheers 
                                     [                                                      [IMG]http://ubuntuforums.org/images/avatars/CircleofFriends80x80.png[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=44990")                                                                                     [**[COLOR=#000000]HermanAB[/COLOR]**]("http://ubuntuforums.org/member.php?u=44990")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]
I have watched a few videos on this on you-tube and it looks a easy job - if in a workshop - but first need to check
whether its the inverter or the backlight that is the main problem ,, mmm need a test to do this.

[http://youtu.be/2Yi6GNFcP3w](http://youtu.be/2Yi6GNFcP3w)

It was my intention to do the change ..... never got around to it though as I have older monitors
sitting around doing nothing - so just hooked them up. 
( maybe one day will take it all to bits but seems having the right tools and testing equipment / also spare parts is important )

The jobs are always easy when the right things are at hand - cheers for the reply though as I may have a go sometime in
the future ...... as I have the tools to do the job .

and from what the op says ...... its probably the backlight or the inverter that has gone .... ( having the sun shine on it or
shine a bright light at it ) - can get to see what I need just to boot the grub menu up and choose the options ....... then the rest can be
 done on the monitor or TV as ( that too is connected via HDMI ).

The OP may have to do the same ?
> 
The screen is extremely dim, but it is readable in the right lighting conditions for short periods of time


Check out more of the videos on that link I posted they show how to replace either the back light or inverter should one
 of those be your problem too .........

This seems to be one of the better videos showing the procedure with the guy telling us all the reasons why he is doing it
the way he is .... [http://youtu.be/w4v20PyomuU](http://youtu.be/w4v20PyomuU) ...... and what to watch out for .....

---

### Post by Quevvy on 2014-04-14
I had tried replacing the inverter before, but will try replacing the backlight.

But in the mean time, is the consensus that I cannot set the external monitor only as default between reboots? If this is true, do you know of any Ubuntu variants(Xubuntu, Lubuntu, etc.) that *can* support this?

What if I just unplugged the laptop's built-in display? (Partially asked as a joke, but may work?)

---

### Post by 23dornot23d on 2014-04-14
I have not tried this out yet - but it may be worth a try ...... ( was a answer I found to someone having problems with a broken screen )
> 
when you power up the laptop close the lid immediately, it will use the external monitor as the default.


Do not shut it fully though as it may go into sleep mode .... my own seems to work with about a inch gap ..... at the front with the
lid partially closed on knoppix - on mint it does this [http://i.minus.com/i1XhWbg2M7eFH.png](http://i.minus.com/i1XhWbg2M7eFH.png)
and ubuntu ..... not tried it - but its the next job on my list of things to try out ..... just keeping this updated with what I have tried
arandr ... nvidia-settings - xorg.conf ....... lid partially closed ...... not taken laptop to bits yet as I quite like it being in one piece
we are heading into bodging it territory and I am trying not to go there - but when all options seem to run out - what do you do.

HELP !!! ( actually time to take it to the repair shop - maybe - as taking things to bits can lead to more problems sometimes )

If it does not work - it may be worth searching around the net for people with broken screens and what they have done
attaching external monitors.  

I found that answer here at Toms Hardware after a lot of searching through the comments ........  
[http://www.tomshardware.co.uk/answers/id-1868501/connect-broken-laptop-screen-external-monitor.html](http://www.tomshardware.co.uk/answers/id-1868501/connect-broken-laptop-screen-external-monitor.html)

---

### Post by Quevvy on 2014-04-16
So, I guess that works - shutting the lid right after pushing the button. I have it set to do nothing when the lid is closed, so that seems to avoid making it go to sleep. I wish there were a better solution, but this works for now. Thanks!

---

### Post by 23dornot23d on 2014-04-16
Your welcome - its by no way ideal - but gets over a problem - but costs nothing ....... 

glad it worked for you .......

My worry is in taking my own apart - although I take desktop computers apart ..... laptops are a little too fiddly
for me to be messing around with . ( otherwise I could try the other method we had mentioned - but no real point now )

---

