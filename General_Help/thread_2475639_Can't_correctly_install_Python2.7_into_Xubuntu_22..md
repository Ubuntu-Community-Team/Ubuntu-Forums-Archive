---
title: "Can't correctly install Python2.7 into Xubuntu 22.04 (needed for Pywo)"
date: 2022-06-02
forum: General Help
---

### Post by Ralph L on 2022-06-02
I have become very depended on Python Windows Organizer for managing my 15" laptop screen. It divides the screen into at least 9 areas (depending on how you count overlaps), and automatically fits windows into those areas using shortcut keys (I generally use "control" with the the 9 touchpad keys). Anyway I really want pywo installed. Pywo was written in 2010 using an older version of Python and will not run using Python3. It will run with Python2.7.
I installed Python2.7 using Synaptic. 
From previous installations of pywo I knew that I had to put a symbolic link into /usr/bin/ from "python" to "python2.7", so I did that. Pywo got an error message saying it could not find Xlib.
I ran through the path to Xlib (/usr/lib/python2.7/dist-packages/). Xlib wasn't there. In fact there were only 2 items in dist-packages, neither of them being Xlib. I checked dist-packages in xubuntu 18.04 and found it had a whole bunch of stuff including Xlib. I tried uninstalling python2.7 with synaptic (didn't uninstall everything) and I reinstalled it using a method outlined in [https://www.how2shout.com/linux/how-to-install-python-2-on-ubuntu-22-04-lts-jammy-linux/#](https://www.how2shout.com/linux/how-to-install-python-2-on-ubuntu-22-04-lts-jammy-linux/#) . Didn't help.
So I renamed dist-packages in 22.04 as dist-packages.old and copied the entire dist-packages folder from xubuntu 18.04 into 22.04. Now pywo ran and seems to work fine. I had to also put it in "Sessions and Startup" so it was launched at system startup.
My question is "why didn't the proper version of dist-packages get installed when I installed Python2.7"? Neither synaptic nor apt installed it correctly. While I got pywo to work this time, I may not be so lucky on future systems. Anybody know how to get Python2.7 installed correctly???  Its very important to me.

---

### Post by dragonfly41 on 2022-06-02
You can sometimes force usage of old legacy Python (or a particular version of Python) by inserting a shebang line at top of each Python script. Although there are other methods to force Python environments. 

```
#!/usr/bin/env python2
```

```
#!/usr/bin/env python3
```

But also there are other tiling grid tools I have used.

---

### Post by dragonfly41 on 2022-06-02
Here is one tool I have used.

[https://www.giuspen.com/x-tile/](https://www.giuspen.com/x-tile/)

---

### Post by #&amp;thj^% on 2022-06-02
> **dragonfly41 said:**
> Here is one tool I have used.

[https://www.giuspen.com/x-tile/](https://www.giuspen.com/x-tile/)

+1 I had forgotten that one, thanks for memory jog.
```
apt search X-tile 
Sorting... Done
Full Text Search... Done
x-tile/jammy,jammy 3.3-2 all
  tile selected windows in different ways

```

---

### Post by TheFu on 2022-06-02
My WM supports different workspaces natively.  The default is a 3x3, but I've downsized to a 3x1.  fvwm.

BTW, python2 is deprecated and there were a number of years of warnings about this, so any tool still using it has not been supported since 2020 and probably shouldn't be used.  [https://www.python.org/doc/sunset-python-2/](https://www.python.org/doc/sunset-python-2/)  Python2 was first released in 2000 - 20 yrs is a very long time for a language version to last. Even C++ has changed versions twice in that period.

> **What happens now?**
As of January 1st, 2020 no new bug reports, fixes, or changes will be made to Python 2, and Python 2 is no longer supported.


---

### Post by Ralph L on 2022-06-03
Thanks to everybody who responded. I appreciate the suggestion of x-tile. I will investigate that, if it is currently being maintained. 
Are there any other windows management programs that I might look at?????
 
The Fu: I realize that software like Python 2 gets old, but at this point I am stuck with Pywo, since I don't know of any other windows management software. What I had hoped was that somebody else had found a way to install Python 2 correctly. Synaptic still has it in its data base, but doesn't install the whole thing. There are several web sites that give instructions for installing it, but again it does not install the "dist-packages" folder correctly. I am just trying to find somebody who knows more than me, and has solved this problem. Also, you mentioned that you used a Windows Manager. If possible would you tell me what that software is???

---

### Post by TheFu on 2022-06-03
The trick with using deprecated scripting languages is to setup a "virtual environment" to use that specific version.  Python, Perl, Ruby, Php, and probably all the other major languages have a tool just for this.  It doesn't install via packages into /usr/bin/.  That would impact the primary system python and will likely break the system.  Python3 is used heavily in Ubuntu since 2020.  Using python2 is a 1-off solution, so it is smartest to keep that completely separate from the OS and where other users might accidentally find it.  
[https://realpython.com/python-virtual-environments-a-primer/](https://realpython.com/python-virtual-environments-a-primer/) explains virtual environments.
[https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/) is the "official" documentation for this.

I don't do python, but I use perl virtual environments. Exactly the same idea. perlbrew is the command to manage different perl versions.
```
$ perlbrew list
  perl-5.36.0                               
* perl-5.35.11                              
  perl-5.29.7          

```That shows for my userid, perl 5.35.11 is currently being used and 5.36.0 and 5.29.7 are also installed.
```
$ perlbrew use 
Currently using perl-5.35.11
```
Shows this too, as does ... 
```
$ which perl
/home/thefu/perl5/perlbrew/perls/perl-5.35.11/bin/perl
```
shows that the current perl program, before even the system perl is 5.25.11 for my userid.  See how it is in a version-specific sub-directory under perlbrew?  If I change to a different perl version, then **which perl** will point somewhere else.  To use the system perl, 
```
$ perlbrew off
perlbrew is turned off.
regulus:~$ which perl
/usr/bin/perl
```

I expect the exact same capabilities are there for python.

As for Window Managers ... you need to understand how Unix systems layer GUI libraries.  There's a diagram here: [https://en.wikipedia.org/wiki/File:Schema_of_the_layers_of_the_graphical_user_interface.svg](https://en.wikipedia.org/wiki/File:Schema_of_the_layers_of_the_graphical_user_interface.svg)  Until recently, all DEs were layered on top of a WM.  Only a few don't use a WM still.  It adds bloat IMHO, but we each like a certain amount of bloat to have a usable system. It is a very personal choice.  I got tired of the GUI massively changing with every release from Canonical, so I hopped off the GUI-change-for-no-good-reason-train and went back to using the extremely featured, customizable, fvwm that I first used in the mid-1990s. Since 2002, there have only been bug fixes.  It works at a lower level in the GUI stack and has few dependencies, besides X/Windows libraries and long-time Xm, Xt libraries which were stable in the early 1990s. Basically, it is the same now as it was then AND supported.  BTW, it uses perl for custom extensions, which I like. ;)

Openbox is a WM that LXDE used before they switched to LXQt. I don't know what they use now.  Openbox wasn't quite enough GUI for my needs, yet, because it uses more dependent libraries, it is more bloated than fvwm.

A list of Window Managers: [https://en.wikipedia.org/wiki/X_window_manager#Types_of_window_managers](https://en.wikipedia.org/wiki/X_window_manager#Types_of_window_managers)  I'd guess there are about 30 of them. Here's a comparison table [https://en.wikipedia.org/wiki/Comparison_of_X_window_managers](https://en.wikipedia.org/wiki/Comparison_of_X_window_managers)  The "graphical configuration" column is laughable, IMHO.  Can't people use an editor? If you want "graphical", then use a fancy graphical editor. ;)

---

