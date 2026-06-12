---
title: "Can't access my laptop"
date: 2014-04-21
forum: General Help
---

### Post by duckfeeder105.5 on 2014-04-21
Wanna know why? I set the panel to its full settings, and not I can't use my Laptop besides the panel; The panel covers the screen

 Any help?

---

### Post by 23dornot23d on 2014-04-21
Can you right click onto the panel and get the dialogue to open to change its sizes back.

Does double clicking it have any effect.

Can you press alt or ctrl down while on the panel and move it out of the way while holding the left mouse button down. 

...... to get to anything behind it ........

---

### Post by duckfeeder105.5 on 2014-04-21
Nope, that did not do anything. Thank you for the help, though

---

### Post by 23dornot23d on 2014-04-21
(Ctrl + alt + T) to bring a terminal up ........ will that work

(Ctrl + alt + f1) goto the console use htop - kill off the panel 

**htop**
> 
it will appear in the long list as xfce4-panel ......... f9  then enter while the selection bar is over it
will kill off the process ...... if you can get to it ok 

then come back into the desktop using (Ctrl + Alt + F7)

Then (Ctrl + alt + T) to bring a terminal up ............ 

This will then at least give you something to work from to fix the problem
but first see if anything is working ........... 

Do you have any other desktops at login to go into ?

LXDE or awesome or E17 ...... will all give you somewhere where you can work from
with a GUI ...... otherwise it needs someone to explain how to reset things from the command
line ....... and although I use the command line a lot - I have never had to alter the panel sizes
from it .......

* Killing off the panel will only be for this session ... to get it back just log out and back in again

you could add a dock or something to work from ..... while fixing the problem ..... docky maybe.

sudo apt-get install docky ...... gives you a dock to work from after getting rid of the panel with
htop.

**sudo apt-get install htop**

incase its not already installed to use all commands can be done from a console 
( ctrl + alt + f1 ) >>>> ( ctrl + alt + f7 ) to get back to the desktop environment.

---

### Post by duckfeeder105.5 on 2014-04-21
> **23dornot23d said:**
> (Ctrl + alt + T) to bring a terminal up ........ will that work

(Ctrl + alt + f1) goto the console use htop - kill off the panel 

**htop**


then come back into the desktop using (Ctrl + Alt + F7)

Then (Ctrl + alt + T) to bring a terminal up ............ 

This will then at least give you something to work from to fix the problem
but first see if anything is working ........... 

Do you have any other desktops at login to go into ?

LXDE or awesome or E17 ...... will all give you somewhere where you can work from
with a GUI ...... otherwise it needs someone to explain how to reset things from the command
line ....... and although I use the command line a lot - I have never had to alter the panel sizes
from it .......

* Killing off the panel will only be for this session ... to get it back just log out and back in again

you could add a dock or something to work from ..... while fixing the problem ..... docky maybe.

sudo apt-get install docky ...... gives you a dock to work from after getting rid of the panel with
htop.

Thanks for the help, my screen is back :) . Anyway, is there anyway I can get the panel back to it's normal size?

---

### Post by 23dornot23d on 2014-04-21
You need to alter a config file I guess ...... but am not familiar with xfce ...... 

I will have a quick scout around to see if I can find anything ......

Found this in a post ..... might help .... sometimes delete and recreate
can give a new one ...... safer to rename or move it though.

Then see if it asks to create a new config on entry back into it ......

[I][I].config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

[/I][/I]And that's where my panel configs were he said ,,,,,

> 

K53SV:~/.config/xfce4/xfconf/xfce-perchannel-xml$ ls
keyboards.xml  xfce4-desktop.xml             xfce4-mixer.xml  xfce4-session.xml
thunar.xml     xfce4-keyboard-shortcuts.xml  xfce4-panel.xml  xfwm4.xml


---

### Post by duckfeeder105.5 on 2014-04-21
So I run them both in terminal?

---

### Post by 23dornot23d on 2014-04-21
I think you should move the 

xfce4-panel.xml 

file into another directory maybe just drag and drop it onto your desktop so you know where it is ...... for the time being

Log out and back in again and see if it asks you to create

a new panel ....... with the normal settings restored .......

___________________________________

if you start in you home directory you can do this copy and paste it ...... do the cd first - makes sure you are in the
right place to start with

**cd**

**mv .config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml xfce4-panel.xml**

it will just move the file out of the way ..... and will probably be re-created properly on rebooting
back into the system ...... may ask you to create a new panel ........

That will work ........ I just tried it on my own system ....... asks on entry to create a default panel

---

### Post by duckfeeder105.5 on 2014-04-21
I'm sorry, I am still in the basics of linux, would you mind telling me in a simpler way?

Edit: never mind, I think got it

---

### Post by duckfeeder105.5 on 2014-04-21
Ok, I now have a new panel. Now, how do I move it to the bottom?

---

### Post by 23dornot23d on 2014-04-21
Let us know how it goes ..... 

I did add a one liner ..... might help in the last thread.

Usually right click on it and then choose properties ....... there are options in there .......

or you can specify from start up not to use the default ones and build and place your own

on the screen ......... from what I have seen they can be almost anywhere .......

[http://xfce-look.org/](http://xfce-look.org/)

There is some more information here ....... maybe it will help ........

[http://unix.stackexchange.com/questions/59975/how-to-modify-dock-bar-in-xfce4](http://unix.stackexchange.com/questions/59975/how-to-modify-dock-bar-in-xfce4)

---

