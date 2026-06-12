---
title: "Questions about Ubuntu/Linux"
date: 2007-01-22
forum: General Help
---

### Post by Torajima on 2007-01-22
I'm a Mac user, but one with a lot of Windows experience (too much!) and a bit of unix (AIX) experience as well. I guess I'm definitely a "power user". For various reasons I'm considering buying a Linux based laptop. But I've got a few questions first:

1. What kind of scripting is available on linux? I use Applescript all the time, both to automate repetitive tasks and to create simple applications. I know a bit about UNIX shell scripting, but can these scripts be saved as an application (execute when you click on them) and shared with other users?

2. Is Python the best choice if I want to try to create more advanced applications (with dialog boxes, pretty graphics, etc)? I'm also considering RealBasic.

3. On the Mac, Applications are in the Application folder and are actually packages rather than a single file... you can right click on them to edit the contents (such as change splash screens and other graphics used by the program). Can you "hack" Linux apps the same way? Everything is in /usr/bin, correct?

4. Is there a good Linux equivalent to Dashboard Widgets? I tried gdesklets... they seemed kinda buggy.

5. Once the proper video codecs are installed, will both quicktime and WMV work? I've never been able to get WMV to work properly on my mac.

6. What kind of specs does a PC need to run Ubuntu at a good clip? These days, you really need at least a gig of RAM and a dual processor to make OSX happy... I'm guessing Linux needs less. I mostly want to run VLC, Inkscape, Gimp, NeoOffice, and internet apps. Will probably install Compiz as well.

Thanks!

---

### Post by allwin on 2007-01-22
I use a different non Linux OS on a laptop.  In my experience trying Linux distros, I think you may be asking the wrong questions!  You might want to consider whether the whole battery power management business works (suspend, resume, etc, things spinning down), whether your touchpad will work, or whether wireless is going to work;  whether attached web cams work, and things like that.  On point 3, while I'm not an expert, not "everything" is in /usr/bin.  A lot of what you need to do is spread all over /etc/ and ~, and some customization requires recompiling from source.  On point 5, yes, I have gotten .mov and .wmv working ok.  In UBUNTU, a lot of issues are solved by installing AUTOMATIX, which is a package that's located in a different repository out there and maintained by another group apparently.

If you are going to run COMPIZ, you also need to worry about getting just the right video driver for your situation.  nVidia and ATI both have various kinds of troubles and can be troublesome to get working as you'll see by these forums.

---

### Post by Torajima on 2007-01-22
I'm not concerned with getting the hardware to work, because if I decide to buy a Linux based laptop I'll get it from System76... preinstalled with Ubuntu and guaranteed to work out of box!

---

### Post by 23meg on 2007-01-22
> 
1. What kind of scripting is available on linux? I use Applescript all the time, both to automate repetitive tasks and to create simple applications. I know a bit about UNIX shell scripting, but can these scripts be saved as an application (execute when you click on them) and shared with other users?If by "application" you mean something with a graphical interface, yes, you can use things like Zenity for that purpose.
> 2. Is Python the best choice if I want to try to create more advanced applications (with dialog boxes, pretty graphics, etc)? I'm also considering RealBasic.It's up to you to decide whether it's the best choice for your purpose, but Python is pretty good and is used a lot. I suggest you also take a look at the FreePascal + Lazarus combination.
> 
3. On the Mac, Applications are in the Application folder and are actually packages rather than a single file... you can right click on them to edit the contents (such as change splash screens and other graphics used by the program). Can you "hack" Linux apps the same way? Everything is in /usr/bin, correct?You can hack Linux apps far more. Packages will install files all over your system, not just /usr/bin, which is where the executable files themselves will usually go.> 
4. Is there a good Linux equivalent to Dashboard Widgets? I tried gdesklets... they seemed kinda buggy.Also see Superkaramba, Adesklets and Jackfield, which it seems will let you run Dashboard widgets as well.
> 
5. Once the proper video codecs are installed, will both quicktime and WMV work? I've never been able to get WMV to work properly on my mac.Both will work.
> 6. What kind of specs does a PC need to run Ubuntu at a good clip? These days, you really need at least a gig of RAM and a dual processor to make OSX happy... I'm guessing Linux needs less. I mostly want to run VLC, Inkscape, Gimp, NeoOffice, and internet apps. Will probably install Compiz as well.Roughly 512 MB RAM and a  recent 1Ghz processor will do.

---

### Post by Torajima on 2007-01-22
> **23meg said:**
> If by "application" you mean something with a graphical interface, yes, you can use things like Zenity for that purpose.

By application I mean something that executes when clicked on. But Zenity looks interesting (similar dialog boxes to Applescript)... I'll have to check it out.

> **23meg said:**
> 
It's up to you to decide whether it's the best choice for your purpose, but Python is pretty good and is used a lot. I suggest you also take a look at the FreePascal + Lazarus combination.


I want to learn a language that's simple to learn, relatively fast, and at least somewhat similar to the two languages I currently know... Applescript and the original BASIC. Python might fit the bill... what I've seen so far, I can generally make sense of it. Less so with Pascal, and c++? I might as well be reading Chinese...

> 
You can hack Linux apps far more. Packages will install files all over your system, not just /usr/bin, which is where the executable files themselves will usually go.


Ah, so Linux is more like Windows then... lots of little files everywhere? I assume there are logs to show where everything was placed?

> 
Also see Superkaramba, Adesklets and Jackfield, which it seems will let you run Dashboard widgets as well.


I couldn't get Adesklets to work under the LIVE CD, but Jackfield looks promising...

> 
Roughly 512 MB RAM and a  recent 1Ghz processor will do.

OK, thanks!

---

### Post by 23meg on 2007-01-22
> By application I mean something that executes when clicked on. But Zenity looks interesting (similar dialog boxes to Applescript)... I'll have to check it out.Sure, you can just double click on a script to execute it. Remember to make it executable.> Ah, so Linux is more like Windows then... lots of little files everywhere? I assume there are logs to show where everything was placed?To see where files from a certain package are installed, go to its properties in Synaptic and look at the "Installed Files" tab.> I couldn't get Adesklets to work under the LIVE CD, but Jackfield looks promising...Try again when you do an install.

---

### Post by ardchoille42 on 2007-01-22
> 
1. What kind of scripting is available on linux? I use Applescript all the time, both to automate repetitive tasks and to create simple applications. I know a bit about UNIX shell scripting, but can these scripts be saved as an application (execute when you click on them) and shared with other users?


You can look into scripting with bash, python, perl, ruby and a few others. I do bash scripting all the time and am learning python and perl at the moment.


> 
2. Is Python the best choice if I want to try to create more advanced applications (with dialog boxes, pretty graphics, etc)? I'm also considering RealBasic.


You can do GUI programming with python and perl. There may be others, but I don't know. You can design the GUI's with glade and then use a scripting language for the code. That's why I like python and perl so much :) I am told that you can use the same GUI (designed in glade) for python, perl, ruby, C/C++ apps.


> 
3. On the Mac, Applications are in the Application folder and are actually packages rather than a single file... you can right click on them to edit the contents (such as change splash screens and other graphics used by the program). Can you "hack" Linux apps the same way? Everything is in /usr/bin, correct?


Lots of Linux apps are written in C/C++ while some are written in python. You can learn C/C++ to write your own apps or you can open python or perl scripts in a text editor and hack away.. if you know what you're doing ;)


> 
4. Is there a good Linux equivalent to Dashboard Widgets? I tried gdesklets... they seemed kinda buggy.


I believe what you are talking about would be superkaramba (KDE) or gdesklets (gnome) in Ubuntu. I have used KDE apps in gnome and gnome apps in KDE with no noticable problems.


> 
6. What kind of specs does a PC need to run Ubuntu at a good clip? These days, you really need at least a gig of RAM and a dual processor to make OSX happy... I'm guessing Linux needs less. I mostly want to run VLC, Inkscape, Gimp, NeoOffice, and internet apps. Will probably install Compiz as well.


I have 11 computers. The fastest one us a P4 3Ghz with 2Gb ram. Ubuntu really flies on that one. The slowest one is a P3 with 256Mb ram. gnome is kinda slow on that one so I use a light window manager instead of a full desktop. Fluxbox, openbox, blackbox and Window Maker are good for this. You might also be interested in using XUbuntu - which uses the XFCE desktop. You can find a good list of window managers [here]("http://xwinman.org/").

---

