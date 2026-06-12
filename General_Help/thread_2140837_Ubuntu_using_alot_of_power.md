---
title: "Ubuntu using alot of power"
date: 2013-04-30
forum: General Help
---

### Post by illmattic on 2013-04-30
Hi,

I'm new to Ubuntu but I've noticed that when I run it my computer sounds like its using alot of power and my laptop gets very hot because of this. I have a hp pavalion dv6. When I run windows 7 it doesn't make the loud noise and the computer doesn't get as hot.

Is there any solution to this?

Thanks in advance.
Matt

---

### Post by JebusWankel on 2013-04-30
I would recommend installing the program powertop. It's a commandline utility so you can install it with
```
[sudo apt-get install powertop]("apt:powertop")
```
and then run it with
```
sudo powertop
```

This should give you some insight about what's going on. It could be a program running and taking a lot of resources or perhaps some hardware features such as cpu scaling not working so that your computer isn't running efficiently. I think you can make a lot of the recommended power saving tweaks through powertop. Another way would be to install the package laptop-mode-tools
```
[sudo apt-get install laptop-mode-tools]("apt:laptop-mode-tools")
```

---

### Post by Linuxisfast on 2013-05-01
Install any or all proprietary drivers listed under hardware drivers and then install TLP from [www.linrunner.de](www.linrunner.de) I have three laptops and with TLP the power consumption matches Windows.

---

### Post by JebusWankel on 2013-05-01
TLP and laptop-mode-tools are similar tools but like say, an anti-virus program, you're going to want to install just one since they might conflict. I think TLP is newer and maybe more advanced but laptop-mode-tools has ease of install on its side since it's in the default repos. You should be able to install it just by clicking my supplied link above.

This link is relevant [http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html]("http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html")

---

### Post by dandroid13 on 2013-05-01
They conflict, install one of them only.

---

### Post by 23senick on 2013-05-01
I had problems for another HP model, conversation here

[HTML]http://ubuntuforums.org/showthread.php?t=1994528&page=3&p=12086641#post12086641[/HTML]

read back and see some of the suggestions...proprietary drivers seem to be part of the solution. There are ways round it!

---

### Post by illmattic on 2013-05-01
how do I install the proprietary drivers?

---

### Post by Rebelli0us on 2013-05-01
You need the proprietary video driver. In Synaptic type fglrx for AMD or NVIDIA, that will list all available drivers.

---

### Post by Resistent on 2013-05-01
Maybe you also can use a Leightweight Desktop Enviroment like Lubuntu or Xubuntu.
You have just to select the Desktop Enviroment at the Login Screen, if already installed.

I am using Lubuntu, is very computer friendly, I am very happy. (it's fast, 
don't work so much in the background like filling the memory, so less work for the PC, less fan activity than Windows,)[COLOR=#444444][FONT=arial]
[/FONT][/COLOR]

---

### Post by dandroid13 on 2013-05-01
System config. > software sources > additional drivers

---

### Post by illmattic on 2013-05-01
Ok so something terrible happened. I installed all 3 of the propietary drivers and then when I installed the last one my internet disconnected and so I restarted the computer and this came up...

The system is running in low-graphics mode

Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself

What would you like to do?
Run in low-graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console login

But I can't see the mouse and I can't click any of the options or hit enter. One time it went into terminal mode but I don't know how I did that.

Please help

---

### Post by illmattic on 2013-05-01
and it seems now that my windows 7 is now operating like the ubuntu did using alot of power

---

### Post by dandroid13 on 2013-05-02
[FONT=Verdana]Windows and Ubuntu are totally unrelated, different partitions and filesystems, must be something else.[/FONT]

---

### Post by illmattic on 2013-05-02
nvm windows 7 works properly now but I'm still having the same problems with ubuntu

---

### Post by illmattic on 2013-05-02
can someone please help me out in this situation

---

### Post by 23senick on 2013-05-05
Can you use up/down keys or tab key to select the options and try them out?  I'd start with troubleshoot.  

You sound seriuously unlucky with this - it isn't usually so painful.  Do check out the conversation I mentioned earlier, there were fairly clear inctructions about installing/uninstalling fglrx, and I found that had a big impact.  Also, if you use jockey (through system menu[System config. > software sources > additional drivers]) apparently it often gives incorrect info about whether proprietary graphics drivers have been installed and are working.  Not sure why. So this may be one instance where using terminal and command line would be more trustworthy.  

Hope it gets sorted - you could always try a fresh install.

---

