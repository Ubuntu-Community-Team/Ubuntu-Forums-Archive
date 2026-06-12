---
title: "x1900 driver help"
date: 2007-02-08
forum: General Help
---

### Post by Nader43 on 2007-02-08
ok guys im new to Ubuntu, i need some help installing the ATI drivers for my x1900. i have been using this guide
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a")

but when it gets to the part when tells me too

      **Disable Composite Extension:**

In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. To disable Composite you must edit the /etc/X11/xorg.conf file, so add these lines at the end of xorg.conf:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection
=======================================================
i dont know where the (xorg.conf:) file is or what to do to it when im there.
please help me out i am a noob when it comes to this, im still learning the OS, thanks

---

### Post by gynther on 2007-02-09
Well, the xorg.conf file is the configuration file for your X server. It's located at /etc/X11/xorg.conf.

First thing you need to do is open up a terminal window.

Then you need to edit the file. Write in your terminal "sudo vim /etc/X11/xorg.conf", press enter and supply your password to get write privileges to the file.

In the editor you scroll down using the "down arrow key" to the very end. Press the "i" key to enter insert mode. Enter the following:

Section "Extensions"
   Option "Composite" "Disable"
EndSection

and then press the "Esc" key followed by ":wq" and enter to save the file and exit the editor. You will need to restart X. To do that press and hold Ctrl + Alt + Backspace. That will end your current session and restart X and you'll be greeted with your gdm/kdm login screen again. Hope this helps.

---

### Post by Nader43 on 2007-02-09
I am very new to this, all i want is my video drivers installed and i have no clue how to do it! i have read many guides explaining it but they dont make sence to me, i need a good step by step instructions on how to do it. does anyone know of such instructions or can you help me out by explaining how i might get this done.

God i wish there was a video or someone i could talk to that could walk me throw it.

I love Ubuntu so far but im getting very frustrated that i cant do any simple task like installing must needed video drivers.

Please someone take pity on me and help me out! thanks

---

### Post by r4ik on 2007-02-09
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by Nader43 on 2007-02-09
thanks i got it working, i really love you for helping me out. thanks again

---

