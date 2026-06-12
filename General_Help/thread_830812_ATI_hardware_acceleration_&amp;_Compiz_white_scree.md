---
title: "ATI hardware acceleration &amp; Compiz white screen"
date: 2008-06-16
forum: General Help
---

### Post by Dbugger on 2008-06-16
Hello. My problem comes from this thread where they suggested me to come here:
[http://ubuntuforums.org/showthread.php?p=5196474#post5196474](http://ubuntuforums.org/showthread.php?p=5196474#post5196474)

When i try to activate the hardware acceleration and restart I get a black screen of death, so I have to enter in recovery mode to go back to the normal settings.

When I try to activate compiz I try to get a white screen of death (which goes away in 30 seconds)

Can you help me to activate hardware acceleration or at least compiz?

Thank you!

---

### Post by crazyness003 on 2008-06-17
Im no expert, but since im having similar problems (the white screen part) im gonna try to help you.
Since you're using an ATI the only thing i can recommend is EnvyNG, you can find it in Synaptic. 
Install the envyng-core and of the others (I used envyng-gtk, since i run gnome). 
After installing, you'll find the program in menu-> System Tools.
Pick ATI and envy will remove whatever's necessary, install and configure what you need.
Its not guaranteed to work (my case being proof) but you may be able to avoid thems black screens of death.

As for the white screen, i too get that. Im using the latest EnvyNG nvidia drivers for my 6150 go card and when i try to get compiz working im confronted with white screen (only mouse pointer is visible and movable).

Thanks

---

### Post by crazyness003 on 2008-06-17
Well, nevermind my reply post. Solved my problem with 
```

sudo apt-get remove xserver-xgl

```
Evidently nvidia chips dont need xgl
....
So im assuming ATI chips do need this xgl.

Can anyone else give their input?

---

### Post by Kilz on 2008-06-17
> **crazyness003 said:**
> Well, nevermind my reply post. Solved my problem with 
```

sudo apt-get remove xserver-xgl

```
Evidently nvidia chips dont need xgl
....
So im assuming ATI chips do need this xgl.

Can anyone else give their input?

I dont use xgl, i use aiglx with ati.

---

