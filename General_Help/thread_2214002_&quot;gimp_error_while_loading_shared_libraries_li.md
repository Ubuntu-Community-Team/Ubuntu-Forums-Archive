---
title: "&quot;gimp: error while loading shared libraries: libgegl&quot;"
date: 2014-03-29
forum: General Help
---

### Post by Kyle_Undercofler on 2014-03-29
I tried running gimp and nothing happened, so I tried opening a .png file with gimp. Still nothing. When I ran gimp in terminal by typing "gimp" the terminal spat this at me. "gimp: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory" I'm semi-new to Ubuntu, plus I'm only 12, so I have no clue how to fix this. If someone can help me, it would be highly apriectiated.
P.S. this is the .png file:[ATTACH=CONFIG]251583[/ATTACH]

---

### Post by monkeybrain20122 on 2014-03-29
Well the terminal output says libgegl is missing. How did you install gimp? If you installed with synaptic or sudo apt-get the package should be installed as a dependency.

---

### Post by SeijiSensei on 2014-03-30
Sounds like you tried installing GIMP from some place other than the official Ubuntu "repositories."

Programs running on systems like Linux rely on "shared libraries" that contain functions that many programs can make use of.  When a program relies on another piece of software, this relationship is called a "dependency."  GIMP has *many* dependencies of which libgegl is one.

If you install a program (or "package" to use the common Linux term) via either the software manager or a command-line program like apt-get, Ubuntu will identify any dependencies that package relies on and installs them, too.  If you don't use one of these tools to install a package from the repositories, you can end up with some missing dependencies.

In your case, if the only missing item is libgegl, the solution is pretty easy.  Just install the libgegl-0.2.0 package.  You can do this from a command prompt with "sudo apt-get install libgegl-0.2.0" or use the graphic software manager that comes with Ubuntu.

---

### Post by Kyle_Undercofler on 2014-03-30
Thanks guys. I'm going to use "sudo apt-get install libgegl-0.2.0" and see if it works. EDIT: after doing that, this was what I got:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgegl-0.2.0
E: Couldn't find any package by regex 'libgegl-0.2.0'"
It's looking for an external drive, but I don't have an external drive! My mom thinks it's because my Linux was installed from a thumb drive.

---

### Post by monkeybrain20122 on 2014-03-30
What do you mean by 'installing on a thumb drive'. It looks like you're running a live session. If you create the bootable usb from tools like unetbootin it is not an installation into the usb, it just copies the iso to it basically so yes many operations won't work and it cannot hold more than 4  G of contents because of the limitation of the file system (regardless how big your thumb drive is) Try do a real install either into your internal hard drive, an external hard drive or a big enough thumb drive (usb flash drive will run slow though)

---

### Post by Kyle_Undercofler on 2014-03-30
I said installed FROM a thumb drive. Basically, we have a thumbdrive with Linux on it (as a backup), and my dad did the installation process to put Linux on my computer. And yes, it's on my internal hard drive.

---

### Post by monkeybrain20122 on 2014-03-30
This is odd. Not sure what your dad did. I always install from usb drives (who would still burns CDs???)  Never have a problem. 
But then how did you manage to install gimp if it cannot find the dependencies??

Maybe you haven't run updates after install? Try
```

sudo apt-get update && sudo apt-get upgrade 
&& sudo apt-get install --reinstall gimp
```

---

### Post by Kyle_Undercofler on 2014-03-30
I did install from a usb drive, though! And it's looking for an external drive. I don't get it. I need some way to make it install to my internal hard drive. EDIT: I'll try doing that. EDIT 2: still not working. I ran gimp in terminal and got the same error as I did the first time.

---

### Post by monkeybrain20122 on 2014-03-30
Open the dash, type software then when "Software and Update" shows up, go to the tab "unbuntu software". See if the box "Cdrom with Ubuntu .." is checked, if it is checked, **uncheck **it.

How did you install gimp?

---

### Post by Kyle_Undercofler on 2014-03-30
I'm so confused! When I type software in dash, the only thing I see is ubuntu software center! I tried installing gimp by using the softwar center, that didn't work, so I found some instructions online on how to install it with terminal, and then it didn't work, so uninstalled it from software center and installed it again from software center. There.

---

### Post by monkeybrain20122 on 2014-03-30
You can access "Software and Updates" from the Software Centre. When the software centre comes up, go to Edit > Software Sources.

---

### Post by Kyle_Undercofler on 2014-03-30
I just looked, and it's unchecked. No idea what to do now. As far as I know it's just a dead end, no gimp for me.

---

### Post by monkeybrain20122 on 2014-03-30
Check this [http://ubuntuforums.org/showthread.php?t=1974266](http://ubuntuforums.org/showthread.php?t=1974266)

---

### Post by Kyle_Undercofler on 2014-03-30
Just remembered the gimp I installed originally is 2.6 or something like that. Not 2.8. Anyway, checking the link. EDIT: Oh my god. You did it! It's working! Thank you so much, sir! Now then, how does one mark a post as solved?

---

### Post by bill17 on 2014-10-11
libgegl-sc-0.3.so was the complaint, for me, it happened when I upgrade from gimp 2.8 to experimental 2.9, when I googled everyone said ;reinstall gimp' but that's like throwing the baby oiut with the bthwater. So somewhere in the upgrade the link from ldconfig to the shared object file wwas broken, there were a number of options to fix this, however for simplicity, apt-get install libgegl* libbabl* worked for me, literally.

---

