---
title: "Lanching gui apps in terminal only system"
date: 2008-06-26
forum: General Help
---

### Post by chadcan on 2008-06-26
I am using Ubuntu 8.04 LTS Server Edition. I want to know how to launch GUI apps in the terminal window, since the server edition does not have a gui system installed. And I do not want to install one. 

Is this possible?

I know for example oracle requires a gui in order to install. Are there any tutorials on open apps in giu mode. And also remotely from another machine. For example from a windows machine using putty.

---

### Post by MacAnthony on 2008-06-26
If an xserver isn't installed, there is nothing to draw and display a window for a gui app. I'm not sure if you are asking for it to run without an xserver or if you think there is some magical way of running them in a console.

---

### Post by KeyserSoze93 on 2008-06-26
if you want a local gui, get a local gui.

on the other hand, if you have another PC with a gui installed, you can ssh into your server box (once it has ssh server installed) and run graphical apps over the ssh. Google "ssh x forwarding" for more information...

this will allow you to see the apps window(s) displayed on your client PC even though they are actually running on your server.

---

### Post by issih on 2008-06-26
You will need some kind of lightweight gui installed, at least to get X I'd have thought.

I've seen LaRoza talk about using the ratpoison window manager to run opera on a laptop used pretty much exclusively as a cli machine. I believe that ratpoison is about as minimal as you could possibly get.

[http://www.nongnu.org/ratpoison/](http://www.nongnu.org/ratpoison/)

As for remote access, if you want a gui at the remote end you need to look at either X11 forwarding or using vlc, if you jsut want a terminal, ssh is all you need.

---

### Post by chadcan on 2008-06-26
Thanks, I think I got my answer. X forwarding would work for remote. 

And I am assuming I have to install xserver if I am on the actual server machine.

Any good tutorials anyone can think of. Googling it didn't help much.

---

### Post by mcduck on 2008-06-26
Some graphical apps are able to run with framebuffer.. I haven't played with it much but at least mplayer works, as well as the graphical mode of Links2 browser (or was it eLinks that has the graphical mode?)..

You can enable the framebuffer simply by adding vga=792 to kernel boot options in Grub. (Different numbers give different resolutions and bit depths, 792 is 1024x768 with 24-bit colors).

You might want to search for more detailed instructions about framebuffer before doing anything..

(of course there are all tiling window managers, like the already mentioned Ratpoison and my favourite, Ion2)

---

### Post by Titan8990 on 2008-06-26
If you were looking for a tutorial to install xserver then that is far too easy to require a tutorial. Just use the following command:


#apt-get install ubuntu-desktop

or if you prefer KDE:

#apt-get install kubuntu-desktop

---

### Post by chadcan on 2008-06-26
I got it installed. It's instructions on running gui apps once it's installed that I need.

I think my question my not be very clear, sorry about that. I am looking to run gui apps on the terminal window once I log into Ubuntu. Note i am not logging into the X system. Only using the terminal.

I found a good example. For example i am installing oracle 11g. It needs to launch the gui install for the software to install. If I am working in a text terminal window how do I configure my system to launch the gui installer.

---

### Post by TheEndIsNear on 2008-06-26
> **chadcan said:**
>  Are there any tutorials on open apps in giu mode. And also remotely from another machine. For example from a windows machine using putty.

Here's a tutorial on X-forwarding in windows using putty.
[http://www.cs.caltech.edu/courses/cs11/misc/xwindows.html](http://www.cs.caltech.edu/courses/cs11/misc/xwindows.html)

Here's were you can download the latest version of Xming.
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

---

