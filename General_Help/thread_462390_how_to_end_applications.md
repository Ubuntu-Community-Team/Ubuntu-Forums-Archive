---
title: "how to end applications"
date: 2007-06-02
forum: General Help
---

### Post by serpentfinder on 2007-06-02
Hi,
I'm new to ubuntu. I installed it a few days ago. I needed to install a driver so that my internet could work in it though. Anyway, I tried to open a couple things, one a driver package and one a modem scanner. I never got the driver installed. Today I tried to run the install package and it says that only one software manager can run at a time. I don't understand how anything could still be running after the pc has been turned off several times, but that is what it says.
Can anyone tell me how to shut down the other instance?:popcorn:

---

### Post by miceagol on 2007-06-02
Use
```
top -u <username>
```
if you started the program without sudo (super user) to see all the processes running. If you use top without arguments it will show you absolutely all programs running. Note the job id of the program you wish to stop and write
```
kill <job id>
```
You may want to install a program called htop to be able to scroll downwards when there are lots of programs running.

---

### Post by miceagol on 2007-06-02
> **serpentfinder said:**
> 
Today I tried to run the install package and it says that only one software manager can run at a time. I don't understand how anything could still be running after the pc has been turned off several times, but that is what it says.


Another thing to remember. You get this error message when you have several instances of synaptic running. E.g. you can't double click a .deb package at the same time as having the update manager running. Another example: You can't run apt get in the terminal when Synaptic is running.

---

