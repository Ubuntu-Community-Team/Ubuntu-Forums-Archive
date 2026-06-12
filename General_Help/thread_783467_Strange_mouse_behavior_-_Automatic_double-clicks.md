---
title: "Strange mouse behavior - Automatic double-clicks"
date: 2008-05-05
forum: General Help
---

### Post by Drax89 on 2008-05-05
Hi,

I just installed upgraded to Hardy and I'm having some very odd problems with my mouse. Whenever I click on something, Ubuntu acts as if I double-clicked, instead. This means that a single click on any icons opens them, instead of selecting them; I have to click and hold on a menu then release on whatever it is that I want to open. I've tried with 3 different mice so far and they all do this on only Ubuntu. Also, very often any Left Mouse Clicks don't even get passed on to the Desktop.
When using my Touchpad, the mouse clicks work correctly, so this leads me to believe that only USB mice don't work.

Is this a known issue? If so, is there a way to fix it?

I'm not using any visual effects, seeing as I'm having a heck of a time getting my video card to work properly :x

---

### Post by PS5000 on 2008-06-22
I am experiencing the same problem on Kubuntu Hardy KDE 3 on an AMD x64. The drag and select text feature also acts a bit funny...  Sometimes, the start position of the selection jumps to a new location.

I tried adjusting the mouse settings, and also I tried a fresh install, but nothing seems to resolve this problem.  (Oddly, I do not have this problem on my Intel based x64 machine running Kubuntu Hardy KDE 3).

Is anyone else experiencing this problem?  What is your hardware?

---

### Post by PS5000 on 2008-07-01
Update:  I am also experiencing this problem on my Intel based x64 machine running Kubuntu Hardy KDE 3.

---

### Post by PS5000 on 2008-07-02
As an FYI for anyone else searching for a solution to this problem, Bug # 196711 provided a fix.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/196711]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/196711")

In /etc/X11/xorg.conf, make the following change...

OLD xorg.conf entry...
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```

NEW xorg.conf entry...
```
# Mouse fix as per bug 196711
Section "InputDevice"
	Identifier	"CorePointer"
	Driver		"mouse"
EndSection
```

This fixes the double-click problem (99% of the time).

However, the start position for the drag and select text operation still jumps to a new location; this is probably an unrelated bug.

---

### Post by mzillich on 2008-08-07
Hi,

I had the same problem after updating from kubuntu 7.something to 8.04.
After reading forum entries and playing around, these are relevant excerpts from my xorg.conf and what solved the problem for me:

  Section "ServerLayout"
  ...
    InputDevice    "Mouse0" "Synaptics Touchpad"
  EndSection
  ...
  Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
    Option         "CorePointer" # <-- ADDING THIS LINE SOLVED THE PROBLEM
  EndSection

Note that adding the following, as was suggested in some posts, did _not_ solve the problem for me:

  Section "ServerLayout"
  ...
    InputDevice    "Mouse0" "CorrrePointer"
  EndSection
  ...
  Section "InputDevice"
    Identifier     "CorePointer"
    Driver         "mouse"
  EndSection

So it seems that  Option "CorePointer"  is the key.

Thanks for You help! Initially I had not the faintest idea where to start...

cheers

---

### Post by hyper_ch on 2008-08-07
well, Kubuntu sets by default to open with 1-click

---

### Post by dvfreelancer on 2008-08-20
I have the same problem on my Ubuntu 8.04 machine using a Logitech USB laser mouse.  It's duplicating mouse clicks.  Here's the mouse configuration from my xorg.conf file:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

I tried changing the identifier to CorePointer but that wiped out my display settings.  

It's so bad I can't use the calculator with the mouse because I can't type in the numbers right.  Instead of 189, I'll get 1889 or 1899.  It does it every second or third mouse click.  Hugely annoying.

---

### Post by mgmiller on 2008-08-20
Here are some things to check.  First go to System > Preferences > Mouse

Look on the Accessibility tab and make sure "Simulated Secondary Click" and "Dwell Click" are not selected.

Next, open your home folder from Places > Home
Click on Edit > Preferences
go to the Behavior tab and make sure "Double Click to Select Items" is selected.

Try toggling between Single click and double click if needed.

Hope this helps.....

---

### Post by dvfreelancer on 2008-08-20
I've been experimenting with some things and it's positively sending two mouse clicks, not a double click, two, sometimes three, single mouse clicks very fast.  

And it goes in streaks.  Some applications seem worse than others, but other than calculator, where it's really obvious, it's hard to tell which ones.

Just an FYI the menu option in preferences is double click to open items, sans select.  

None of those changes or changing the double click speed has made any difference.

---

### Post by IT-Joker on 2008-10-19
I have the same problem.

Sometimes mouse clicks are duplicated, ie after I click my mouse, sometimes second click is fired automatically.
Whether the exta click happens or not seems to be completely random, so far I have failed to observe any pattern in it. 
Checked the mouse settings, nothing "suspicious" enabled. I believe that no setting or feature would produce this anyway, as the behaviour seems random rather than systematic.

I use Microsoft Intellimouse Optical 5-button mouse and have modified the xorg.conf file to support the 4th and 5th button.

The mouse configuration from my xorg.conf
```
Section "InputDevice"
	Option		"Configured Mouse"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"#new explorer protocol...even works with usb mice
	Option		"Buttons"	"7"#tells X11 the number of buttons on the mouse
	Option		"ZAxisMapping"	"4 5"#tells X11 which buttons to use for scrolling, 4 is up, 5 is down (i think)
	Option		"ButtonMapping"	"1 2 3 6 7"
	#	Identifier	"Configured Mouse"
	#	Driver		"mouse"
	#	Option		"Emulate3Buttons"	"true"
EndSection
```
Tried changing the "Configured Mouse" to "CorePointer", but the problem persisted.
Then I tried to comment everything out and only use "minimal" mouse config:
```

	Identifier	"CorePointer"
	Driver		"mouse"
```
but that didn't work either.
Needless to say that the 4th and 5th button stopped working with this setting. 

So, any other ideas, what to try to get this fixed? This bug is extremely annoying :(
Do you think an upgrade to 8.10 (after it's released) would help?

---

### Post by mgmiller on 2008-10-19
One other thing I have experienced over the years is a hardware failure of the mouse itself.  

Sometimes I get multiple clicks or a "failure to click" or the scroll wheel behaves erratically.  Replacement of the mouse was the only practical thing that worked.  I even tried disassembly and cleaning contacts, but that proved temporary or impossible depending on the design of the mouse.   

I also favor the Microsoft 5 & 7 button optical explorer mice. They work great and are fairly inexpensive.  Try swapping the mouse and see what happens.

---

### Post by dvfreelancer on 2008-10-19
> One other thing I have experienced over the years is a hardware failure of the mouse itself. 

Ding! Ding! Ding! We have a winner.  I tried a new mouse and the behavior stopped immediately.  

Don't know why I didn't try that sooner, other than I don't remember a mouse going bad ever before.  

If your mouse starts acting wonky, swap it out with another one and rule out a hardware issue before you start tearing into the OS settings.

---

### Post by mgmiller on 2008-10-19
> Ding! Ding! Ding! We have a winner.  I tried a new mouse and the behavior stopped immediately.    :lolflag:

Glad  I could help.  Like I said, I have had mice fail in the past and they can drive you crazy till you figure that out.

---

### Post by IT-Joker on 2008-10-19
> **mgmiller said:**
> One other thing I have experienced over the years is a hardware failure of the mouse itself.

I have tried connecting my mouse to another computer with the same hardware, but running Windows. It worked perfectly there.
Therefore I suppose that the problem is caused by something in Ubuntu.

---

### Post by mgmiller on 2008-10-20
IT-Joker....Here is what my configuration looks like.  It's a little different from yours.  I am using the same MS 7 button mouse as you.  I am running Hardy at the moment.

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

---

### Post by IT-Joker on 2008-10-22
mgmiller: I have tried tit and seems the problem is fixed
Yay! Thanks

---

### Post by IT-Joker on 2008-11-02
Well, my previous post was a bit premature :(
At first it seemed to be allright with this config, but after some time I noticed that there are duplicated clicks again.

Because it was only couple of days before Ubuntu 8.10 release, I decided to wait and upgrade.

I have upgraded to 8.10 but the problem persists. 
8.10 doesn't use the xorg.conf to configure input devices so currently I'm running my mouse without any specific configuration, but the problem of duplicated clicks still remains.

Also I have tried switching my mouse from USB to PS/2 port... the identifier changed from something like: "Microsoft Microsoft 5-button Mouse with the IntelliEye(TM)" to: "ImExPS/2 Generic Explorer Mouse"
...but it didn't solve the problem.

I noticed that if I run xinput -list there are two other pointer devices: "Virtual core pointer" and "Macintosh mouse button emulation". Should it be like this?

Additionally I noticed that there's quite a little documentation about how to configure devices using the HAL :( And it seems that HAL ignores the button mapping, so I have been so far unable to make the side buttons work.

Is the MS Intellimouse Optical so rare? It's being sold for years now, quite good and inexpensive mouse, I'd say that many people have it.

Anyway, this is very serious problem which makes the whole system barely usable so I hope there's some solution.

---

### Post by mgmiller on 2008-11-02
Since I have the same mouse as you, I figured I'd show you the output of ```
xinput -list
```  in my setup.
```
marty@tux:~$ xinput -list
"Virtual core keyboard"    id=0    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Virtual core pointer"    id=1    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
"Macintosh mouse button emulation"    id=2    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Chicony Saitek Eclipse II Keyboard"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
"Chicony Saitek Eclipse II Keyboard"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
marty@tux:~$ 



```

I also show the mac mouse and my system works fine.  It also shows an entry specific for my mouse: 

"Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"    id=5    

I should also mention I am running 6 Ubuntu boxes, all with the same mouse and no problems on any of them.  Some are hardy, 1 is Intrepid.  The only thing I lost on the Hardy to Intrepid upgrade was the back and forward buttons in nautilus.  They still work fine in Firefox.  If you have any other configuration file questions, let me know.  Hopefully we can find the difference between our systems that is causing your problem.

---

### Post by IT-Joker on 2008-11-03
> **IT-Joker said:**
> I have tried connecting my mouse to another computer with the same hardware, but running Windows. It worked perfectly there.
Therefore I suppose that the problem is caused by something in Ubuntu.
Well, I was still suspicious that the problem might be caused by the mouse itself... so after all I managed to get a brand new mouse of the same model (MS Intellimouse Optical) and check whether that one will have the same problem.
And guess what... it works flawlessly! 

So it's propably safe to say that at least part of the problem actually IS a hardware problem of the mouse itself and replacing the mouse should help.

On the other side... even my old mouse (the one which is duplicating clicks in Ubuntu) seems to be working allright in Windows. 
Therefore I suppose there is something the mouse driver or configuration can do to prevent this problem. 

But the easiest way would propably be to just replace my mouse... I'd say that after more than 4 years of heavy usage it's ready for retirement anyway :lol:

---

### Post by mrb88 on 2008-11-03
I'm having this problem on a Dell XPS M170 laptop. Started when I upgraded 8.04 to 8.10. Reformatted and reinstalled 8.10 from scratch to try to fix, but with no luck. Mouse in question is a laptop touchpad. Anyone had luck?

---

### Post by sadicote on 2009-02-12
Hi, I went to Mouse and saw that Simulated secondary click and Dwell Click were deselected by default, so i selected Simulated secondary click instead and increased the delay to almost 75% of the maximum--and it worked!!

--and now there is this annoying side-effect; everytime i restart i get this message "Assistive Technology is not supported: Enable?/Disable",

also, since this is a recent problem for me, i am inclined to suspect a virus or something.

---

### Post by Davaris on 2009-08-29
delete me

---

