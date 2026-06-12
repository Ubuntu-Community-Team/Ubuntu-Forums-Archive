---
title: "Ubuntu freezez after login. Video card settings?"
date: 2013-02-19
forum: General Help
---

### Post by ne0phyte on 2013-02-19
Hi.

First of all, when entering my crypt password at boot my screen(s) goes to "no signal".

And at the login screen, my left monitors shows a normal image, but the left one copies half the right one, and is acting weird.

The system was working before reboot (except the crypt no signal), and after doing a system update and changing to theme to another one provided by ubuntu, it does not work.

This is a fresh install.

Videocard: Asus 6950


EDIT: I was now able to boot using only one monitor. After installing the other monitor, it is found but black.

EDIT2: After another clean install, I noticed that this only occurs after installing updates.

This is how it looks like after updates installation and reboot, and the GUI is freezed. I am able to enter CTRL+ALT+F1.

[IMG]http://i48.tinypic.com/9a5xlv.jpg[/IMG]

Any help would be appreciated.

---

### Post by ne0phyte on 2013-02-19
I did not choose to install any proprietary drivers this time during installation.

---

### Post by firekage on 2013-02-20
I have similar behaviour on Ubuntu but on nvidia card and all of their drivers (from nvidia website, from xswat, from xorg-edgers and from ubuntu repo).

In my case, i have only one monitor, but ubuntu detects few of them, than divides my screen and it looks like this:

[http://ubuntuforums.org/showthread.php?t=2098315](http://ubuntuforums.org/showthread.php?t=2098315)

Don't know what to do, i use nouveau because only this works. On a clean system it is nearly ok - sometimes there is no screen at all, i have to kill X few times, and i can login, but after login screen can be divided, or not...totaly randomly.

---

