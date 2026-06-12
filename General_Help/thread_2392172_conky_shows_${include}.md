---
title: "conky shows ${include}"
date: 2018-05-17
forum: General Help
---

### Post by nraygun on 2018-05-17
I'm trying to load a new widget in conky and one of the simpler ones shows ${include} instead of using the actual file it references. It originally had $USER in the path and I changed it to the actual path but it still doesn't want to include the file. I'm sure the file is in the area being referenced.
Any ideas? Maybe this is old syntax or something?

     ```
${include /home/nraygun/.conky/templeterino.conf}
```

```
$ ls -la templeterino.conf 
-rwxrwxrwx 1 nraygun nraygun 1473 Aug  5  2016 templeterino.conf
$ pwd
/home/nraygun/.conky

```

---

### Post by again? on 2018-05-17
Looking at [http://manpages.ubuntu.com](http://manpages.ubuntu.com),
$include seems to be a variable dropped after conky 1.9 (ubuntu 14.04)

```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] conky -v**
conky 1.10.8 compiled Wed Feb 28 17:11:42 UTC 2018 for Linux 4.4.0-101-generic x86_64
```

What is the name of the conky and where did you get it?

Searching for templeterino.conf brings up this conky which has a version for conky 1.10
[https://github.com/davidrlunu/dots-and-dashes](https://github.com/davidrlunu/dots-and-dashes)

---

### Post by nraygun on 2018-05-18
Nice detective work! That's the one! On both fronts - the conky and the version.

I suppose I could just expand out whatever the #include was trying to do or use current syntax. But I'll have to figure that out. I'm new to conky.

Looks like it was just trying to include a common set of variables or something like in C.

---

### Post by dino99 on 2018-05-18
The main place: [https://ubuntuforums.org/showthread.php?t=1771033&highlight=vindsl](https://ubuntuforums.org/showthread.php?t=1771033&highlight=vindsl)

---

### Post by again? on 2018-05-18
> **nraygun said:**
> Nice detective work! That's the one! On both fronts - the conky and the version.

I suppose I could just expand out whatever the #include was trying to do or use current syntax. But I'll have to figure that out. I'm new to conky.

Looks like it was just trying to include a common set of variables or something like in C.
conky 1.10 changed to using lua syntax configs.
Conky 1.10 will load old style configs but conky 1.9 won't work with the new lua configs.

_old config syntax_ (conky 1.9)
```
background no
use_xft yes
xftfont monofur:size=9.5
xftalpha 0.8
update_interval 1
total_run_times 0
```

_Lua config syntax_(conky 1.10)
```
conky.config = {
	background = false,
	use_xft = true,
	font = 'monofur:size=9.5',
	xftalpha = 0.8,
	update_interval = 1,
	total_run_times = 0,
```

Just use the **conky_OPSAT_v1.10** from the github page I linked.
ReadMe says...
> Everything inside `conky_OPSAT_v1.10` directory, should go into `/home/youruser/.conky/` and you are ready to go.
If you encounter conky files not working with the default settings, try exporting your $USER to the enviornment as every path in the conky files has `/home/$USER/..` as path.

I would rename your current ~/.conky folder to ~/.conky.bak
then 
create a new ~/.conky directory and move the contents of conky_OPSAT_v1.10 into it.

---

### Post by nraygun on 2018-05-18
Thanks guber.
I tried copying the contents of the OPSTAT 1.10 directory into a new .conky directory and it seemed to recreate the old stuff along with the the OPSTAT stuff.
But it doesn't show up in Conky Manager.
I can see that $USER resolves properly.
Any ideas?

---

### Post by again? on 2018-05-18
Ohh.. your using conky-manager.
Conky-manager creates a ~/.conky directory as well to store it's conky configs so if you moved 
~/.conky, you removed the conky-manager configs.

conky-manager is just a bunch of scripts to manage some conky configs.
You can start the included configs manually.
eg
```
conky -c ~/.conky/Gotham/Gotham
```

I suggested starting with an empty ~/.conky directory because conky_OPSAT  sprawls it's files in this directory
and didn't want to conflict with the conky_OPSAT_v1.10 version.

I just installed conky-manager and these are the files conky-manager installs to ~/.conky.
[ATTACH=CONFIG]279740[/ATTACH]

Copy them over from your backup (or I think they may be reinstated when conky-manager starts)
To have conky_OPSAT_v1.10 configs show in conky-manager they probably need to be contained in a  conky_OPSAT folder
but that would involve readjusting all the paths in the configs.

There is mention of a manual for conky-manager @ [http://www.teejeetech.in/p/conky-manager.html](http://www.teejeetech.in/p/conky-manager.html) but
looks like it requires a paypal donation.

---

### Post by nraygun on 2018-05-19
Yes, I see that some of the individual components work with a "conky -c ~/.conky/blah".
I think this set of components rely too much on older forms of conky including certain python modules that are either no longer available or have changed so much that they don't work with these scripts.
Unfortunately, I may have to abandon ship on this one. Too bad too, would look cool with my background image with all this stuff around the center logo.
I may come back to "ricing" after finishing up a few other projects and honey-do's. ;-)
Thanks for all the help and investigation!!!

---

