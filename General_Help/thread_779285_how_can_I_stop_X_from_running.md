---
title: "how can I stop X from running?"
date: 2008-05-02
forum: General Help
---

### Post by fraterchaos on 2008-05-02
Ok, as i posted in an earlier message, I am aving MAJOR trouble with the Nividi restricted driver as supplied with Hardy...

I went to the Nvidia site, and they HAVE drivers for Linux, but it is a .run file, which isn't a major problem as I figured out how to execute it...

The problem is, the installer must be run as root, and X must be turned off, I can use sudo to run it as root, but how in the world do I shut down the X server to install it???

I have looked in all the help and can't find anything about stopping the X server, or starting at a different runlevel.

I really need to fix this, as 800x600 and no openGL support just won't cut it, and 640x480 with OpenGL is even worse, I need 1024x768 screen resolution and I KNOW my system is capable of that, its actually capable of higher resolutions, but the drivers simply won't let me.

Please, someone help me find a way to fix this.

---

### Post by qwalton on 2008-05-02
press ctrl+Alt+F1 and login using your normal user name then run ```
sudo /etc/init.d/gdm stop
``` this will stop x server from running.  You can then navigate to where the nvidia installer you need to run is stored and run it.  Once you want to start X again run ```
sudo /etc/init.d/gdm start
``` and that should start up x server again and put you at the gnome login screen.

---

### Post by fraterchaos on 2008-05-02
thanks, yes, that works to stop X from running, unfortunately, once X isn't running I can't seem to run the Nvidia installer... if I try to run it from a terminal window under X, it brings up a graphical start screen that tells me I have to have X stopped... if I stop X first, then try to run the file with the command given ( sh NVIDIA-Linux-x86.96.43.05-pkg1.run ) it says cannot run command.

I tried this with both using sudo and without, and its always the same thing...

I guess, until they come up with a fixed driver from Ubuntu, I really have no reason to even use Ubuntu, or I might as well go back to Dapper, as 640x480 resolution is jjust not satisfactory and I don't know enough about all this to fix the problem myself

thanks anyway

---

### Post by carlhako on 2008-05-02
I had no issues installing the nvidia drivers from their website. whats the exact output when trying to install?

---

### Post by fraterchaos on 2008-05-02
I honestly do not recall the EXACT output...

when I try to run the install from a terminal window, it opens a graphic installer window that says first, that it must be run as root, and if I DO run it as root, the installer window opens with a message saying X must be stopped before running the program.

when running it after shutting down X, it says something to the effect that "cannot find command" or "<name> is not a valid command"

I tried using sudo, not using sudo, using sh <name> and NOT including the sh, I tried ./<name> with and without both sudo and sh, in fact I tried every combination I could think of, and in all cases it was the same, either "cannot find command" or "<name> is not a command"

(for ,name> substitute NVIDIA-Linux-x86.96.43.05-pkg1.run)

and I tried extracting the files manually and running various files that way, and still the same thing.

As I said, its all way beyond my knowlege what I should do... since Nvidia doesn't offer an Ubuntu specific version of the drivers, with a standard Ubuntu package installer, and Ubuntu's drivers do not function, I'm basically screwed.

But thanks for trying anyway

---

### Post by qwalton on 2008-05-02
I have had no problems running the nvidia drivers on my computer running hardy, have you enabled them in the hardware drivers menu(System>Administration>Hardware Drivers)?  You shouldn't have to run an installer at all to get the drivers installed since the hardware drivers manager should automagically pull the drivers from the repos. *EDIT* You could also try using [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to install the drivers, I haven't used it personally but I have heard good things about it.

---

### Post by fraterchaos on 2008-05-02
um... please see the first post...

I enabled the drivers that were supplied with Hardy, and the highest resolution available is 640x480, and the only other option is even lower.

with the driver disabled, I can get 800x600, but I really want at least 1024x768

so, either there is something badly wrong with the entire install of Ubuntu, or the drivers it is downloading when I enable them are not dopwnloading or installing properly, or there is something wrong with the drivers, which is why I tried to get drivers straight from Nvidia

---

### Post by qwalton on 2008-05-02
I edited my post right around the time you posted your reply, so I'm not sure if you saw the part I added.  If using envy doesn't work you could always try having hardy rebuild your xorg.conf by running ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

and then

 sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by fraterchaos on 2008-05-02
well, I was going to wait to try envy because I am a little frustrated with it all right now, but since I'm not doing anything else, I think I will try envy now.

If that does not work, I'll try the code you supplied

thanks for all the help

---

### Post by fraterchaos on 2008-05-02
ok, I tried the Envy program, and it installed and then I rebooted and it brought up a warning that I was running in low graphics mode, and gave me a box to configure the graphics...

I entered the right video card and monitor data, set the resolution to 1024x768 and continued to boot...

at firt, I was sure it was not working, as it came up in 800x600 again, and when I tried to change the resolution, it still only offered the max of 800x600

so then i realized that I might need to enable the drivers, which turned out to be true, so I enabled and rebooted...

when the screen came up to log in, I could tell it was in the higher resolution right away, so i thought it was all fixed, until the machine finished booting and my display was all distorted (rounded on the sides, with the top and bottom skinnier and all bulging out in the center)

But when i went to the screen resolution settings again, it said it was still 800x600 (even though it was plainly higher) so I set it to 1024x768, and lo and behold, it worked!!!

So thanks very very much for the suggestion to try Envy, I wonder why machines with Nvidia cards don't automatically use this, as it seems much better than the standard method.

Again, thank you greatly, as this really helps alot, and makes it worth using Hardy :)

---

