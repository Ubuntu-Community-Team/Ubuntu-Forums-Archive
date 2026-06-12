---
title: "[SOLVED] Nothing shows up on screen! (Graphics driver?)"
date: 2008-03-15
forum: General Help
---

### Post by pkiula on 2008-03-15
Hello. My ubuntu was installed properly and working, but the windows were too slow to draw, i.e., the GUI felt a bit clunky. 

I called up Dell (Dell Latitude C840 is what I have) and they told me that I should use nVidia's drivers. 

So I went into Ubuntu's "System --> Graphics" settings, and it indeed recognized the graphics card, but showed that nVidia card was not enabled because it is a "restricted drivers" or something like that. 

Anyway, in this case, I didn't mind using nVidia's own drivers, so I enabled them. Ubuntu downloaded something, then installed "nvidia.glx". Then I was asked to restart. 

But now when I restart, the screen is totally blank! Only when I force boot (keep the power button pressed for a few seconds), it shows me some messages and then sputters and dies. 

What can I do? Can I make sure nVidia drivers work somehow, or if not, how shd I get the default graphics card to come back as before? 

Thanks!

---

### Post by amd-64 on 2008-03-16
The Nvidia driver should give you better 3D acceleration. Your GUI may be slow only if you were using compiz. If you just want to restore what you had before, boot to a console (recovery mode) in grub and edit the xorg config file. 

```
sudo nano /etc/X11/xorg.conf 
``` 
Find the following line under device, 
 
>   Driver         "nvidia" 

in my case I changed nvidia to nv, which is the non-restricted driver. 
Press Ctrl-x to exit and type
 
```

sudo init 2
```


Once you get back to the gui mode, check if nvidia is indeed installed and available. First place to look is the log file /var/log/Xorg.0.log
Check for error messages at the end of the file.

---

### Post by pkiula on 2008-03-16
Thanks amd, but there's no "grub" on my machine. It only boots in Ubuntu directly. 

1. How do I get to this grub console?

2. How do I check that I am using something called "compiz"?  (Do I need it anyway and why?)

---

### Post by pkiula on 2008-03-16
Ok, I did F12 on my machine and got the grub boot menu, then came into recovery mode. 

But when I do "sudo nano.." (correct file path, checked thrice, and it is the same as your note above) the file that opens up is a blank file! What gives?

---

### Post by zxscooby on 2008-03-16
you should be given the option to enter the grub menu as your system first starts booting.
it doesnt give you very long to decide so u gotta be quick.
i think if you had compiz you would know it :)

---

### Post by zxscooby on 2008-03-16
nm cool ! 

the file path is case sensitive , did you use a capitol X in X11?  i do that alot

---

### Post by pkiula on 2008-03-16
Ok, the X11 was in uppercase. So found the file. Thanks for the instructions, and they work! But how should I now make sure I have the proper drivers for nvidia Force 440 Go? so many thanks for any pointers or advice! (The xorg.0.log file has many geeky instructions that i dont understand)

---

### Post by zxscooby on 2008-03-16
Anything with an EE or a WW in front of it is an error or warning. 

check here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
for instructions on installing the restricted drivers.

---

### Post by pkiula on 2008-03-16
Thanks for that link. I followed the very useful suggestion there to insert: 

> 
Option "UseDisplayDevice" "DFP"


So now my machine starts up and I can see it, but the monitor is kinda split. I see 1024 resolution in about 3/4ths of the screen, then on the right and the bottom I see either vertical lines or a repeat of the window that is open on the screen.  

Any idea how to resolve this? The look of this is MUCH better than the previous graphics driver ("nv" -- the free default ubuntu thing)  but the screen splitting is distracting. 

Thanks!

---

### Post by amd-64 on 2008-03-16
Check if any lines are starting with (EE) in your xorg.0.log file

Do you have grandr installed. you can install it from synaptic. It will let you try some different desktop resolutions.

---

### Post by zxscooby on 2008-03-16
You can change the settings of your nvidia driver
by typing the code 
```
nvidia-settings
```
in your console

---

### Post by pkiula on 2008-03-16
> **amd-64 said:**
> Check if any lines are starting with (EE) in your xorg.0.log file

Do you have grandr installed. you can install it from synaptic. It will let you try some different desktop resolutions.


Thanks. In my Xorg.0.log file there is no line beginning with EE for error. Those two letters only appear in words like "screen", "needed", "sourceError", etc. Anything else I should look at?

I have now installed grandr, and it looks like a useful app! But when I change the resolution, the resolution of the screen changes within just the 3/4ths of my screen in which my current 1024x768 resolution is showing up. 

I tried taking a screenshot of this, but PRT SCRN only takes the screen of the active screen area for some reason (this browser window in which I am trying this message) so I cannot share it with you. But imagine that from the left top, only 75% of the screen is being used both horizontally and vertically. Rest is full of vertical lines...

Thanks for any pointers. I can attach my entire Xorg.0.log file if that would be helpful.

---

### Post by pkiula on 2008-03-16
> **zxscooby said:**
> You can change the settings of your nvidia driver
by typing the code 
```
nvidia-settings
```
in your console


Thanks. Tried it. Looks useful, but when I change the resolution or "panning", all of it changes only in the 75% area that is being used on the screen. I want the OS to use the entire screen as is normal on every computer in the world! What's the setting to do that?

---

### Post by pkiula on 2008-03-16
Is  there no recourse for this? Do all people who have the market-leading nVidia cards have to use a default open source Ubuntu driver and live with subpar visuals? I'm trying to do more geeky things than I have ever had to do with other OSes, and am willing to do whatever else is necessary. Is there some other file or location where I can see what the problem is?

---

### Post by zxscooby on 2008-03-16
Im using the nvidia restricted drivers, it installed flawlessly.
There is an issue with nvidia binary driver probing information from the monitor 
try this guide
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

read this too 
[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

---

### Post by pkiula on 2008-03-16
Thank you so much for the pointer. 

But it doesn't work. When I try the nvidia specific instructions (to add that option in the 'Section "Screen"'), it doesn't do anything. The 75% of the monitor is still used. 

With "nvidia-settings" nothing works either. 

Then I try the whole autodetect thing again. After painfully answering an endless list of annoying and geeky questions (um, what part was "auto" here?) it came up with some configuration that again leads to my original problem of blank screens. So I followed AMD's useful procedure to change my xorg.conf back from a backup. 

I'm back to square one. Still working with "nv" driver instead of "nvidia" restricted ones, and the screen is very clunky. 

What else can I try to get this working??!!

---

### Post by danwood76 on 2008-03-16
Just had a quick google for you and found an interesting thread.
[http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2)

They seem to be having similar problems yo you, in post 26 there is a custom EDID file.
It seems that this laptop has EDID issues.

Hope it helps.

---

### Post by pkiula on 2008-03-17
> **danwood76 said:**
> Just had a quick google for you and found an interesting thread.
[http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2)

They seem to be having similar problems yo you, in post 26 there is a custom EDID file.
It seems that this laptop has EDID issues.

Hope it helps.


Wow, thanks so much! That did it!!! The RAW EDID file is what I needed too. I hope this helps someone else in the future too. Thanks!

---

### Post by danwood76 on 2008-03-17
Excellent, please mark the thread as solved so that other people searching might find it easier.

regards,
Danny

---

