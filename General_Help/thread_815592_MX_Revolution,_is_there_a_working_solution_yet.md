---
title: "MX Revolution, is there a working solution yet?"
date: 2008-06-01
forum: General Help
---

### Post by Leefmc on 2008-06-01
System: Ubuntu 8.04
Mouse: MX Revolution

I've been digging the forums, and i thought i had a solution in Btnx, turns out it does not work for me. A: It does not support standalone modifiers (Ctrl/Alt/Shift), and B: It does not seem to support "holding" a button down (*eg, custom MMB since the revolution doesn't have one*), and for Blender/3D Apps, this is essential.

With that said, has anyone written instructions on how to manually get this functionality? I've seen a couple instructions, but [**_this_**]("http://ubuntuforums.org/showthread.php?t=546346&highlight=mx+revolution+mouse") is the only one i have found that seems like it may work.

I am however, asking still because a specific Revolution tutorial would ofcourse be best. Specially since i need a fully working "Custom MMB", again, because the mx revolution does not have one by default (My MMB if choice is Left ScrollWheel Tilt).

I'll be attempting the link i provided if no one else can provide information, but i would much appreciate any more information you can give me.

Thank You,
Lee

---

### Post by Leefmc on 2008-06-02
bump

---

### Post by fktt on 2008-06-03
Well, im not entirely sure if [this would be of help]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Activate_side-mouse-buttons_in_FireFox"), also i dont own a logitech mouse.
Currently only working 'mouse' is my wacom graphire 4.

---

### Post by Leefmc on 2008-06-03
Well, not knowing much about xorg.conf, i better not guess.

I wanted to follow it, but they mention that my xorg.conf's device area should look like:
```

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	...
	Option "Protocol" "ExplorerPS/2"
	...
	Option "Emulate3Buttons"       "true"
EndSection

```

But instead it looks like this, by default.
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

```


Any thoughts?

I'm also a bit confused on how adding
```

       Option "Buttons" "7"
       Option "ButtonMapping" "1 2 3 6 7"

```
really does anything. Your telling the system you have those buttons, but what is binding them to actions? I need ScrollWheelTiltLeft (*no idea what the machine identifier for that is*) to be equal to MMB, and the "back and forward" thumb buttons to be equal to CTRL and ALT respectively.

Not to mention a few other ones, but these 3 are the most important for my use in blender/3d apps (which is my #1 priority).

---

### Post by Leefmc on 2008-06-04
bump

---

### Post by mustang on 2008-06-05
Hi Lee,

my MX revolution just came in today. 

Question: revoco doesn't get enabled. BTNX says it didn't detect a MX revolution so I'm kind of stuck. When I run xev, it doesn't detect the side buttons, the side scroll wheel, or the the button by the top scroll wheel.

Any ideas?

---

### Post by Leefmc on 2008-06-05
> **mustang said:**
> Hi Lee,

my MX revolution just came in today. 

Question: revoco doesn't get enabled. BTNX says it didn't detect a MX revolution so I'm kind of stuck. When I run xev, it doesn't detect the side buttons, the side scroll wheel, or the the button by the top scroll wheel.

Any ideas?

Heh no idea.. i dont know anything about making the MX Revolution work in ubuntu, if i did i wouldn't be here asking hehe.

Although for me, BTNX works. It detected my MX Rev fine, and revoco worked just as fine for me. My problem is that BTNX simple does not have the features i need.. its useless to me heh.


This seems to be a widely lacking part of Ubuntu. It would be nice if the devs would actually have dynamic support for any input device you shove into a computer, since drivers for the mice are often only supported for windows, that leaves users sort of screwed when it comes to linux.

Its nice that hardy can recognize my back/forward buttons, but im not sure who actually uses that functionality anyway.. so its sort of a useless attempt.

Anyone have any ideas?

---

### Post by WiseTroll on 2008-06-18
Hi, people.
My MX Revolution came today and I have successfully configured it through btnx-config. But I have one bug - my side forward button doesn't work properly. Currently it calls context menu instead of forward action (BTN_FORWARD).
Any solutions?
Thanks.

---

### Post by Leefmc on 2008-06-18
> **WiseTroll said:**
> Hi, people.
My MX Revolution came today and I have successfully configured it through btnx-config. But I have one bug - my side forward button doesn't work properly. Currently it calls context menu instead of forward action (BTN_FORWARD).
Any solutions?
Thanks.

Heh, i have none (but then again.. this is a thread of questions and no answers, not sure why you thought you'd find answers here ;P).

But its a good bump for my question aswell. heh :o


I really hope Ubuntu has some official mouse support here soon, its a bit lame that so many mice are pretty useless without proper support.

---

### Post by WiseTroll on 2008-06-19
Yep! I fixed it! Now all seem to work like it should.
[This]("http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/") article was very helpful.

So, I inserted a new section in my /etc/X11/xorg.conf:
```

Section "InputDevice"
Identifier   "MouseMX"
Driver       "evdev"
Option       "Device" "/dev/input/event4"   # cat /proc/bus/input/devices
Option       "Name" "Logitech MX Revolution"
Option       "CorePointer"
EndSection

```

And now I can configure all buttons with btnx-config. :mrgreen:

---

### Post by Leefmc on 2008-06-19
I've had no luck, because btnx is useless for my needs. It does not have the ability to "hold" a button, so holding alt/shift/ctrl is impossible.

Thus far it seems IMWheel cannot do this holding either.. im not sure what my other options are.. if any.

I suppose this is my first "Linux can't do this" moment heh

---

### Post by WiseTroll on 2008-06-20
Maybe, I've misunderstood something. But I've tried to set Modifier 1 for my Side Scroll Back button and left Key Code field empty (NONE). So, in the result I'm able to use Side Scroll Back button as Ctrl key. For example, such combinations as SSB+A (Select All) or SSB+Scroll Up/Down (Zoom In/Out in Firefox) work properly.
I've tried such options as Windows Key (META) and it works then set Modifier 1 to Ctrl an Modifier 2 to Shift and got working language switch.

---

### Post by Nepherte on 2008-06-20
I can set modifiers as well in btnx just like in the previous post.

---

### Post by Leefmc on 2008-06-20
> **WiseTroll said:**
> Maybe, I've misunderstood something. But I've tried to set Modifier 1 for my Side Scroll Back button and left Key Code field empty (NONE). So, in the result I'm able to use Side Scroll Back button as Ctrl key. For example, such combinations as SSB+A (Select All) or SSB+Scroll Up/Down (Zoom In/Out in Firefox) work properly.
I've tried such options as Windows Key (META) and it works then set Modifier 1 to Ctrl an Modifier 2 to Shift and got working language switch.

Interesting! Using BtnX correct? The thing is, i was unable to, then i actually read the developer saying that this was impossible, so i gave up on btnx. I'll give btnx anther shot when i get home, as this seems very odd heh.

IIRC, i did not do the xorg.conf changes that you did, so perhaps that has to do with it? But as i said, when i used btnx it all worked except the modifier ability.

---

### Post by WiseTroll on 2008-06-20
> **Leefmc said:**
> Interesting! Using BtnX correct? The thing is, i was unable to, then i actually read the developer saying that this was impossible, so i gave up on btnx. I'll give btnx anther shot when i get home, as this seems very odd heh.

IIRC, i did not do the xorg.conf changes that you did, so perhaps that has to do with it? But as i said, when i used btnx it all worked except the modifier ability.
I had a problem mentioned above with side forward key. After modifying xorg.conf this bug disappeared.

---

### Post by wayward on 2008-06-21
This may or may not have been mentioned in previous posts, but here's how I got both my Logitech MX and VX working with XOrg 1.4.90, kernel 2.6.24-19 (stock Ubuntu 8.04 "Hardy Heron"), without btnx.  All the buttons work under X, even the infamous "Search" button on top of the mouse.

Xorg.conf:

```
Section "ServerLayout"
        # ...
        InputDevice     "Logitech Revolution"
EndSection

Section "InputDevice"
        Identifier      "Logitech Revolution"
        Driver          "evdev"
        Option          "Name" "Logitech USB Receiver"
        Option          "Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
        Option          "CorePointer"
EndSection
```

Note that this way of specifying the device avoids USB plug-specific addressing.  The only downside is that the mouse stops working after you unplug the receiver, since Xorg still can't reconfigure devices on-the-fly, and won't be able to until Xinput hotplugging takes off (or so I'm told).

---

### Post by Leefmc on 2008-06-21
No luck so far with that config. Infact with that config, even the bottons that did work are not haha. I'll continue to toy though.

But yea.. this is horrible on Linux. I've wasted 6 hours of my time on getting a _mouse_ to work.. yeesh. For all the effort so many people put into making GUIs and planning layouts etc, they didn't put much thought into getting the users interface *to* the interface, working well. Rather ironic i spose. :o

---

### Post by Leefmc on 2008-07-12
Ok, i was complaining more, but then all of a sudden i seemed to have the result i was looking for.. oddly enough.

I believe it is still believed to be impossible, no? 

(This post for example, shows a possible hack solution though)
[http://ubuntuforums.org/showpost.php?p=5091282&postcount=1053](http://ubuntuforums.org/showpost.php?p=5091282&postcount=1053)

---

### Post by noremac on 2008-07-14
I don't mean to hijack a thread, but I have recently come into problems with btnx and my MX Revolution...

I had it all seemingly to be working fine to change song with it, while playing music in Amarok. For a long time I had set a global shortcut in Amarok of something like Alt+N for next song. I didn't realize there was a "KEY_NEXTSONG" in the list of commands. Well about a week ago I changed it to that for next song, previous song, and play/pause. Now though, none of these seem to work. 

It seems like it is Amaroks problem too. Various things point to that anyhow. What would be a good method of just starting amarok over from scratch? I see no /.amarok folder anywhere to delete. Is it hidden somewhere else?

---

### Post by Macdelaney on 2008-08-22
I'm bumping this just to avoid creating a new thread.
I'm having a similar issue as OP, what i want to do is to configure my thumb scroll click to the Scale effect on Compiz, but i can't get it to work. Also, if anyone knows how to configure the thumb scroll, for example, to plat next song when foward, i would appreciate the sharing.

---

### Post by NobodySpecial on 2008-12-05
Guys, I'm posting my solution to try to help out.  I use both Ubuntu and Archlinux, and I actually did this on my Arch install, but should work in Ubuntu - if any differences, please post them here.  Maybe somebody here could take this info and post a new how-to topic with it all explained in a more newbie-friendly way.  I hope this helps.

Many of us were using BTNX to run the buttons on the MX Revolution.  But BTNX is now broken with the new XORG.  The good news is, the new XORG is good enough that you don't really need BTNX, for the most part.

Here's how I use mine.
First, I'm not even using the evdev driver - I guess you could.  But "mouse" works fine:
/etc/X11/xorg.conf
```
Section "InputDevice"
	Identifier	"MX Rev"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"no"
	Option		"Buttons"		"3"
EndSection
```
To start, install a couple packages:
```
sudo apt-get install xbindkeys xvkbd
```
Then find the buttons you want with xev and enter in ~/.xbindkeysrc
My code under ~/.xbindkeysrc makes the thumb buttons go forward/back and also the middle mouse wheel rock left/right will change tabs in firefox:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]""
  m:0x0 + b:6
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Down]""
  m:0x0 + b:7
```
To automate, add /usr/bin/xbindkeys to System -> Pref -> Sessions.
Next, I like the left-sided wheel to rotate the desktop in compiz:
Compiz Settings -> Desktop -> Rotate Cube -> Bindings -> Initate "Button17", Rotate Left "Button13", Rotate Right "Button15"

Finally, its annoying to me that the middle button below the scroll wheel is set to "search".  Its far handier to have it as the middle mouse click.  The only way I found to do this is through Xmodmap, which isn't ideal, but works (PLEASE post here if you know a better way).
To list xmodmap keys: xmodmap -pk  OR  xmodmap -pke
Under xev above, my button gives "keycode 225", so I do this:
```
echo "keycode 225 = Pointer_Button2" >> ~/.xmodmaprc
```
Log out and in again - gnome should autodetect the ~/.xmodmaprc file.
The trick only works when "mousekeys" are on.
So either gnome-keyboard-properties -> Mousekeys -> Enable pointer OR toggle with SHIFT-ALT-NUMLOCK (you want to be able to toggle so you can use the numeric keypad at times).
However, the xmodmap trick has one more issue - it messes up keybindings in vmware.  This solved it for me:
```
su
echo "xkeymap.nokeycodeMap = true" >> /etc/vmware/config
```
I suspect that you'll have to do the above line again every time there is a kernel update different enough to have to do the "sudo /usr/bin/vmware-config.pl" command.

If you know a better way to do any of this, please post.

---

