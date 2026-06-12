---
title: "Many windows are so stretched the OK/Cancel buttons go off screen"
date: 2020-05-02
forum: General Help
---

### Post by deutschegabanna on 2020-05-02
In LibreOffice, for example, stuff like options and other dialog boxes have arbitrarily set height that's bigger than my 600 px and these windows cannot be resized - well, width can be, but height apparently no, which is mindboggling.

I tried Monitor Settings but the highest I could go was exactly 1024x600. I also tried a command like "gtf 1900 1600 60" but that didn't do anything.

What can I do then? I'm unable to use LibreOffice without it.

Thanks for any help and have a nice day :KS

---

### Post by CelticWarrior on 2020-05-02
Welcome.

The first question that begs for an answer is about the resolution. Are you really limited by that resolution or are you using it because somehow the system isn't detecting the proper resolution correctly? If that's the native resolution then you'll have to live with it, there's nothing that can change that.

The next question is about the desktop environment. Are you using the standard Ubuntu or some flavor, like Xubuntu, Kubuntu, Lubuntu, Ubuntu-MATE, Ubuntu-Budgie, etc.? Adjustments, if any, are specific to the DE.

Finally, even if limited by 1024x600, all you need to do is maximize the windows. Everything should fit the available area. Of course, such resolution which is typical of the netbooks of 10-12 years ago, is the worse for productivity because of the reduced "real estate". If you can use an external monitor with higher resolution that will mitigate the problem.

---

### Post by deutschegabanna on 2020-05-02
> **CelticWarrior said:**
> The next question is about the desktop environment. Are you using the standard Ubuntu or some flavor, like Xubuntu, Kubuntu, Lubuntu, Ubuntu-MATE, Ubuntu-Budgie, etc.? Adjustments, if any, are specific to the DE.

I thought I set the topic prefix to Lubuntu. Well, if that didn't work, i'm sorry.

> **CelticWarrior said:**
> Finally, even if limited by 1024x600, all you need to do is maximize the  windows. Everything should fit the available area.

That's the most logical option, true, but it still doesn't work. The height won't budge. It's more than 600 even when maximised.

EDIT: And yes, it's the biggest resolution available in Monitor Options. If that's actually the biggest **possible**, I don't know.

---

### Post by CelticWarrior on 2020-05-02
Please give some hardware specifications. Again, the only laptops I know that had such limitation were the infamous "netbooks" from 10-12 years ago, with 8"-10" screen size.

If any other then the resolution is likely to be wrong and that would explain why the program windows is bleeding outside of the usable screen, something that wouldn't happen in those aforementioned "netbooks".

---

### Post by deutschegabanna on 2020-05-02
It's an Acer Aspire One laptop D257-N57DQkk

---

### Post by CelticWarrior on 2020-05-02
> **deutschegabanna said:**
> It's an Acer Aspire One laptop D257-N57DQkk

So, yes, it is one of those I was talking about. 1024x600 is indeed the max resolution the small screen supports. The old Intel iGPU supports higher resolution in an external monitor but if you don't have one that's a moot point.

Let's try to find solutions for the available hardware. Have you tried grabbing (click and hold) the top bar of those options windows and drag them all the way to the top? If possible for those windows they should then stretch to full screen and make the buttons in the bottom visible.

---

### Post by ajgreeny on 2020-05-02
Although it's not quick nor very intuitive to do, you can hold left Alt, click anywhere in the window or dialogue box you're using and move it anywhere you need to get to parts that are invisible.

I'm a bit surprised that Libreoffice is even worth using on that hardware, and just wonder if abiword and gnumeric might be far better to use; both are in the repos.  You might even find dialogue boxes from them are more appropriately sized.

---

### Post by Dennis N on 2020-05-02
Click Window Menu on title bar (upper left). **Leave menu open** and position mouse for dragging anywhere on the window. Don't press any mouse buttons. Press M. Cursor changes to hand and grabs the window. Without pressing a mouse button, move the window partly above top screen edge with the mouse so you can see the lower part. Click the window to cancel the move and click the action you want. If necessary, Alt+F4 usually will close a window.

Hold Alt+Mouse Click doesn't work in LXQt destop (Lubuntu). Get XFCE or MATE to have this feature.

---

### Post by deutschegabanna on 2020-05-02
> **ajgreeny said:**
> Although it's not quick nor very intuitive to do, you can hold left Alt, click anywhere in the window or dialogue box you're using and move it anywhere you need to get to parts that are invisible.

I'm a bit surprised that Libreoffice is even worth using on that hardware, and just wonder if abiword and gnumeric might be far better to use; both are in the repos.  You might even find dialogue boxes from them are more appropriately sized.

The alt thing did indeed work. You're a lifesaver! Thank you :)

A propos LibreOffice, the distro had abiword by default but I need Zotero add-on for bibliography and it only supports LibreOffice.

---

### Post by deutschegabanna on 2020-05-02
> **Dennis N said:**
> Hold Alt+Mouse Click doesn't work in LXQt destop (Lubuntu). Get XFCE or MATE to have this feature.

With all due respect, but it seems to work for me no problem. I don't know why, but I'm glad.

---

### Post by Dennis N on 2020-05-02
> **deutschegabanna said:**
> With all due respect, but it seems to work for me no problem. I don't know why, but I'm glad.

What version of Lubuntu? Are you still on 18.04 with LXDE? It does still work with that desktop. But not in Lubuntu 19.10 with LXQt.

---

### Post by CelticWarrior on 2020-05-02
> **deutschegabanna said:**
> With all due respect, but it seems to work for me no problem. I don't know why, but I'm glad.

It depends on the release. If running Lubuntu 18.04 that's LXDE whereas any 18.10+ is LXQt to which the comment you replied to mentions.

---

