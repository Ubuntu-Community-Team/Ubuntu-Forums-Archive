---
title: "Unity has crashed, many injured..."
date: 2016-09-14
forum: General Help
---

### Post by TrueNorthist on 2016-09-14
I shutdown my fully functioning and previously flawless 16.04 system today and when I restarted it an hour or so later unity did not respond nor appear when summoned with the mouse pointer, nor did the top bar with the clock etc appear and control-alt-t does not open a terminal any more. I have tried various "google fixes" including the ccsm tool and enabling unity, but nothing has worked. It's weird, I just shut the system down and restarted but unity has run away. I can open a terminal by right clicking the desktop and managed to load firefox that way. Can anybody help me figger this one out? 

Thanks.

---

### Post by Frogs Hair on 2016-09-14
Try Ctrl +Alt + F1, login to TTY and run the following commands. 

```
sudo apt-get install dconf-tools
``` ```
dconf reset -f /org/compiz/
``` ```
sudo reboot
```

---

### Post by TrueNorthist on 2016-09-14
Thanks for responding so quickly! I did as you suggested and got:
```
Cannot autolaunch D-bus without X11 $display
```
Needless to say a reboot had no effect.

---

### Post by Frogs Hair on 2016-09-14
I was afraid of that, but thought it was worth a try. Enter TTY again and try the following because there were many Unity related updates recently.  ```
 sudo dpkg --configure -a 
``````
sudo apt-get -f install
``` ```
sudo reboot
``` 

It might help to know if you are running any proprietary video drivers and if you have any right click/context menu.

---

### Post by TrueNorthist on 2016-09-14
No change I'm afraid. To answer your questions I think I am running the Ubuntu drivers, but did switch them around a while ago while trying to get this machine to cool off a bit. I have no way to check using the gui. This is an Asus N56-VJ laptop with an Intel/Nvidia optimus chipset. As for the right-click/context menu, I am still able to right click the desktop and open a terminal, but nothing else is working. That's how I am running programs like Firefox right now. Unity simply does not function and the dash is refusing to answer as well. I have no way to close any windows or resize etc and have to run everything through a terminal. 

This is an odd failure as I did not do anything other than shut it down and restart an hour later. I vaguely recal an update yesterday but I restarted it a few times since with no trouble, right up until earlier today. An older kernel has the same problems.

---

### Post by Frogs Hair on 2016-09-14
> As for the right-click/context menu, I am still able to right click the desktop and open a terminal

If that's the case try the command posted earlier and reboot. 

```
dconf reset -f /org/compiz/
```

---

### Post by TrueNorthist on 2016-09-14
Still no unity after the restart.

---

### Post by TrueNorthist on 2016-09-14
Sounds like you have joined me in the unity-free space. Do you have an Nvidia chipset?

---

### Post by TrueNorthist on 2016-09-14
Many more and I'll start charging rent. Interesting about the guest account, mine is also functioning as per normal but I am unable to get it online. Based on the very limited info so far I am starting to feel a bit less culpable and am leaning towards some sort of buggy update? If this thread becomes populated with more inmates in unity-free space, then I think it might be confirmed. I guess it happens from time to time.

---

### Post by Frogs Hair on 2016-09-14
Try the following Unity reset command .

```
setsid unity
```

---

### Post by TrueNorthist on 2016-09-14
I should respond as it's my thread, but with the same answer unfortunately. No dice Chicago.

---

### Post by ventrical on 2016-09-14
When booting  hold down shift key to get to GruB bootloader.
Choose <advanced> and then highlight an earlier kernel (if you have one) and then proceed to boot from there.

Regards..

---

### Post by Frogs Hair on 2016-09-14
One last command for now.

 

```
DISPLAY=:0 unity
```

---

### Post by TrueNorthist on 2016-09-14
I already tried an older kernel before posting this question, with no luck. Unfortunately I keep a clean machine and delet really old kernels so I only have 2 aside from the current. Thanks for the suggestion though.

---

### Post by ventrical on 2016-09-14
This might work:

[https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959](https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959)

regards..

---

### Post by TrueNorthist on 2016-09-14
I tried ```
DISPLAY=:0 unity
``` with no change evident. I just noticed I cannot create a new gedit document either, but I digress. I got as output: ```
Invalid Mit-Magic-cookie-1 
Keyunity-panel-service stop/waiting
Unity7 stop/waiting
Unity-panel-service start/running, process 7979
unity7 start/running, process 8040

``` ... Or words to that effect. I may have mis-spelled some of that but I get the feeling unity is running, but just not running properly?

---

### Post by TrueNorthist on 2016-09-14
> **ventrical said:**
> This might work:

[https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959](https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959)

regards..

What part of that conversation? Do I need to go back to the start? This is getting confusing...

---

### Post by ventrical on 2016-09-14
...

```

sudo mv ~/.Xauthority ~/.Xauthority.old
sudo service lightdm restart

```

Do it in a tty (Ctrl + Alt +F1)

---

### Post by Frogs Hair on 2016-09-14
See ventrical's link , I'm out of options for now.

---

### Post by ventrical on 2016-09-14
> **Frogs Hair said:**
> See ventrical's link , I'm out of options for now.

uhhhmmm.. I wish I could see some info from inxi.

Can you :

```

sudo apt-get install inxi

```

and then:
```

inxi -Fxz

```

and paste results...

 if not try..

```

sudo apt-get install nouveau-firmware

```

and reboot

---

### Post by TrueNorthist on 2016-09-14
Still no improvement. I may have typed the commands wrong but I did not get any errors. Just to be safe I also rebooted but no joy in unity-free space. Any body else get a positive result?

---

### Post by TrueNorthist on 2016-09-14
I missed the latest response from Ventricle. It is kinda tricky as I cannot copy and paste into a terminal and have to first write the code, then type it and come back here to report. I will go try the new code and post back.

---

### Post by QIII on 2016-09-14
A note about the context and continuity of this thread:  I have removed a number of hijack posts to provide the OP with one on one help.  That may leave a few odd sentences that may no longer seem to make sense in a couple of posts.

---

### Post by TrueNorthist on 2016-09-14
That's a lotta info to manually write it all down then repost here! But if you could point me to some specific parts of the output you wish to see? I did see a section describing the display driver etc. That part? I could copy that down in detail if you wish. Sorry, but I do not have copy/paste functions and have to close everything to go into tty, then reboot etc, all while using muscles in my hand that have grown weak to write everything on paper.

I did try the second code
```
sudo apt-get install nouveau-firmware
```
with no joy in Palookaville. Still floating in a shapeless and souless unity free void.

---

### Post by QIII on 2016-09-14
TrueNorthist --

Although typically not appropriate, an image of the screen captured by a cell phone camera might be appropriate in this sort of circumstance.  Cramping hands are not fun!  :)

---

### Post by TrueNorthist on 2016-09-14
> **QIII said:**
> TrueNorthist --

Although typically not appropriate, an image of the screen captured by a cell phone camera might be appropriate in this sort of circumstance.  Cramping hands are not fun!  :)
I seen a book once. I will boot up some hardware and take a few selfies of my mug in front of the output! Great idea. I shall see if I can snap a still of that inxi output.

---

### Post by ventrical on 2016-09-14
I am just wondering about Xorg and driver.

---

### Post by TrueNorthist on 2016-09-14
Behold the wonders of modern technology, in the hands of an ape:
[IMG]http://i.imgur.com/GikTZgM.jpg[/IMG]

The writer's cramp!

NA out of X? Hmmmm....

---

### Post by ventrical on 2016-09-14
Ahhh ... amazing  looks like it has Intel driver for Intel set but which one is internal/external.  I would bet if you hooked up external monitor to extra video out you would get screen. :)


Uh.. I think you have to set video priority in BIOS and perhaps you tried to use 2 screens and it broke ?

regards..

---

### Post by TrueNorthist on 2016-09-14
I have never run a separate screen. It has never been used as a display driver, but this makes sense. I get the strong feeling unity is actually working but something has changed the display? How can I reset the display to the correct one using terminal? I am really loathe to start monkeying in the bios if I can avoid it... How could a bios setting get messed up by rebooting the system?

---

### Post by TrueNorthist on 2016-09-14
And for the record I do not see a display selection or priority or whatever in the bios. I did notice that the clock was wrong on the windows side of my computer and corrected it. It does kinda feel like the display has been changed somehow, like my system thinks I have a TV hooked up to it and it's not showing the unity etc side of things? I guess I'll search google some more and see if there is a way to switch the display in a terminal. I can't even close a window, or a program or anything that used to have a close x. That's all gone. Everything opens full screen, just like it would on a separate display. Well, not quite everything but darned near.

Many thanks for all past and hopefully future assistance. Here's to hoping I wake up to an update that sorts this out. I know it can be hard to believe but I really didn't do anything to cause this. Except maybe turn it off and on again...

---

### Post by TrueNorthist on 2016-09-14
Good news and bad news... Good news is unity is back up, but will need some restorative actions to get it back walking and chewing gum at the same time again. Bad news is I have no idea why, only that running Bleachbit did something that worked in my favour. I read another comment in General Help where a fella described how --among a wholesale deleting/renaming/modifying extravaganza -- he also deleted his cache and he was fairly sure that was therapeutic. But which cache I wondered, and what other worms would I be poking at by invoking the dreaded Bleachbit? I deselected many of the items that BB annihilates _ensuring the system cache was selected_, then let her rip. After a good scrub I rebooted et voilà, a "normal" but very inexperienced desktop. 

I just need to customize it a bit, then get back to mindlessly chewing on hay while staring blankly at the screen. Nothing like swatting a fly with a 50 megaton thermonuclear device set to explode at ground level. Kaboooom. Good morning gentlemen. I am an H.A.L. 9000 computer. Would you like to hear me sing a song?

Thanks to all who tried valiantly to assist a drowning slug.

edit: I marked this thread as solved, mostly because the problem is gone and that I have described the manner I used to get there. I do NOT make any claims as to what exactly went wrong, only that deleting the system cache seems to work for the problem I had. It would be nice to find out precisely what went sideways but beggars can't be choosers. I'll take the win by hook or by crook.  My gut feeling is a setting was changed, not by me, that made the OS "think" I was using a monitor, and Unity was not active. Clearing the cache restored display back to defaults, maybe?

---

### Post by ventrical on 2016-09-14
Here is the manual:

[http://dlcdnet.asus.com/pub/ASUS/nb/N56VJ/E6951_Emanual_N56VM_N56VZ.pdf](http://dlcdnet.asus.com/pub/ASUS/nb/N56VJ/E6951_Emanual_N56VM_N56VZ.pdf)

 [s]I think maybe something got toggled. In some cases you have to hook and external monitor to get it back.[/s]

Also noticed : tty size 170X48 which is not right.

[s]You can try to just boot from a USB ISO stick and see what happens.

If you had Windows and did the Windows upgrade to Windows 10 it may have spoofed the nVidia chip.

Also if you accidently changed the video mode you might have to hook up external monitor. If USB boot works then something is borked in your install and we'll have to start from scratch:)[/s]


 I think perhaps this is xorg problem.
Regards..

---

### Post by TrueNorthist on 2016-09-15
Thanks for striking all that out. I fully understand that it can be nearly impossible to believe when folks say they did nothing to cause a problem when most of the time they did, but simply might not realize it. However in this case I really did not do anything other than turn my system off and on again. I did not connect any monitors nor manipulate any settings and a long since upgraded windows 10 had not been awakened for weeks. Nope, in this case something external must have triggered a change to the display settings I reckon. I will still check my recent updates and watch for a bug report as I want to know what went wrong and make sure things are stable after all the fiddling I did yesterday. Fortunately I did not tamper with anything fatal.

Everything seems to be fine today however. Just a few tweaks needed and a few lost settings. I will adjust the TTY res once I divine a method. Maybe related?

---

### Post by ventrical on 2016-09-15
I believe you.  I was thinking of another matter altogether and somehow I bifurcated from the focus of your original message. My apologies.

Perhaps Frogshair might have somehting up his sleeve :)

Regards

---

