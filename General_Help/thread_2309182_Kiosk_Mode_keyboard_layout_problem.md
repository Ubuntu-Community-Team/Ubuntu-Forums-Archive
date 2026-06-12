---
title: "Kiosk Mode keyboard layout problem"
date: 2016-01-08
forum: General Help
---

### Post by mr_b2 on 2016-01-08
Hi!

I have a user that I can log in with Kiosk Mode (outlined here: [http://askubuntu.com/questions/132262/booting-in-kiosk-mode](http://askubuntu.com/questions/132262/booting-in-kiosk-mode))
This works great, and the application launches (Gnome-Terminal or VMware View and not Firefox, as in the example above).

The one problem I have is the keyboard layout. It appears to be US, but I am using a UK keyboard.
If I log in to Ubuntu normally, to the desktop, I have confirmed that the locale/keyboard is UK and works correctly...[B]it is only when using Kiosk Mode that the keyboard reverts to US.
[/B]

Can any shed some light on this? How can I retain my default UK keyboard settings in Kiosk Mode?

Thanks

---

### Post by matt_symes on 2016-01-08
Hi

> **mr_b2 said:**
> Hi!

I have a user that I can log in with Kiosk Mode (outlined here: [http://askubuntu.com/questions/132262/booting-in-kiosk-mode](http://askubuntu.com/questions/132262/booting-in-kiosk-mode))
This works great, and the application launches (VMware View and not Firefox, as in the example above).

The one problem I have is the keyboard layout. It appears to be US, but I am using a UK keyboard.
If I log in to Ubuntu normally, to the desktop, I have confirmed that the locale/keyboard is UK and works correctly...[B]it is only when using Kiosk Mode that the keyboard reverts to US.
[/B]

Can any shed some light on this? How can I retain my default UK keyboard settings in Kiosk Mode?

Thanks

I'm unfamiliar with *VMWare View* but does it start a Virtual Machine and, if so, have you changed the keyboard layout in that Virtual Machine ?

Maybe you could explain what VMWare View is and how you are using it ?

Kind regards

---

### Post by mr_b2 on 2016-01-08
The application doesn't matter in this case...
I get the same problem if Kiosk Mode starts with gnome-terminal - the keyboard is incorrect in the terminal.

[VMware View is a client that will allow remote connections to VMs. A bit like an RDP client. It is only prompting with a user/pass field in a native Linux application at this stage]

---

### Post by matt_symes on 2016-01-08
Hi

> **mr_b2 said:**
> The application doesn't matter in this case...
I get the same problem if Kiosk Mode starts with gnome-terminal - the keyboard is incorrect in the terminal.

[VMware View is a client that will allow remote connections to VMs. A bit like an RDP client. It is only prompting with a user/pass field in a native Linux application at this stage]

Thanks for the clarification. Personally, I use KVM so I'm unfamiliar with VMWare.

Does Kiosk Mode log in under a different user than Non Kiosk Mode ?

I'm wondering if this a user settings issue.

Kind regards

---

### Post by mr_b2 on 2016-01-08
> **matt_symes said:**
> Hi



Thanks for the clarification. Personally, I use KVM so I'm unfamiliar with VMWare.

Does Kiosk Mode log in under a different user than Non Kiosk Mode ?

I'm wondering if this a user settings issue.

Kind regards

Using the gnome-terminal that was launched through at kiosk mode, **whoami **shows that it is the same user! :confused:
I can't understand why the starting in non kiosk mode will initiate the correct keyboard layout, but kiosk mode does not!

---

### Post by matt_symes on 2016-01-08
Hi

> **mr_b2 said:**
> Using the gnome-terminal that was launched through at kiosk mode, **whoami **shows that it is the same user! :confused:
I can't understand why the starting in non kiosk mode will initiate the correct keyboard layout, but kiosk mode does not!

Odd.

Let's try a sanity check. Boot into kiosk mode, open gnome terminal and type

```
setxkbmap -layout gb
```

Does that give you a uk keyboard ?

This may be an ibus issue perhaps ?

What version and flavour of Ubuntu are you using ?

```
cat /etc/lsb-release
```

Kind regards

---

### Post by mr_b2 on 2016-01-08
> **matt_symes said:**
> Hi

```
setxkbmap -layout gb
```

Does that give you a uk keyboard ?


Yes, that does give me a UK keyboard.
The £ symbol works, which is the test I'm performing at all times (when it's not working, it gives a # symbol).


> 
What version and flavour of Ubuntu are you using ?

```
cat /etc/lsb-release
```


14.04.2 LTS Trusty.

---

### Post by coldraven on 2016-01-08
if you are running 15.10 it could be a bug in ibus. In "Text Entry" try adding US layout as a second choice. 
After behaving itself for days as I typed this my keyboard randomly flipped to US layout again :(
I filed this as a bug.
My original post here:
[http://ubuntuforums.org/showthread.php?t=2304609&p=13398654#post13398654](http://ubuntuforums.org/showthread.php?t=2304609&p=13398654#post13398654)

---

### Post by matt_symes on 2016-01-08
Hi

> **mr_b2 said:**
> Yes, that does give me a UK keyboard.
The £ symbol works, which is the test I'm performing at all times (when it's not working, it gives a # symbol).



14.04.2 LTS Trusty.

Excellent. So the problem is either configuration or something connected with ibus.

I am about to go and see someone in hospital so i am going to be AFK until late UK time.

We can continue this tonight (if you're online), tomorrow or someone else may step in and help, in the meantime.

If you find the fix yourself before either I, or others, help then please post the solution you find as it'll help others.

Will you be online tonight or tomorrow ?

**EDIT:**

He's using Trusty coldraven.

> 14.04.2 LTS Trusty

I was also wondering if he's suffering with that bug. 

Does that bug go back to Trusty ?

Kind regards

---

### Post by mr_b2 on 2016-01-08
> **matt_symes said:**
> Will you be online tonight or tomorrow ?
I might be! I'm a sucker for these kind of problems... although I am now a little further forward, so might call it a night shortly.

My kiosk.sh script did a few things before launching the application - mostly just screensaver disable commands, etc.
I previously had ```
[COLOR=#000000][FONT=Ubuntu Mono]setxkbmap -layout gb[/FONT][/COLOR]
``` set in the code, but it was having no effect.

I have since changed this to:
```

sleep 5s
[COLOR=#000000][FONT=Ubuntu Mono]setxkbmap -layout gb[/FONT][/COLOR]
```

and this now changes the keyboard layout to UK.

I checked that it wasn't just the application launching too quickly before the language settings applied (by leaving the sleep, but removing the layout command) - the application will NOT get the correct layout unless specifically set in the script, and even then it MUST be after a sleep. So far that has proven consistent.

Whilst this is a "workaround" for me, it doesn't sit well that it doesn't work natively... I'll check back later, might have a beer; always fun troubleshooting with a decent ale in hand.


So to recap, the following code does NOT give you UK keyboard:
```

#!/bin/bash
xset -dpms
xset s off
disper -e
[COLOR=#000000][FONT=Ubuntu Mono]setxkbmap -layout gb
[/FONT][/COLOR]gnome-terminal

```

However, the following code **DOES GIVE ME UK keyboard**:
```

#!/bin/bash
xset -dpms
xset s off
disper -e
sleep 5s
[COLOR=#000000][FONT=Ubuntu Mono]setxkbmap -layout gb
[/FONT][/COLOR]gnome-terminal

```

---

### Post by matt_symes on 2016-01-08
Hi

> ```

#!/bin/bash
xset -dpms
xset s off
disper -e
sleep 5s
setxkbmap -layout gb
gnome-terminal

```


For a test, if you comment out the lines as shown below, do you get a UK keyboard ?

```

#!/bin/bash
#xset -dpms
#xset s off
#disper -e
#sleep 5s
setxkbmap -layout gb
gnome-terminal
```

Kind regards

---

### Post by mr_b2 on 2016-01-11
Thanks for persisting :)

> **matt_symes said:**
> Hi
```

#!/bin/bash
#xset -dpms
#xset s off
#disper -e
#sleep 5s
setxkbmap -layout gb
gnome-terminal
```


The above still gives the error.

```

#!/bin/bash
sleep 5s
setxkbmap -layout gb
gnome-terminal
```


The above works. It seems there is a timing issue.
To confirm that....

```

#!/bin/bash
while true; do
    setxkbmap -layout gb
    gnome-terminal
done

```

I get the wrong layout the first loop, but second it is set ok.

1) I wonder why the language in non-kiosk mode (GB) is not the same in kiosk mode. Because I'm calling a bash script? Is it defaulting to something else because bash is running?
2) Setting layout doesn't work immediately either: a) another layout is being set somehow after my command or b) something isn't initialised to take my command yet.

I also checked the exit code for the layout command, it was 0 on the first and second loop, so it thinks it was OK even when it doesn't appear to set.

8-[

---

### Post by matt_symes on 2016-01-11
Hi
> 
I get the wrong layout the first loop, but second it is set ok.

1) I wonder why the language in non-kiosk mode (GB) is not the same in kiosk mode. Because I'm calling a bash script? Is it defaulting to something else because bash is running?
2) Setting layout doesn't work immediately either: a) another layout is being set somehow after my command or b) something isn't initialised to take my command yet.

I also checked the exit code for the layout command, it was 0 on the first and second loop, so it thinks it was OK even when it doesn't appear to set.

It could be any of those scenarios and a couple others.

Let's try to eliminate some things.

1. Set UK English as system wide.

System Settings->Language Support->Lanuguage Tab->Language for menus and windows (English UK)-> Apply system wide.

2. Disable ibus.

System Settings->Language Support->Language Tab->Keyboard Input Method->None.

Reboot.

Confirm ibus not not running

```
ps aux | grep ibus
```

Any joy ?

Kind regards

---

### Post by mr_b2 on 2016-01-12
> **matt_symes said:**
> Hi


It could be any of those scenarios and a couple others.

Let's try to eliminate some things.

1. Set UK English as system wide.

System Settings->Language Support->Lanuguage Tab->Language for menus and windows (English UK)-> Apply system wide.

2. Disable ibus.

System Settings->Language Support->Language Tab->Keyboard Input Method->None.

Reboot.

Confirm ibus not not running

```
ps aux | grep ibus
```

Any joy ?

Kind regards

No joy.
I think we'll just have to take it as designed for now, unless the build (it's on USB - is that relevant?) is incorrect.
At least I can work around.

Thanks for the help on this one.):P

---

### Post by matt_symes on 2016-01-12
Hi 

> **mr_b2 said:**
> No joy.
I think we'll just have to take it as designed for now, unless the build (it's on USB - is that relevant?) is incorrect.
At least I can work around.

Thanks for the help on this one.):P

It's unlikely to be a USB issue but you have a workaround.

Do you want to mark this thread as solved ?

I'll leave that decision up to you.

Kind regards

---

