---
title: "3Ddesktop - it actually works.  :-)"
date: 2005-06-05
forum: General Help
---

### Post by GTKpower on 2005-06-05
A 3D desktop switcher.  Download it through Synaptic.

Very cool.  Reminds me of OS X's Expose, but it works a bit differently

Recommended for slightly faster hardware, as there are some very slight slowdowns while using it.  Still, it's worth trying.

I thikn I'll keep it for a while.

Install it, and in the console, type 3ddesk to run it.  I just create a launcher on the panel that will launch the 3ddesktop view when I click on it.  Use the mouse to navigate desktops.

---

### Post by hondje on 2005-06-05
:O That's so cool.  If I wasn't so addicted to edge flipping (like with Brightside) I'd always use it....

---

### Post by GTKpower on 2005-06-05
I did notice two minor bugs:

When you first run 3ddekstop, it doesn't immediately map all your desktops, just one or two.

Gneral desktop performance can be a bit choppy at times if you're on a slower machine.

Otherwise, it showcases what is possible when even a half-decent videocard does some of the desktop rendering tasks (a la OS X.)

The GNOME dev team should consider looking into 3ddesktop, and perhaps integrating it, or a similar 3D or other OpenGL-based desktop switching solution.

---

### Post by trash on 2005-06-05
WOW, thats perdy!! The launcher is the way to go for sure:)

---

### Post by angkor on 2005-06-05
Cool! I want this one:

[http://www.gnome.org/~seth/blog-images/monkey-hoot/mpeg4/WorkspaceSwitching.avi](http://www.gnome.org/~seth/blog-images/monkey-hoot/mpeg4/WorkspaceSwitching.avi)

---

### Post by enquiry on 2005-06-05
Sweet! Never got this working under Warty. Good to have when showing off your OS to Windows users  :wink:

---

### Post by m0biu5 on 2005-06-05
[QUOTE=enquiry]Sweet! Never got this working under Warty. Good to have when showing off your OS to Windows users  :wink:[/QUOTE]

Yeah, they enjoy it.  :grin: 

I would use it more often but the daemon spikes my CPU up to about 40% every other second.

---

### Post by mtron on 2005-06-05
Works great with P4 1.8 GHZ, 256Ram and an old GeForce2 MX400

Nice goodie, thanks for the tip

---

### Post by trash on 2005-06-07
Anybody noticing that after using it once it messes up the cursor? mine looks all jagged and no more color, only black and white and sometimes the cursor changes to a solid black arrow... very strange.

Also I was wondering if it's possible somewhere to assign a hotkey to launch the app?

---

### Post by tristan on 2005-06-07
I've noticed that it won't display maximised windows. Other than that, it's pretty slick looking.

---

### Post by mjsoccer1 on 2005-06-07
Cool tool, however I can't use it... I'm running a Pentium3 at 1.2ghZ, with 256mb RAM, and when run 3ddesk, my CPU usage spikes to near 100%... May have something to do with the fact that I'm using KDE (Kubuntu)... This is unrelated, but what is Xorg? IS that the X window manager, its taking up 23% of my CPU usage?... hmmmm.

---

### Post by andrewsawyer on 2005-06-08
Would you believe I have it working on my Acer Travelmate C110 laptop! Got it as an icon. A bit slow, and to be fair you might as well just click on one of the screen buttons on the bottom right of your screen, but it works all the same.

---

### Post by vladuz976 on 2005-07-07
[QUOTE=GTKpower]A 3D desktop switcher.  Download it through Synaptic.

Very cool.  Reminds me of OS X's Expose, but it works a bit differently

Recommended for slightly faster hardware, as there are some very slight slowdowns while using it.  Still, it's worth trying.

I thikn I'll keep it for a while.

Install it, and in the console, type 3ddesk to run it.  I just create a launcher on the panel that will launch the 3ddesktop view when I click on it.  Use the mouse to navigate desktops.[/QUOTE]
 the application launcher is good. but how can i add a keycombo that launches 3ddesktop? 
the keyboard shortcuts in the menu is only for preconfigured applications

---

### Post by Lunde on 2005-07-07
3ddesktop is a great app, I've used it a long time, but it needs som tweaking.

For making the 3ddesktop not start several processes and how to create a key launcher check this out:
[https://wiki.ubuntu.com//3ddesktopHowto](https://wiki.ubuntu.com//3ddesktopHowto)

Some more Tweaking:
**$ sudo gedit /etc/3ddesktop/3ddesktop.conf**

Look for this section:
```

# Examples (uncomment to use)
#

#texturesize 512
wm          gnome2
autoacquire 0

```

You reduce the memory usage by:
Lower the texture size by changing the value:: 
**texturesize 512**

The default option of allways keeping track of the changes you do on the different desktops is for most users just taking up CPU and memory, you can disable this by:
[B]autoacquire 0
[/B]

I now use this app all the time and I never think about the cpu and memory it uses. I find great use of it when i have VMware windows on one workspace and linux on the others. 

I use the F12 to active, the arrow keys changes desktops by default and enter zooms in on selected.

There is also a possibuility to set up something like Alt + right mouse button if you are a great mouse user. The mouse wheel changes desktops and mouse click zooms in by default.

---

### Post by rotorwash on 2005-07-15
I am using the F12 button to activate 3ddesk also. I have a tiny annoyance... when I press the F12 button to switch desktops there is a (approx 2 sec) delay between the button press and the zoom. I've gotten everything else to respond the way I like it but cannot seem to get rid of the delay when activating 3ddesk. My hardware is an A64 3200+ with ATI X800 XT with fglrx accel (should be fast enough, I think.). Has anyone else notice this and Is there a workaround?

---

### Post by vladuz976 on 2005-07-26
how did you set the F12 button to execute 3ddesk?

---

### Post by Lunde on 2005-07-26
[QUOTE=vladuz976]how did you set the F12 button to execute 3ddesk?[/QUOTE]
 As explained in the readme file of 3ddesk:
```

Run "gconf-editor". Drill down to apps --> metacity -->
global_keybindings. Find "run_command_1" and change it to your key
such as "F12" or "<Control><Alt>S".  Then in apps --> metacity -->
keybinding_commands find "command_1" and set it to "/usr/bin/3ddesk".

```

---

### Post by vladuz976 on 2005-07-26
thanks,

i guess i didn't read the readme file carefully enough then.
this works fine.
only interesting thing is, if i try to set the F13 key for it, it doesn't work.
I have an apple keyboard and on it the F13 key is slightly more convenient.
thanks a lot though.

---

### Post by Lunde on 2005-07-26
[QUOTE=vladuz976]thanks,

i guess i didn't read the readme file carefully enough then.
this works fine.
only interesting thing is, if i try to set the F13 key for it, it doesn't work.
I have an apple keyboard and on it the F13 key is slightly more convenient.
thanks a lot though.[/QUOTE]
 Just a guess, but your F13 probably needs to be recognized by the system first. 

Try this:
[http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)

---

