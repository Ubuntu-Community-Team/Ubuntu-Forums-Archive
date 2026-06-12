---
title: "How to stop jumpiness while typing?"
date: 2015-05-02
forum: General Help
---

### Post by csete on 2015-05-02
All,

I could really use some help to stop things from jumping around while I'm typing.  I'm running 14.10 on a Dell XPS 15 laptop.  

This doesn't seem to be related to "disable while typing", as I believe I have fixed that.  I'm running the following script on startup:
```

#!/bin/bash

killall syndaemon
syndaemon -i 1 -K -d

```

With this in place, I can not move the cursor with the touchpad for a second after typing.  So, that part seems to be working correctly.  However, when I'm running Android Studio or Mozilla Thunderbird, some strange things seem to happen while I'm typing.  For instance, in Thunderbird, I can be typing along and all of the sudden a new compose window is opened up and the cursor will jump to it.  The cursor has jumped back a line twice while I was typing this into Firefox.  Based on some things I read online, I disabled iBus from the preferences, hoping that might resolve it, but no luck yet.

This is really driving me crazy and I don't know what to do to resolve it.  Can anyone offer any suggestions?

Thanks,
Craig

---

### Post by sudodus on 2015-05-02
I turn off the touchpad completely, when I have a mouse.

```
synclient touchpadoff=1
```

You can turn it on again with

```
synclient touchpadoff=0
```

See ```
man synaptics
``` for more details

```
       Option "TouchpadOff" "integer"
              Switch off the touchpad.  Valid values are:

              0   Touchpad is enabled
              1   Touchpad is switched off
              2   Only tapping and scrolling is switched off
              Property: "Synaptics Off"

```

---

### Post by csete on 2015-05-02
I'm not entirely convinced this is related to the touchpad.  It isn't clear to me that the mouse/trackpad cursor is moving at all when this happens.  It is almost like the keyboard is entering special characters or something.  As I said, I can clearly validate that the cursor will not move for a second after I've stopped typing.

Unfortunately, I need the touchpad as I rarely have a mouse at hand.  Other options?

---

### Post by sudodus on 2015-05-02
You can increase the delay until the touchpad responds after typing (to two or three seconds or even more).

---

### Post by csete on 2015-05-02
True.  This *seems* to occur while I'm typing, so I wouldn't expect the delay to change anything.  However, I will bump it up just to see if that provides a solution.

If others have any different ideas, please let me know.

Thanks again,
Craig

---

### Post by csete on 2015-05-02
Unfortunately, this is still happening with a 3 second delay.  What other suggestions do people have to debug this wonkiness?

---

### Post by csete on 2015-05-31
> **csete said:**
> Unfortunately, this is still happening with a 3 second delay.  What other suggestions do people have to debug this wonkiness?

I'm back to working with this laptop again and seeing the same issues and I'm not sure where to go next.  I created a script to use evtest to capture the touchpad and keyboard events into the same file.  I can see events being capture for both.  However, when I see the cursor jump, there is **NOT** any associated touchpad events in the log.  Here is the capture at the point that I saw a jump occur:

```

Event: time 1433076902.276639, -------------- EV_SYN ------------
Event: time 1433076902.323435, type 4 (EV_MSC), code 4 (MSC_SCAN), value 39
Event: time 1433076902.323435, type 1 (EV_KEY), code 57 (KEY_SPACE), value 0
Event: time 1433076902.323435, -------------- EV_SYN ------------
Event: time 1433076902.387286, type 4 (EV_MSC), code 4 (MSC_SCAN), value 2a
Event: time 1433076902.387286, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 1
Event: time 1433076902.387286, -------------- EV_SYN ------------
Event: time 1433076902.519275, type 4 (EV_MSC), code 4 (MSC_SCAN), value 16
Event: time 1433076902.519275, type 1 (EV_KEY), code 22 (KEY_U), value 1
Event: time 1433076902.519275, -------------- EV_SYN ------------
Event: time 1433076902.569749, type 4 (EV_MSC), code 4 (MSC_SCAN), value 16
Event: time 1433076902.569749, type 1 (EV_KEY), code 22 (KEY_U), value 0
Event: time 1433076902.569749, -------------- EV_SYN ------------
Event: time 1433076902.636930, type 4 (EV_MSC), code 4 (MSC_SCAN), value 2a
Event: time 1433076902.636930, type 1 (EV_KEY), code 42 (KEY_LEFTSHIFT), value 0
Event: time 1433076902.636930, -------------- EV_SYN ------------
Event: time 1433076902.867026, type 4 (EV_MSC), code 4 (MSC_SCAN), value 26
Event: time 1433076902.867026, type 1 (EV_KEY), code 38 (KEY_L), value 1
Event: time 1433076902.867026, -------------- EV_SYN ------------
Event: time 1433076902.955071, type 4 (EV_MSC), code 4 (MSC_SCAN), value 32
Event: time 1433076902.955071, type 1 (EV_KEY), code 50 (KEY_M), value 1

```

The jump happened between the "U" and the "l".  The only thing that appears to have occurred during that time was that I let go of the left SHIFT key.  I'm definitely seeing mouse events in the log file, just not at the point of the cursor jump... for instance, at the beginning of the log file:

```

Event: time 1433076672.009775, -------------- EV_SYN ------------
Event: time 1433076672.023598, type 3 (EV_ABS), code 53 (ABS_MT_POSITION_X), value 3571
Event: time 1433076672.023598, type 3 (EV_ABS), code 54 (ABS_MT_POSITION_Y), value 2684
Event: time 1433076672.023598, type 3 (EV_ABS), code 0 (ABS_X), value 3571
Event: time 1433076672.023598, type 3 (EV_ABS), code 1 (ABS_Y), value 2684
Event: time 1433076672.023598, -------------- EV_SYN ------------
Event: time 1433076672.048043, type 3 (EV_ABS), code 53 (ABS_MT_POSITION_X), value 3566
Event: time 1433076672.048043, type 3 (EV_ABS), code 54 (ABS_MT_POSITION_Y), value 2686
Event: time 1433076672.048043, type 3 (EV_ABS), code 0 (ABS_X), value 3566
Event: time 1433076672.048043, type 3 (EV_ABS), code 1 (ABS_Y), value 2686
Event: time 1433076672.048043, -------------- EV_SYN ------------
Event: time 1433076672.058144, type 3 (EV_ABS), code 53 (ABS_MT_POSITION_X), value 3561
Event: time 1433076672.058144, type 3 (EV_ABS), code 54 (ABS_MT_POSITION_Y), value 2691
Event: time 1433076672.058144, type 3 (EV_ABS), code 0 (ABS_X), value 3561
Event: time 1433076672.058144, type 3 (EV_ABS), code 1 (ABS_Y), value 2691
Event: time 1433076672.058144, -------------- EV_SYN ------------

```

It is really difficult to work with this machine when it does this.  I need to use the touchpad, so I can't just turn it off.  However, looking at these events, it seems like this isn't necessarily touchpad related.  Are there any cases where the touchpad would cause keyboard events to show up and, if so, how would I troubleshoot that?

Any other ideas on how to troubleshoot this?

Thanks,
Craig

---

### Post by sudodus on 2015-06-01
Does it make a difference if a mouse is connected or not? Or another mouse? (A faulty mouse might cause events too.)

Do these events occur at all, if the touchpad is turned off?

Do they happen with another version (12.04 LTS, 14.04 LTS, 14.10, 15.04) or flavour of Ubuntu (standard Ubuntu, Kubuntu, Lubuntu, Ubuntu Gnome, Ubuntu Mate, Xubuntu)? Or another linux distro? You could test it live (booting from CD/DVD/USB without installing).

---

### Post by monkeybrain20122 on 2015-06-01
It happens sometimes but only when typing in some places (e.g UF) I am kind of used to it by now. Disabling touchpad is not an option for many of us who don't use a mouse.

---

### Post by csete on 2015-06-01
> **monkeybrain20122 said:**
> It happens sometimes but only when typing in some places (e.g UF) I am kind of used to it by now. Disabling touchpad is not an option for many of us who don't use a mouse.

Are you saying that you see the same behavior?  As you say, turning off the touchpad really isn't a viable option for me.

---

### Post by sudodus on 2015-06-01
If you keep a terminal window open, you can use an alias (a short command for example ***TT*** (touchpad-toggle)) to toggle between on and off, so that it is easy to turn off the touchpad, when you want to write a lot without getting interrupted by touchpad events. You can select window with ***alt + TAB***, so without using the mouse you can select the terminal window and you can turn on the touchpad with ***TT***, when you want to use it again.

I admit that it is not a perfect solution, but it works for me (I use it in Lubuntu and I think it works in Xubuntu). It does not work in Ubuntu and Kubuntu, because those flavours use a system that over-rules synclient.)

```
aliases and touchpad-toggle
---------------------------

# Appended to /etc/bash.bashrc

alias l='ls -l --group-directories-first'
alias rm='rm -i'
alias TT='touchpad-toggle'

###

function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}

####

alias TT
```

The crucial commands are

```
synclient touchpadoff=1
synclient touchpadoff=0
```

and you can make direct aliases to them if you like that better.

---

### Post by HermanAB on 2015-06-01
What happens when you plug a USB keyboard into the machine?

---

### Post by csete on 2015-06-05
Thanks for the script file to toggle the touchpad.  I've wired that up to a keyboard shortcut using Autokey and I will spend some time with the touchpad toggled off to see what that does for me.  Thus far while typing this in, it does seem better.  It is disappointing to have to do something like this, but I guess it at least makes the machine usable.  Thanks for the help.

Craig

---

### Post by sudodus on 2015-06-06
I hope it helps in the long run.

Anyway, whatever result you get (good or bad in the long run), please come back and share it :-)

---

