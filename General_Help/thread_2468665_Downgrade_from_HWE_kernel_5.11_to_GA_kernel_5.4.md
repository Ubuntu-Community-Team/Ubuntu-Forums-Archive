---
title: "Downgrade from HWE kernel 5.11 to GA kernel 5.4"
date: 2021-11-07
forum: General Help
---

### Post by maglin2 on 2021-11-07
Hello
last year I put vanilla ubuntu 20.04 onto a neighbours windows vista laptop.
All went well till about January this year, when it upgraded to HWE kernel 5.8, which wouldn't boot on his old machine.
Following a thread in this forum (which I can't now find) I got him back on to 5.4 GA kernel series. Installing linux-generic and removing linux-generic-hwe-20.04 was part of the solution I think, but there was more that I've forgotten.

All was well until a few weeks ago, when HWE kernel 5.11 was installed during an update, and won't boot.
Kernel 5.4 is still there, so I can get him booted using advanced options, but at next boot it tries to use 5.11 again and hangs. I think I need to completely remove HWE.
I tried 
```
sudo apt remove linux-{image,headers}-generic-hwe-20.04
``` picked up from an askubuntu post.
This didn't fix matters. I then tried to remove the 5.11 kernels using synaptic, but it wants to install an unsigned version of the same kernel at the same time as removing, which doesn't seem to me likely to help.
Any guidance much appreciated. Thanks

---

### Post by Impavidus on 2021-11-07
You were on the right track. Install linux-generic, remove linux-generic-hwe-20.04, then remove all packages pulled in by linux-generic-hwe-20.04: linux-image-generic-hwe-20.04, linux-headers-generic-20.04, linux-image-generic-5.11.*, linux-modules-extra-5.11.*, linux-headers-5.11.*. In synaptic it should be fairly straightforward to track them down. First remove the metapackages, then their dependencies. But with a bit of luck they will be autoremovable.

If linux-generic-hwe-20.04-edge was installed, remove that, but that would normally not be the case. If there's not the generic kernel but a different one (Ubuntu Studio comes with the low-latency kernel), deal with that, but that shouldn't be the case on a normal Ubuntu system.

BTW, if you already got him away from the 5.8 kernel and on the 5.4 kernel, it shouldn't upgrade to 5.11. Maybe linux-generic-hwe-20.04 was accidentally reinstalled? From the metapackage, kernel 5.11 would have been installed in July.

---

### Post by maglin2 on 2021-11-07
Thanks - I'll give it a go when I'm next in his house and report back. I think I've already removed most of what you listed, but I may well have missed something. My guess is I also missed something last time, and that is why HWE came back.

Would synaptic wanting to install the unsigned 5.11 kernel packages when I tried to remove signed 5.11 kernel packages be because I'd missed something that has the package as a dependency?

There were a few 5.11 kernels on his machine, so i guess it must have been OK when initially installed, then the latest version caused boot issues about 3 weeks to a month ago.

---

### Post by ajgreeny on 2021-11-07
To stop the 5.11 kernel series being upgraded every time you update the system you must remove the linux-generic-hwe-20.04 as mentioned by  impavidus and replace it with linux-generic.
That will then ensure that the 5.4 kernel series is upgraded every time a new version is released.

---

### Post by mastablasta on 2021-11-10
generic is updated as long as it is installed. you can have both kernel at same time. it is how i have it now along with windows XP (not that i can boot it), because i haven't upgraded to 20.04 yet and i need 5.4 for the CPU.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

GPU addiitonal drivers (e.g. nvidia proprietary drivers) or any patched drivers connect to kernel. so you might have to remove those.
install generic if you haven't already:

```
[COLOR=#1C1C1C][FONT=&quot]sudo apt install linux-generic[/FONT][/COLOR]
```

remove:
```
 [COLOR=#1C1C1C][FONT=&quot]linux-generic-hwe-20.04
```

then:
```
sudo apt autoremove[/FONT][/COLOR]
```

but you can also keep HWE and set generic as default.

---

### Post by maglin2 on 2021-11-11
Setting generic as default would probably be best. 
Can you advise me how to do that?
 It still boots to 5.11 by default even after all the linux-generic-hwe stuff is gone.

---

### Post by Impavidus on 2021-11-12
It can't boot the 5.11 kernel if all 5.11 stuff is gone, so what's left?```
dpkg --list "linux-*" | grep 5.11
```

---

### Post by maglin2 on 2021-11-12
The 5.11 stuff hasn't gone. The linux-generic-hwe stuff has gone.
Attempt to remove one of the individual 5.11 kernel packages produced a synaptic response to want to install the unsigned 5.11 kernel instead.
(When I'm at his laptop pondering and scratching my head I can see him  looking very fretful. I know he isn't someone who has backups, and he's  clearly very worried I break it completely.To be honest I'm a bit concerned  about that myself). 
There seems to be a sequencing issue around removing the 5.11 packages in the right order.
I have set up a virtual machine on my little netbook to try to replicate the issue to figure that out. It gives me eye-strain if I play with it for too long though!
Responding to your reasonable requests for info isn't easy, since I'm not at his machine often. That's why I thought it might be easier if I could just change the default kernel to 5.4. 5.11 being there isn't really a problem if it's not the default.
Thanks
Dave

---

### Post by maglin2 on 2021-11-12
I think my VM trial has now found a sequence for removing the 5.11 packages that works without wanting to install an unsigned 5.11 kernel image.
(I'm getting close to breaking my golden rule of never complaining about a free OS here, but I wish Ubuntu 20.04 initial release hadn't shipped w[COLOR=#1C1C1C]ith [/COLOR][COLOR=#1C1C1C][FONT=&amp]linux-generic-hwe-20.04 instead of linux-generic)[/FONT][/COLOR]

---

### Post by ajgreeny on 2021-11-12
In future, assuming things do not change from the current regarding the hwe kernel updating system, make sure you install nothing later than the .1 version when downloading the .iso file you use for the installation, eg 20.04.1 did not include the hwe kernel series but the 20.04.2 version did.

If you have really up to date hardware it can be worth using the hwe system from 20.04.2 but if your hardware is older it is unlikely to offer any advantages.

For your information, I have never so far needed, nor used, a Xubuntu version that includes the hwe series of kernels.

---

### Post by maglin2 on 2021-11-12
I did install from Ubuntu 20.04 (.0). I still have the LiveUSB.
Unfortunately Ubutnu 20.04 was the first LTS to start with HWE as the meta (the flavours like Xubuntu didn't).
[https://ubuntuforums.org/showthread.php?t=2456332&p=14012930#post14012930](https://ubuntuforums.org/showthread.php?t=2456332&p=14012930#post14012930)
My problem was that I didn't know that.

---

### Post by ajgreeny on 2021-11-13
I haven't checked the details of the current situation, but if you read to the end of the thread you gave in the link you will see that the addition of the hwe stack seemed to be an accidental occurrence when the .iso manifests were created.
Hopefully this means that things will go back to normal with the next LTS version in April 2022.

---

### Post by maglin2 on 2021-11-13
Well I'll be certain to check for that before I install, and to install offline and replace linux-generic-hwe with linux-generic (if necessary) before updating!

---

