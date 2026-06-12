---
title: "searching for a virtual keyboard application in UbuntuStudio 22.04.1"
date: 2022-09-21
forum: General Help
---

### Post by Nosphky on 2022-09-21
I've just moved up from years of UbuntuStudio with Xfce to the new US 22.04.1 with Plasma and it's taken me a while to get lots of things sorted but one thing I can't find is an on-screen virtual keyboard that I can use with clicks of the mouse. When I search for virtual keyboards I get midi keyboards and Jack keyboards but what I would like is a plain old qwerty which I can swap to an azerty as needed.

A search in the KDE help manual tells me that a virtual keyboard is offered if a hardware keyboard is not available. This is not my case. And I don't need a touchscreen board.

I was so used to having this functionality linked to a keypress shortcut in the old Xfce UbuntuStudio that I took it for granted (as I do in a Windows 10 box) and, sadly, did not even note the name of the application.

I'd appreciate it if someone could advise an appropriate application/ package. Thanks.

---

### Post by dragonfly41 on 2022-09-21
Looking at my Ubuntu 20.04 (not 22.04) I have Florence virtual keyboard to use.
Also in Synaptic Package Manager search "keyboard" and I see others.

---

### Post by Nosphky on 2022-09-21
Hi dragonfly41 - The name Florence 'rings a bell' somewhere in my  memory. Unfortunately, neither Muon Package Manager (which seems to be  the 22.04 equivalent to Synaptic Package Manager) nor the Software  application produces any results for a Florence search.

Muon  Package Manager does produce some results for a virtual keyboard search  but they seem to be mainly Jack and midi keyboards (for music and audio  apps). It also produces several results for qtvirtualkeyboard-plugin and  libraries - but they seem to be related to front ends for qt 5 and if  they could be useful, I don't find the file to execute.  I don't  understand where to progress on that one.

---

### Post by dragonfly41 on 2022-09-21
Seems that this is one obstacle I must prepare for when I make the jump to 22.04.


[https://askubuntu.com/questions/1410105/florence-virtual-keyboard-missing-from-22-04-lts](https://askubuntu.com/questions/1410105/florence-virtual-keyboard-missing-from-22-04-lts)


[https://ubuntuhandbook.org/index.php/2022/05/enable-on-screen-keyboard-ubuntu-22-04/](https://ubuntuhandbook.org/index.php/2022/05/enable-on-screen-keyboard-ubuntu-22-04/)

---

### Post by Nosphky on 2022-09-22
dragonfly41 - yes, doesn't look easy. The 2 links you provided : the first (askubuntu) enables a Florence download but it's not clear to me that it's appropriate for my installation. The second link (ubuntuhandbook) does provide a couple of solutions for the Gnome desktop but I now have the Plasma desktop since UbuntuStudio moved from Xfce to Plasma.

I need to keep looking.

---

### Post by Nosphky on 2022-09-22
I found the answer for KDE Plasma.  I had a little revelation. I suddenly remembered that I used to fire up the virtual keyboard in UbuntuStudio 20.04 with Xfce desktop by using the shortcut Meta+O.  Knowing my habit of naming shortcuts by using the initial letter, I searched for software starting with O and found Onboard.

Onboard doesn't appear when searching for virtual keyboards - it is called a "Flexible onscreen keyboard". Who would have guessed?

Anyway - it's installed and coupled up to my old shortcut. It doesn't allow to change to an azerty keyboard but it does permit to type all international characters.

---

