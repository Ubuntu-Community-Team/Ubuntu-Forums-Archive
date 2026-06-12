---
title: "login troubles...please help"
date: 2008-02-12
forum: General Help
---

### Post by hamalama on 2008-02-12
just installed ubuntu on one of my comps, loads stuff, prompts me for my user name and pass, and i type them in correctly, and it says a lot of stuff then spams 
-bash: /dev/null: Permission Denied

any ideas?

---

### Post by pytheas22 on 2008-02-12
do you mean that you're trying to log in on the command line?  Are you able to log in to Gnome graphically?  What is the other "lot of stuff" that you get before the permission denied line?

also take a look at [http://ubuntuforums.org/showthread.php?t=683836&page=1](http://ubuntuforums.org/showthread.php?t=683836&page=1) or search google for "/dev/null: Permission Denied" ; there are a lot of results.  But I am not sure if your situation is the same; it depends on whether you're able to log in to anything at all, or whether it's just when opening up a terminal in graphical mode that you get this error.

---

### Post by hamalama on 2008-02-13
ok heres what it says when i start it up:
it does the load bar then it says:
Starting up...
[    0.684000] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[   0.768000] PCI: failed to allocate mem resource #3:2000000@fe000000 for 0000:05:00.0
loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/8733db72-1178-498c-b752-93aa4b7ee190) =sda(8,5)
kinit: trying to resume from dev/disk/by-uuid/8733db72-1178-498c-b752-93aa4b7ee190
kinit: No resume image, doing normal boot...

Ubuntu 7.10 negrodamus tty1
negrodamus login: 
(i log in)
it tells me my last login 
it says sum **** about ubuntu is free software, blah blah blah, then spams the -bash: dev/null: Permission denied

---

### Post by hamalama on 2008-02-13
is there any way to uninstall trhough text mode or sumthing cus i was thinking of just starting over

---

### Post by pytheas22 on 2008-02-13
If you want to reinstall, you just boot to the live CD and reinstall; it will overwrite your existing installation.  It might also not be a bad idea to check the live CD for defects; I believe there is an option for this at the menu that you first get when you boot to the CD.

Otherwise, your boot process looks normal; nothing to indicate a problem that I can see.  It's weird that X doesn't start, but I'd imagine that's related to the /dev/null permissions error.  I think that all you would need to do is change the permissions on /dev/null, but since you can't log in, I don't know how you could do that.  Reinstalling might be the best thing to try right now.

---

### Post by hamalama on 2008-02-13
yeah im pretty sure theres sumthing wrong with my live cd cus the only was i could get it working was by using the wubi-cboot (windows based installer) then booting off dsk i couldnt just go right off disk

---

### Post by hamalama on 2008-02-13
solved, but then another login problem appered so im just gonna keep the thread. i reinstalled ubuntu and it worked!!!! so i installed all the driver updates, and activated the nvidia driver that ubuntu called a "restricted driver" restarted, and now, after the ubuntu logo/ bar load screen, my screen just goes into sleep mode and doesnt get out unless i restart the comp

---

### Post by pytheas22 on 2008-02-14
That's really strange.  Are you sure it's going into sleep mode or is the graphical interface maybe just failing to load--if you press control-alt-f2, do you get a text-based a login prompt?  What model is your nvidia card?  Do you by any chance have more than one graphics card in your computer?

Since it would appear that the proprietary nvidia driver is the root of the problem, you should be able to solve it by editing your xorg.conf file and changing back to the open-source driver.  To that you have a few options:

1. you could try pressing control-alt-f2 while Ubuntu is loading, or keep pressing control-alt-backspace so that the X server will be killed.  If this works, you will get to a command line asking you to log in.  Enter your username and password, and then type

```
sudo nano /etc/X11/xorg.conf
```

and look for a line under the "Device" section of that file that looks like "driver nvidia"  Change it to say "driver nv"  Save the file and reboot and hopefully the problem will be solved.

2. if you can access your Ubuntu partition from Windows, which can be done if you install the appropriate utilities to allow Windows to read your ext3 (or reiserfs or whatever you chose) filesystem, navigate to the /etc/X11/xorg.conf file there and do the same thing as above, replacing "nvidia" with "nv"

3. you could also access xorg.conf by booting to the live CD and mounting your Ubuntu partition, and then using a text editor or a terminal to edit the file.  I won't go through how to mount a partition now, but if you need to go this route and don't know how to mount stuff, I can give you directions or you can find them with a search.  The above two options would probably be easier than this one, however.

If editing xorg.conf doesn't at least get you back to where you were originally, it could be that one of the hundreds of updates you installed caused the problem.  In that case, the best thing to do might be to reinstall Ubuntu, then install all the updates WITHOUT installing the restricted nvidia driver, and see if you have the same problem.  That would help isolate the cause.

I am also thinking that trying to install all the updates and the restricted drivers at the same time without a reboot in between might cause problems because you would be doing a kernel update but the restricted drivers that get installed might be for your current kernel, not the updated one, which has the potential to cause all sorts of problems if some of your important modules are not built against the running kernel.  The installer should be smart enough not to make such a mistake, but it's plausible...

---

### Post by hamalama on 2008-02-14
ugh.... reinstalled, installed nvidia driver through envy, rebooted, got same problem.
i did the control alt f2 whatever, logged in, and before i had the chance to finish typing ur command, my monitor went to sleep again....
what utilities are needed to edit ubuntu through windows?

---

### Post by hamalama on 2008-02-14
went into recovery mode and did ur driver nv change, now it appears to be working.
is my nvidia driver stil there? will i have to find a new driver if i want my card to work? i have an 8600 gtx if that helps

---

### Post by pytheas22 on 2008-02-14
By replacing "nvidia" with "nv" in xorg.conf, you didn't uninstall anything; you simply told your system to use the open-source driver instead of the proprietary one, which is what gets installed by the restricted drivers thing.  So yes, the closed-source driver is still installed on your system; it's just not activated.  Obviously activating it causes serious problems for your computer, and I'm not sure why; I did some quick searches and no one else seems to be having trouble with your kind of card in Ubuntu 7.10 (you are using Ubuntu 7.10, right?).

One solution might be to install the closed-source driver directly from nvidia's website.  If the version that's in the Ubuntu repositories is not completely up-to-date, the one direct from nvidia might have bug fixes or something.  It's available at [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) ; make sure you choose the right one for your architecture (32 or 64 bit).

First, make sure you have a compiler and kernel headers installed:
```

sudo apt-get install build-essential
```

It's been a while since I last installed the nvidia driver manually, but I think that what you have to do next is press control-alt-f2 to get to a terminal, then login, and kill X with
```

sudo kill $(ps -e | grep X)
```

which is a dirty command but it should work.  Next, run the nvidia installer with
```

sudo sh ~/Desktop/NVIDIA-Linux-x86-169.07-pkg1.run
```

note that the name of the installer file could vary depending on what it's called the day you download it, and that its location might be different--in the command above I assumed that it was saved to your desktop.

Then the installer should run and do what it needs, and after a reboot, your machine will hopefully work properly, with hardware acceleration.  Report back on the outcome.

---

### Post by hamalama on 2008-02-14
i have 7.10 and the iso i got was the desktop-i386 so what driver does that mean i should get?

i dunno if thats gonna work cus i was searching forums and found this: 
[http://ubuntuforums.org/showthread.php?t=615215&highlight=8600gt](http://ubuntuforums.org/showthread.php?t=615215&highlight=8600gt)   10 pages of peoplewhining about the same video card as me(8600gt) and the exact same problem with no solution

---

### Post by pytheas22 on 2008-02-14
> i have 7.10 and the iso i got was the desktop-i386 so what driver does that mean i should get?

You want the 32-bit build then.

Unfortunately I agree with you, it looks like 8600gt does not work well using the driver from the Ubuntu package manager.  However this thread looks promising [http://ubuntuforums.org/showthread.php?p=2791480](http://ubuntuforums.org/showthread.php?p=2791480)  Try following the directions there and see if it helps you.  Apparently it will work if you install the driver from nvidia.

---

