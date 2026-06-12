---
title: "Tricky mouse to set up"
date: 2005-03-26
forum: General Help
---

### Post by dlanor78 on 2005-03-26
I've read lots and lots of pages and posts about getting all the mouse buttons/scroll wheels working in linux.  I know it involves editing the xorg.conf file, and using imwheel.  I just can't seem to find the magic configurations to get my mouse working.  My mouse is a GE Deluxe Optical Mouse Model:  97769.  You can see a picture of my mouse by clicking [here.](http://www.4compu.com/applications/search/itemdetails.asp?sku=CG-HO97769)

This little sucker has a left button and right button, two side buttons, and 2 scroll wheels, only 1 clickable.  I beleive in linux speak that makes it a 9 button mouse.

Ideally, I'd like to get the side buttons to go back and forward in firefox/konqueror and the two scroll wheels to scroll in opposite directions (top wheel scrolls down when rolled down, bottom wheel scrolls up when rolled down.  The rest of the buttons should to default normal stuff.  Somehow Knoppix gets the scroll wheels right, but the back and forward buttons still won't work.  I can't seem to figure out how they get those wheels working  :-? 

And while I'm at it, how to you change how fast each turn of the scroll wheel goes?  In xmms this is fairly easy for adjusting the volume, but in web pages and pdf files I'd like it to go a bit faster.

Thanks in advance to anyone that can help with this.

---

### Post by c_dog on 2005-03-27
You really probably don't need to use imwheel, since most programs that scroll now days handle the wheel on the own.

Because this mouse is a non-standard mouse you are going have make some assumptions and fiddle around a little bit. In your xorg.conf file is a line probably something like this:

Option "Protocol" "ImPS/2"

This is basically the langauge your machine is going to try talk to the mouse with. You may be thinking that you want to use it a USB mouse, but for now keep things simple and use it as a PS/2 mouse. First off the "ImPS/2" protocol only understands the most basic mouse codes so use the MS Intellimouse Explorer protocol:

Option "Protocol" "explorerps/2"

It can understand more buttons. You'll then need to guess at how buttons your mouse has. CLUE: the mouse wheel in a linear device, so it's really 2 or 3  (up, down, and maybe center click) buttons depending on whether it has a "wheel click" button or not. So if the each of the wheels total 5 buttons, then you're probably dealing with 9 button mouse. So:

Option "Buttons" "9"

2 of the wheel buttons (one wheel up & down) will tell the PC which buttons are the   
ZAxisMapping Buttons.  We don't know which they are, but for now we'll use buttons #6 & #7"

Option "ZAxisMapping" "6 7"

Save your xorg.conf file and restart X

If you now tried to scroll in Firefox, the side buttons would probably act like a scroll wheel and the wheel like side buttons. Here's where the problem comes in. The buttons may be "1 2 3 4 5 6 7 8 9", but to nautilus or knoq that's are probably not the same order these programs see them. We need to find out once X is started what buttons do what. A little CLI utility called 'xev' ran in a terminal will report back which buttons are which numbers. If it doesn't give a 'button #' for each button click, either the protocol is wrong for the mouse, or you have told xorg the wrong total number of buttons. Once you get all of the buttons reporting you'll need to change their order with xmodmap. Let's say our real side buttons are 6 & 7 and the wheel is 4 & 5, we can change their order:

xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" 

Then try a some pages in Firefox to see if you hit the scroll and side button remapping right. Once they're in the right order you'll probably want to make an executable script file out of your xmodmap command and put it somewhere that will execute on starting X. If you use Kubuntu the ~/.kde/autostart/ directory will do, or you could put it in /etc/X11/xinit/xinitrc.d/ folder

#! /bin/bash
xmodmap -e "pointer = 1 2 3 8 6 7 4 5 9"

Because the wheels up and down are only buttons clicks the way to speed up the scroll is by telling each program scroll more lines per click. Firefox doesn't seem to have menu config to do this, so you'll have to acess it's config by entering 

about:config

in the page address box. There is a mousescrollwheel section which you can change the number of lines to jump per scroll click.

---

### Post by dlanor78 on 2005-03-28
Okay, here's what I have so far:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"explorerps/2"
	Option		"Buttons"		"9"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

with the ZAxisMapping, my main scroll wheel works just fine.  With this config, xev shows no action at all on the second scroll wheel.  I don't think I want to mess with xmodmap until I get X to see this wheel.  I'm pretty sure I'm right about how many buttons it is (left=1, right=1, back=1, forward=1, clickable wheel=3, non-clickable wheel=2).  You were right it using ImPS/2, so I changed that.

I am using this mouse as a usb mouse, but I have no choice right now because I lent my usb-to-ps/2 adapter to someone.  Could this be what's keeping the second scroll wheel from being seen in xev?

Here's what xev says so far:

left click is button 1
scroll wheel is button 2
right click is button 3
main scroll wheel up is 4
main scroll wheel down is 5
back is 6
forward is 7

I guess that would leave the second scroll wheel as 8 and 9...unless they get changed when I finally get the X to see it.

All other buttons are seen in xev so far.  Any other ideas?  Maybe a different protocol or try a different number of buttons in the xorg.conf file?

[edit]
I just noticed that explorerps/2 should be ExplorerPS/2.  No change on that second scroll wheel though :/
[edit/]

---

### Post by c_dog on 2005-03-28
Are the side buttons doing anything  now when you try them forward and back in Firefox? If you're getting xev feedback for them and they're not working in Firefox it's probably because for some crazy reason it still wants 4 & 5 swapped with 6 & 7 to work. Sometimes Button 8 on some mice is also dead button mapping, so you may need to use 10, 11, or 12 Option "Buttons". For USB, ExplorerPS/2 and MouseManPlusPS/2 are a about as advanced as they come. The valid protocol XFree86 or Xorg by default understands are 'Auto, Microsoft, MouseSystems, MMSeries, Logitech, MouseMan, MMHitTab, GlidePoint, IntelliMouse, ThinkingMouse, ValuMouseScroll, AceCad, PS/2, ImPS/2, ExplorerPS/2, ThinkingMousePS/2, MouseManPlusPS/2, GlidePointPS/2, NetMousePS/2, NetScrollPS/2, BusMouse, SysMouse, WSMouse, USB, or Xqueue'. Who knows,  maybe one of the others will squeek a little better.

---

### Post by dlanor78 on 2005-03-29
The back and forward side buttons are actually working correctly (after upping buttons from 9 to 10) but that damn second wheel still has no effect when running xev.  Everything else is working great though :)

Thanks for the list if different mouse protocols.  I might try a few out to see what happens.  And I may up the buttons again and see what that does.  Although if memory serves, Mandrake has been the closest to getting my mouse working properly.  Maybe I'll just install that and try to figure out how they did it.

In the mean time more suggestions are welcome ;)


[update]
I tried upping the buttons to 10, 11, and 12.  No change on the scroll wheel.  I also tried using MouseManPlusPS/2 instead of ExplorerPS/2, and it seemed to have less functionality.  I'm now down to two things I can think of.  Using the mouse as a usb mouse may be having an effect (I'll have to try to get my adapter back from friend).  Or, installing Mandrake because I do believe they had the mouse working by default (or nearly so) and trying to figure out how they did it.  If I can just get xev to at least see the extra scroll wheel, I think the rest would be easy (I hope) ;)
[update]

---

### Post by dlanor78 on 2005-04-02
Hey guys, I just realized I put this in the wrong section.  Just because this problem has stumped me and others I've asked doesn't mean it belongs in the Stumper Questions section!!!

Could an admin or whatever move this to a more appropriate area (maybe  	
"Hoary 5.04 Hardware Help" or "X.org Configuration")?

---

### Post by ubuntu_demon on 2005-04-02
did you try :
sudo dpkg-reconfigure xserver-xorg

---

### Post by dlanor78 on 2005-04-03
demon666_nl, I didn't try that but will give it a try next time I boot into linux.  Results to come later....

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=dlanor78]demon666_nl, I didn't try that but will give it a try next time I boot into linux.  Results to come later....[/QUOTE]
 okay. don't forget to backup your /etc/X11/xorg.conf

"sudo dpkg-reconfigure xserver-xorg" at least works for logitech mouses in my experiences :)

go to system->preferences->mouse to adjust the speed if necessary

---

### Post by dlanor78 on 2005-04-04
Okay, finally got the chance to try that "sudo dpkg-reconfigure xserver-xorg" command.  Still no activity on the second scroll wheel in xev.  Of course I may not answered the options correctly, so I'll keep playing around with it.

And I'm still considering the Mandrake option, just to see if I'm right that it all worked there and to see how it was done.

Thanks for all the help so far.  I think this is the farthest I've gotten on getting this mouse working.  Just 1 wheel left to go!!!

Oh yea, I forgot to mention that I'm using kubuntu (and thus kde) so to change the scroll wheel speed it's a bit different.  In case anyone comes looking, go to Control Center>Perhiperals>Mouse>Advanced tab and change Mouse Wheel Scrolls By: option.

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=dlanor78]Okay, finally got the chance to try that "sudo dpkg-reconfigure xserver-xorg" command.  Still no activity on the second scroll wheel in xev.  Of course I may not answered the options correctly, so I'll keep playing around with it.

And I'm still considering the Mandrake option, just to see if I'm right that it all worked there and to see how it was done.

Thanks for all the help so far.  I think this is the farthest I've gotten on getting this mouse working.  Just 1 wheel left to go!!!

Oh yea, I forgot to mention that I'm using kubuntu (and thus kde) so to change the scroll wheel speed it's a bit different.  In case anyone comes looking, go to Control Center>Perhiperals>Mouse>Advanced tab and change Mouse Wheel Scrolls By: option.[/QUOTE]
 good luck then :)

---

### Post by dlanor78 on 2005-04-10
Well, I give up for now.  I just don't have the time right now to mess with this any longer.  If I ever find a solution to this, I'll try to remember to come back here and post my findings.

---

### Post by ubuntu_demon on 2005-04-11
[QUOTE=dlanor78]Well, I give up for now.  I just don't have the time right now to mess with this any longer.  If I ever find a solution to this, I'll try to remember to come back here and post my findings.[/QUOTE]
 good luck

---

### Post by dlanor78 on 2005-04-13
Okay, so I figured I'd give it another shot.  I booted up knoppix and all the buttons/wheels are detected (although mapped wrong).  I boot back into ubuntu and edit the relevent (I think) parts of the xorg.conf file to match the XFree86Config-4 file from knoppix.  That damn second scroll wheel still can't be seen in ubuntu.  Here's what I have for the mouse in the xorg.conf file now...

```

Section "InputDevice"
	Identifier	"USB Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/input/mice"
	Option		"SendCoreEvents"	"true"
	Option		"Protocol"		"IMPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"5"

```

and under Section "ServerLayout"...

```

InputDevice	"USB Mouse" "CorePointer"

```

So, what could be the problem now?  Could the difference be between xfree86 and x.org?  Or could there be a program that knoppix uses to see and make use of that second scroll wheel?  Please, if anyone knows how knoppix deals with mice, lend me a hand here :)

I'm almost tempted to just install knoppix and go with that...but I'd rather use gnome and just gnome.

Oh yea, I almost forgot to mention that xev in knoppix sees both scroll wheels up and down movements as buttons 4 and 5.  Maybe that will shed some light on the situation to those in the know.

[update]
This in interesting.  I specifically told knoppix to boot using the 2.6.x kernel and the second scroll wheel stopped working.  Booted again like normal (using the 2.4.x kernel) and the seconds scroll wheel worked again.  Now I'm really lost   :wink: Any ideas what to do now (besides buy a new mouse  :-P)?

---

### Post by dlanor78 on 2005-04-13
Okay, the trick is with evdev.  And the first thing to know is that you don't have to apply the gentoo xserver patches to get it to work.  I was stuck on that for awhile.  Here's a direct quote to a post that helped me out...

> 
Just now got this to work WITHOUT imwheel. (Similar to the above) When I used imwheel, my top "fast scroll" button went back in history while everything else worked as it should. This problem has been resolved by not using imwheel.

In my /etc/X11/xinit/xinitrc file I have added:
/usr/bin/X11/xmodmap -e "pointer = 1 2 3 6 7 4 5"

And in my xorg.conf file (I'm running Hoary) I commented out the old pre-configured stuff and replaced it with:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
## Using a fix from [http://www.ubuntuforums.org/showthr...28&page=5&pp=10](http://www.ubuntuforums.org/showthr...28&page=5&pp=10)
Option "Protocol" "evdev"
Option "Dev Name" "Logitech USB Receiver" # cat /proc/bus/input/devices
Option "Dev Phys" "usb-0000:00:0d.0-3/input1" # cat /proc/bus/input/devices
Option "Device" "/dev/input/event4"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
EndSection

Note the different ZAxisMapping. Also, be sure to change the values of Dev Name, Dev Phys, and Device to the appropriate values of your system (`cat /proc/bus/input/devices`). Also, if this is your second pointer (like it is mine) be sure to add Option "SendCoreEvents" "true" in there.


I didn't even have to do the xmodmap bit.  All I did was edit the xorg.conf file like above (but with my own info) and it just worked.  Here's what I have for that section of my xorg.conf (mostly for my future reference  :-P):

```

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "Protocol" "evdev"
	Option "Dev Name" "A4Tech USB Optical Mouse" # cat /proc/bus/input/devices
	Option "Dev Phys" "usb-0000:00:03.1-1/input0" # cat /proc/bus/input/devices
	Option "Device" "/dev/input/event4"
	Option "Buttons" "9"
	Option "ZAxisMapping" "4 5"
EndSection

```

And with that I'm one step closer to becoming linux only  :grin:

---

### Post by Venzor on 2005-08-04
[QUOTE=dlanor78]And with that I'm one step closer to becoming linux only  :grin:[/QUOTE]
I can completely relate.

Thanks for the info! I have the exact same mouse, so you made it easy for me. 

I think a lot of people are using imwheel and setting their **Option "ZAxisMapping"** to the last two numbers of their buttons because, from what I can tell, with older versions of X, anything else would cause problems.

I'm just happy to be able to use the second scroll-wheel for scrolling up and down, now. It's a lot more comfortable for my hand to do it that way.

---

### Post by tanari on 2005-10-19
Help me please configure my mouse. I have A4Tech NB-90 BatteryFREE 2W (2 wheels, one click-able). 

There are total 10 buttons:
1) left mouse button
2) right mouse button
3) wheel click
4) wheel-up
5) wheel-down
6) second wheel-up
7) second wheel-down
8) additional button 1
9) additional button 2
10) additional button 3

You can see photo on a4tech [site]("http://www.a4tech.com/en/product2.asp?CID=90&SCID=92&MNO=NB-90").

"xev" shows:
left button		-	button 1
right button		-	button 3
wheel button  	-	button 2
wheel up		-	button 9
wheel down		-	button 10
second whell up	-	button 10
second wheel down -	button 9
additional 1		-	button 4
additional 2		-	button 5
additional 3		-	button 1

as you can see some buttons "xev" recognize as the same buttons.

my xorg.conf:
> 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons"		"10"
	Option		"ZAxisMapping"		"9 10"
	Option		"Resolution"		"100"
EndSection


---

### Post by greenwom on 2005-11-08
Thanks for the how-to ---- Great Mouse for 12.00 from target.

I have the same GE mouse, this post has helped me get all of the buttons working but how do I get the second scroll wheel going?  

I set the protocal option to "Auto" and the Buttons options to "9"

I haven've tried this part: 
        Option "Dev Name" "A4Tech USB Optical Mouse" # cat /proc/bus/input/devices
	Option "Dev Phys" "usb-0000:00:03.1-1/input0" # cat /proc/bus/input/devices
	Option "Device" "/dev/input/event4"

I changed the cat settings to mach my box, now the second scroll wheel works but it's also 4 and 5 
the two wheels have the same address (4 & 5) now what?

Other than that the back & forward buttons work like a champ and the scroll wheel is sweet.

[http://www.jascoproducts.com/cgi-local/SoftCart.exe/online-store/scstore/p-HO97769.html?L+scstore+rjgg9583ff364036+1131485760](http://www.jascoproducts.com/cgi-local/SoftCart.exe/online-store/scstore/p-HO97769.html?L+scstore+rjgg9583ff364036+1131485760)

Thanks again -- great input

---

