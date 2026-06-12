---
title: "How to get special mouse buttons working in ff3?"
date: 2008-07-10
forum: General Help
---

### Post by shamusl on 2008-07-10
Is there a simple way to get my forward and back buttons on my logitech mouse to work as forward and back in firefox and in nautilus?

---

### Post by jonlemur on 2008-07-10
I posted a way to easily add that functionality a while ago.  Let me look through my posts to see if I can find it.  It has to do with editing your /etc/X11/xorg.conf file.

---

### Post by shamusl on 2008-07-10
> **jonlemur said:**
> I posted a way to easily add that functionality a while ago.  Let me look through my posts to see if I can find it.  It has to do with editing your /etc/X11/xorg.conf file.

Well, thanks.

---

### Post by jonlemur on 2008-07-10
Shoot, maybe I didn't make such a post.  I'm pretty sure that when my buttons didn't work, I had to add the line ```
Option    "ButtonMapping"  "1 2 4 5 6 7"
``` under the section ```
"Section "InputDevice"
	Identifier	"Configured Mouse"
``` 

Before you edit it though, you should make a backup of the file. ```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` Then restart the X server with Ctrl+Alt+Backspace.  

If that doesn't work, it may help others though to know what model of Logitech mouse you're using.

---

### Post by shamusl on 2008-07-10
[http://www.amazon.com/Logitech-Optical-Marble-Mouse-USB/dp/B00005T406/ref=dp_cp_ob_title_0](http://www.amazon.com/Logitech-Optical-Marble-Mouse-USB/dp/B00005T406/ref=dp_cp_ob_title_0)

Thats the mouse, but how does that change things?

---

### Post by jonlemur on 2008-07-10
Here's my old xorg.conf file that I used when my Logitech mouse buttons weren't working by default. ```
Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Button Mapping" "1 2 3 6 7"
EndSection
```

I don't know exactly how all of those options work, but I think the number of mouse buttons may not be recognized, so "Buttons" "7" tells it how many buttons to use, and the next two options tells it how to map those buttons.  I could be wrong on that.

---

### Post by shamusl on 2008-07-10
Okay, noob question. How come when I try to save the file it's telling me I don't have the permissions to? And what do I need to do to save it?

EDIT: Nevermind, I forgot that I need to be root to save the file. I just don't know how to become root (just installed ubuntu recently). What do I have to do?

---

### Post by jonlemur on 2008-07-10
You'll need to put sudo in from of cp ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` then enter your password.  Linux doesn't let you write to /etc (or any other files under / except your home without super user privileges (sudo) for security reasons.

You can the edit the file with ```
sudo gedit /etc/X11/xorg.conf
```.  Then you can save by pressing Ctrl+s or File->Save.  

If something goes terribly wrong, you can ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
``` to restore the old file.

---

### Post by jonlemur on 2008-07-10
I've got to head to bed, but I'll check back in the morning.  [This thread]("http://ubuntuforums.org/showthread.php?t=44191&highlight=side+buttons+nautilus") may have some answers as well.  As I remember, I never got the back and forward buttons working properly in Nautilus, only in Firefox, but some people have.  I think they use the program imwheel to do it.

---

### Post by shamusl on 2008-07-10
After Ctrl-Alt-Backspace, the configuration change didn't affect my buttons on my mouse, any other suggestions?

---

### Post by jonlemur on 2008-07-10
With the mouse that you have, you probably don't have a z-axis like mine.  I would recommend trying to take out the Option zaxis line, and changing ButtonMapping to "1 2 3 4 5 6 7".

---

### Post by jonlemur on 2008-07-10
I'd also recommend installing imwheel ```
 sudo apt-get install imwheel
``` and reading the man page on it ```
man imwheel
```If you haven't used a man page before, q quits out of it once open, and the arrow keys move up and down, and the space bar moves one page at a time.  It seems to explain a fair amount about the Options in xorg.conf.

---

### Post by jonlemur on 2008-07-10
This [thread]("http://ubuntuforums.org/showthread.php?t=219894") may also help.

It does a lot of things that I didn't have to do to get mine working properly.  I just had to add the line "ButtonMapping" "1 2 3 6 7" and it worked.  But you may have to follow something more like that thread shows.

---

### Post by jonlemur on 2008-07-10
Also, if you run xev from the terminal, then click with your mouse buttons, the terminal output should tell you what button is being pressed.  If you click the forward and backward buttons while doing that, you can see what the buttons are numbered.  Then you can edit the xbindkeys resource file in your home folder (man xbindkeys to find out exactly where it's installed and what it's called, and to find the syntax) to map those buttons to Alt+left arrow and Alt+right arrow.  I didn't think it was going to be this hard, and sorry if I'm making it more complicated than it needs to be.

---

### Post by orro_xo on 2008-07-11
I have the same problem with FF3. The back button doesnt work and I have fixed the keybindings in xorg and the back button on the mouse works fine in Galeon but not in FF3. What can be the problem? It worked well in FF2 but not in FF3.

---

### Post by jonlemur on 2008-07-12
I added this section to my ~/.imwheelrc file.  ```
".*"
None,Thumb1,Alt_L|Left
None,Thumb2,Alt_L|Right
```  This gave me forward and backward thumb button functionality in both FF3 and Nautilus.

You may have to kill any old imwheel instances with ```
imwheel -k
``` and restart it with ```
imwheel
```  If this works for you, you should be able to add imwheel to the startup scripts.  I don't remember now how to do that, but it wouldn't be hard to find it.

---

