---
title: "No Sound bluetooth A2DP sink"
date: 2022-03-12
forum: General Help
---

### Post by matrooswolf on 2022-03-12
Hi,

I have a Sony wh-1000mx3, which worked just fine until lately. Now I have no sound when bluetooth connects with A2DP sink (high quality sound), but only when the headphones connect as a headset (horrible mono sound).
I can connect just fine, choose the A2DP sink profile, but no sound. In pavucontrol, I can see the sound meter moving, but no sound comes out of the headphones.

I don't really know what changed and I've tried a 100 possible solutions, but nothing works. 

I am on Ubuntu 20.04.4 LTS, fully updated, Gnome 3.36.8, X11, and kernel 5.16.12

I suspect it is a problem with the package bluez 5.53-0ubuntu3.5 and I would like to try to update it to the latest version 5.63 to try if that fixes problems, or bluez-git, but I have no idea how to do that. Is there a PPA for bluez? Downloading the package only gives me errors.

Any help would be greatly appreciated.

Sounds works perfect with a cable by the way, just not with bluetooth (and it used until some time ago).

---

### Post by him610 on 2022-03-13
I have bluez 5.53-0ubuntu3.5 installed, and I have no problems connecting to my Sony SRS-XB-13.

Please show the results, between the code tags, of...
```

dpkg -l blue* 

```

---

### Post by matrooswolf on 2022-03-15
Hi thanks for the reply,
I also have bluez 5.53-0ubuntu3.5 installed (I can see it in synaptics), and never had a problem, until recently, still can connect as a headset, but not with high quality audio.
```
dpkg -l blue*
``` gives met nothing (no packages found matching blue horse .jpg (which is a picture of a painting of a blue horse ;) ) 
```
dpkg-query: geen pakketten gevonden die overeenkomen met blue horse .jpg

```
Cheers

---

### Post by him610 on 2022-03-17
matrooswolf,

It looks like you are missing something. Here is what I get...
```

$ dpkg -l blue* | grep ii
ii  blueman                2.1.2-1ubuntu0.3 amd64        Graphical bluetooth manager
ii  bluez                  5.53-0ubuntu3.5  amd64        Bluetooth tools and daemons
ii  bluez-cups             5.53-0ubuntu3.5  amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd            5.53-0ubuntu3.5  amd64        bluez obex daemon

```

They can be reinstalled using apt or apt-get, you can also use synaptic.
```

sudo apt-get update
sudo apt-get install blueman bluez bluez-cups bluez-obexd

```
That should reinstall the missing bluetooth programs.

---

### Post by matrooswolf on 2022-03-20
Hi Him60,
There must be something wrong with the command that gives me the weird error.
If I put ```
dpkg -l bluez* | grep ii
``` I get ```
ii  bluez          5.53-0ubuntu3.5 amd64        Bluetooth tools and daemons
ii  bluez-cups     5.53-0ubuntu3.5 amd64        Bluetooth printer driver for CUPS
ii  bluez-obexd    5.53-0ubuntu3.5 amd64        bluez obex daemon

``` and when I put ```
dpkg -l bluem* | grep ii
``` I get ```
ii  blueman        2.1.2-1ubuntu0.3 amd64        Graphical bluetooth manager

``` So it seems I have all packages installed. I can also see them in Synaptics.

What I would like to know is, how can I update bluez to a newer version (5.64 is the latest) to see if that fixes the problem. But I don't know how to do that or if their is a repository for that.

Cheers

---

### Post by matrooswolf on 2022-03-23
Okay, problems is not with bluez or some software, but with the headphones settings.

Headphone is a Sony WH-1000xm3.

From the Sony help guide.
```
To select the “Priority on sound quality” mode

When the headset is in the “Standard” mode, turn it on while holding the VOLUME + button down. The “Priority on sound quality” mode is selected.

From the “Priority on stable connection” mode, turn on the headset while holding the VOLUME + button down. Turn off the headset once, then turn it on while holding the VOLUME + button down again.
```

Problem, there is no volume button on the WH-1000xm3, the right earpiece serves as a volume button. So turning off the headphone while touching the right earpiece and then turning it back on while putting a finger on the right earpiece solved the problem.

Back on high quality sound.
Pff....

---

