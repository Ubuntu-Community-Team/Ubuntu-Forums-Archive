---
title: "Cannot start gui applications from Ubuntu CLI"
date: 2015-05-09
forum: General Help
---

### Post by leotemp on 2015-05-09
I have installed a minimal install of unbuntu (precise) via crouton to my chromebook using the cli-extra parameter to get an install without a desktop as to save space for a virtual machine i wish to install. My installation is bare except for xorg which installed via apt-get install xorg and firefox via the same method.

When I attempt to run firefox I get "error no display specified"

I did a little reading but all i could find was information on setting up a remote server, i still tried the following
export DISPLAY=:0
export XAUTHORITY=~/.Xauthority
error no protocol specified
error no protocol specified
error no protocol specified
cannot open display :0

I want to be able to launch gui apps from the terminal, specifically firefox, virtualbox and photoshop. Thanks for reading!

Okay so i made a little progress on this, i have put the following in my .bashrc

XAUTHORITY=~/.Xauthority
DISPLAY=0:0

However now when I run firefox or sudo firefox I get:
error cannot open display ""


So obviously I am still missing something here..

---

### Post by sudodus on 2015-05-09
I don't know how much you have installed. You need a window manager. I make a very light graphical system (from the basic text system created with the Ubuntu mini.iso) by installing three extra packages:

```
sudo apt-get install fluxbox xinit xterm
```

You can use another window manager (than fluxbox) if you wish, for example openbox or jwm.

You can start a graphical session with the command startx (from the text screen).

---

### Post by leotemp on 2015-05-09
Thanks for the reply, I have installed the above apps but now when I startx I get:

Fatal server error:
Server is already active for Display 0

It also informs me that I can delete /tmp/.X0-lock to fix the issue however this caused me to go back to the "no protocol specified" and "cannot open display ''" errors so i have reverted my .bashrc to before I removed the xauthority and display lines.

Also I wasnt necessarily looking for a desktop, is it not possible to launch graphical applications right from the terminal without having a desktop?

---

### Post by sudodus on 2015-05-09
You need not have a full desktop environment, but I think you need a window manager.

I think that graphical programs want a window manager. They don't work directly from a text screen.

Maybe you have something installed or running now, that creates a conflict with the three packages, that I suggested. Maybe it will work after a reboot. Otherwise it might be easiest to re-install and get it right from the beginning.

Do it manually, or if you wish, you can get some help, using the One Button Installer installing [URL="https://help.ubuntu.com/community/OBI#Trusty-mini-txt"]Trusty-mini-txt


[/URL]

---

### Post by dragonfly41 on 2015-05-09
Actually right now I'm researching a similar requirement .. to launch app from browser links ..

I found this thread .. [http://askubuntu.com/questions/330937/is-it-possible-to-open-an-ubuntu-app-from-html](http://askubuntu.com/questions/330937/is-it-possible-to-open-an-ubuntu-app-from-html)

which possibly might help you

and I can run commands like this .. xdg-open 'app://nautilus' 		
 	     	    	 		 		     			 			 
Trying other approaches I had received the error message Gtk: WARNING cannot open display
and I have now switched to trying xdg-open.

---

### Post by leotemp on 2015-05-09
going to try reinstall and I will report back with my results.

---

### Post by sudodus on 2015-05-09
Good luck :-)

---

### Post by leotemp on 2015-05-09
So after trying both a cli-extra install and a core install i get the same results.. perhaps there is something already built into either of these install scripts that is already using the display. I ams lost :(

---

### Post by sudodus on 2015-05-09
Try starting the installation from Ubuntu ***mini.iso***, that you find at [http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/)

I suggest that you try 14.04 LTS. That is how I start. I select no extra packages, and after rebooting into the installed system, I install the three packages ***fluxbox xinit xterm***. Then it is possible to ***startx***, and in the graphics session to start x programs, one of them is xterm. Install ***firefox***, and it can be started from ***xterm***.

If you still have problems, it might be caused by problems with the graphics driver, that your graphics chip does not work well the the linux drivers for graphics. What is yours graphics chip or card? I think your chromebook is rather new, so I think you have better chances to succeed with 14.04 than with 12.04 alias precise. You might also try the newest version, 15.04 (but it is supported for only 9 months).

---

### Post by sudodus on 2015-05-09
If you still have problems, there might be something special with the chromebook, that I don't know about.

---

### Post by Holger_Gehrke on 2015-05-10
You might want to read the manual page of xinit. If X is installed correctly you should be able to just run
```

xinit firefox

```
If I boot to a pure cli environment on my Ubuntu 12.04, doing that gives me a minimal (no window manager, no nothing) graphical environment with firefox running. If I close ff, X shuts down, too. Since there's no window manager, the window is undecorated -- no title bar, no borders, no "minimize", "maximize" and "close" buttons, but I can switch to full screen using F11 (that's a firefox function, not one provided by a wm) and close firefox by hitting ctrl-q.

---

### Post by sudodus on 2015-05-10
Holger, 

Thanks for sharing this tip to make things as simple as possible :-)

---

