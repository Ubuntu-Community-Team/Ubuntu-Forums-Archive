---
title: "Starting programs on other monitor"
date: 2013-12-21
forum: General Help
---

### Post by chris137 on 2013-12-21
Hi,
I got an additional monitor attached to my notebook.
When working on the monitor I can't see the notebook's display and vice versa so it is important that programs I start - e.g. in the taskbar - on monitor A they will appear on monitor A.
I work most of the time on the attached monitor so it would also be a solution if alle the programs would start on this monitor.

---

### Post by Bucky Ball on 2013-12-21
Do you need the other notebook monitor on? Perhaps install arandr as that will prove helpful probably. You can then switch the notebook monitor off and force everything to start on the monitor. You can switch back on at anytime using the arandr applet.

I find if I click on the monitor I want to use then launch a program, that is where it will launch, but I have a different setup to yours I imagine (laptop monitor with regular monitor above it and setup up like one big screen I can more between, only one task bar).

---

### Post by chris137 on 2013-12-22
When using the attached monitor which is the case most of the time I do not need the other screen on.
Problem is that *if *I want to use the notebook's screen it should be available when I open the notebook.
What you explain seems to require an input over the attached monitor which is not really helpful because that I can do without any additionial program (I think) by just switching the screen off in the usual preferences.

---

### Post by Bucky Ball on 2013-12-22
Okay. Confused. Your monitors are not showing identical display? What you do on one is not replicated on the other, whether you can see it or not, or how have you got them set up???

---

### Post by chris137 on 2013-12-22
Oh I completely forgot that.
At first I tried to mirror them but the option is not available and I don't know why.
This would be also a solution.
It might be connected to the resolution beacause my notebook's display is 16:9 and my monitor is 4:3
I tried to change the resolution but the option just won't come available.

---

### Post by Bucky Ball on 2013-12-22
arandr doesn't allow you to mirror them either?

---

### Post by chris137 on 2013-12-22
I did not find any option there but I now just put the monitor over the notebook's display so they overlap.
Problem is that they do not have the same resolution so programs might start outside the monitor's range.

I will have a break now too because it's my birthday and there are a few things to do which are more important than my display settings of my 2nd computer :D

---

### Post by Bucky Ball on 2013-12-22
You can set the resolutions for each monitor individually with arandr (Outputs>choose output>resolution). 

Oddly, this works fine and no overlap with my minimal install, but when I'm using a regular Xubuntu install it has the overlap problem you mention ... except the resolutions on my laptop monitor and second monitor are both 1366x768! Haven't been able to figure out the problem there.

---

### Post by chris137 on 2013-12-22
I see that option but I can not modify the resolution of the notebook's display.
There is only one to choose from (1366x768) but I want to use 1024x768.

---

### Post by Bucky Ball on 2013-12-22
Ah. Is that resolution (1024x768) native to the notebook display and being prevented by an nvidia driver by any chance (have you a third-party graphics driver, nvidia or ATI, installed)?

---

### Post by chris137 on 2013-12-22
I actually thought I did not have any driver installed but I just checked and NVIDIA accerlerated graphics driver is activated.

---

### Post by Bucky Ball on 2013-12-22
With you. If the resolution you are trying you know to be native to that display then that driver is probably preventing it. There are various ways of going about this, and it came up just today. You can try post #1 here:

[http://ubuntuforums.org/showthread.php?t=1045106](http://ubuntuforums.org/showthread.php?t=1045106)

I used this method when installing just the other night and replaced the xorg.conf with what is on that post then rebooted. All sweet. This method allows you to use the nvidia driver while bypassing its nonsensical resolution restrictions. 

Just remember, though, before changing anything in xorg.conf to:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If anything goes pear-shaped then you have a copy of the original which you can put back with:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

If that method doesn't work, you might try disabling the nvidia driver altogether and running on the open source drivers (they should take over automagically). Change the resolution using Settings>Display in both instances, rather than in the nvidia-settings gui. 

Hope that helps. I have to get to bed now because am driving 750Kms home from the in-laws first thing tomorrow (we do an early xmas with them). I'll be back to see how things are going in around 20 hours, if I'm not, send out a search party! In the meantime, good luck and hope those suggestions get you somewhere.

PS: I would avoid going down the path of writing modelines for the monitor. That can be a real headache and rarely have I seen any success with it (dated approach). Removing the nvidia block altogether proves most fruitful from what I've seen.

---

### Post by chris137 on 2013-12-22
I am not sure xorg.conf is even used.
While trying to solve an other issue a few weeks back I think I read something about that.
But I can't remember where the configuration is stored here.
my xorg.conf looks like that so I do not think that it is being used in my case.
```
Section "Device"
Identifier	"Default Device"
Option	"NoLogo"	"True"
EndSection
```

---

