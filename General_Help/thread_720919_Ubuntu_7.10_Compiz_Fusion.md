---
title: "Ubuntu 7.10 Compiz Fusion"
date: 2008-03-10
forum: General Help
---

### Post by but2002 on 2008-03-10
How would I get the best version of Compiz Fusion out there?

I've searched and searched, and even when I install, it conflicts somehow, and only the one that comes with Ubuntu works, however, this version is glitchy, as in it does not run smooth

It runs like the framerate is 10 or something along those lines, however on my Ubuntu Ultimate install, I managed to get it EXTREMELY smooth
Any ideas?

---

### Post by PurposeOfReason on 2008-03-10
What is your hardware and did you enable the restricted drivers if needed? Also, did you edit your xorg.conf file to make best use of the hardware?

---

### Post by but2002 on 2008-03-10
I'm on an Nvidia Geforce 6200, yes I enabled the restricted drivers, and I have NO clue what to do with the xorg.conf.
 Ideas? :p

---

### Post by PurposeOfReason on 2008-03-10
> **but2002 said:**
> I'm on an Nvidia Geforce 6200, yes I enabled the restricted drivers, and I have NO clue what to do with the xorg.conf.
 Ideas? :p
With nvidia, it's pretty easy. Run these two commands. The first backs it up because that's good practice, the second enables the options you need. After you run them, restart X (ctrl+alt+backspace)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nvidia-xconfig --composite --render-accel --add-argb-glx-visuals

```

---

### Post by but2002 on 2008-03-10
I did what you said, however it still runs a little glitchy

I can tell no difference, anny other ideas?

---

### Post by PurposeOfReason on 2008-03-10
> **but2002 said:**
> I did what you said, however it still runs a little glitchy

I can tell no difference, anny other ideas?
Can you explain what exactly is glitchy and are you still using the compiz that came with 7.10?

---

### Post by but2002 on 2008-03-10
Yes I am using the one that came with 7.10, because any other version I have found either doesn't run, or runs in the same fasion

It's hard to explain, easiest is that the framerate is low, kinda like watching something at 15 frames a second ( Not that bad, but it's definately noticable )

---

### Post by PurposeOfReason on 2008-03-10
It just might be your settings. I'm not there to know your exact settings or your exact hardware and I can't sent you my config because I'm using a git repo. However, go into general options and mess with the texture filter and refresh rate In the output box, edit it so that it is XxY+0+0 where X and Y are your screen width and height (1280x800+0+0 for me. I also don't know if it helps but it is more correct).

Disable plugins one by one until it speeds up. Right after it does speed up (if it does) see if it was just that plugin by enabling a few others.

---

### Post by but2002 on 2008-03-10
Tried to no avail

I KNOW it's possible to have it smooth, however I did this to a Ubuntu Ultimate install, however I switched to official Ubuntu for the fact that Ubuntu Ultimate took over 10GB for itself and only itself

---

### Post by but2002 on 2008-03-10
I'm just going to *bump* a 30 minute old topic, because I don't have much time for the day :P

---

### Post by Therion on 2008-03-10
> **but2002 said:**
> ... I switched to official Ubuntu for the fact that Ubuntu Ultimate took over 10GB for itself and only itself
Remove unnecessary applications. Ultimate is an awesome distro and runs like silk on my machine, which is more than I can say for any other.  With hardly any effort you could remove a lot of applications you're probably not using.  That's one of the first things I do after a fresh install of Ultimate: remove the the duplicate applications and apps I'll never use (like Blender).  

Trimming Ultimate down is easy.  Getting a distro that doesn't like your hardware to run smoothly can be hard.

---

### Post by forrestcupp on 2008-03-10
Well, you could try disabling your proprietary nvidia drivers in the Restricted Drivers Manager, then try installing the very latest nvidia drivers with [Envy](http://albertomilone.com/nvidia_scripts1.html).  I really doubt if it is a problem with the version of Compiz you are using.

---

### Post by but2002 on 2008-03-10
> **PurposeOfReason said:**
> What is your hardware and did you enable the restricted drivers if needed? Also, did you edit your xorg.conf file to make best use of the hardware?

> **forrestcupp said:**
> Well, you could try disabling your proprietary nvidia drivers in the Restricted Drivers Manager, then try installing the very latest nvidia drivers with [Envy](http://albertomilone.com/nvidia_scripts1.html).  I really doubt if it is a problem with the version of Compiz you are using.


I don't know why i never thought of Envy, trying now, will report later

---

### Post by but2002 on 2008-03-10
> **but2002 said:**
> I don't know why i never thought of Envy, trying now, will report later

Installed driver through envy,  still a little glitchy

Any ideas on a different compiz fusion install that would suit me well?

---

### Post by por100pre1 on 2008-03-10
This may sound dumb but... Did you try the general settings of compiz?

```
ccsm
```

In **General Options** look for the **Display Settings** tab.

---

### Post by but2002 on 2008-03-11
> **por100pre1 said:**
> This may sound dumb but... Did you try the general settings of compiz?

```
ccsm
```

In **General Options** look for the **Display Settings** tab.

Yeah, of course I did, however, nothing there speeds it up

I know for a fact that in Ultimate, all installs did the same thing, then I came across ONE that installed, and it ran smooth, and that one install always ran smooth, no matter which ultimate in installed it on, however, I can't find that one now. >,<

---

### Post by but2002 on 2008-03-11
> **but2002 said:**
> Yeah, of course I did, however, nothing there speeds it up

I know for a fact that in Ultimate, all installs did the same thing, then I came across ONE that installed, and it ran smooth, and that one install always ran smooth, no matter which ultimate in installed it on, however, I can't find that one now. >,<

Naturally, right after I posted this I found a semi-fix that fixed most of it, 'cept for the desktop cube

---

### Post by gottifour on 2008-03-20
> **Therion said:**
> Remove unnecessary applications. Ultimate is an awesome distro and runs like silk on my machine, which is more than I can say for any other.  With hardly any effort you could remove a lot of applications you're probably not using.  That's one of the first things I do after a fresh install of Ultimate: remove the the duplicate applications and apps I'll never use (like Blender).  

Trimming Ultimate down is easy.  Getting a distro that doesn't like your hardware to run smoothly can be hard.

I have installed ubuntu ultimate coming from a stock ubuntu set up..and I love it..its awesome, but for some reason my compiz fusion is not working like it did before with all the same hardware. I used to go to system-preferences-advanced appearance settings (i think thats what it was called) and it would get me into the settings for compiz.or I could right click on the desktop and go to change desktop backround-appererance preferences-visual effects and it would give me 4 choices none-normal-extra or i think it was advanced or custom, but now its not there..

anyone know why its not there? 

thanks for any help...d

---

### Post by gottifour on 2008-03-23
Ok now I have the custom option under appearance but when I select it my screen goes white and I have to resart. Does that make sense to anyone? Do I need to install anything else?

Thanks for any help...d

---

