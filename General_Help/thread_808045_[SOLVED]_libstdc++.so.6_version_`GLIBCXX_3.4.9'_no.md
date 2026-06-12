---
title: "[SOLVED] libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by libqscim.so)"
date: 2008-05-26
forum: General Help
---

### Post by Zorael on 2008-05-26
So I've been trying to get OpenOffice to accept SCIM (and by extension, Japanese) input **under KDE** for a while now, with no mentionable success. Installing the KDE extensions from the openoffice.org-kde package makes it completely ignore SCIM hotkeys, and manually selecting languages via the tray icon doesn't change what characters are sent to OO.o. It works in all other programs, with the sole and only exception being OpenOffice with the KDE extensions. Replacing the KDE extensions with the Gnome ones (openoffice.org-gnome package) makes SCIM work, but OpenOffice becomes unusable. All the icons under the menu bar in the writer disappear upon mouseover, for instance.

This *only* happens without the Gnome extensions.

I figured it might be something with the version available from our repositories, so I downloaded the latest 2.4.0 version from openoffice.org, with the same results. Now I'm trying with the 3.0.0 beta (300_m2), which doesn't work either. BUT, it output something interesting to the terminal when I open up a text document.
```
/opt/openoffice.org3/program/../basis-link/ure-link/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/qt3/plugins/inputmethods/libqscim.so)
```

GLIBCCX is related to gcc, isn't it? Has it been compiled with an outdated version of it? Would compiling it myself help?

---

### Post by Zorael on 2008-05-27
Well, problem circumvented by actually *fixing* the system to use scim in XIM-dependent programs. My [FONT="Courier New"]/etc/X11/xinit/xinput.d/skim[/FONT] file, which was chosen as the alternative for [FONT="Courier New"]/etc/alternatives/xinput-all_ALL[/FONT], was *incomplete*. I didn't have the option to choose scim or scim-bridge instead. That likely would've fixed the issue straight-away, since I only have scim installed because skim pulled it as a dependency.

The top of said skim file read:
```
XIM=SCIM
**XIM_PROGRAM=" "**
```
Obviously, the latter line worried me, since all guides and howtos I've read says to modify scim and/or scim-bridge to say the following:
```
XIM=SCIM
[B]XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes[/B]
```
So I modified it thus, logged out, did a /etc/init.d/kdm restart, and everything now works.

Tagging as solved.

---

### Post by hongleong on 2008-11-10
My error message is slightly different from yours:

[SIZE="1"]> (soffice:8588): Gtk-WARNING **: /opt/openoffice.org3/program/../basis-link/ure-link/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so)

(soffice:8588): Gtk-WARNING **: Loading IM context type 'scim' failed
[/SIZE]Maybe that's why your solution didn't work for me.

Here's the solution that works for me:

> cd /opt/openoffice.org3/basis-link/ure-link/lib

sudo mv libstdc++.so.6 libstdc++.so.6.orig
sudo ln -s  /usr/lib/libstdc++.so.6.0.9 libstdc++.so.6

sudo mv libgcc_s.so.1 libgcc_s.so.1.orig
sudo ln -s /lib/libgcc_s.so.1

Hope this helps those suffering from the same issue.

If anyone knows of a better solution, please share. :)

---

### Post by Kleenux on 2009-02-22
hongleong your post is worth gold. Thanks a lot!

Why did the O/O guys forced such libs in their distrib is a mystery...
Renaming them (don't need to [and better not] create the links actually, on intrepid) solves this long known scim problem.```
sudo mv libstdc++.so.6 libstdc++.so.6.orig
sudo mv libgcc_s.so.1 libgcc_s.so.1.orig
```

No more "Thanks" button?

---

### Post by hongleong on 2009-02-23
Thanks paris-unmatch. I deleted the links and it still works fine. Yep, I think yours is a better solution. :)

---

### Post by barghest on 2009-03-08
**hongeong** and **paris-unmatched** thank you very much for this tip. renaming the two libraries worked perfectly for me. I guessed by the error message that linking to the library in my /usr/lib directory would work but the GLIBCXX_3.4.9 part of it made me unceirtain...
but the solution with just renaming the files in the OO directory is realy neat. thank you so much again

---

### Post by nutsy.ben on 2010-07-09
Honestly between the different forums and explanations. I never found a working method.
I can admit that this is mostly my fault, but if someone also have the problem here is the solution from Matthias Kell. The only one that worked for me after struggling for a week:

My error was:
 usr/local/matlab2008/sys/os/glnxa64/libstdc++.so.6: version  `GLIBCXX_3.4.9' not found 

The solution
In the directory $MATLAB/sys/os/glnxa64 (make a backup before you  start to change things) do the following: 
 
Delete the these  libs (first one is a symlink to the second) 
 
# **rm  libstdc++.so.6       **
 # **rm libstdc++.so.6.0.3 **
 
Then  subsitute the last two by the current ones used by gcc (copy or  symlink).  I found them in /usr/lib: 
 
# **ln -s  /usr/lib/libstd*** . 
 
Then, remove Matlab's libgcc_s.so.1 
 
# ** rm libgcc_s.so.1 **
 
And copy (or make a symlink) to the OS's  current one (I found it in /lib) 
 
# **ln -s /lib/libgcc_s.so.1 **.

---

### Post by dubious5 on 2011-06-02
Thanks hongeong and paris-unmatched! I used the same method for a similar problem, except used "libstdc++.so.6.0.14" instead of "libstdc++.so.6.0.9"

This was the error while running a simulation in Xilinx...

opt/Xilinx2/13.1/ISE_DS/ISE/bin/lin/ise
/usr/lib/firefox-4.0.1/firefox-bin: /opt/Xilinx2/13.1/ISE_DS/ISE//lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/firefox-4.0.1/libxul.so)
/usr/lib/firefox-4.0.1/firefox-bin: /opt/Xilinx2/13.1/ISE_DS/ISE//lib/lin/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /usr/lib/firefox-4.0.1/libxul.so)

...which was solved with this;

cd opt/Xilinx2/13.1/ISE_DS/ISE/lib/lin
sudo mv libstdc++.so.6 libstdc++.so.6.orig
 
sudo ln -s /usr/lib/libstdc++.so.6.0.14 libstdc++.so.6

---

### Post by profgus on 2011-06-13
Thanks dubious5, hongeong, and paris-unmatched!

Got the same error in Xilinx ISE "Errors" and "Warning" hyperlinks.
Almost exactly the same solution (only changes are in first line):

cd /opt/Xilinx/13.1/ISE_DS/ISE/lib/lin64
 sudo mv libstdc++.so.6 libstdc++.so.6.orig
  
 sudo ln -s /usr/lib/libstdc++.so.6.0.14 libstdc++.so.6 	




"
Dubious5 said:
...which was solved with this;

cd opt/Xilinx2/13.1/ISE_DS/ISE/lib/lin
sudo mv libstdc++.so.6 libstdc++.so.6.orig
 
sudo ln -s /usr/lib/libstdc++.so.6.0.14 libstdc++.so.6
"

---

### Post by tommpogg on 2011-07-18
Thank you guys.

The commands
```

cd *xilinx_path*/ISE_DS/common/lib/lin64
 sudo mv libstdc++.so.6 libstdc++.so.6.orig
 sudo ln -s /usr/lib/libstdc++.so.6.0.14 libstdc++.so.6

```
also solved my problem.
After installing Xilinx ISE I could not open an html file by using the terminal. Indeed, the following error was displayed:
[INDENT]/usr/lib/firefox-5.0/firefox-bin: *xilinx_path*/ISE_DS/common/lib/lin64/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/firefox-5.0/libxul.so)
[/INDENT]But now, everything is back to normality

---

### Post by 2eagle2 on 2011-07-29
Hi I also replace libstdc++.so.6 with link to libstdc++.so.6.0.14
but after that I get segmentation fault - any ideas ??

---

### Post by gokhanyucel on 2011-09-28
Guys i have that problem too. I cannot do anything about on my computer but open terminal. I tried some of the  solutions but nothing changed. And even it's not my computer, could u help me pls? Can i fix it with open with LiveCD and changing some files?

---

### Post by comascii on 2012-02-14
A little bit late, but thanks guys!

```
cd /opt/Xilinx/12.3/ISE/lib/lin
sudo mv libstdc++.so.6 libstdc++.so.6.orig
sudo ln -s /usr/lib/libstdc++.so.6.0.14 libstdc++.so.6
```
 
worked properly for me!

Thanks again

---

### Post by swissz on 2012-04-10
> **nutsy.ben said:**
> Honestly between the different forums and explanations. I never found a working method.
I can admit that this is mostly my fault, but if someone also have the problem here is the solution from Matthias Kell. The only one that worked for me after struggling for a week:

My error was:
 usr/local/matlab2008/sys/os/glnxa64/libstdc++.so.6: version  `GLIBCXX_3.4.9' not found 

The solution
In the directory $MATLAB/sys/os/glnxa64 (make a backup before you  start to change things) do the following: 
 
Delete the these  libs (first one is a symlink to the second) 
 
# **rm  libstdc++.so.6       **
 # **rm libstdc++.so.6.0.3 **
 
Then  subsitute the last two by the current ones used by gcc (copy or  symlink).  I found them in /usr/lib: 
 
# **ln -s  /usr/lib/libstd*** . 
 
Then, remove Matlab's libgcc_s.so.1 
 
# ** rm libgcc_s.so.1 **
 
And copy (or make a symlink) to the OS's  current one (I found it in /lib) 
 
# **ln -s /lib/libgcc_s.so.1 **.


Thanks a lot nutsy.ben! I also had a similar problem with MATLAB, an this helped!

---

### Post by ramnath123 on 2012-10-15
Thanks - It worked for me too

---

