---
title: "Installing a GUI on Ubunutu 5.10"
date: 2005-11-02
forum: General Help
---

### Post by Keshyden on 2005-11-02
I have ran the server install for Breezy on an old Thinkpad (333 MHz, 64MB Ram) after previously trying GNOME. GNOME ran horribly.  WHat I am looking for is a way to install a GUI (recommend one) from the command line. I am connected to the internet via Wifi.  I am not good with command line stuff, so the more specific the better.

I can use apt-get and all that. I just don't know what exactly I am looking for.

Thanks.

:D

---

### Post by Kyral on 2005-11-02
Well, there are Metapackages for GNOME, KDE, and XFCE. It sounds like you don't like GNOME, and if GNOME didn't run well, I don't think KDE will either (CPU specs?) so I'd try XFCE, I have a high end computer and I prefer XFCE anyway :D Anyway the command is

```
sudo apt-get install xubuntu-desktop
```

---

### Post by Keshyden on 2005-11-02
I am not at my desk right now. But that command will get me a simple GUI? Does it include something like synaptic? And I can install and use apps lke Firefox and that sorta thing?

Edit: Any advanced setup? How do I launch the GUI? Just a restart after install?

---

### Post by Qrk on 2005-11-02
It gives you a very gnome like gui. You may have to apt-get synaptic (sudo apt-get synaptic) or firefox, but both will run on it.

---

### Post by Keshyden on 2005-11-02
I type sudo apt-get install xubuntu-desktop and this what it says:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xubuntu-desktop

Why is this? Does it have something to do with the universe I have read about. I don't know how to make sure that is enabled or whatever.  It didn't ask me for the cd so I don't know.

Did I type it wrong?

---

### Post by Qrk on 2005-11-02
No. You need to add universe

Type

sudo nano /etc/apt/sources.list

and remove the # in front of the lines of repositories you want added. (all of them, but not the lines of intructions, only the lines of addresses.

---

### Post by Keshyden on 2005-11-02
Great! It is installing now.

Two more things.

How do I start the GUI, or is it start automatically?

Can I add more than one GUI? Like Redhat uses both KDE and GNOME

Thanks alot.

---

### Post by Kyral on 2005-11-02
Hmm, xubuntu-desktop doesn't bring in xdm, kdm, or gdm...

GDM would suffice.

```
sudo apt-get install gdm
```

It will load at boot and allow you to login and select your Window Manager (Sessions button)

It should auto configure itself, and yes you can install more than 1 GUI (I have like 5 right now..) and all of them SHOULD automatically put an entry in the DM when they install

---

### Post by Keshyden on 2005-11-02
GDM is a boot manager?  Is there any other good GUIs that I should try. I am just trying to learn as much as I can about Linux.

My next goal is to get the stupid WUSB11 set up.

---

### Post by Qrk on 2005-11-02
GDM is a login manager. It basically allows you to choose which desktop you want to run. 

After you install GDM, type 

startx

it will start xorg and your desktop.

---

### Post by Keshyden on 2005-11-02
Awesome! Looks great and runs better! Thanks for your help guys.

---

