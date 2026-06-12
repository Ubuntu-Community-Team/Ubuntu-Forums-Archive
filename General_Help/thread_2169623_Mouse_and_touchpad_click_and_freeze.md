---
title: "Mouse and touchpad click and freeze"
date: 2013-08-22
forum: General Help
---

### Post by Kegeg on 2013-08-22
I have a problem with my mouse and touchpad, they click and stays this way without never letting go of the item. I thought it might be an ubuntu problem as both my usb mouse and laptop touch pad are doing it. I tried an early update to 13.10 to see if it would have fix it but no luck... It is keeping me from using my computer for now because as soon as i open the desktop, it click it and drag rectangle. 

If anyone has an idea to point me in a direction

Thanks

---

### Post by leoh on 2013-09-01
Hi everyone.
A firend of mine brought me his Acer 5720z notebook.
He had Ubuntu 11.04 (or 11.10? can't remember).
He could only click by tapping on the touch pad, but not on his USB mouse (I tried the mouse on another windows computer, works OK).
He couldn't click either with the mechanical button on the touch pad. The only way to click was by tapping on the touchpad.
The left click and moving the mouse worked fine on either mouse.
The touchpad has 3 buttons: left click, right click, and an up/down/left/right scroll. The scroll doesn't do anything (i don't need it anyway).
I updated to 12.04 (or 12.10?) and got the same thing.

So I made a fresh install of 13.04.
Now it's not possible to click in any of the 3 ways (tapping, clicking on touchpad, clicking on usb mouse).
Sometimes it works, sometimes it doesn't work. But most of the time, it doesn't work. I can't figure out what makes it start working.

I installed linux mint 15 "olivia", and the same thing happens.
I noticed that when it boots, it's as if the click was stuck clicked (moving the mouse selects an area on desktop).

In both Ubuntu and Mint I installed all the updates, and didn't change any setting.

I got the same behaviour on the live versions of Ubuntu 13.04 and Mint 15.

What should I do?

---

### Post by leoh on 2013-09-01
Right now I am trying to install Debian.
On the graphical install, the touchpad did not respond at all. The USB mouse worked fine. Then the touchpad started working (still on the installer), and the USB left click stopped working. Like if it was stuck clicked.

I know mint and ubuntu are debian based, but I have a possible theory.
What if the touchpad left click is broken and it's stuck clicked? I haven't tried it with anything else than linux. How could I try that?
In case that's the problem, how could I ignore that input from ubuntu?

---

### Post by leoh on 2013-09-03
I solved the problem. It turned out that the cause was the touchpad left click button, that got stuck in clicked position, so any other click input was ignored since the mouse was already clicked. I am not 100% certain if that was indeed the cause, but it's the only explaination I found. I didn't try to troubleshoot the touchpad via software (i.e. driver, etc), since it seemed unlikely and complicated.
 
I dissassembled the notebook and disconnected the touchpad, and everything went fine with the external USB mouse.

---

### Post by Kegeg on 2013-09-04
[I]It seem to be the exact same problem then I'm having with my Gateway NV57H13h. Do anyone knows of a way to find out if it's really and hardware problem? And I also experienced the same problem with my external USB mouse.
 
Thanks [/I]

---

