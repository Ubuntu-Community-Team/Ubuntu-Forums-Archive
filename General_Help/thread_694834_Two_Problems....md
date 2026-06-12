---
title: "Two Problems..."
date: 2008-02-12
forum: General Help
---

### Post by stuartwood89 on 2008-02-12
Hi everyone, I'm completely new to Ubuntu (just installed it today)

So I've finally got Ubuntu Studio on my PC, however I'm having a few problems which maybe some of you guys can help me figure out.  I've taken a photo of my screen just to clarify what problem I'm having:

[IMG]http://i147.photobucket.com/albums/r315/stuartwood1989/DSC00443.jpg[/IMG]

As you can see, I have a 19" widescreen, but although the resolution is set at 1440x900 in Ubuntu, I'm still getting the huge black bar on the left side of the screen, and everything is squashed horizontally.  When I start Ubuntu my monitor says 'out of range' and then 'auto configs', leaving me with what you see in the photo.

So that's one problem...

The other problem is that I can't get the internet to work.  I open up Firefox and I get 'Server not found'.  This is probably something to do with a message appearing during installation saying that my network interface adaptor hasn't been found.  Does anyone know how to get this working?

I'll post my system specifications just in case:
[LIST]
[*]ASUS M2V Motherboard (socket AM2)
[*]AMD Athlon 64 Processor (2.4GHz)
[*]200GB SATA HDD (also 80GB SATA for WinXP)
[*]ASUS nVidia GeForce 7600GS 512MB graphics card
[*]19" Widescreen Monitor
[/LIST]

I'd appreciate any help at all!

Thanks again.

Stu :grin:

---

### Post by apetresc on 2008-02-12
**Problem 1.** Have you installed the binary NVidia driver? If not, you should. Google "envy", install the package, and use it to get yourself the latest NVidia driver. Should help in more ways than one.

**Problem 2:** What is the output of ```
sudo /etc/init.d/network restart
```?

---

### Post by FuturePilot on 2008-02-12
You could also check the Restricted Driver Manager for a driver. System&#8594;Administration&#8594;Restricted Driver Manager

---

### Post by stuartwood89 on 2008-02-12
> **AdrianP said:**
> **Problem 1.** Have you installed the binary NVidia driver? If not, you should. Google "envy", install the package, and use it to get yourself the latest NVidia driver. Should help in more ways than one.

**Problem 2:** What is the output of ```
sudo /etc/init.d/network restart
```?

I just get 'unknown command' or 'incorrect *something else*'

I have to keep restarting to switch between OS's

I've tried typing that with and without spaces. :confused:

---

### Post by stuartwood89 on 2008-02-12
> **FuturePilot said:**
> You could also check the Restricted Driver Manager for a driver. System&#8594;Administration&#8594;Restricted Driver Manager

I looked there, and I saw the nVidia driver, so I went to check the box and I came across a message telling me to enable the driver.  I click yes and I get '*driver* not enabled'.

---

### Post by ugm6hr on 2008-02-12
I would suggest starting a new thread for the internet problem - it can get confusing with 2 issues being dealt with simultaneously in one thread.

Make sure you include the following details in your new thread:
How you connect to the internet (i.e. wifi / ethernet / router etc)
Security settings if you use wifi
The output from the following commands (case sensitive!):
```
lspci
lshw -C network
```

---

