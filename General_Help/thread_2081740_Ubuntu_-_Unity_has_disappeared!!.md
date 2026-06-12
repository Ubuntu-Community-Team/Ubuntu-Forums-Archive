---
title: "Ubuntu - Unity has disappeared!!"
date: 2012-11-07
forum: General Help
---

### Post by TheAntiDoctor on 2012-11-07
Hi Everyone,

As you can probably see I'm new to this forum so thanks in advance for any replies I really appreciate the help :) 

I recently installed Ubuntu 12.10 as a dual boot on my Toshiba laptop alongside Windows 7. Everything worked perfectly, very happy with Ubuntu etc until this morning. 

Last night I downloaded a couple of updates (I can't remember the details but they might have been security updates). Next morning I booted it back up as normal and when I selected the Ubuntu option from the boot screen the login screen resolution had changed and the mouse no longer worked. 

After a little googling I came across a solution and managed to login, navigate my way into command prompt and I used the following fix: 

(Before I ran this I used 'sudo dpkg --configure -a' because apparently a package was broken up and it wouldn't let me do the following.)

sudo apt-get remove nvidia-current
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current
sudo shutdown -r now


So then I rebooted and the login screen is back to normal!!! Excellent, however upon login the desktop is completely blank - no unity, no menu bar at the top, just the files I usually have on the desktop.
 
Looking back I'm kind of surprised the first fix worked at all as it seems to refer to nvidia graphics cards and my laptop doesn't have one, it uses a standard intel one..........

Any help returning the unity and top menu bar would be greatly appreciated!!!!!!!

---

### Post by Fitoschido on 2012-11-07
So it seems that Compiz fails to start, preventing Unity from appearing. Try to open a terminal (press Ctrl+Alt+T) and run:

```
compiz --replace &
```

Compiz should appear. But anyway, why did you have installed an nvidia driver if your PC has an intel card? Use the Additional Drivers tool (Ubuntu 12.04 and earlier) or the Software Sources tool (Ubuntu 12.10) to install an appropiate driver for your card.

---

### Post by TheAntiDoctor on 2012-11-07
Thanks a lot for the tip I will try it out now! I didn't have nvidia drivers installed to my knowledge, I only saw the same symptoms as mine and tried the fix on the off-chance it worked and it did, I just can't understand why...??

---

### Post by TheAntiDoctor on 2012-11-07
Ok, so I gave it a go. I loaded up Ubuntu, same problem. Without unity I found it very hard to open a command prompt, but eventually Alt-Ctrl-F2 did the job. Logged in, used the compliz suggestion and it didn't do anything. 

I couldn't copy it exactly, but it said the following:

compliz (core) - Info: Starting plugin: core
compliz (core) - Fatal: Couldn't open display
compliz (core) - Info: Stopping plugin: core
compliz (core) - Info: Unloading plugin: core

Any more suggestions? :/

---

### Post by josephmills on 2012-11-07
what is the output of 
```

/usr/lib/nux/unity_support_test -p

```

thanks

---

### Post by TheAntiDoctor on 2012-11-07
Hi thanks for your help everyone, but I think I finally found a fix. 

I spent ages playing around with compliz and trying to install and run ccsm so I could bring unity back like that, but at the end of the day a simple update and upgrade solved the issue.

Once I had tried a number of fixes unsuccessfully, I eventually removed the nvidia drivers (I don't know what exactly whether this solved anything, but it definitely didn't hurt). The really curious thing was why the fix that I tried originally did anything at all?  

After this I used 'sudo apt-get update && apt-get upgrade' I'm not sure exactly what this downloaded and installed (it was a lot), but I did notice it saying something about a 'new unity' this seemed to fix the hole that had developed in my OS! I'm guessing this also fixed my original problem as well, whatever that was. The only thing I can think of as the cause of this was simply some sort of dodgy update that just had some weird symptoms. Thanks for everyone's help, I really appreciate it! :)

---

