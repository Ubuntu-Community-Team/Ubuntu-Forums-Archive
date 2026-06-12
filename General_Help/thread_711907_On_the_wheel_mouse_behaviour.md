---
title: "On the wheel mouse behaviour"
date: 2008-03-01
forum: General Help
---

### Post by elio.mussi on 2008-03-01
Hi everybody, I'm a relatively new user to Linux and would like someone to clear this out.
I've discovered recently (pardon my unexperience!) that, if some text is highligthed and you press the mouse wheel (third button) you paste the selection in the cursor position.

My problem.
I'm writing sources on NetBeans and often I scroll up and down in my source. I do this by fastly rotating the wheel. Sometimes, a very light prssure on the wheel makes me paste unwanted selections in my source. Moreover, as I'm going up and down fastly, I get at noticeing this only at compile time.

Dreamed solution.
Does anyone envision a way to make the pasting action happens only when I really want to paste? Any way to disable the pasting function from the wheel? I definitely would prefer to copy and paste just only with Ctrl-C and Ctrl-V.

---

### Post by banewman on 2008-03-01
you can edit your /etc/X11/xorg.conf file for that.
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
Change the second last line to
```
	Option		"Emulate3Buttons"	"false"

```
:)

---

### Post by jeffus_il on 2008-03-01
> **banewman said:**
> you can edit your /etc/X11/xorg.conf file for that.
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection
```Change the second last line to
```
    Option        "Emulate3Buttons"    "false"

```:)

There is a problem here, the opposite might work, but not this.
 ```
"Emulate3Buttons"    "true"
``` will cause the left and right buttons pressed together to emulate the center button. This would be preferable since it would move the click away from the mouse wheel which is what elio.mussi wants. I don't know if this will work on a 3 or 5 button as he has as it is meant to work on an old two button mouse.
```
"Emulate3Buttons"    "false"
``` is the behavior which he currently has, that is the middle button (combined with button four and five as a button, scroll up, and scroll down) is not being emulated by the two side buttons.

My guess is that ```
"Emulate3Buttons"    "true"
``` has a chance of working. I should test it first, but I can't mess with my xorg.conf right now.

---

### Post by happyhamster on 2008-03-01
- It's possible to get around middle-click paste by mapping the middle-button to something else. For a standard 3-buttoned mouse, you could try:

Option         "ButtonMapping"      "1 1 3"

- This will make the middle-button behave like the left one. And:

Option         "ButtonMapping"      "1 3 3"

- would make it behave like the right one. (Default value is "1 2 3".) In my xorg.conf file, it looks like this:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "ButtonMapping" "1 1 3"
EndSection

```

- See this page for more info: [http://linux.die.net/man/4/mouse-driver](http://linux.die.net/man/4/mouse-driver)


Good luck, and keep us informed.

---

### Post by elio.mussi on 2008-03-02
Thanks to everyone of you guys, It's nice to see how the community interacts to fix problems and make Ubuntu even better.

So, I've tried out the 1st suggestion from banewman. it ddn't work. I have a mouse which human beings would define as a two buttons + 1 wheel mouse. Though I now understand should be defined as a 5 buttons mouse, the third being the wheel, 4th and 5th its rotating movements up and down.

So I reverted back to 
Option		"Emulate3Buttons"	"true"
but with 
    Option         "ButtonMapping" "1 2 3"
which makes the pressure of the wheel behave like the right button. This is working to me. Now when I scroll thru the source and, inadvertently, press the wheel, I get the popup window. Maybe annoying, but my source never get messed randomly.

I think this fixes my problem. I'm just not closing this post for a few days, because I'd like comments from the community on this issue.

Shouldn't we have, in a control panel, a way to define, at will, which actions to associate with every mouse event? If we already have such, could someone say a few words on it?

Again, thanks to every one, Elio

P.S. My actual section, if anyone is intersted in: 
 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option         "ButtonMapping" "1 3 3"
EndSection

---

