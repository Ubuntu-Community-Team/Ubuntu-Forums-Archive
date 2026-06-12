---
title: "application windows getting hidden"
date: 2008-06-17
forum: General Help
---

### Post by sandipg on 2008-06-17
Hi all,

I run Ubuntu Hardy on an AMD 3200+ 64-bit machine with Nvidia graphics card. I have all the latest Nvidia-linux drivers installed. My monitor is an old LG 15'' CRT model. I have a screen resolution of 800 by 600 with a refresh rate of 75 Hz. 

My problem is that some application windows get partly hidden behind the top and bottom panels. Resizing them doesnt work because the windows **overflow out of the screen area**. So some buttons/options are not visible.

Here is the screenshot: The problem is highlighted in red.

[IMG]http://www.flickr.com/photos/13104583@N00/2587023523/[/IMG]

Any solutions to the problem?

---

### Post by sandipg on 2008-06-17
oops..forgot to attach the screenshot. Here it is....

---

### Post by overdrank on 2008-06-17
> **sandipg said:**
> Hi all,

I run Ubuntu Hardy on an AMD 3200+ 64-bit machine with Nvidia graphics card. I have all the latest Nvidia-linux drivers installed. My monitor is an old LG 15'' CRT model. I have a screen resolution of 800 by 600 with a refresh rate of 75 Hz. 

My problem is that some application windows get partly hidden behind the top and bottom panels. Resizing them doesnt work because the windows **overflow out of the screen area**. So some buttons/options are not visible.

Here is the screenshot: The problem is highlighted in red.

[IMG]http://www.flickr.com/photos/13104583@N00/2587023523/[/IMG]

Any solutions to the problem?

HI and it appears you need to adjust your resolution to view more of you desktop. Have you tried to adjust your resolution and you may try using the alt , F2 keys and enter the command ```
gksu displayconfig-gtk
```and adjust your screen resolution.

---

### Post by sandipg on 2008-06-17
Hi,

I did try gksu displayconfig-gtk before, but the current resolution gives the best results (I even matched the exact model of the monitor).

1024*768 gives way too much flicker at the available refresh rates (and its a 15'' screen). 

I just realized that I cannot make any changes via the GUI, because most confirm buttons are at the bottom of the application window!

---

### Post by overdrank on 2008-06-17
Hi and using the alt, key and single click and hold with the mouse should enable you to move the window.

---

### Post by sandipg on 2008-06-17
Is there a permanent/better solution? Can I set window sizes so that they fit perfectly? Or alternately, set the resolution to 1024*768 and get rid of the flicker?

---

### Post by overdrank on 2008-06-17
> **sandipg said:**
> Is there a permanent/better solution? Can I set window sizes so that they fit perfectly? Or alternately, set the resolution to 1024*768 and get rid of the flicker?

Hi and yes, what is the model of nvidia card? Also have you used the nvidia settings to adjust the resolution. ```
gksu nvidia-settings
``` using the alt, F2 keys

---

