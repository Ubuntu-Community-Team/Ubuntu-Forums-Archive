---
title: "Tap to click is right clicking and I want it to left click"
date: 2018-03-20
forum: General Help
---

### Post by patrick852 on 2018-03-20
When I tap my mousepad on my dell inspiron it does a secondary (left) click but I want it to do a primary (right) click I cannot find any setting to change this.

---

### Post by TheFu on 2018-03-20
Which desktop? 
Which window manager?

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I use 2-fingers to get a right-click and 3 fingers to get a middle-mouse click on my system.  I'm running Openbox as the WM without any DE.

---

### Post by patrick852 on 2018-03-20
16.04 Unity taping with two fingers for me does a left click

---

### Post by TheFu on 2018-03-20
> **patrick852 said:**
> 16.04 Unity taping with two fingers for me does a left click

Well, that isn't nearly as useful as a left-click with 1 finger.

Could you have setup a left-handed mouse accidentally?
[https://help.ubuntu.com/stable/ubuntu-help/mouse-lefthanded.html](https://help.ubuntu.com/stable/ubuntu-help/mouse-lefthanded.html)

There is a bug: [https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/824436](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/824436) - is the description what you are seeing too?

---

### Post by patrick852 on 2018-03-20
My mousepad is set to right handed

---

### Post by TheFu on 2018-03-20
> **patrick852 said:**
> My mousepad is set to right handed

Sorry, I was thinking that perhaps the mouse settings were being applied to the touchpad as well.  

In my window manager session startup, I setup the touchpad like this:
```
synclient TapButton1=1 &
synclient TapButton2=3 &
synclient TapButton3=2 &

```
I think it can be run from a terminal as well, within the session and it will impact everything. I don't know how normal Ubuntu session startup things are invoked. Sorry.

---

### Post by patrick852 on 2018-03-20
That makes it work how it is supposed to, but when I restart it reverts I know there is a way to setup commands to automatically run on startup but is there an easier way?

---

### Post by TheFu on 2018-03-20
> **TheFu said:**
> Which desktop? 
Which window manager?


You can't do it at startup. It must wait until a session login happens, which is why I asked the above questions first.  Not that I can help with anything other than the GUI I use, which is openbox, without any DE.  Anything other than that and you should seek out a desktop guide document for the version you are using - look for "autostart at login" programs.

---

### Post by patrick852 on 2018-03-21
Ok I'll look for a way but until then I'll just run them manually whenever I restart my pc. If I find a way to automatically run the commands at startup I'll put them here. Should I mark it as solved or wait until I find a program to run the commands?

---

### Post by TheFu on 2018-03-22
> **patrick852 said:**
> Ok I'll look for a way but until then I'll just run them manually whenever I restart my pc. If I find a way to automatically run the commands at startup I'll put them here. Should I mark it as solved or wait until I find a program to run the commands?
If you figure out what DE you are running, then there **is** a method to have commands run automatically at login via a GUI session.  Popular choices for DEs are:
* Unity
* Gnome3
* XFCE
* LXDE
* Mate
* KDE

Each of those has a method, which is documented.   For example: [https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html) - is for Unity (I think).  Might be for Gnome3 since it says 17.10.  IDK.

---

### Post by patrick852 on 2018-03-22
I'm using Unity 16.04 LTS for now but once the next LTS comes out I'm probably going to switch to it. I tried pasting the command into the startup program but it didn't work the command works in the command line though so I think that program is only for programs.

---

### Post by patrick852 on 2018-04-05
A recent update seems to have fixed this problem.

---

