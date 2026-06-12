---
title: "Lost boot up progress screen 7.1"
date: 2007-10-29
forum: General Help
---

### Post by tashmooclam on 2007-10-29
I downloaded and burned a disc of Ubuntu 7.1 a while ago.
This looked fine on live CD, I did the check first, and installed it fine on an HP Zt1000 laptop, 4+ years old. That works fine.
I also installed it on a smaller lighter "travel" laptop, Dell Latitude D600. At first it was fine. 
Just soon thereafter, when I restarted, there was NO boot screen, (black background with ubuntu and an orange progress bar) 
My only idea to "fix" this was to re-install Ubuntu 7.1, a process that took about 40 minutes.
It's the same result, no boot up screen.
Otherwise it seems to be working OK. Boot up seems a bit slow.
Any ideas would be appreciated.

---

### Post by maybeway36 on 2007-10-29
The bootup screen is purely asthetic and wont make your computer boot any faster or slower. Try pressing Alt+F1 when the screen goes black to see what's going on.

---

### Post by tashmooclam on 2007-10-29
Thanks, I'll give it a look.
I suspect I also have another OS still residing on the hard drive. My drive is 40mb. I looked at the disk usage analyzer and it shows 2.1 gigabytes being used, and 35.3 gigabytes available. I have no files except Ubuntu, Skype, and Flash on the drive.

---

### Post by Iztari on 2007-10-30
Hi, I have the same problem, I tried the alt+F1 and it loaded a lot faster than with the black screen, without errors, but i was wandering if there was a way to get back the boot up progress screen?

---

### Post by tashmooclam on 2007-10-30
I found a solution for this, and it works OK. It is a combination of things I have read here and there.
I downloaded a little program called: Start up manager. I went to terminal.
Applications>accessories>terminal

sudo startupmanager

The startup manager is now found under the menu. System>administration>startup manager.

I opened the startup manager and set the resolution to my screen resolution, i.e. 1024x768
I checked the little box "show boot splash". 

I closed it and restarted the computer. It worked fine. 
Here is the link I used, but I did NOT follow those instructions to the letter, I used my computer's real resolution and only used the startup manager. 
[http://vntutor.blogspot.com/2007/10/blank-screenon-bootup-and-shutdown.html](http://vntutor.blogspot.com/2007/10/blank-screenon-bootup-and-shutdown.html)

I now have an ubuntu laptop that starts up in 31 seconds. 
Regards

---

### Post by robc02 on 2007-11-10
I had the same problem. I now realise that it came after I changed xorg.conf to allow the correct screen resolution (it was incorrectly detected during installation).

The program startupmanager, available via Synaptic, solved the problem.

---

