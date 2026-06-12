---
title: "Screen Shot"
date: 2016-03-17
forum: General Help
---

### Post by Jason_Hunter on 2016-03-17
When I click PrtScr, the whole screen flashes and I hear a snapshot camera sound, then nothing happens. Is something supposed to happen?

I would imagine it has taken a screen shot, but if I go into gimp and hit paste, it says nothing is in the clip board. 

What exactly is this button supposed to do?

I'm on GNOME on Ubuntu 15.10.

---

### Post by QDR06VV9 on 2016-03-17
Check in the desktop or pictures to see any new photos with .png format or ending.
Hope this is clear enough..
But yes it takes a screenshot of your desktop.

---

### Post by grahammechanical on 2016-03-17
It should produce a dialog box asking if you want to save the image. The default is the pictures folder. But there is a drop down menu where we can change the location. We can also copy the image to the clipboard.

This is on Ubuntu + Unity. But it is still Gnome Screenshot. So, it should work the same. We can also load gnome-screenshot from the Dash where we get dialog that gives us more control. Grub the whole screen (default); Grab the current window; Select area to grab.

Regards.

---

### Post by vasa1 on 2016-03-17
> **Jason_Hunter said:**
> When I click PrtScr, the whole screen flashes and I hear a snapshot camera sound, then nothing happens. Is something supposed to happen?

I would imagine it has taken a screen shot, but if I go into gimp and hit paste, it says nothing is in the clip board. 

What exactly is this button supposed to do?

I'm on GNOME on Ubuntu 15.10.

AIUI, "the whole screen" should _not_ flash.

How Linux deals with the clipboard isn't easy for me to explain.

The PrtScrn button is supposed to take a screenshot. How exactly it does it, depends on which program is set to do the actual work and the settings of that program.

---

### Post by Jason_Hunter on 2016-03-17
Ok, I get it; it just places the screen shot in images. 

However, before, it started gnome screenshot; I guess that is not default anymore?

---

### Post by yetimon_64 on 2016-03-18
> **vasa1 said:**
> AIUI, "the whole screen" should _not_ flash....Using gnome-screenshot on Unity (14.04) here. It flashes the whole screen for me.

> **Jason_Hunter said:**
> ...
However, before, it started gnome screenshot; I guess that is not default anymore?
When first installed, to get gnome-screenshot to use the save dialog and to save anywhere but in Pictures, I installed dconf-tools and set the "auto-save-directory" for gnome-screenshot to another location, in my case ~/Screenshots (a directory I made myself). 

The key to open in "dconf-editor" is org.gnome.gnome-screenshot; two subkeys you may want to set are auto-save-directory and last-save-directory (if you want different settings, I set "auto-save-directory" as Screenshots and "last-save-directory" as Desktop). 

You may need to install the "dconf-tools" package to use the "dconf-editor" command.

IIRC, to get the "save screenshot" box to come up initially I had to run gnome-screenshot in interactive mode from terminal with the auto-save-directory set where I wanted it to go manually in dconf-editor ... the command to use to get the save dialog is ...
```
gnome-screenshot -i
``` then after that any time I ran the "normal" screenshot the save dialog would pop up again. 

Like you, I would just get a screen flash and an automatic save to Pictures, but after tweaking the settings in dconf-editor and running it in interactive mode for the first run everything now works with the save dialog coming up and will save to where I want, not automatically to Pictures as was initially set up. 

Not sure if there are any major differences in the set up between gnome and unity and 14.04. and 15.10 but being the same package, gnome-screenshot, it may be worth trying the above procedure with dconf-tools and initially running gnome screenshot in interactive mode to bring up the save dialog. Hope it works for you.

Good luck, yeti.

---

### Post by vasa1 on 2016-03-18
> **yetimon_64 said:**
> Using gnome-screenshot on Unity (14.04) here. It flashes the whole screen for me.
...
You made me check again. It does flash! Even on Lubuntu's Openbox session.

---

### Post by vasa1 on 2016-03-18
> **yetimon_64 said:**
> Using gnome-screenshot on Unity (14.04) here. It flashes the whole screen for me.


When first installed, to get gnome-screenshot to use the save dialog and to save anywhere but in Pictures, I installed dconf-tools and set the "auto-save-directory" for gnome-screenshot to another location, in my case ~/Screenshots (a directory I made myself). 

The key to open in "dconf-editor" is org.gnome.gnome-screenshot; two subkeys you may want to set are auto-save-directory and last-save-directory (if you want different settings, I set "auto-save-directory" as Screenshots and "last-save-directory" as Desktop). 

You may need to install the "dconf-tools" package to use the "dconf-editor" command.

IIRC, to get the "save screenshot" box to come up initially I had to run gnome-screenshot in interactive mode from terminal with the auto-save-directory set where I wanted it to go manually in dconf-editor ... the command to use to get the save dialog is ...
```
gnome-screenshot -i
``` then after that any time I ran the "normal" screenshot the save dialog would pop up again. 

Like you, I would just get a screen flash and an automatic save to Pictures, but after tweaking the settings in dconf-editor and running it in interactive mode for the first run everything now works with the save dialog coming up and will save to where I want, not automatically to Pictures as was initially set up. 

Not sure if there are any major differences in the set up between gnome and unity and 14.04. and 15.10 but being the same package, gnome-screenshot, it may be worth trying the above procedure with dconf-tools and initially running gnome screenshot in interactive mode to bring up the save dialog. Hope it works for you.

Good luck, yeti.

@yeti, what is the purpose of "last-save-directory" in the context of gnome-screenshot (and generally)?

===================================================

I installed *gnome-screenshot* using *--no-install-recommends*. My system is the Openbox session in Lubuntu 14.04 (where *scrot* is the default screen capture utility).

I found that gnome-screenshot works pretty decently on my system from the command-line although I don't get the screen for specifying anything (but see later[SUP]***[/SUP]) :(```
** Message: Unable to use GNOME Shell's builtin screenshot interface, resorting to fallback X11.
```

Examples: ```
gnome-screenshot -p -w -d 10 --file /home/vasa1/a-ztemp/$now
gnome-screenshot -p -w -d 10 -c
gnome-screenshot -a --file /home/vasa1/a-ztemp/$now
```
Re. *$now*, I have this line in my *.bashrc*:```
now=$(date +%b%d%H%M%S)
```


[SUP]***[/SUP]
I can get the interactive window if I want by using *-i*.

---

### Post by yetimon_64 on 2016-03-18
> **vasa1 said:**
> @yeti, what is the purpose of "last-save-directory" in the context of gnome-screenshot (and generally)?...

It _*gets set automatically*_ to that if I change the save dialog to a different directory eg the Desktop, working directly to the desktop can be handy at times but without changing the auto-save setting. 

It is the auto save setting the OP really should focus most on to change the directory from Pictures. If the OP wants to auto save to the desktop then it is not at all needed. I set it for a bit more flexibility of usage. If I want to normally save to screenshots but on one or two occasions I may save to the desktop for work purposes that is when it gets set. Depends on the job I am using the screenshot program with at the time, it is a setting the program changes regularly with usage so not really important here. Note the save screenshot interface will use the last-save setting as a means to remember where the user last saved to, the auto-save will be used as a fallback location in such usage.

> ** Message: Unable to use GNOME Shell's builtin screenshot interface, resorting to fallback X11. 
I don't know for certain vasa1, but I suspect the no-recommends switch may have a bit to do with that error. I've only used gnome-screenshot on the gnome-fallback and unity desktop environments, openbox and lubuntu I don't know much about. 

Cheers, yeti.

**Edit:** the "last-save-directory" only works to remember the last directory used in interactive mode, not normal mode.

---

