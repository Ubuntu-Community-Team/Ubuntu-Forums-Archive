---
title: "Xubuntu power management?"
date: 2007-01-22
forum: General Help
---

### Post by brucedeluxe169 on 2007-01-22
Hey guys,

I just recently transitioned to Xubuntu from Ubuntu (mostly because I just love streamlined desktop environments).  Anyway, one of the first problems that I've run into, that I havent yet found a solution to is power management.  I run Xubuntu on a laptop, but I haven't been able to find any power options such as how long before the hard drive/display/system goes to sleep, CPU throttling options when plugged in, unplugged, etc.  All of this is available in regular Ubuntu, so I was wondering if these sort of options are in Xubuntu or am I just out of luck?

Thanks for any help guys!  :KS 



PS: I am a longtime reader of the Ubuntu forums, and have finally decided to register and partake in the forum activities!  I look forward to learning and contributing a great deal to the Ubuntu and Linux communities!

---

### Post by brucedeluxe169 on 2007-01-22
anyone know?

---

### Post by kerry_s on 2007-01-22
menu>settings>screensaver>the 2nd tab. Sorry i can't remember the exact wording i uninstalled that part when i installed, I don't use those, i prefer "xset".

---

### Post by -Phi- on 2007-01-22
Might not be your solution of choice, but I installed gnome-power-manager to give me more options on battery life and brightness settings etc.  You'll want to add it to Autostarted Applications too.

- Phi

PS. Welcome!

---

### Post by riceriot on 2007-02-13
Just

% sudo apt-get install gnome-power-manager

Then add it to your Settings > Autostarted Applications as command "gnome-power-manager"

You can access the configuration file by typing

% gnome-power-preferences

---

### Post by charding on 2007-11-12
gnome-power-manager doesn't allow CPU throttling which is what I need. I can't find anything that will give me these options, I guess installing powersaved instead?

---

### Post by snap on 2008-01-18
Don't know if this is too late but you can always enable laptop_mode

```
man laptop_mode
```

should help out a lot on configuring laptop mode, it is turned off by default.

And if you are not using a laptop then try installing cpufreq tools.
for example to set powersave mode on the cpu i use this
```
sudo cpufreq-set -g powersave
```
give this tool a try

and another option is to install the cpu frequency applet from gnome and run it in xfce.(Sorry  forgot the correct name of the applet , should not be too difficult to find if you search)

---

### Post by hristiyan on 2008-06-08
Very simple (even though it took me a while to figure it out, and remember exactly how i found it before)

Click on Applications, then Settings, then Settings Manager, then Screensaver, and right at the bottom, you'll see Power Management next to the Close button

---

