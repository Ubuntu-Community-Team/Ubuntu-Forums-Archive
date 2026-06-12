---
title: "Ubuntu Crashes"
date: 2006-12-13
forum: General Help
---

### Post by mohdridha on 2006-12-13
Hello guys, I got some problem..

Whenever i insert my thumbdrive to the USB port, the X desktop will hang and nothin can be done. I cant move my mouse and keyboard also. SO there are nothing that can i do just pressing the reset button.

I try to remove the automount feature through gnome-volume-properties, and it didnt work. So how?


One more thing, can i manage a bandwidth for LAN using Ubuntu?
Thanks

---

### Post by _Phil on 2006-12-13
Hi

hmm strange problem.
Have you tried to kill the X Server and restart it? if not do so by pressing
**Ctrl + Alt + Backspace**.
This will kill X Server and normally restart it. If not and you are in the console try **startx**

Can you change to consoles after X Server freezes? (**Crtl + Alt + F1-6**)

cheers
phil

---

### Post by wpshooter on 2006-12-13
How long has it been doing this ?  Has it always done this or is this something that worked and has since stopped working ?

If the former, I would say that something went bad during your O/S installation.

Did you check the integrity of your Ubuntu installation CD by running the verification test that is found on the initial Ubuntu boot screen menu ?

---

### Post by mohdridha on 2006-12-14
> **_Phil said:**
> Hi

hmm strange problem.
Have you tried to kill the X Server and restart it? if not do so by pressing
**Ctrl + Alt + Backspace**.
This will kill X Server and normally restart it. If not and you are in the console try **startx**

Can you change to consoles after X Server freezes? (**Crtl + Alt + F1-6**)

cheers
phil

yeah i have tried it and nothing can be done when X is freezes.. Nothing happened when i press those keys... 

[QUOTE=wpshooter]
 	How long has it been doing this ? Has it always done this or is this something that worked and has since stopped working ?[/QUOTE]

Before this, it's ok when i plug my thumbdrive to my PC. Yesterday, i browsed Internet using a WIndows Machine and save some web pages on archive format(.mht) on the drive.
When i get back home, i plugin the drives into Ubuntu machines and BOOOM!.. Ubuntu crashes.. Is it because the archive files of Windows are the reason behind it? I'm using Ubuntu 6.06.

---

### Post by mohdridha on 2006-12-14
hey guys.. i have solved my problem.. i remove the gnome-volume-manager and hoila.... problem solved.. I can plug in my thumb drive with no problem.. yay :) 

Thanks

---

### Post by mohdridha on 2006-12-18
Sorry guys, i thought i have solved that one.. but still fails and the system keeps freezing.

Its weird actually, cos the time i remove that gnome-volume-manager and then plugged my thumbdrive, it looks fine (although the drive still auto-mounted). Few Days later, the same problem keeps happening, where my Ubuntu freeze whenever i plug it.

Is it because of the some chipset problem or any hardware issues regarding this matter?

---

### Post by mohdridha on 2007-01-02
Can anyone help me out? I still cant used my USB thumbdrive until now...
:confused: 

Plug In, System Freeze, Reset the Machine
](*,)

---

### Post by mohdridha on 2007-01-02
Can anyone help me out? I still cant used my USB thumbdrive until now...
:confused: 

Plug In, System Freeze, Reset the Machine
](*,)

---

### Post by mxrten on 2007-01-02
Have you tried inserting the thumbdrive without X started? (By choosing "recovery mode" in the grub boot menu for example?) Does that yield any error messages?

---

### Post by mohdridha on 2007-01-02
I have tried on Recovery mode.. I plug it and my machine is freezing..
and no error message is displayed also.. weird..

I have tried all the possible key combination on keyboard plus ctrl+alt+del but nothing happens

---

