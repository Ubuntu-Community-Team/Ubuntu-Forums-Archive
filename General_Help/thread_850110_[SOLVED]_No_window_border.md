---
title: "[SOLVED] No window border"
date: 2008-07-05
forum: General Help
---

### Post by thefishki345 on 2008-07-05
Hi,

I recently have ran into a problem, which for some reason all my windows (firefox, synaptic, terminal etc) do not have borders. If anyone has a solution to this problem I would greatly appreciate it because it is rather annoying

attached image is what it looks like: (look at the top)

---

### Post by Gunman1982 on 2008-07-05
Such behavior can be a problem with compiz. Had this some times and fixed it by installing the fusion-icon and compizconfig-settings-manager (if I remember right). Then start fusion icon (should appear in your panel) right click on it and play around with the window decorator settings or reload window manager. If nothing helps you can turn of compiz by choosing 'select window manager' and then selecting metacity.

you can install the packages by switching to terminal 1 (ctrl+alt+F1) log in as normal user and type in 'apt-get install fusion-icon compizconfig-settings-manager'.

---

### Post by nikgare on 2008-07-05
Your window manager has crashed.
The easiest way to restart it is to go to System-Prefences->Appearance and under the visual effects tab, change the button there.

---

### Post by thefishki345 on 2008-07-05
ok thanks guys, I am going to try both, and i think this has happened just after I upgraded compiz...

---

### Post by thefishki345 on 2008-07-05
When I turn off compiz the window borders come back, so its a problem with compiz. But does anyone know how I revert to an earlier version of compiz? and gunman 1982 I did what you said but it didnt do anything I dont think...

---

### Post by sdennie on 2008-07-05
It's probably not a problem with compiz.  Try:

```

glxinfo | grep direct

```

If it says direct rendering is not enabled and you aren't using the normal nvidia-glx-new drivers from Ubuntu, it probably means that a package has clobbered your OpenGL libraries (probably xserver-xorg-core) and, you'll need to reinstall your drivers.

---

### Post by thefishki345 on 2008-07-06
Nope, it says it is enabled. but thanks anyway. anyother ideas?

---

### Post by overdrank on 2008-07-06
> **thefishki345 said:**
> Nope, it says it is enabled. but thanks anyway. anyother ideas?

Hi and have you checked in CCSM advance desktop settings to ensure that window decoration is checked?

---

### Post by thefishki345 on 2008-07-06
Yes I have and it is.

---

### Post by danwood76 on 2008-07-06
Do you have emerald installed?

Emerald is the alternative window decorator that comes with compiz, normally ubuntu uses metacity window decorations.
It could be that for some strange reson compiz is trying to use emerald when its not installed.

You could try installing emerald and installing some themes to see if it helps.

---

### Post by thefishki345 on 2008-07-06
Thanks, but I do have emerald installed, but I dont use it I dont think.

---

### Post by overdrank on 2008-07-06
> **thefishki345 said:**
> Thanks, but I do have emerald installed, but I dont use it I dont think.

ok then for grins  use the alt, F2 keys and enter ```
emerald --replace
```

---

### Post by thefishki345 on 2008-07-06
thanks lol, it gives window borders, but in the wrong colour and theme, and only works until I close the terminal (alt+f2 didnt do anything so I used a terminal...was I meant to do that?)

---

### Post by hamzaB on 2008-07-06
open "sessions" and add the command :emerald --replace.log out and in .hope that fixes your problems.

---

### Post by thefishki345 on 2008-07-06
Thanks, did that but it just gave me a red window border, which is not part of my theme...

---

### Post by overdrank on 2008-07-06
> **thefishki345 said:**
> Thanks, did that but it just gave me a red window border, which is not part of my theme...

Hi and you can use emerald theme manager to change the theme. Located under system, preference.

---

### Post by esmtll on 2008-07-06
I'm having the same problem.  Same dud solutions.  Both 7.04 and 7.10
It happens when switching from Emerald-based desktop to compiz (from "None" Effects to "Normal" "Extra" or "Custom" Effects

just for reference: nVidia graphics 7.10

---

### Post by danwood76 on 2008-07-07
to go back from emerald type:
```

metacity --replace

```

If this doesnt bring back the borders I would say that there is something wrong with your installed theme.

---

### Post by esmtll on 2008-07-07
Yes, I can get the borders to return if I go back to metacity.  But I would much rather get compiz working properly.  And I'd much rather see this solution fixed now that I know I'm not the only one.  

Is there any suspicion that this is a problem with compiz/nVidia drivers?

---

### Post by danwood76 on 2008-07-07
It might just be that the window decorator is set wrong in compiz.

Make sure you have the compiz control center installed, open it up and make sure 'Window Decoration' is set, without this your windows wont have borders.

You used to be able to switch netween the window managers but im not 100% sure how you do this now.
You want to try and set compiz to use metacity, or you could find a good theme for emerald, I find the emerald themes look a lot nicer anyway.

---

### Post by AmericanYellow on 2008-07-07
By any chance did you install compiz and compiz fusion from the GIT repository of Compiz Fusion main website? If you did, did you use the script that was made in the compiz forums?

If you did, all you have to do is to run the fusion icon and it will fix all your problems. If you have the fusion icon installed, make sure it  loads every session by adding it to "Sessions" using 'fusion-icon'.

---

### Post by thefishki345 on 2008-07-07
I ran fusion Icon and selected metacity as window manager, but then that means I cant use compiz...

So that means there is a problem in compiz. and I think I installed it from the git repository. 

Thanks for all your help. But Maybe the easiest way would be to revert to the previous version of compiz I was using before (which gave me window borders) does anyone know how to do that?

---

### Post by cszikszoy on 2008-07-07
This used to happen to me.  Pressing Alt + F2 (which brings up the run dialog) and typing "compiz --replace && emerald -- replace" used to fix everything for me.  If you type this in a normal terminal window they will all go away when you close the terminal window again.  You have to type this in the run dialog box.

---

### Post by thefishki345 on 2008-07-07
thanks, but when I press alt f2 it doesnt do anything...

EDIT: even when I typed it in terminal it didnt do anything and gave this output:

[Output]compiz --replace && emerald -- replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0600 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_border_picture
gtk-window-decorator: symbol lookup error: gtk-window-decorator: undefined symbol: decor_blend_border_picture
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


[/Output]

---

### Post by angry_johnnie on 2008-07-07
Have you tried

```
gtk-window-decorator --replace & disown
```

from a terminal?

You should get your normal window borders, without losing compiz.  Adding **& disown** at the end of a command, will allow it to continue running after you close the terminal.

---

### Post by thefishki345 on 2008-07-07
thanks for that, but this is what I get as an output and nothing happens:

[output]
gtk-window-decorator: symbol lookup error: gtk-window-decorator: undefined symbol: decor_blend_border_picture [/output]

---

### Post by thefishki345 on 2008-07-07
Hi, thanks for that, but when I run it this is what I get as an output:

```
gtk-window-decorator: symbol lookup error: gtk-window-decorator: undefined symbol: decor_blend_border_picture
```

---

### Post by danwood76 on 2008-07-07
Run the gconf editor and delete the key that is causing it issues.

So press alt+f2 (or run in terminal) and type:
```

gconf-editor

```

Then navigate to:
/apps/compiz/plugins/scale/allscreens/options/initiate_edge
And delete what it says 'decor_blend_border_picture'

---

### Post by thefishki345 on 2008-07-07
thanks danwood, but when I go to:
/apps/compiz/plugins/scale/allscreens/options/initiate_edge
and click on initiate_edge it opens up a window where I can edit values in it, and it has no values in it anyway...

---

### Post by danwood76 on 2008-07-07
You could always try and reinstall compiz.

Open up synaptic and search for compiz, you want to right click compiz-core and completely remove.
This will remove all compiz and the settings associated with it.

Then search compiz again and reinstall the packages you just removed.

---

### Post by cszikszoy on 2008-07-07
Also, if you go to system > preferences there should be a menu item that lets you set gnome related keyboard shortcuts.  Find the one that says run command, or something similar (i forget what it says) and set it to alt + f2.  This should be the default, not sure why it doesn't work for your machine.

---

### Post by StumpyMcDonut on 2008-07-07
I had a problem a while back with alt+f2 being touch-and go.
With gnome, right click on a blank bit of the menu bar go to "add to panel" and choose "Run application" from the menu - it brings up the same menu as alt+f2 would (although you should really try and get the shortcut working).
Then open up emerald, click the theme you want so that its highlighted, click on that shortcut you just added and run emerald --replace from the box, the effect should stay this time.

---

### Post by thefishki345 on 2008-07-07
Danwood76: I completely removed and reinstalled compiz, logged out and back in, but still no window borders.

cszikszoy: I couldnt find the run application thing in gnome keyboard shortcuts. But its Okay.

StumpyMcdonut: I have done that, so thanks.

all this still doesnt resolve the issue :( maybe I could run my standard theme (custom ubuntustudio style theme) in emerald, if I could find out where custom themes are kept...does anyone know?

---

### Post by danwood76 on 2008-07-07
I dont think you can directly convert metacity themes to emerald, it may take a bit more work than that.
There are loads of themes with emerald and you can customise them far better than with metacity.

I would have a play with emerald if I were you, you can get the default ubuntu theme for it and then customise it the same as your theme.
You may need to download the emerald themes from the compiz site or I think there might be a download section within emerald.

---

### Post by thefishki345 on 2008-07-07
Ok, but I have kind of grown attached to my ubuntu studio theme :(

---

### Post by danwood76 on 2008-07-07
The theme will still be the same as you have when running compiz its just the window decoration that will change.

Im not sure what your theme looks like but I found this on GNOME-Look:
[http://www.gnome-look.org/content/show.php/UbuntuStudio+Emerald?content=59198](http://www.gnome-look.org/content/show.php/UbuntuStudio+Emerald?content=59198)

---

### Post by esmtll on 2008-07-07
I found a solution using [Envy ]("http://albertomilone.com/envyngfaq.html")  Seems it was a Graphics driver problem.

---

### Post by thefishki345 on 2008-07-07
I dont think its a driver problem, and danwood, I downloaded that theme and imported it to emerald before, but how do I actually activate it? because it doesnt change from any metacity theme.

---

### Post by syahid_zul on 2008-07-07
try this
go to ccsm > window decoration > command
put = /usr/bin/compiz-decorator

or..

press alt+f2

put metacity --replace

---

### Post by thefishki345 on 2008-07-07
syahid_zul, in ccsm the command didnt do anything :(

and metacity replace works, but then I get no compiz :(

---

### Post by cszikszoy on 2008-07-08
if the metacity --replace works,

try doing compiz --replace && emerald --replace.

That should enable compiz and emerald.

---

### Post by thefishki345 on 2008-07-08
thanks, but I tried that, and tried it again but it didnt do anything. :(
this is really annoying as so far I have tried:

all the commands you guys have helpfully given me (compiz replace etc)
completely reinstalling and uninstalling compiz
upgrading compiz from git
and everything else all the people here have kindly suggested,
yet, I still get no window borders :(

I think the only way I can do this is if I go back to my earlier version of compiz, as I think the newer version is giving me problems with window border etc. Does anyone know how do go back to an earlier version of compiz (or the original one in the ubuntu repos before  I upgraded/replaced it) ?

EDIT: should I remove all the compiz fusion stuff in my filesystem aswell???
as maybe the reason why it is screwing up was cos I think I might of installed another version of compiz while the synaptic one was still there :( oh-oh...

---

### Post by danwood76 on 2008-07-09
In a previous post you said that emerald gave you window borders (doing emerald --replace) why not just use emerald?

You can control the themes and settings from the emerald control panel (may need to install it if you havent already)

---

### Post by thefishki345 on 2008-07-09
Thanks for all your help guys, but all I did was this:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/) Which deleted all gnome etc config things. Then I just reset my theme, and added the ¨window border"tick in compiz settings (as it wasnt checked once I reset gnome) and it all worked!!!!

yay! thanks for all your help guys and I hope that helps anyone else having problems with window borders!

---

### Post by thefishki345 on 2008-07-09
Crap, Now that I have just logged back in my windows borders arent there when I switch on compiz (even after adding window decoration setting to it) Because it doesnt seem to remember compiz, even when its added to sessions. I think im gonna use emerald, but I am yet to find a good emerald theme... I will keep looking.

---

### Post by oneafrikan on 2009-05-20
Thanks guys, this has helped a lot!!!

[http://www.oneafrikan.com/archives/2009/05/19/jaunty-jackalope-upgrade-issues-evolution-window-decoration-workspace-switcher-alt-tab-not-working/](http://www.oneafrikan.com/archives/2009/05/19/jaunty-jackalope-upgrade-issues-evolution-window-decoration-workspace-switcher-alt-tab-not-working/)

---

