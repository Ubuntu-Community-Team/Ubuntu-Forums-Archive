---
title: "help! ctrl-alt-f1 doesn't work"
date: 2008-06-18
forum: General Help
---

### Post by lightstream on 2008-06-18
I need to get to a TTY login to reinstall nVidia drivers but ctrl-alt-f1 (and ctrl-alt-f2, f3 etc) have stopped working.

Does anyone know what could be causing this??

thanks for any help ..

Also, if I boot into a root console from the Grub menu and type 'telinit 3' to get to runlevel 3, X will start up, which is obviously not what I wanted... I thought runlevel 3 was text-only?

---

### Post by VMC on 2008-06-18
Can you get to a Terminal with Applications - Accessories - Terminal. If so,

What's the output of,
```
ps a
```

---

### Post by lightstream on 2008-06-19
Thanks for your response. The command you suggested gives me: 

```
  PID TTY      STAT   TIME COMMAND
 4795 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4796 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4800 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4801 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4802 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5760 tty7     SLs+   0:10 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut
 5943 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 6306 pts/0    Ss     0:00 bash
 6323 pts/0    R+     0:00 ps a
```

So it looks like the TTYs are there doesn't it?

---

### Post by VMC on 2008-06-19
Yes, exactly like mine. Not to sound stupid, but you are using Ctrl+Alt+F1 altogether , right?

---

### Post by mempman on 2008-06-19
> **lightstream said:**
> I need to get to a TTY login to reinstall nVidia drivers but ctrl-alt-f1 (and ctrl-alt-f2, f3 etc) have stopped working.

Does anyone know what could be causing this??

thanks for any help ..

Also, if I boot into a root console from the Grub menu and type 'telinit 3' to get to runlevel 3, X will start up, which is obviously not what I wanted... I thought runlevel 3 was text-only?

Maybe your keyboard keys are messed up?

---

### Post by lightstream on 2008-06-19
> **VMC said:**
> Yes, exactly like mine. Not to sound stupid, but you are using Ctrl+Alt+F1 altogether , right?

Yeah, all the keys at once: I hold down Ctrl & Alt, then press F1.

Until I upgraded to Hardy (which was only 10 days ago) I could get to all the TTY consoles no problem.

> **mempman said:**
> Maybe your keyboard keys are messed up?

I have thought that but Ctrl-Alt and any other key - eg left & right arrow to change workspaces - works fine.

It's just Ctrl-Alt plus an F-key that doesn't do anything - no screen flicker, absolutely nothing at all. I really don't know where to start trying to fix the problem :confused:

---

### Post by llama320 on 2008-06-19
when you say ctrl+alt+f1 doesn't work..do you mean that you just get a black screen? like the screensaver just started?

to see if the tty's are working but you just can't see them, try this...go to ctrl+alt+f1...enter login...enter password (even though you can't see any of it)..then try typing

```
sudo reboot
```

then enter your root password and see if the computer reboots...if it does, then you know your virtual terminals are working...OKAY, so if they're working, read on because this same thing happened to me
***
So what I did was uninstall my current driver (it was nvidia-glx-new) and then install nvidia-glx (you may also try nvidia-glx-legacy) such that i could get my virtual terminals working...the only problem was compiz was now disabled, so I downloaded the nvidia driver 100.14.23..it sounds like you did something similar already...and then went into the virtual terminal, uninstalled my current driver, stopped gdm, and then manually installed the driver

So to summarize

1. uninstall current driver
2. reinstall one that works with the virtual terminals
3. reboot
4. Once rebooted, uninstall the driver with TTY support
5. stop gdm (sudo /etc/init.d/gdm stop)
5. Manually install nVidia driver
6. start gdm (sudo /etc/init.d/gdm start)

Good Luck and sorry for being so wordy :)

---

### Post by lightstream on 2008-06-20
Thanks for your help llama320...

> **llama320 said:**
> when you say ctrl+alt+f1 doesn't work..do you mean that you just get a black screen? like the screensaver just started?

Actually nothing happens at all! There is not even a loss of focus on the app I'm using at the time - it is literally as if the keys aren't being picked up (but I know they are for the reasons given previously)

(Funnily enough though, during my investigations, I discovered the TTY's on my work computer don't work properly either, and in fact do give a blank screen, so I'll try your suggestions for that when I'm back in on Monday - Yeah I'm lucky enough to have Ubuntu at home and the office :D)

> **llama320 said:**
> So what I did was uninstall my current driver (it was nvidia-glx-new) and then install nvidia-glx (you may also try nvidia-glx-legacy) such that i could get my virtual terminals working...the only problem was compiz was now disabled, so I downloaded the nvidia driver 100.14.23..it sounds like you did something similar already..

Yeah, I do use the drivers off the nvidia site - I have to reinstall them every time there's an X update - or at least when there's a kernel update. I think this is because the installation process creates a kernel module which would need to match my kernel version.

I really do suspect the video drivers do have something to do with this though! Although I don't see how video drivers should matter when I access a text console !?

Maybe the nvidia installer does something or doesn't do something that ubuntu expects? At least, nothing shows up in Administration > Hardware Drivers even though I do have restricted drivers running (the nvidia x-server settings applet reports their presence quite happily)

---

### Post by Greyed on 2008-06-20
What make/model of keyboard do you have?

---

### Post by lightstream on 2008-06-20
> **Greyed said:**
> What make/model of keyboard do you have?

I use a Saitek Eclipse, backlit jobby. I had it with Gutsy too, and Ctrl-Alt-F1 etc all worked fine then...

---

### Post by Greyed on 2008-06-20
Well, that shot down my theory.

I have a Logitech *mumble* which has a dumb "feature" of remapping the function keys to different actions like "email" and "browse web".  To get the PC standard function keys one needs to turn on the "function lock".  The last time I had CNTL-ALT-[F1-F6] fail on my was because I rebooted and forgot to turn the function lock back on. ](*,)

However it looks like the Saitek does not have that particular inanity.  Carry on.

---

### Post by r0ydster on 2008-06-20
I think that this post will solve your problem:

[http://ubuntuforums.org/showthread.php?t=667271](http://ubuntuforums.org/showthread.php?t=667271)

Specifically post number 3.

I don't think that it's a keyboard problem - for some reason Ubuntu doesn't enable this by default.  I was under the impression that this was going to be fixed in Hardy - but apparently not.

Another must do is to alter your terminal font size, in the /boot/grub/menu.lst file.  

First back up the file: sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig

Then, depending on your screen size add this to the end of kernel line: vga=791

For more info look here:

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

Look under Linux video mode numbers


Here is my current line:

kernel	          /boot/vmlinuz-2.6.24-19-generic root=UUID=6e692be6-7bdb-41e6-ad00-0b078a7fbc04 ro quiet splash vga=791

After you make the changes, reboot and log in, then go to <CTRL><ALT><F1> - this should fix it - but if you get a blank screen, you'll need to use a lower resolution, such as vga=788.

Hope this helps!

Mike

---

### Post by llama320 on 2008-06-20
> **lightstream said:**
> 
Yeah, I do use the drivers off the nvidia site - I have to reinstall them every time there's an X update - or at least when there's a kernel update. I think this is because the installation process creates a kernel module which would need to match my kernel version.

I have to do the same thing...not a huge deal though, just a little extra something to do every month or so

---

### Post by lightstream on 2008-06-20
> **llama320 said:**
> I have to do the same thing...not a huge deal though, just a little extra something to do every month or so

True, it's a piece of cake now I have a little script that does the complete compilation and installation for me. Before that, well I'm afraid there was a little gnashing of teeth and tearing out of hair !

---

### Post by lightstream on 2008-06-20
> **r0ydster said:**
> I think that this post will solve your problem:

[http://ubuntuforums.org/showthread.php?t=667271](http://ubuntuforums.org/showthread.php?t=667271)

Specifically post number 3.

Nice one r0ydster, that definitely looks like my problem too! Will be trying those suggestions out tomorrow. I'll post back how I get on, but pretty sure how to fix it is in there so thanks a lot

Edit: to my surprise, the fix there did **not** work for me. Will have to keep looking!!

---

### Post by lightstream on 2008-06-20
> **Greyed said:**
> Well, that shot down my theory.

I have a Logitech *mumble* which has a dumb "feature" of remapping the function keys to different actions like "email" and "browse web".  To get the PC standard function keys one needs to turn on the "function lock".  The last time I had CNTL-ALT-[F1-F6] fail on my was because I rebooted and forgot to turn the function lock back on. ](*,)

However it looks like the Saitek does not have that particular inanity.  Carry on.

Nope, the Saitek is blessed with standard function keys thankfully - I have a M$ keyboard on another machine which does have that annoying thing where you have to press the "don't muck up my function keys thanks" button at every boot :-|

---

### Post by lightstream on 2008-06-21
OK so I've tried various things - the changes suggested by r0ydster (which I really thought would help but didn't), reinstalling xkb-data, xbase-clients, x11-xkb-utils, adding vga=791 to the kernel line in /boot/grub/menu.lst, all to no avail.

I have however discovered how to switch to a virtual terminal from the command line:
```
sudo chvt 1
```
This actually works! I get the text login, everything is fine, I can even switch to other VTs (eg Ctrl-Alt-F2) and even back to the graphical X session with Ctrl-Alt-F7.

I just can't use the Ctrl-Alt-<Fkey> combination from graphical X. This is very strange but at least I can get to the VTs now!

---

### Post by r0ydster on 2008-06-28
Lightstream, I'm suprised that the fix I suggested didn't work.

But at least you got something to work.

Mike

---

### Post by rainekiss on 2010-01-23
Hi all,  I'm having an issue with viewing my virtual terminals, I did what llama320 said to confirm that my virtual terminals are working (which they are), but I don't know how to reinstall the drivers, could someone please tell me what do?? I'd be really really greatful, thanks.

---

