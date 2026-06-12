---
title: "Ubuntu Turns Into Kubuntu...!!???"
date: 2007-12-07
forum: General Help
---

### Post by GravutyGuy on 2007-12-07
Right, here is the problem (and I am very annoyed)!

I've been running ubuntu now for about a year but i've always had xp for a few things that i didn't believe I could do on linux. Around the same time as getting my new pc i discovered wine and how it could replicate all the things i needed.

Decided to go all the way and install just ubuntu on my new dell machine. When i was at my local supermarket i saw the magazine 'Linux Format' and low and behold it had a distro of gusty supplied within. So i decided to buy it to save having to download, md5sum and burn - saving me time (or so i thought).

The cover of the dist dvd says "Ubuntu - new 7.10 realease! Exclusive enhanced version of the worlds most popular distro - Includes Gnome, KDE and Xfce"

I understand what gnome is (as it is my preferred environment) - i also know what KDE is (i tried it and didnt like it). Didn't know what Xfce was though so just installed the distro.

Everything went as normal, ubuntu installed and i follwed it up by adding the couple of bits on there that i needed - like wine, azureus and boinc. i had only restarted it after the installation. I kept it running as i run 'climateprediction.net' via boinc and takes a very long time to work through.

2 days later (today) i restarted my machine. Still my ubuntu log in page came up and i logged in as normal. Only this time the screen suddenly turned light blue and everything had changed. After trying to work out what the hell had happened i realised that it was xfce. So i had the great idea of 'removing' anything that said xfce in synaptic manager and restarted hoping that it would all be ok again. No such luck!!! I'm now presented with a KDE enviroment which i hate..

can anyone understand just what has happened? Why did it suddenly bring up xfce and then KDE (Kubuntu) after restarting???

More importantly, can i get ubuntu back without having to reinstall?

i know that was long winded but i wanted to give the full story in the vain hope that ican sort this out without reinstalling.

Anybody? Please?

Mikey

---

### Post by derby007 on 2007-12-07
They are just the different desktop enviornments, or sessions, you can choose what session (Gnome, KDE or XFCE) you want to log into. You can also have a default session. The choice should be at the bottom left on the 'login' screen.

---

### Post by sloggerkhan on 2007-12-07
have you tried selecting a gnome session when you log in?

---

### Post by rsambuca on 2007-12-07
You can also remove the other desktop environments with the following

sudo apt-get remove kubuntu-desktop
sudo apt-get remove xubuntu-desktop
sudo apt-get autoremove
sudo apt-get autoclean

---

