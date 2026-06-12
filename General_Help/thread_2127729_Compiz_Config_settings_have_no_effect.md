---
title: "Compiz Config settings have no effect"
date: 2013-03-20
forum: General Help
---

### Post by Parkerman1700 on 2013-03-20
Hello

I have instaled compiz config, and have been searching constantly throughout these forums to try to find a way to fix it,  but I just can't. I tried to install compiz-check, but I recieved the error that I have two graphics chips, and that the script can't handle it. 

I have ubuntu 12.04.01 LTS installed, AMD Radeon HD 6600M Series  graphics card, I currently have the ATI/AMD propietary FGLRX graphics  driver (post release updates) activated.

I ran several commands that all pointed towards a repeating error of: Fatal: *Root visual is not a GL visual.*

And after that my screen became super buggy and everything got screwed up. I would have to log out and back in. 

Any commands to run or info I can provide to get this resolved? 

Please and thank you.

---

### Post by GameX2 on 2013-03-20
Sometimes, nothing happen, in my case, if I try to use CompizConfig-Settings-Manager on a too old machine (Dell Optiplex GX260, a P4 with only 1.5 GB of RAM.  Ubuntu with Unity isn't really smooth, but Xubuntu is).

---

### Post by Parkerman1700 on 2013-03-20
My machine was bought less than a year ago, it's pretty dang new.

---

### Post by JOHNNYG713 on 2013-03-21
How bout some spec's please ! cant help ya if we dont know what we are working with ! :confused:

---

### Post by Parkerman1700 on 2013-03-21
I have ubuntu 12.04.01 LTS installed, AMD Radeon HD 6600M Series graphics card, I currently have the ATI/AMD propietary FGLRX graphics driver (post release updates) activated. Any more coherent specs I should give?

---

### Post by deadflowr on 2013-03-21
Which fglrx version?

Did you install through Ubuntu, or use the a version from the AMD site?

From what I know that card should work fine on 12.04 ( but then again, what do I know!)

Ubuntu 12.04 had a secondary fallback desktop known as Unity-2d. In essence, when your system boots up a small script runs to determined if your hardware is able to run the full 3d environment of Unity. However, the hardware usually reads the drivers in use.
You can run this:
```
/usr/lib/nux/unity_support_test -p
```
in a terminal to see if your system is able to run full unity.
Full unity uses the compiz window manager.
Unity-2d does not. If using unity-2d, making changes to compiz is futile.
Looky here to try and figure out a driver solution:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Sometimes the drivers install poorly, or borked, and the best thing to do is purge/or uninstall and start over.
Personally, I would uninstall and run the system with the open-source radeon drivers first, look over the functions of the desktop, and then try reinstalling drivers. 
The radeon drivers are pretty well built, and sometime offer better stability than the fglrx drivers.

---

### Post by Parkerman1700 on 2013-03-21
flgrx version: fglrx 9.0.2 [Sep 20 2012]

I installed the driver through the console, following instructions I found elsewhere on the forums.

I ran the code and got this:

```
$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22

```

I also reinstalled both the driver and compiz multiple times. 

Should I change from the flgrx driver to something else?

I will also be looking at the link you provided.

---

### Post by Parkerman1700 on 2013-03-21
Okay! I managed to solve the problem. Thanks deadflowr, your information gave me just enough understanding to figure out that it was a problem with the fglrx driver. Using the error I got with both fglrxinfo and the code you gave me, I figured out the code that I needed to enter: 

```


sudo aticonfig --initial

```

Then restarted my computer. Now it works fine. Thank you for your help!

---

### Post by deadflowr on 2013-03-21
Good to see it work (so far)

Now you can have fun enabling all the goodies within compiz.

I think you can install some extra compiz-plugins, though I don't remember their names.
I usually install extras through synaptic. I believe the extra are compiz-plugins-extras, but not sure.

Something to remember though, when enabling changes to compiz through ccsm, sometimes the system needs to reset itself, and the screen might get out-of-wack for a while. Best practice is to wait it out (sometimes it might take a few minutes), Don't Panic and try to shutdown or restart the system as this will most likely leave the system in a twilight zone.

---

### Post by Parkerman1700 on 2013-03-21
Sweet! I'll check out the extras, and obviously if I have any problems I can just ask again. Thanks again!

---

