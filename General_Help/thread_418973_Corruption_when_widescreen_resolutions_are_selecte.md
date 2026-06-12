---
title: "Corruption when widescreen resolutions are selected"
date: 2007-04-22
forum: General Help
---

### Post by Gooch on 2007-04-22
im using Feisty Fawn, and when i try to select my monitor's native resolution (1280x800) it causes lots of graphical corruption, so i have to switch to (a very blurry) 1024x720, any one any ideas as to how to remedy this?

---

### Post by dcstar on 2007-04-22
> **Gooch said:**
> im using Feisty Fawn, and when i try to select my monitor's native resolution (1280x800) it causes lots of graphical corruption, so i have to switch to (a very blurry) 1024x720, any one any ideas as to how to remedy this?

Without any details of what is actually occurring, no.

---

### Post by Gooch on 2007-04-22
[IMG]http://i171.photobucket.com/albums/u320/Gooch2k4/Screenshot.jpg[/IMG]
heres a screenshot of whats happening :confused:

---

### Post by Gooch on 2007-04-23
after much messing around in xorg.conf i eventually got it working :)

---

### Post by craigyjack on 2007-04-24
Could you explain how you got this to fix?

I have looked over the forum now to try and find the solution to the new restricted manager NVIDIA driver and it not displaying correct resolutions right. I know it isnt supported by Ubuntu, but this seems to be a common problem now, and it is hard to use/enjoy the new Feisty Fawn when the resolution is messed.

I tried the actual NVIDIA drivers from their site (that is what I had on Edgy and they worked beautifully) but this time around, it had to compile its own module because of the new kernel, and then once it got done setting up, X server wouldnt load. I messed around with it for a while, changing some stuff, but i eventually gave up and did another install of Feisty Fawn.

Now I'm back to the restricted drivers manager NVIDIA driver, and waiting to see if I can get the resolution fixed.

Could you or someone please inform me on how to fix this.
Thanks,
Craig

---

### Post by craigyjack on 2007-04-24
Hey,
I got my problem solved. There was actually several problems and several threads for each problem.
The problem in this thread, the corruption on the side of the screen, I believe was fixed by adding 
```

Option         "AddARGBGLXVisuals"  "True"

```
in the "Screen" section of your xorg.conf, if anybody else comes across this problem.

It seems the binary nvidia driver in restricted driver manager is having some problems making the xorg.conf correcting and interpreting settings from your monitor. [and seeing as how the nvidia from the nvidia website no longer works in feisty fawn and the new kernel (at least it didnt for me at all), you must use the restricted manager nvidia driver]

Other problems that were involved with the binary nvidia driver were resolutions not showing up that should (you couldnt change the resolution to your preferred setting), and refresh rates were not interpreted and displayed right at all.
this all seemed to be mostly [i say mostly because idk if the refresh rates are perfectly correct still, but the resolution works fine, and the refresh rates seem more reasonable than before] fixed by adding these lines
```

Option		"UseEdid" "false"

```
to your "Screen" section of xorg.conf
[Also you will need to add in your desired resolution in the "Screen" section under the Mode option right in front of all the other standard resolutions there] 

and
```

Option		"DynamicTwinView" 	"false"

```
to your "Device" Video Card section in xorg.conf

and
```

	Option	"HorizSync"	"30-82"
	Option	"VertRefresh"	"56-76"

```
to the "Monitor" section of your xorg.conf **Make sure you change the numbers there to the rates of your monitor
if you dont know those rates up there, you should be able to find them out by getting the package "xresprobe" from synaptic package manager, and then running this command in terminal
```

sudo ddcprobe | grep monitorrange

```

If you do all those steps, you should have no more problems with the binary nividia drivers from the restricted driver manager [at least, all this worked for].

I hope this helps anyone that comes across these problems.
-Craig

---

