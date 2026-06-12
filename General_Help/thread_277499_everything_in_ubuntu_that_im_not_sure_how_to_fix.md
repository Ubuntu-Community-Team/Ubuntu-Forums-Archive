---
title: "everything in ubuntu that im not sure how to fix"
date: 2006-10-14
forum: General Help
---

### Post by proselyte on 2006-10-14
I've decide against making many new threads for each problem, so I'm going to list my computer, and my problems.  Any solution I find will also be linked to/quoted.  
HP pavilion dv8000t laptop
Intel Core Huo 2.16ghz
Nvidia Geforce Go 7600
Synaptics touchpad
keyboard, with numpad, 7 buttons above the keyboard, a power button, two buttons for HP's Quickplay software, volume up, volume down, and mute, and a calculator button
Creative Audigy 2 ZS notebook PCMCIA sound cardt
Razer Diamondback mouse
two 80 gigabyte hard drives (one with Linux and one with Windows)
smp kernel with the proprietary Nvidia drivers
running Dapper Drake, with XGL and Beryl

Here is the list

Important!

Suspend and hibernate don't work, suspend leaves blank screen on restore, and hibernate gives random brown junk with lines in it, then gives blank screen. Also, every boot, i get a message saying "clearing suspend2 signatures) whether i shutdown with suspend or not.  

Using the touch pad, or accidentally touching it while typing with the mouse connected makes pointer go in random directions, and click.  I'm not sure if this happens when the mouse is not connected from boot up, I'll check soon. I changed the mouse settings when i started using the diamondback, so that may play a part in it. I solved this problem for a little bit by using 'synclient TouchpadOff=1', but that very recently stopped working.  
             **Update: reboots work wonders, this problem is solved**

I don't know how to configure the 4 buttons on either side of the mouse.

I need to set the super key as a modifier, the layout options of the gnome preferences are blank.  Using layout "us"

Not so important 

Numpad does not work with numbers unless i press the shift while using it

The volume buttons do not work with Audigy card. Also, the volume control applet does not work either, i use alsamixer

In windows, my graphics card has a "Powermizer" battery powersave option, is there a way to access this in Linux?

Other things

My touch pad (before i plugged in the diamondback, when it was working well, started emulating a triple click with a double finger tap, and a double click with a three finger tap.  I don't know how this started, but its a good thing, and i would like to know how to configure the touch pad

I'll add more as i think of it

---

### Post by jsnelli2 on 2007-02-20
I just read that the Audigy 2 ZS Notebook prevents the notebook from going into suspend and hibernate....It comes from the fact that the card can't be hotplugged without crashing the kernel.  Hope that helps explain.

---

