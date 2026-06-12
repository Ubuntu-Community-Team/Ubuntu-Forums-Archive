---
title: "How can I stop ubuntu from updating nvidia drivers?"
date: 2023-03-13
forum: General Help
---

### Post by christosg7 on 2023-03-13
I am using Ubuntu at work..

Sadly the updates are driving me crazy, as they keep messing up with the GPU drivers (Nvidia card).. I have tried holding the packages but apparently "Software Updates" keep updating them.. (To a point where I am unable to install them again, as the additional drivers error out with the message "Ok")
What would be a viable way to stop updates - completely.. Just removing every source from APT so it's unable to recieve/list updates?

Any help would be appreciated, Thank you very much for your time!

---

### Post by coffeecat on 2023-03-13
Support, not chat. *Thread moved to **General Halp**.*

---

### Post by christosg7 on 2023-03-13
Thank you for moving the thread, I hadn't noticed that the support category was available..

---

### Post by MAFoElffen on 2023-03-13
You could pin the driver packages... but then you would also have to pin the Linux Kernel from updating also... That is where the challenge with NVidia drivers come from... nvidia-dkms successfully recompiling the nvidia drivers during a kernel update.

Having used NVidia on Linux for over a decade, I just accept that there will be intermittent NVidia driver update challenges from time to time. 

I wish I could be more helpful with that. Not updating the kernel is not a wise option. That opens up vulnerabilities, and the chance that other packages will not work (because they were updated to run with a newer kernel).

---

### Post by christosg7 on 2023-03-14
Hello there,

How would I go about pinning the driver packages? I did "hold" them after re-installing, yet "Software Updates" managed to update something, even though I had them disabled..
I was thinking of (after re-installing the OS - where the gpu driver works flawlessly), to remove all source.list entries to prevent the system from updating..

I don't mind if the kernel stays outdated, honestly, it's less headache for me - this is a desktop that solely runs terminator, vscode, teams and a bunch of browsers..

Thank you for taking the time to reply, I truly appreciate it!

---

### Post by MAFoElffen on 2023-03-14
First. turn off automatic updates... This is how I do it for 22.04.2
```

sudo nano /etc/apt/apt.conf.d/20auto-upgrades

```
I edit that file to look like this:
```

APT::Periodic::Update-Package-Lists "0";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "1";

```
I check and update my systems manually. I want to see what is going to get updated and have control over the when. By doing that, it will not update unless you do it manually.

If you wanted to go a step further, then you would mark packages to hold ony the versions you have installed. Since you are wanting not to update and hold packages back... As it relates to NVidia Drivers... Those are affected by the NVidia Drivers and by the version of the Linux Kernel...

That would take some research on your part to see what versions of packages you have installed...
```

sudo apt list nvidia-* --installed
sudo apt list linux-*$(uname -r)* --installed

```
Then when you get that list, dyou would take the names of the packages and do
```

sudo apt-mark hold package_name

```
...replacing "package_name" in that command with the package names. It's some work to do that.

Just turning off the automatic updates may be enough, unless for some reason you forget... LOL

---

### Post by mIk3_08 on 2023-03-15
> **christosg7 said:**
> 
What would be a viable way to stop updates - completely.. Just removing  every source from APT so it's unable to recieve/list updates?

 I agree with MAFoElffen. I have used this method and it is safe ever.  Just specify the package name that is to be on hold. Regards and cheers.
> **MAFoElffen said:**
> 
```

sudo apt-mark hold package_name

```


---

### Post by christosg7 on 2023-03-18
Hello everyone,

I was holding the packages in the past but I guess something slipped by(?).. I now managed to both hold the packages and "removed" all sources from apt (by commenting them out), thus my drivers & kernel are at a working condition! Obviously it is not recommended to run an outdated system, but that managed to solve my issue..

Thank you everyone for your input, you may mark this thread as resolved / closed..

Have a great day / weekend <3

---

### Post by MAFoElffen on 2023-03-18
The Original Poster (OP) that opened the thread (christosg7, you) has the go to the Thread Tools link in the upper right of the first of of the thread, the mark it as Solved. That is how that works.

---

