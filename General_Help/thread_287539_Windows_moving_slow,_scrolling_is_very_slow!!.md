---
title: "Windows moving slow, scrolling is very slow!!"
date: 2006-10-28
forum: General Help
---

### Post by iMac on 2006-10-28
I just installed the 64-bit version of the new Ubuntu, and when i try and move any open window it moves very slowly. Like when i start to drag it the top moves followed by the bottom at a delay. Also when scrolling in firefox it scrolls very slow and takes a very long time. I'm running it on a Acer desktop with a 17" LCD 1280X1024 monitor.

All help is greatley appriciated

---

### Post by taurus on 2006-10-28
Perhaps you need to install a driver (nvidia or ATI) for your graphic card!  What video card do you have and what driver are you using right now?  Look in /etc/X11/xorg.conf and you would see it.  Otherwise, paste it here...

```
more /etc/X11/xorg.conf
```

---

### Post by DeathOnJuice on 2006-10-28
What graphics card do you have? I had to use the vesa driver to get my eVGA 7800GT to work, and I had the exact same problems. If you have an NVidia card, you can install the drivers using these instructions, plus a little addition of my own:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Also, in addition to these instructions, there is a security hole in the NVidia drivers, unless you're using the beta release. It can compromise your system or (more likely) just restart the X server while you're using Firefox. To fix it, open a terminal and enter:

```

sudo gedit /etc/X11/xorg.conf

```

In the Device section, above the line that says Driver "nvidia" (if you followed the instructions), add this line:

```

Option "RenderAccel" "false"

```

Then log out and press control-alt-backspace. That's it! There may be a very slight performance hit.

---

### Post by iMac on 2006-10-28
well it just says "generic video card" so obviousley that isn't the driver I need. I have a Nivida 6100 graphics card.

---

### Post by DeathOnJuice on 2006-10-28
No, an NVidia 6100 should use that driver. Give it a shot. If you need help with the guide, just ask!

---

### Post by iMac on 2006-10-28
ok thank you very much for the info!

---

### Post by DeathOnJuice on 2006-10-28
No problem at all; I'm glad to help!

---

### Post by gerowen on 2006-10-29
I just installed the proprietary driver with:
```
sudo apt-get update
sudo apt-get install nvidia-glx
```

Then I reconfigured xorg so I could choose the "NVidia" driver instead of the "nv" driver by running:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by iMac on 2006-10-29
> **marcusdean.adams said:**
> I just installed the proprietary driver with:
```
sudo apt-get update
sudo apt-get install nvidia-glx
```

Then I reconfigured xorg so I could choose the "NVidia" driver instead of the "nv" driver by running:
```
sudo dpkg-reconfigure xserver-xorg
```

thanks so much that worked! instead of using the GUI reconfigure thing from the terminal i had to open it in gedit and manually type in driver nvidia. 

Thanks everyone it works great now!

---

### Post by DeathOnJuice on 2006-10-29
That's great! However, I still would make sure you did these things from the guide. This should only take a second for you.

First, type this in the terminal:

```

uname -r

```

In the output, you should see either the number 386 or, more likely, the word generic. Open Synaptic and install linux-generic or linux-386, depending on what it said. This will make system upgrades much smoother.

Then, MAKE SURE YOU DO THE SECURITY FIX I MENTIONED EARLIER!

That's it!

---

### Post by iMac on 2006-10-29
> **DeathOnJuice said:**
> That's great! However, I still would make sure you did these things from the guide. This should only take a second for you.

First, type this in the terminal:

```

uname -r

```

In the output, you should see either the number 386 or, more likely, the word generic. Open Synaptic and install linux-generic or linux-386, depending on what it said. This will make system upgrades much smoother.

Then, MAKE SURE YOU DO THE SECURITY FIX I MENTIONED EARLIER!

That's it!
thanks again! I did the security fix, and also followed the guide to install the linux-386. now when i type uname -r i get this line
2.6.17-10-386

---

### Post by dimeotane on 2006-10-29
I love the functions that Cream offers as a text editor. However, once I've got a page of text and try to select with the mouse or scroll up and down, it becomes so very slow.   Especially when editing a text file which is wrapped.
  Any solutions to this?  As a terminal program it should be so much faster on a Pentium  4 processor!  I have nothing else running too.

---

### Post by gerowen on 2006-10-29
> **iMac said:**
> thanks so much that worked! instead of using the GUI reconfigure thing from the terminal i had to open it in gedit and manually type in driver nvidia. 

Thanks everyone it works great now!

Glad I could help, :D

---

