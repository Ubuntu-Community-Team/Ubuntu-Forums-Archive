---
title: "How to enable desktop compositor"
date: 2014-02-11
forum: General Help
---

### Post by oldtraveler2 on 2014-02-11
I have a program that requires desktop composition to be enabled.  How can I do that?

---

### Post by slickymaster on 2014-02-11
Don't know with what DE are you dealing, but in Xubuntu the compositor can be checked (if it is not already) via the window-manager tweaks, under the Compositor tab.

---

### Post by oldtraveler2 on 2014-02-11
Using Ubuntu 13.10 neither Unity Tweak Tool nor Tweak Tool has a "compositor".

---

### Post by ajgreeny on 2014-02-11
Is it in compizcconfig settings manager, where you enable or disable the various compiz plugins?

I don't use unity or compiz so do not know the answer, but it would seem to be a possibility, as I am pretty sure that compiz has compositing available.

---

### Post by deadflowr on 2014-02-11
^^^^Aye, ccsm has a plugin called composite.
I don't know if that's what you're looking for, though.

I thought it was set already.

What's the program, anyway?
Maybe knowing the app can help us determine the compositing situation.

---

### Post by oldtraveler2 on 2014-02-11
> **ajgreeny said:**
> Is it in compizcconfig settings manager, where you enable or disable the various compiz plugins?

I don't use unity or compiz so do not know the answer, but it would seem to be a possibility, as I am pretty sure that compiz has compositing available.
Ubuntu doesn't seem to have compiz.

---

### Post by deadflowr on 2014-02-11
> **oldtraveler2 said:**
> Ubuntu doesn't seem to have compiz.

What are you running then?
compiz is a core part of the unity desktop.

Are you running 12.04?
If that's the case, then you might be running unity2d which doesn't use compiz, but instead uses metacity.
(Or something like that)

---

### Post by oldtraveler2 on 2014-02-11
[QUOTE=deadflowr;12926647
What's the program, anyway?
Maybe knowing the app can help us determine the compositing situation.[/QUOTE]

The program is Oxynger KeyShield. It is installed on win7 & as a guest of VMWare Player in Ubuntu 13.10.

---

### Post by deadflowr on 2014-02-11
> The program is Oxynger KeyShield. It is installed on win7 & as a guest of VMWare Player in Ubuntu 13.10.                 

This is what you would call relevant information.
I don't know anything about how VMware works, but others do.
Good Luck, anyway.

---

### Post by grahammechanical on 2014-02-11
Compiz is a compositor/windows manager and it is installed in Ubuntu by default. Without Compiz Ubuntu would not have a desktop user interface.

Ubuntu does not have CompizConfiguration Settings Manager (CCSM) installed by default. We have to install it. It is in the Ubuntu Software Centre. And it does have a setting called Composite.

Oxynger Keyshield is a Windows application. which you knew but we did not. If you are running it in Windows that is being run in a virtual Machine that in turn is running in Ubuntu then, it could be that you need to change a setting in the Virtual Machine.

Regards.

---

### Post by oldtraveler2 on 2014-02-11
I just opened Ubuntu Software Center and searched for CompizConfiguration Settings Manager. The message received was "no items match CompizConfiguration Settings Manager".  Same for 
Compiz Configuration Settings Manager.

 Is there another way to get there?

---

### Post by deadflowr on 2014-02-11
The package is compizconfig-settings-manager.

---

### Post by oldtraveler2 on 2014-02-11
> **deadflowr said:**
> The package is compizconfig-settings-manager.

Thank you.  I now have CompizConfig Settings Manager. There is a plugin called "enable composite" which is checked by defaut.

I have not found a way to enable desktop composition in the WIN 7 guest OS so I was hoping that it could be enabled in Ubuntu to solve the problem.  No dice.

The program I wanted to run (Oxynger Keyshield) prevents keylogging.  I like to use it with passwords. I'll search for another similar program.

---

