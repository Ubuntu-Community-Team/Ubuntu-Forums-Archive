---
title: "Execute a keycode on a command line"
date: 2017-10-13
forum: General Help
---

### Post by pemartins on 2017-10-13
I'm looking for a way to reproduce a keycode on a command line. The specific keycode is for fn+f7 on my laptop, for which xev returns this:
```
KeyPress event, serial 38, synthetic NO, window 0x4800001,
    root 0x497, subw 0x0, time 1061645, (93,-36), root:(99,36),
    state 0x10, keycode 253 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
So what I wanna do is run a command on the terminal that mimics pressing fn+f7, using its keycode 253. How can I do this?

---

### Post by dragonfly41 on 2017-10-13
There are several utilities in Ubuntu repo I use for this purpose.   There may be others.

Actiona 3.9.1 allows an automation script to run from a pipeline of actions.
Look for Device > Key.

Actiona appears under Accessories menu.

To run an Action script from command line use actexec command.
e.g.

```
actexec mykeypress.ascr
```

There is also Autokey to try.

---

### Post by pemartins on 2017-10-13
Thank you very much for helping me.

I tried both mentioned applications but I had no idea what to do, I was totally lost. I couldn't figure out how to use a keycode and I do not have the knowledge to write a script.
In Actiona I presume it could be done in Device - Key - Standard - Key - click editor and then insert code there but I do not have the slightest clue of what to write in there.

Meanwhile I tried xte, xvkbd, xbindkeys and xmodmap but without success. The closest I've been to success was with xmacro and xnee but I couldn't get them to record the action because of the use of fn key.

---

### Post by again? on 2017-10-13
I don't use the fn key on my keyboard and don't know how the key is used as I have never had a laptop.
Testing here with this command 
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
then pressing fn+F7 I get this...
```
glen@GU17:~$ xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
199 **XF86TouchpadToggle**
50 Shift_L
133 Super_L
```

Perhaps try running what your output shows when pressing fn+F7 with xdotool.
eg
```
xdotool key **XF86TouchpadToggle**
```
or
```
xdotool key **XF86TouchpadToggle**+F7
```

This command to list your keycodes may also be useful.
```
xmodmap -pke
```

---

### Post by pemartins on 2017-10-13
Thank you very much for the help.

Keyboards change from machine to machine concerning the use of fn key and its combinations, on my laptop fn+f7 is to turn off the screen on the kernel. fn+f7 has no designation on my laptop, which makes it more difficult because if it had a designated name I would be able to use "xdotool key ___<name>" and that would be it. But unfortunately it isn't so:
```
$ xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
253 NoSymbol
```

Here's my output of xmodmap -pke: [https://pastebin.com/raw/2MNgHLu6](https://pastebin.com/raw/2MNgHLu6)

Turning off the screen this way is the only way it works properly for what I need, I tried everything with xset with no luck and xrandr always breaks something when the screen is turned back on.

---

### Post by again? on 2017-10-14
Reading up on the fn key I see answers like this.
> The Fn key is handled by hardware, not the OS.
Pressing the Fn key does not send any keycode to the operating system, therefore you cannot fake pressing the Fn key.
Sorry, don't have an answer for you in regards to this.

I gather **xset dpms force off** doesn't work on your laptop.

---

### Post by dragonfly41 on 2017-10-14
I now see from further reading ..
 
 >  The Fn key is generally handled via the ACPI BIOS rather than directly by the operating system, so there is unlikely to be anything that Ubuntu itself can do.
 
 Emulating Fn key
 
 [https://askubuntu.com/questions/103928/how-to-emulate-fn-function-key-keypress-in-xte](https://askubuntu.com/questions/103928/how-to-emulate-fn-function-key-keypress-in-xte)

 run in terminal ..
 
 ```
tail -f /var/log/kern.log
```
 
 press Fn + F7  
 
 You see the character string .. ^[[18~
 
 You might be able to use this.

 source: [https://askubuntu.com/questions/103928/how-to-emulate-fn-function-key-keypress-in-xte](https://askubuntu.com/questions/103928/how-to-emulate-fn-function-key-keypress-in-xte)

 ==================================================
 
 Regarding earlier suggestion to try Actiona .. I now see that Fn is not recognised by Actiona ...
 
 But for other actions ...
 
 With each action in the Edit Action window (which opens when you click on the action in the main window) there is a button to the left of the [Control] [OK} buttons.

This takes you to a wiki page explaining how to use that action.

[https://wiki.actiona.tools/doku.php?id=en:actions:actionkey](https://wiki.actiona.tools/doku.php?id=en:actions:actionkey)

However the documentation is not very full with examples. 
               
 ==================================================
 
 I explored using a virtual keyboard .. Universal Access > Onboard
 but again Fn key is not shown on virtual keyboard.
 
 Actiona could also autotype key sequences on a virtual keyboard.
 
 The x:y target (x:y of centre of each target key on your screen) can be found by running ...
 
 ```
watch -n 1 xdotool getmouselocation
```

==================================================

[Later edit]
Your first use of Actiona.
> [COLOR=#000000]In Actiona I presume it could be done in Device - Key - Standard - Key - click editor and then insert code there but I do not have the slightest clue of what to write in there.

In fact writing code (javascript) is optional. No extra code is required for key emulation unless required to expand the action.[/COLOR]

---

### Post by dragonfly41 on 2017-10-14
OP does not specify laptop in use.

Or the required function triggered by Fn + F7.

If it is to switch displays ([as in this thread]("https://ubuntuforums.org/showthread.php?t=1413998")) then there are other ways of switching displays.

e.g. recently I had to use SuperKey + P to toggle displays.

---

### Post by HermanAB on 2017-10-14
I suggest autokey.  It is easy to use and it works.  I use it every day:
sudo apt install autokey

---

### Post by pemartins on 2017-10-14
Thank you all very much for the help.

@dragonfly41 fn+f7 returns nothing with tail -f /var/log/kern.log.
I went through all you mentioned but no luck. Other than executing a keycode I see no other way of making it happening.

The laptop is an ASUS X55U-SX038H. What I wanna do is turn of the screen of the laptop so it doesn't turn back on unless the same action (mimic fn+f7 key press) is repeated, no matter if there are key presses or mouse moves or if there are programs running that surpass screensaver or dpms off.

@HermanAB can you tell me how? As I mentioned previously I tried autokey but I wasn't able to do it.

---

### Post by pemartins on 2017-10-28
I found this [here]("http://t-sato.in.coocan.jp/xvkbd/events.html") that seems like a possible solution:
```

Sending Key Events

To send key events, we can use XSendEvent(), a standard Xlib function, or XTestFakeKeyEvent(), an interface to the XTEST extension.

Sending events with XSendEvent()

To send key events with XSendEvent(), we must set required parameters in a XKeyEvent struct and then invoke XSendEvent().

  XKeyEvent event;

  event.display = display;
  event.window = destination of the event;
  event.root = the root window;
  event.subwindow = None;
  event.time = CurrentTime;
  event.x = 1;
  event.y = 1;
  event.x_root = 1;
  event.y_root = 1;
  event.same_screen = TRUE;

  event.type = KeyPress;  or  event.type = KeyRelease;
  event.keycode = keycode;
  event.state = modifiers;

  XSendEvent(event.display, event.window, TRUE, KeyPressMask, (XEvent *)event);


```
but I literally have no idea what to do with this. How can I use this to send the mentioned keycode 253 to X?


edit: I also found [this page]("https://rosettacode.org/wiki/Simulate_input/Keyboard") that perhaps is helpful but I do not have the knowledge to sort it out.

---

### Post by efflandt on 2017-10-29
I used to know how to turn off a laptop backlight many years ago, but that was when I was running SuSE on a laptop from Jan 2000.

This thread may help find an alternate method, even though it is several years old:
[https://ubuntuforums.org/showthread.php?t=2231004](https://ubuntuforums.org/showthread.php?t=2231004)

---

