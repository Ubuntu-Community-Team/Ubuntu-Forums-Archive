---
title: "Constant Apport-gtk Errors, All 4 CPU Cores Maxed Out For No Reason?"
date: 2013-04-04
forum: General Help
---

### Post by cbanakis on 2013-04-04
Running Ubuntu 32bit 12.10 on an Intel Core i3-2100 (3.1GHz Quad-Core)

I have no idea how or why, but my system recently started spitting error messages out of Apport-gtk like crazy.

Not sure if a recent update caused this or what, but the system is barely usable.

Additinally, all 4 cores are periodically maxed out at 100%, but if I look under processes, the highest cpu usage listed is for gnome-system-monitor itself at a only 4%.

Most of the pop ups do not even load correctly.

Apport just shows up in the dock, and the pop up is just a tiny square window with no text or controls.

If this were windows, I would think I have a virus.

Everything worked perfectly up until about 2 weeks ago.

The errors I am getting are...

```
Blank popup
```
```
System program problem detected
(Do you want to report the problem now?)
```
```
Possible GPU Hang
Did your system recently lock up?
```

I have been using Ubuntu for a few years, and I have never had any problems like this.

Please, does anyone have a clue whats going on with my system?

Thank you very much for any help.

---

### Post by ibjsb4 on 2013-04-04
I don't know if this cpu usage is apport or not, but take a look at this.

[http://ubuntuforums.org/showthread.php?t=2132316&p=12588783#post12588783](http://ubuntuforums.org/showthread.php?t=2132316&p=12588783#post12588783)

---

### Post by cbanakis on 2013-04-04
Thankyou very much for the super fast reply.

I dissabled Apport.

So far so good...

It is pretty funny that the ubuntu's error reporting process was causing all my errors.
(Right up there with "In order to recieve Windows Updates, you must first update Windows Update")

---

### Post by cbanakis on 2013-04-04
Well, it looks like my gpu is in fact hanging.

Not horrible, but there is definitely a problem.

It seems that my entire desktop locks up for a moment every now and then, but it recovers after a few seconds.
(Way better without all the Apport garbage though)

I guess I can live with it for now, but any suggestions would be great.

Thanks again for the idea of dissableing Apport.

Things are much better without it.

---

