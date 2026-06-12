---
title: "How to restart mouse?"
date: 2005-10-17
forum: General Help
---

### Post by ChrisTheGeek on 2005-10-17
Hi,

I have an intermittant problem with the touchpad on my aging Dell Inspiron 8100.  Every so often the touchpad just stop working (most usually I have horizontal but no vertical control).  

I'm running breezy now, but had this problem with Hoary too.

The problem is always fixed by a reboot but this isn't ideal.  Is there a way to restart or re-initialise the mouse somehow without rebooting?  I've googled extensively but haven't found a solution.

Many thanks,
Chris

---

### Post by kabus on 2005-10-17
My USB Mouse ocassionally freezes in Breezy. Restarting Hotplug fixes it :

```
sudo /etc/init.d/hotplug restart
```

Not sure if it works for a touchpad too, but it's worth a try.

---

### Post by ChrisTheGeek on 2005-10-17
Thank you very much for the reply - I hadn't thought of restarting hotplug.  Unfortunately it doesn't seem to solve the touchpad problem.

Do you know of anything else in init.d that may help? None of the options look very likely to me, but then I'm still quite new to Linux.

---

### Post by seldenthuis on 2005-10-17
I had the same problem with my mouse. I just plug it out and put it back in to get it working again.

---

### Post by ChrisTheGeek on 2005-10-19
I think that would work for USB mice but alas I can't pull out my lappy's touchpad everytime it hangs!

There must be a way to make it re-initialise a mouse device without rebooting?

---

### Post by ChrisTheGeek on 2005-10-28
Anybody?

---

### Post by Nomad64 on 2005-10-28
Although restarting the hotplug subsystem was a good idea, since the touchpad *isn't* a hotplug device, it wouldn't work.

I am going to take a stab-in-the-dark here and ask, have you tried restarting X via CTRL + ALT + BKSP? This is a hotkey that is put in as a "last resort" to get something to work without restarting. Basically (from my understanding) the command kills xserver and every process running inside of it (so be sure you aren't doing anything important when you try this!).

From my understanding of Linux, restarting X would reinitialize the xorg.conf file, which would restart the mouse.

---

### Post by dave9191 on 2005-10-28
My shot at this one would be unloading the kernel module that touchpad uses and reloading it. If i could only work out which module that is...

---

### Post by ChrisTheGeek on 2005-10-30
Thanks for the replies, I've tried restarting X with the Ctrl+Alt+Backspace but it doesn't fix the mouse, only a full reboot does.

I think I know roughly what a kernel module is but have no idea which one would control my lappy touchpad.  How would I find out?  What commands load/unload kernel modules?  Is this dangerous?  It would be very nice to avoid rebooting but I'm not sure about messing with the kernel!

Thanks.

---

### Post by dave9191 on 2005-10-30
[QUOTE=ChrisTheGeek]I think I know roughly what a kernel module is but have no idea which one would control my lappy touchpad.  How would I find out?  What commands load/unload kernel modules?  Is this dangerous?  It would be very nice to avoid rebooting but I'm not sure about messing with the kernel!

Thanks.[/QUOTE]

A kernel module is like a driver I guess. Which one controls the touchpad I don't know. It would be nice to find out tho, my touchpad goes funny after a hibernate. But since I don't hibernate much its not been my top priority. 

You can get a list of all the loaded kernel modules by doing a 

```
modprobe -l | less
```

then you can scroll up and down to read them. You can also search using "/" followed by what you want to search for. 

```
sudo modprobe <module_name> 
```

will load a module into the kernel

```
sudo modprobe -r <module_name>
``` 

will remove a module from the kernel. 

It's not really dangerous. If you unload a module that you need your system might become unstable or act funny, nothing a reboot won't fix. But if a module is currently in use, it won't let you unload it anyway. So no permenetant damage i can think of :) You only want to start being careful when compiling your own kernel which you aren't doing here. 

Dave

---

### Post by ChrisTheGeek on 2005-11-03
Hey, thanks very much for the help.

I did modprobe -l | grep mouse

To find likely contenders.  I then tried

sudo modprobe -r psmouse
sudo modprobe psmouse

And the touchpad started working again!  Lucky first guess! :D

---

### Post by dave9191 on 2005-11-04
Why didn't I think of greping for mouse... Ah well, glad you got yours working :D

I'll give it a go next time my touchpad stops working properly. You can also put those two commands in a script so rather then typing them out each time you can just run a single command like "mouse_restart". 

Dave

---

### Post by Eldan on 2005-11-11
I have had a similar problem with breezy recenty, where my USB mouse suddenly hangs for no apparent reason.  I have found that switching to a new terminal and jumping right back to the GUI also resolves the issue.  (CNTRL + ALT + F1)  then back to the GUI (CNTRL + ALT + F7)

Obviously not a permanent fix, but I have yet to find out what might be causing this to happen, and nothing breaks when I do this.  Frustrating as I am attempting to migrate from M$ entirely, /shrug what can you do.

---

