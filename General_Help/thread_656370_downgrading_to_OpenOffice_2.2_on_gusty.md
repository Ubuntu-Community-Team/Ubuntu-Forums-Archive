---
title: "downgrading to OpenOffice 2.2 on gusty"
date: 2008-01-02
forum: General Help
---

### Post by dcolombara on 2008-01-02
Gutsy repositories only have OpenOffice 2.3.0.

I need to use OpenOffice 2.2.0 which is available in Feisty's repository. Due to a bug in 2.3, which has been confirmed with the OpenOffice folks, I cannot use it with Cambodian (Khmer Unicode). This has nothing to do with the many other problems users are having with 2.3.0 and I have been told it will not be fixed until the next release. 

I thought about adding the repository for Feisty to my software sources list but came across[ another thread]("http://ubuntuforums.org/showthread.php?t=575061") in these forums which warned against it.

So, the questions is, " What is the easiest way to install OpenOffice 2.2.0 on Gutsy?"

My inclination is to remove OpenOffice 2.3. Then add the cd from the Feisty install to my software list and install OpenOffice 2.2 from there. Then, when I'm done, I'll remove the CD. That way I avoid the problems of having an "open" repository for a different release. Any thoughts on this?

Thanks in advance!

---

### Post by ~LoKe on 2008-01-02
You could add the Feisty repository, but make sure you don't do "sudo apt-get upgrade".  Just try:
```
sudo apt-get install openoffice.org
```
Then remove the repository, go into synaptic and lock the openoffice package.  Then you can apt-get update && apt-get upgrade all you want.

---

### Post by p_quarles on 2008-01-02
> **~LoKe said:**
> You could add the Feisty repository, but make sure you don't do "sudo apt-get upgrade".  Just try:
```
sudo apt-get install openoffice.org
```
Then remove the repository, go into synaptic and lock the openoffice package.  Then you can apt-get update && apt-get upgrade all you want.
That would still install the newest version of OpenOffice.org (i.e., 2.3). 

Two ways to do this:
1) Add the Feisty repos as a non-default source. This involves doing the following:
-- Create a file called /etc/apt/apt.conf and place the following line in it:
```
APT::Default-Release "gutsy";
```
-- Add the Feisty main repository to your sources.list.
-- To install a Feisty package, you would now run this:
```
sudo apt-get install -t openoffice.org
```
2. (the easy way) Grab the .deb from Ubuntu Packages:
[http://packages.ubuntu.com/feisty/editors/openoffice.org](http://packages.ubuntu.com/feisty/editors/openoffice.org)

---

### Post by dcolombara on 2008-01-02
Thanks for the quick replies!

I'm currently trying p_quarles' first method (adding feisty repos as non-default source). I tried the "easy" method but the .deb file that downloaded was too tiny to be the software I wanted so I guess I couldn't find the proper download. 

Regardless, following the first method:
1) I completely uninstalled OpenOffice 2.3.0
2) I created the apt.conf file as stated above
3) I added the Feisty main repository to my source.list
... up to here everything seems fine. 

But then, when I tried step 4, which is installing the Feisty package, I got the following:
     M45:~$ sudo apt-get install -t openoffice.org
     Reading package lists... Done
     Building dependency tree       
     Reading state information... Done
     0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I then tried using Synaptic Package Manager. If I select the OpenOffice.org metapackage, the default is 2.3.0 but, if I select it, then go to "Package >> Force Version", I can select "2.2.0-1ubuntu3 (feisty)". Unfortunately, all the component parts don't follow suit (meaning the remain 2.3.0). 

So, I've disabled all repositories except for Feisty. Now all the component parts are also 2.2.0. My plan is, after downloading it overnight, to Lock Version 2.2.0, then disable the Feisty repository, then enable the my normal Gutsy repos. 

Please give a heads up if I'm going to cause some problems down the road this way.

---

### Post by dcolombara on 2008-01-02
Whatever I did, it didn't work. 

After installing all 2.2.0 components and Locking them in that version, I tried running the OpenOffice. 

When I clicked on the icon, a window popped up for 2.2 and it seemed as if it were loading properly. Unfortunately the program froze (but didn't freeze the system). 

I used force quit to kill it, restarted and then tried again with command line. It didn't work again. Here is the error message ... 
[INDENT]me@M45:~$ oocalc

(process:8820): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.14.1/gobject/gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:8820): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:8820): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

me@M45:~$[/INDENT]

Any suggestions?

---

### Post by p_quarles on 2008-01-02
D'oh! #-o

I left out a rather important part of that fourth step. It should be:
```
sudo apt-get install -t feisty openoffice.org
```
Sorry about that. Anyway, if you want to try to undo the other stuff, that still might be worth a shot. 

I kind of doubt it will work any better than what you did, though. From the error output you got, I'm guessing that Gutsy's glibs are just incompatible with OOo 2.2.

---

### Post by dcolombara on 2008-01-05
Thanks again for the feedback.

I undid all of my steps then followed your command line instructions. 

I have the same exact problem that I did with my method. 

In desperation I tried to install OOo 2.2 for Windows with WINE. I didn't work and now I can't uninstall it. Bummer. 

Anyway, for now I quit. I'll get rid of the Feisty repo in my sources list and put 2.3 back as normal. 

Thanks for your efforts to help me out.

---

