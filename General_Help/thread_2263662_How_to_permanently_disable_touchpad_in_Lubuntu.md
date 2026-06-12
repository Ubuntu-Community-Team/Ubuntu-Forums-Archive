---
title: "How to permanently disable touchpad in Lubuntu"
date: 2015-02-02
forum: General Help
---

### Post by rdh61 on 2015-02-02
I have Lubuntu 14.04 LTS installed on my laptop. While I am typing the cursor often jumps down several lines on the page. I suspect I am inadvertently touching the touchpad with my sleeves, so I want to disable it. The hard keys dedicated to this (Fn + F6) do not do it. I installed the package GPointing Device Settings, which offers me the possibility to disable the touchpad while typing. I check the box and click OK. It does not work, and the next time I open GPointing Device Settings, I find the box unchecked. There is also the option just to disable the touchpad permanently. That works for my session, but the next time I boot up, the touchpad is enabled again. When I open GPointing Device Settings however, the box to disable the touchpad is still checked. To disable it again for the session I have to uncheck it, OK it, recheck it, and OK it again. Please someone tell me how to disable the touchpad permanently.

Many thanks.

---

### Post by Rex Bouwense on 2015-02-02
I am not sure if this capability was ever made permanent in GPointing device.  
[https://help.ubuntu.com/community/Lubuntu/Mouse](https://help.ubuntu.com/community/Lubuntu/Mouse) 
offers a solution under Touchpad settings.

---

### Post by rdh61 on 2015-02-02
Hi,

Thanks for your reply. I had found that link but found it unhelpful. I was interested in:

**Disable touchpad while typing**

 ```
@syndaemon -d -t
```

So as instructed I added that line to the file ~/.config/lxsession/Lubuntu/autostart, saved and rebooted.

My touchpad is still enabled while I type.

---

### Post by mc4man on 2015-02-02
I don't use Lubuntu but have the same issue with Ubuntu. In the case of Ubuntu it's a known [bug that likely won't be fixed ]("https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1283863")that while one can disable the touchpad it's always re-enabled on a restart, log out/in & resume from suspend.

A partial 'fix' for Ubuntu is to use Startup applications to disable the touchpad after login via gsettings. (resolves all but 'resume from suspend'

So if you can find a command that works for you on Lubuntu & a means to have it autorun just after login that may provide some relief..

---

### Post by sammiev on 2015-02-02
You can shut it off in your BOIS if you are not using it at all.

---

### Post by rdh61 on 2015-02-03
> **mc4man said:**
> A partial 'fix' for Ubuntu is to use Startup applications to disable the touchpad after login via gsettings. (resolves all but 'resume from suspend'

So if you can find a command that works for you on Lubuntu & a means to have it autorun just after login that may provide some relief..

Thanks. Can anybody suggest such a script and where to put it?

---

### Post by rdh61 on 2015-02-03
> **sammiev said:**
> You can shut it off in your BOIS if you are not using it at all.

Thanks. I've looked in the bios but there doesn't seem to be anything there that would do this.

---

### Post by gopi_nath_vajpai on 2015-02-03
Hi, I faced the same problem with my Dell laptop. So I made a script to disable it at startup. First of all type 'xinput list' in a terminal window, and it will list all input device.
In my case the device name is 'DualPointStick'. 

Next open a blank text document and type below:

#! /bin/bash
xinput -set-prop "DualPoint Stick" "Device Enabled" 0

Change name with the device name as shown in your system (as exactly shown in your 'xinput list' output and beware that capitalization should be exact and save the file to your home directory (or elsewhere as may suit) with any name (don't add any filename extension)
Right click the file>properties and select Executable by =All (this will make it executable)

Next go to start menu>preferences>default tools for LX session

Now go to the 'Autostart' tab and give path of your file e.g. /home/user/filename in the space provided and click the +Add button next to it. this will make the file executable once you login to your system.

That should work.

Please do comment for further query.

Regards

---

### Post by sudodus on 2015-02-03
If you want to turn off the touchpad only for one user, add the following code into your **~/.bashrc** file, if you want it for all users, add it into the **/etc/bash.bashrc** file.

Append (add to the end of the file)

```
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

and you can turn it off manually with the terminal window command ***TT***.

If you want to turn off at once and automatically, ***autostart a terminal window*** and add a call to the function (that you just created)

```
touchpad-toggle
```

at the end of the **~/.bashrc** file or **/etc/bash.bashrc** file.

---

### Post by sudodus on 2015-02-03
See also this link, if you want a simple way to turn it off (not interested in the toggle feature).

[http://ubuntuforums.org/showthread.php?t=2252169&p=13164172#post13164172](http://ubuntuforums.org/showthread.php?t=2252169&p=13164172#post13164172)

> Basically

```
synclient touchpadoff=1
```

switches it off

---

### Post by rdh61 on 2015-02-04
Thanks folks. I decided to go with Sudodus as I'd like to be able to toggle rather than just disable at start up. But the scripts you provided Sudodus don't work for me. They have no effect. I notice that some of the lines are commented out (#). I used the scripts "as is". Should I uncomment them?

These easy commands are useful, thank you:
synclient touchpadoff=1
synclient touchpadoff=0

---

### Post by sudodus on 2015-02-04
I have used this script many times (in several computers, and in many cases with Lubuntu) so I'm pretty sure it works.

The comments are 'true comments' and should not be uncommented.

If you want it to happen *automatically*, you should autostart a terminal window with a command to turn off the touchpad.

Please describe how you try to use the script (what you have done so far), and I can tell you what to add or change.

---

### Post by rdh61 on 2015-02-04
> **sudodus said:**
> Please describe how you try to use the script (what you have done so far), and I can tell you what to add or change.

Well, I copied the code from your message above and pasted it to the end of my **~/.bashrc** file. I saved the file and rebooted. I checked that the touchpad was working. I opened a terminal and typed: 

```
TT
```

I hit the "enter" button.

My touchpad was still working.

---

### Post by sudodus on 2015-02-04
You did what you should do, and I think it should work. Did you copy the first line, which defines the alias?

```
alias TT='touchpad-toggle'
```

What happens, when you type the following line?

```
alias TT
```

---

### Post by rdh61 on 2015-02-04
I copied all of the following code:

```
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

If I type either **TT** or **alias TT** in a terminal (then press enter) nothing happens. My touchpad is still active.

As an alternative, I wonder, could I make a custom launcher to run the commands **synclient touchpadoff=1** and **synclient touchpadoff=0 **at a click? Even better if a single launcher could show both options. If that is possible, could you tell me how to achieve it?

---

### Post by sudodus on 2015-02-04
I think that for some reason the **alias TT **is not defined

```
alias TT='touchpad-toggle'
```

Either your **~/.bashrc** file does not contain that line, or never executes it or is not executed at all. Are you running another shell, not ***bash*** but for example ***csh*** or ***tcsh***?

What happens if you type the long function name (launch the command with the Enter key)

```
touchpad-toggle
```

-o-

It is also possible to make a shell-script of touchpad-toggle (instead of a function in .bashrc).

```

#!/bin/bash

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

```

Create an own **bin** directory

```
cd
mkdir bin
cd bin
leafpad TT

```

Put this toggle code above (starting with #!/bin/bash) into an editor (leafpad) and write it to a file named whatever you prefer, for example ***TT*** or ***touchpad-toggle***.

Make the file executable

```
chmod ugo+x TT
```

(if TT is the name you selected)

Otherwise you can make two super simple scripts ttoff (touchpad off) and tton (touchpad on)

```
echo synclient touchpadoff=1 > ttoff
```
```
echo synclient touchpadoff=0 > tton
```

and keep them in you **bin** directory.

```
chmod ugo+x tto*
```

And then you can run

***ttoff*** to turn the touchpad off
and
***tton*** to turn the touchpad on.

---

### Post by rdh61 on 2015-02-05
Now a strange thing happened. I typed **TT** and it *did* toggle the touchpad. But the next time I did it, the terminal window crashed and there was no change in touchpad behaviour. I rebooted and tried again. On the first and second tries, the terminal crashed, but from try 3 onwards, the command worked. 

I deleted the script from .bashrc, and instead set up your shell script. I rebooted. On tries 1 and 2 it returned: 
"Couldn't get touchpad status from synclient"

From try 3 onwards, it worked. I'll let you know if this behaviour is stable.

---

### Post by sudodus on 2015-02-05
I agree, this is strange. It is getting interesting :-)

 Which version are you running? You wrote Lubuntu 14.04 in the opening post. Is it updated/upgraded to 14.04.1 with all current versions of the packages involved? Are there complaints when you run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Have you installed some special PPAs or some programs from deb-files, that might have an influence on the touchpad?

What happens if you uninstall and reinstall synclient?

```
 sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by rdh61 on 2015-02-07
Lubuntu 14.04.1 all upgrades current. 

dist-upgrade done with no errors. 

No applications installed from downloaded deb files (that I recall).

Added software sources:
ppa.launchpad.net/gencsfm/ppa/ubuntu
apt.insychq.com/ubuntu

Uninstalled, reinstalled synclient.

No change in behaviour. Success of scripts in toggling touchpad is very erratic. The only thing that consistently works is synclient touchpadoff=1 (0). I guess I'll have to stick with that.

> **sudodus said:**
> I agree, this is strange. It is getting interesting :-)

 Which version are you running? You wrote Lubuntu 14.04 in the opening post. Is it updated/upgraded to 14.04.1 with all current versions of the packages involved? Are there complaints when you run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Have you installed some special PPAs or some programs from deb-files, that might have an influence on the touchpad?

What happens if you uninstall and reinstall synclient?

```
 sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by sudodus on 2015-02-07
> **rdh61 said:**
> Lubuntu 14.04.1 all upgrades current. 

dist-upgrade done with no errors. 

No applications installed from downloaded deb files (that I recall).

Added software sources:
ppa.launchpad.net/gencsfm/ppa/ubuntu
apt.insychq.com/ubuntu

Uninstalled, reinstalled synclient.

No change in behaviour. Success of scripts in toggling touchpad is very erratic. The only thing that consistently works is synclient touchpadoff=1 (0). I guess I'll have to stick with that.

Your installed system looks healthy :-) Those added software sources seem to manage other things (not related to the touchpad), so they should not create this problem. I don't understand why toggling is erratic, but I guess you can get along with 

```

synclient touchpadoff=1
synclient touchpadoff=0

```

It *should* work for you to run them as scripts or aliases if you don't want to type them every time.

Is there someone else who can chip in and help solve this problem?

---

### Post by rdh61 on 2015-02-08
Thanks for your help Sudodus - much appreciated.

---

### Post by rdh61 on 2015-02-10
@ Sudodus -

I've found that if I have your TT toggle script autostart on start up, the touchpad is off on start up, and then the TT command will toggle it on and off normally. That's good.

I'm marking this thread solved. Thanks again.

---

### Post by sudodus on 2015-02-10
I'm glad you found a way to use TT, that works well :-)

---

### Post by celiapgt on 2015-09-26
@ Sudodus

I use your script as well. Thanks, first of all! Nice and elegant solution.


I found out that the script as you pasted here doesn't use the [FONT=Courier New]synclient TouchpadOff=0[/FONT] capitalization...

Maybe that was the issue...

---

### Post by sudodus on 2015-09-26
Thanks for the heads up :-)

I tested right now in a Lubuntu 14.04.2 LTS live session (with no extra packages or tweaks), and it works with lower case letters too (without capitalization)

```
synclient touchpadoff=0
synclient touchpadoff=1
```

---

