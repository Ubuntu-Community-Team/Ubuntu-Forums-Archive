---
title: "Make middle mouse click scroll"
date: 2007-06-19
forum: General Help
---

### Post by torswin on 2007-06-19
My search skills are not the best in the world, but I've tried to fix this for a week.

Anyway, I want to make the middle mouse button click to a scroll like you see in Windows. I'm getting so #%!"%¤! annoyed that it starts PASTING instead of scrolling and it has made me almost going back to windows...

Could anyone help me? I've tried to add two lines in the /etc/X11/xorg.conf file, but it didn't help...

this is how it looks like:
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option 		"EmulateWheel" 		"true"
	Option		"EmulateWheelButton" 	"2"
EndSection

Thanks for the help :)

---

### Post by FuturePilot on 2007-06-19
The middle click functions as Paste. I'm not sure if you can get rid of that. I find it a handy feature. When you scroll the wheel does it still act as a scroll? I've never heard of clicking it to scroll.

---

### Post by torswin on 2007-06-19
scrolling without clicking works as a charm, it is just that i prefer to NOT PASTE when i click the middle mouse button cause that is waht i use Ctrl + v for. if i cant at least disable it from pasting, i'll go over to windows as it makes the surfing experience much more difficult for me

---

### Post by Znupi on 2007-06-19
You can do it in Firefox by typing in the address bar **about:config** and changing **general.autoScroll** to **true**.

---

### Post by arsenic23 on 2007-06-19
It took me a long time to stop hitting the middle mouse button to lock in autoscroll when I first started using linux.  It was really annouying, because in Opera, if you paste randomly outside of a text box like this then your taken to a google search for the last thing you highlighted or copied.  I'd go to scroll down the page and suddenly be at a google search page for some random bit of text my idle hand had highlighted while I was reading.

I still sometimes miss autoscrolling with my hands behind my head all nice and reclined in my chair, but I think I've finally gotten used to not using the middle mouse button.  Though if you have a way to get autoscrolling with it to work ( but only when using a certain program ) I'd be terribly interested in see it.

---

### Post by tak1150 on 2007-06-19
Thanks Znupi!

Your how-to really works! (but not too good with Beryl; the cursor leaves a trail, but hey)

BTW, I noticed this autoscroll works by default in Thunderbird

Also, for xorg.conf, this is what I have and my middle button works like a real middle button.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

hope this helps

---

### Post by Znupi on 2007-06-19
> **tak1150 said:**
> but not too good with Beryl; the cursor leaves a trail, but hey

It works perfect for me...

---

### Post by firstlife on 2007-06-19
Here's how you can fix it in Firefox. Go to about:config and (optionally) type in "mouse" in the search line. 
Find the following and change them to the value indicated.

To stop pasting with middle click and instead invoke the auto scroll "+"

In preferences, on the Advanced tab, enable "Use autoscrolling", "Smooth Scrolling", and (optionally) change in about.config:
middlemouse.contentLoadURL = false
middlemouse.openNewWindow = false
middlemouse.paste = false

Turn off Horizontal Back with mouse (mainly touchpad):

mousewheel.horizscroll.withnokey.action = 1     (default 2)
mousewheel.horizscroll.withnokey.numlines = 1   (default -1 which will be wrong direction)

Turn off changing font size with Ctrl + Vertical Scroll (which can be a horrible accident)

mousewheel.withcontrolkey.action = 0 (default 3)

About the action values for scrolling:
0=nothing but scroll
1=nothing but scroll???
2=back
3=change font size
4=no smooth scroll

Now you can all go back to using the middle mouse button.

---

### Post by Adanac on 2007-09-01
Ah YES!!! I finally got frustrated by not being able to lock the scroll when reading sites with lots of text, that I finally searched how to get it to work in linux and found this. THANK YOU!

---

### Post by jac0b on 2007-09-06
> **Znupi said:**
> You can do it in Firefox by typing in the address bar **about:config** and changing **general.autoScroll** to **true**.

Worked like a charm thanks

---

### Post by TwoD on 2007-10-22
Awsome, thank you so much!

This combined with these settings in xorg.conf, to make my extra mouse buttons become Back and Forward, is really convenient. (Logitech MX518 mouse)
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
EndSection

```

It puzzles me why standard settings like this are set different between OS:es.
It's extremely annoying to switch from Windows to Ubuntu because of all these "hidden" options being different in programs which you think "should" behave the same.

Many people don't even know about the "about:config" page, and when they can't even find a hint about even more advanced settings being customizable on that page they simply give up, thinking Windows is more user-friendly by default.

I read somewhere that Microsoft says what features do in their "ads", while Linux users/devs state their (cryptic) names/acronyms. Like "Get news and weather directly on your desktop now with RSS/ATOM feeds!" vs "Desktop integrated RSS & ATOM parser", or something like that.

Search for "Linux NFS" on Google for example. The first hit is their sourceforge page with "Linux NFS Overview, FAQ and HOWTO Documents", but you need to read quite a bit before even finding out what NFS means and is used for. Same thing with finding out about these settings in Firefox...

Anyways, sorry for dragging this a bit off topic, but I think user-friendliness is more than just having customizable options in an app, you've got to tell people they are there too. Especially if the default-behavior differs largely from a wide-spread alternative app.

---

### Post by idomagic on 2007-10-26
In opera, just go to tools, preferences, advanced, shortcuts, "middle click options" and select your preferred mode.

Regarding finding information about different systems and technical features wikipedia is usually the better choice compared to google, no matter OS. 

Commercials and different "userfriendly" translations of technical terms usually end up quite the opposite for everyone who needs or wants to know more details on what technology is behind it all.

In the end it's all about your perspective, to me "RSS" says a whole lot more and is far more userfriendly than the term "newsfeed".

---

### Post by Klab0 on 2008-04-27
Thanks a lot guys. I really love the auto scroll function as well. It really comes in handy when being a linux newb, having tons of forum threads to browse through as well =)

---

### Post by hsushi22 on 2008-06-17
Thanks, this has been really helpful.

---

### Post by prabath_fun on 2008-06-18
I did just 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Buttons" "5"
EndSection

works. Can anyone tell me what is 
"Buttons" "7", 
"Emulate3Buttons"	"true",   
"ButtonMapping" "1 2 3 6 7"

Option's.

Prabath

---

### Post by unutbu on 2008-06-18
According to 
/usr/share/doc/xserver-xorg-input-mouse/README.gz

> "Buttons" "7"
means you have a 7-button mouse. "Currently there is no reliable way to automatically detect the correct number. This option is the only means for the X server to obtain it. The default value is three."

> "Emulate3Buttons" "true"
means pressing buttons 1 and 3 simultaneously will emulate button 2. (Actually, the readme does not say this, but I believe that's what it means).

> "ButtonMapping" "1 2 3 6 7"
is a remapping of the physical buttons to new button meanings. 
```

  Physical Buttons        Reported as:
  ------------------------------------
  1 Left Button             Button 1
  2 Wheel Button            Button 2
  3 Right Button            Button 3
  4 Wheel Negative Move     Button 6
  5 Wheel Positive Move     Button 7

```

---

### Post by prabath_fun on 2008-06-18
Hi,
  Thanks.
Yes, The default value is 3. and for 3 different buttons.

But 5 buttons are sufficient right! why 7? 
1. left click
2. right click.
3. middle click.
4. up scroll
5. down scroll.

Why 4 and 5 is mapped to 6 and 7? Is there any specific reason?

With Thanks,
Prabath

---

### Post by unutbu on 2008-06-19
You know prabath_fun, I think you are right and I think the documentation (/usr/share/doc/xserver-xorg-input-mouse/README.gz) might be wrong.

The xorg.conf line 

```
"ButtonMapping" "1 2 3 6 7"
```

makes sense if it is telling X that whenever the 6th button on the mouse is pressed, treat it like a Wheel Negative Move event (which is usually called button 4), and similarly, when the 7th button is pressed, treat it like a Wheel Positive Move event (which is usually called button 5). 

So perhaps the table (which essentially came from the README) is backwards, and it should really be:

```
  Physical Buttons        Reported as:
  ------------------------------------
  1      		  Button 1  Left Button        
  2      		  Button 2  Wheel Button       
  3      		  Button 3  Right Button       
  6      		  Button 4  Wheel Negative Move
  7      		  Button 5  Wheel Positive Move
```

I don't know for sure. However, if you have an 8-button mouse like the Logitech MX518, it would be easy to find out with just a bit of experimenting.

---

### Post by TwoD on 2008-06-19
I have an MX518, what kinds of experiments do you mean, unutbu?
In my setup, see my post above, the 8th button (up on top of the mouse), acts just like the middle button/scroollwheen click.

The 6th and 7th buttons (left side) work like back and forward in FF etc.

---

### Post by unutbu on 2008-06-19
As far as any X application is concerned, when you click a mouse button, it recognizes that a "Button 1 ButtonPress event" has occurred. (Or Button 2,3,4, etc.)
The X app knows nothing about left clicks or right clicks, it only knows Button # events. 

So it is the job of the ButtonMapping option to map physical mouse clicks to X events.

I was a little cloudy on exactly how ButtonMapping worked, however, but TwoD's question prodded me into realizing I could do an experiment to learn how ButtonMapping worked myself.

I only have a 3-button mouse, so the question that I tried to resolve was:

What does
Option		"ButtonMapping" "2 3 1"
mean?

Does it mean

```
Physical Button is reported as X Button (Right)
---------------------------------------
1 Left                         2
2 Wheel                        3
3 Right                        1
```

or does it mean

```
Physical Button is reported as X Button (Wrong)
---------------------------------------
2 Wheel                        1
3 Right                        2
1 Left                         3
```

I found out it means the former, not the latter.

Here is what I did:

I edited /etc/X11/xorg.conf to include
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ButtonMapping" "2 3 1"
EndSection
```

Log out, log back in. This causes the X server to re-read xorg.conf. 
Run xev. A little window pops up, in which you make the following sequence of clicks: Left click, Wheel click, Right click

xev outputs the following:

```
ButtonPress event, serial 30, synthetic NO, window 0x2200001,
    root 0x13a, subw 0x0, time 2727278431, (80,110), root:(926,142),
    state 0x10, **button 2**, same_screen YES                                <-- left button

ButtonPress event, serial 30, synthetic NO, window 0x2200001,
    root 0x13a, subw 0x0, time 2727280825, (80,110), root:(926,142),
    state 0x10, **button 3**, same_screen YES                                <-- wheel button

ButtonPress event, serial 30, synthetic NO, window 0x2200001,
    root 0x13a, subw 0x0, time 2727282737, (80,110), root:(926,142),
    state 0x10, **button 1**, same_screen YES                                <-- right button
```

I edited the output a little so it's easier to see the important lines.

As you can see, a left button press corresponds to a Button 2 event, wheel means 3, right means 1. 

So: 
```

Option		"ButtonMapping" "2 3 1"
```

means

```
Physical Button is reported as X Button
---------------------------------------
1 Left                         2
2 Wheel                        3
3 Right                        1
```


By extension, I conclude that 
```

"ButtonMapping" "1 2 3 6 7" 
```

means

```
Physical Button is reported as X Button
---------------------------------------
1 Left                         1
2 Wheel                        2
3 Right                        3
4 ?                            6
5 ?                            7

```
(The documentation /usr/share/doc/xserver-xorg-input-mouse/README.gz was correct, my second-guessing it was wrong).

What an X application decides to do with a Button 6 or 7 X event is up to the application. Apparently, for TwoD, Firefox has been programmed or configured so that when ever a Button 6/7 event occurs, it goes back/forward a link.

TwoD, would you please open a terminal and run xev, and then click each of your 8 mouse buttons? Using the output of xev, you should be able to fill in the blanks of this table:

```
Physical Button is reported as X Button
---------------------------------------
1 Left                         1
2 Wheel                        2
3 Right                        3
4 ?                            6
5 ?                            7
6 ?                            6?
7 ?                            7?
8 ?                            8?

```

I'd particularly like to know:

1) What physical action you need to do to produce each X Button event. 
2) Can you produce a Button 4 or 5 event? My prediction is you can't.
3) What happens if you comment out the ButtonMapping option in xorg.conf? Then log out, log in, and run xev. Can you now produce Button 4 and 5 events? and does your table now look like this:

```
Physical Button is reported as X Button
---------------------------------------
1 Left                         1
2 Wheel                        2
3 Right                        3
4 ?                            4
5 ?                            5
6 ?                            6?
7 ?                            7?
8 ?                            8?

```
TwoD, please also post the Section "InputDevice" stanza corresponding to your mouse from your xorg.conf. Other options there might affect the results in the table.

---

### Post by peakshysteria on 2008-06-19
> **Znupi said:**
> You can do it in Firefox by typing in the address bar **about:config** and changing **general.autoScroll** to **true**.

Is there a way to keep the paste on midle click feature and still have smooth scroll in FF (i guess you guys are talking about smooth scroll??).

Also I can use the thumb buttons on my Logitech MX510 to go back or forward in pages in FF. But not in the filemanager. Is there a way to navigate back and forward with the buttons in both filemanager and FF?

---

### Post by prabath_fun on 2008-06-19
:confused:    :cry:      :sad:

Thanks

---

### Post by TwoD on 2008-06-21
Peakshysteria: I have paste on middle-click and I can use the thumb buttons on my MX518 as back/forward both in FF and the filemanager Nautilus. As noted below, those buttons are simply mapped to Alt+Right and Alt+Left respectively, so any program using that key combo for back/forward should have support for the thumb buttons too.

Ubutnu:
You can see my Input Section in post #11 in this thread.
Here's my xev output:
```

=====================================
Left

ButtonPress event, serial 30, synthetic NO, window 0x5400001,
    root 0x1a6, subw 0x0, time 138836720, (138,119), root:(1438,181),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x5400001,
    root 0x1a6, subw 0x0, time 138836788, (138,119), root:(1438,181),
    state 0x110, button 1, same_screen YES

=====================================

Middle/Scrollwheel

ButtonPress event, serial 30, synthetic NO, window 0x5400001,
    root 0x1a6, subw 0x0, time 138838164, (124,118), root:(1424,180),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x5400001,
    root 0x1a6, subw 0x0, time 138838300, (124,118), root:(1424,180),
    state 0x210, button 2, same_screen YES

=====================================
Right
ButtonPress event, serial 30, synthetic NO, window 0x5400001,
    root 0x1a6, subw 0x0, time 138839240, (93,115), root:(1393,177),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x5400001,
    root 0x1a6, subw 0x0, time 138839332, (93,115), root:(1393,177),
    state 0x410, button 3, same_screen YES

=====================================
Scroll up/forward (away from me)

ButtonPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139194420, (15,126), root:(2247,902),
    state 0x10, button 4, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139194420, (15,126), root:(2247,902),
    state 0x810, button 4, same_screen YES

=====================================
Scroll down/backward (towards me)

ButtonPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139265432, (2,26), root:(2234,802),
    state 0x10, button 5, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139265432, (2,26), root:(2234,802),
    state 0x1010, button 5, same_screen YES
=====================================
"Forward" (small thumb button away from me)

LeaveNotify event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139435952, (3,149), root:(2139,191),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

KeyPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139435954, (3,149), root:(2139,191),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139435954, (3,149), root:(2139,191),
    state 0x18, keycode 102 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139435954, (3,149), root:(2139,191),
    state 0x18, keycode 102 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139435954, (3,149), root:(2139,191),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

EnterNotify event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139436104, (3,149), root:(2139,191),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

=====================================
"Back" (big thumb button nearest me)

KeyPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139477816, (8,102), root:(2144,144),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139477816, (8,102), root:(2144,144),
    state 0x18, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139477816, (8,102), root:(2144,144),
    state 0x18, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139477816, (8,102), root:(2144,144),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

EnterNotify event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139477991, (8,102), root:(2144,144),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


=====================================
Top

ButtonPress event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139568155, (3,150), root:(2139,192),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x5600001,
    root 0x1a6, subw 0x0, time 139568339, (3,150), root:(2139,192),
    state 0x210, button 2, same_screen YES

```

Which gives this table:
```

Physical Button is reported as X Button
---------------------------------------
1 Left                         1
2 Wheel                        2
3 Right                        3
4 Scrool up                    4
5 Scroll down                  5
6 Small thumb/forward          Alt_L+Right (7)
7 Big thumb/backward           Alt_L+Left  (6)
8 Top button                   2

```

NOTE:  I just found out that if I hold one button down and click the thumb buttons, they generate Button 6/7 messages instead of the Alt+Left/Right key messages. This is not the case when commenting out the ButtonMapping line.


With ButtonMapping commented, the result was this:
```

Physical Button is reported as X Button
---------------------------------------
1 Left                         1
2 Wheel                        2
3 Right                        3
4 Scrool up                    4
5 Scroll down                  5
6 Small thumb/forward          9
7 Big thumb/backward           8
8 Top button                   2

```
Back/Forward in FF still worked as expected, but in Nautilus those buttons worked just like the left button.

I also tried changing the number of buttons from 7 to 8 (which is actually what the MX518 has), but that made no difference, was hoping to make the top one do something different and perhaps make it useful in games.

---

### Post by unutbu on 2008-06-21
TwoD, what happens if you change your xorg.conf mouse section to:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons" "8"
	Option		"ButtonMapping" "1 2 3 4 5 6 7 8"
EndSection
```

Also, do you have the imwheel package installed?
The behavior of your side buttons sounds like you have an imwheel config file controlling this functionality.

I found some information about this which possessors of mice-with-many-buttons may find useful:
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)
[https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons)

---

### Post by TwoD on 2008-06-22
The thumb buttons stopped working completely. They did not generate any events at all. The other buttons still worked fine.

Yes I have imwheel installed, with default config I believe.

On a sidenote, I got tired of the "Emulate3Buttons" options the other day, because some program required me to switch between left/right button quickly, and absolutely not press the middle button. Now I can let the left/right button clicks overlap without worrying about it triggering a middle button event. :)

---

### Post by unutbu on 2008-06-22
> **peakshysteria said:**
> 
Also I can use the thumb buttons on my Logitech MX510 to go back or forward in pages in FF. But not in the filemanager. Is there a way to navigate back and forward with the buttons in both filemanager and FF?

Peakshysteria, try 

```

sudo apt-get install imwheel  # You probably have this, but just in case...
imwheel -c
```

A configuration window should pop up which should allow you to define what your side thumb buttons do on a per-application basis.

If you define the thumb buttons to produce Alt_L+Left and Alt_L+Right key press events in Nautilus, then I think you'll get the behavior you want.

See
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)
[https://help.ubuntu.com/community/In...ForwardButtons](https://help.ubuntu.com/community/In...ForwardButtons)
for more information.

---

### Post by peakshysteria on 2008-06-23
Thanks a million man. But will this leave my precious paste on middle-click? Or those it remove it? I really would like both to work.

---

### Post by unutbu on 2008-06-23
I've never used imwheel, so I can't say for sure, but my guess is imwheel should help you add functionality to your side buttons and should not change your middle mouse click. Here is the description from the imwheel package:
```

apt-cache show imwheel

Description: program to support non-standard buttons on new mice
 Many new mice include side or "thumb" buttons that have little or no function
 in Linux, as well as a wheel that is still not used by all applications.
 .
 IMWheel supports these non-standard buttons and/or wheel operations by
 allowing the user to map their input to key combinations which can vary
 depending on the application in use.

```

---

