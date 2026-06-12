---
title: "DVI - VGA issues..."
date: 2008-04-01
forum: General Help
---

### Post by byzantines2000 on 2008-04-01
When I start my computer up, I can only see the boot screen with the VGA cord in my monitor. Then, it will go to "No Signal", after that I have to insert my DVI cord. I have an Nvidia 8800 GTS and a HD widescreen monitor. This effect is even worsened when I try to get vista to work. Is there a way to make one cord be universal?

I have had a pretty strong experience with this issue for almost a year now. With vista, I had to spend hours on the gateway tech support line ever since I have recieved this, and they rigged up vista where I could use the VGA cord all the time, but with all my 3d support neutered... which meant no games, video editing. AKA --> Damn near worthless.

Any help would be very appreciated, or just some explanation. I have updated all my drivers and checked other forums such as the Nvidia forums, and other random googled ones. Bad Nvidia support for my certain type of card has been mentioned, and RAM issues possibly?
I don't know...

---

### Post by danwood76 on 2008-04-01
If you just leave the DVI in from the start what hapopens?
It might just be that the splash screen is messed up and for some reason likes vga as opposed to DVI

---

### Post by byzantines2000 on 2008-04-01
It will just stay no signal. But, it I was to start out with the dvi cord, and when I hear the little sound that comes with the login screen, I can switch to the vga cord and everything will work.

I have to switch out my cords at sometime to be able to see what I am doing. I can't leave any cord in from start to finish - per say.

---

### Post by danwood76 on 2008-04-01
sounds like a graphics card issue if it does the same in vista.
it doesnt switch to the other output on the card does it?

When you knock the cable out of my ati card it switches outputs, that had me guessing for a while.

---

### Post by byzantines2000 on 2008-04-01
What do you mean exactly? The other output slot in the card itself? I thought that was for crossfire purposes, which if i had another card maybe i could just link the two and then connect each cord to a different card and both to my monitor? lol, i doubt that would work though...

This is the second card I have gotten too. They replaced my hard drive and my graphics card both. Maybe I should try to pawn this one off and get an ati?

Ill check with the other slot and see what happens....

---

### Post by danwood76 on 2008-04-01
The second DVI slot on your card is for a second monitor but it can also be used (in modern graphics cards anyway) can be used as a primary screen aswell so its worth a try.

---

### Post by byzantines2000 on 2008-04-01
It doesn't work. I know my video card should be good enough for it. It should be somewhat top-end still... I might just get an ATI of similar specs and see what that does...

---

### Post by Nunu on 2008-04-02
I have a 8800 as well. I also have two LCD's connected to it one VGA and one DVI and both start up fine. obviously they are cloned on the initial install but after installing the OS and loading the restricted driver every thing is cool, i can select either to span the desktop across both screens or have two seperate desktops. Maybe there is a problem with your card.

---

### Post by danwood76 on 2008-04-02
if you boot with the live CD do you get the same behaviour?

---

### Post by byzantines2000 on 2008-04-02
Nunu - But to have it replaced with a new one and it still does the same thing?

Danwood - If I boot up with the cd, I can only use the vga cord. I only really can use the dvi cord until after I install the driver. 

Maybe, I should spill some liquid on it, and try to milk gateway for a new computer via warranty....hehehe

I don't think anyone can really understand my problem as it is a very unique one from what I understand due to reading other forums and spending hours on the phone with tech. support.

---

### Post by danwood76 on 2008-04-02
Are you installing the latest driver(from the nvidia site) or the one from the restricted drivers manager?

I have a feeling that the vesa driver (probably used on the live CD) wont access your DVI but only VGA.
Also during the boot until X loads it uses the vesa driver aswell.

btw spilling water on something voids your warranty so I wouldnt do that.

---

### Post by byzantines2000 on 2008-04-02
Its the restricted driver that i have on linux. I have the newest driver from nvidia on vista. and what is this vesa driver? is it possible to reinstall it? 

and thanks for the warranty info. :P

UPDATE: I found and downloaded my driver from Nvidia. I am having issues installing it, I type the command into the terminal but it cannot open the file. When I do figure out how to install it, and if it doesnt work (my screen going out on both cables), how would i be able to fix it?

---

### Post by danwood76 on 2008-04-02
The vesa driver is a generic driver for all graphics cards.
They all comply to the vesa standards at basic level so that BIOS and so on can access them.

What errors are you getting from the terminal when trying to install the nvidia driver?
And what are the steps you have taken?
I will help you install these drivers.

If it doesnt work then I would say that maybe your graphics card has some incompatibilities with your motherboard, so if it doesnt work I would update your motherboards BIOS this may help with hardware incompatibility.
But otherwise try a different graphics card if you can.

---

### Post by byzantines2000 on 2008-04-03
It says that it must be installed under root. so does that mean under the directory or under the user root, I saw that there is a root user and i tried to delete it, but got a message saying that if i delete the administrator then my computer will be unusable. Then i changed my mind.

---

### Post by danwood76 on 2008-04-03
the command sudo allows you to run programs or scripts with root user privaliges.
The root user is your administrator account and has access to everything on the system, its best not to use sudo too often but it is needed when installing drivers or insyalling software manually.

so im assuming you have downloaded the latest version (169.12) of the nvidia drivers, this would be the full command:
```

sudo ./NVIDIA-Linux-x86-169.12-pkg1.run

```
it will then ask you for your password and the installer should start.

---

### Post by byzantines2000 on 2008-04-03
ok that makes sense. I tried it, and then it gave me an error about an x server...
Ill do more research on it in the morning, i need to go to bed, early class tomorrow.

---

### Post by danwood76 on 2008-04-03
Oh yeah the nvidia drivers require you to shutdown GDM and X to install the drivers.

You might try the envy script:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It will install the latest driver for you so will save you a bit of bother.

---

### Post by byzantines2000 on 2008-04-03
Does it automatically detect the needed driver?

Oh, well it says its done and i need restart my computer. *crosses fingers and hopes it will work*



I still have to switch cords at the login screen.

How would one go about updating the BIOS?

---

### Post by danwood76 on 2008-04-03
WHat exact model of computer or motherboard do you have?

---

### Post by byzantines2000 on 2008-04-03
My motherboard is Intel (Big Arm) 975X Viiv Motherboard [Part #4006151R]

Its in a gateway fx 500 series....


Can i reinstate the restricted 3d driver for desktop effects purposes? I tried to get my cube back, but it says I need to enable the driver. Will that clash with my new driver?

---

