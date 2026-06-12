---
title: "Help Help Help"
date: 2008-02-09
forum: General Help
---

### Post by antiderivative on 2008-02-09
I tried to install new graphics drivers, so I had to uninstall the others, and this was for the same graphics card. Obviously, the new ones didn't work, so I uninstalled them, and reinstalled the old ones. Obviously, this didn't work, even after I tried it for the millionth time!!! The problem is that my computer keeps defaulting the card driver to some other card, not the one I'm using (nvidia). Each time I change it back, and when I reboot it goes back to the drivers of a card that I'm not using!!!:(:(:(:( Now when I enable the drivers for my card, I can get back some settings, but heaven forbid the special effects settings, where each time I click it enable, it says "couldn't enable drivers" without providing why or what caused it to not enable!!! I've had an internet connection too the whole time. Please Help!!!

---

### Post by yabbadabbadont on 2008-02-09
If you haven't already, try running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see if it helps.

---

### Post by antiderivative on 2008-02-09
Now get this, each time I enable the driver, my graphics get worse? When I click disable nvidia drivers, my graphics get betterl. And yes, it is definitely an Nvidia card I have, an Nvidia Mx 4000 to be exact, which was running fine earlier today. It's only because I tried to install an open gl thing, and I had to uninstall another to test it. I reinstalled what I unistalled. I am completely unable to do anything to fix this! I've tried your code. My computer just repeats the same thing!!! Ok, why is it when I click 'enable _**NVIDIA**_' drivers, it defaults to the drivers for a card called Vesa????!!!! A card I've never heard of or ever had in my computer!!!

---

### Post by yabbadabbadont on 2008-02-09
VESA is a graphics specification to which most modern video cards comply.  That is why it defaults to it when it runs into trouble.  ;)

An MX4000 card probably needs the "legacy" version of the nvidia drivers.  I imagine that it is trying to install the wrong version (or you chose the wrong version).  :D

---

### Post by PmDematagoda on 2008-02-09
Do this:-
1) Kill the GUI(Graphical User Interface) using:-
```
sudo /etc/init.d/gdm stop
```

2) Install the legacy Nvidia drivers:-
```
sudo apt-get install nvidia-glx-legacy
```

3) Enable the driver using:-
```
sudo nvidia-settings --config enable
```

4) Reconfigure your X-Server using:-
```
sudo dpkg-reconfigure xserver-xorg
```
select the driver as "nvidia" and any other options you may need.

5) Restart the GUI using:-
```
sudo /etc/init.d/gdm start
```

---

### Post by antiderivative on 2008-02-10
It's not legacy drivers, because I installed the legacy drivers, and then when I clicked 'enable restricted drivers', it uninstalled the legacy drivers, and installed the the plain open gl drivers (not legacy or new). This then repeated the same problem I've had for the past few hours. Does Ubuntu have any equivalent to Windows XP's system restore?

---

### Post by yabbadabbadont on 2008-02-10
I wonder if the MX 4000 is one of the cards that got blacklisted in Gutsy?

Do you know PmDematagoda?

---

### Post by rainwalker on 2008-02-10
Also, if you're having trouble with graphics and you're trying to change settings, you can login in safe graphics mode by selecting it at the login screen under "Session" (wherever it's located, different for each theme).

---

### Post by antiderivative on 2008-02-10
No, I know this for sure because my system ran this card fine a for the past few weeks.

---

