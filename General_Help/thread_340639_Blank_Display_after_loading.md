---
title: "Blank Display after loading"
date: 2007-01-17
forum: General Help
---

### Post by dmachine on 2007-01-17
I installed Ubuntu and after I get the loading screen it just goes to a blank screen. I am using an ATI AIW 2006 edition with an Apple 20" Cinema Display. I also had this same problem when I installed Fedora Core 6. Can someone please help me?

---

### Post by dcstar on 2007-01-17
> **dmachine said:**
> I installed Ubuntu and after I get the loading screen it just goes to a blank screen. I am using an ATI AIW 2006 edition with an Apple 20" Cinema Display. I also had this same problem when I installed Fedora Core 6. Can someone please help me?

CTRL-ALT-F1 should get you to a text login screen, then you should be able to log in and manually edit your xorg.conf file to a state to get a basic working system.

Do a forum search for detailed instructions on how to get the VESA driver set up, then you can try and resolve the underlying problem that you have.

---

### Post by dowbjts on 2007-01-17
Boot up in recovery mode and type startx at the # prompt.  Does the desktop load?

---

### Post by dmachine on 2007-01-18
> **dcstar said:**
> CTRL-ALT-F1 should get you to a text login screen, then you should be able to log in and manually edit your xorg.conf file to a state to get a basic working system.

Do a forum search for detailed instructions on how to get the VESA driver set up, then you can try and resolve the underlying problem that you have.

When I get to the login it asks for a login name and I am not sure what it is.

---

### Post by jakson84 on 2007-12-15
Hi all,
Even i face a similar problem,
Can anyone help me how to Install Ubuntu 7.10 properly. Nothing comes after loading. I get CPU frequency scaling not supported as error. And also **AIGLX: Screen 0 is not DRI capable as error**. I tried sudo **dpkg-reconfigure xserver-xorg **and set the appropriate values. But i can see my gnome is running. I get half my background in the display and the remaining half i get 2 ubuntu logo which is 4 bit colour.

I have AMD Semphron and Samsung 17 inch monitor.

I tried to startX in Recovery mode still its not coming.
It showed **AIGLX: Screen 0 is not DRI capable as error**
 Some one please help me i need it very urgently. Thanks.

---

