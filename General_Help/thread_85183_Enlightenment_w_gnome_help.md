---
title: "Enlightenment w/ gnome help"
date: 2005-11-01
forum: General Help
---

### Post by Whatthehello on 2005-11-01
hi. i would like to try out enlightenment. I just recently tried out:

[http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment](http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment)

which is to integrate enlightenment with gnome. unfortunately. i dont know what to do from there. i do not know how to do really cool things in enlightenment. Can someone teach me or provide me with a link? I am really new to this stuff so please try not to give me links to webpages that dont say much. thanks. :rolleyes: 

I am really liking ubuntu.

---

### Post by krye on 2005-11-02
If you already have enlightenment working, you just need to learn how to use it... [www.get-e.org](www.get-e.org) has a User's Guide, try to give it a read, and I guess you'll be able to do what you want to.

I have it running right now, and after downloading and installing some themes, wallpapers, e17genmenu, engage, and evidence I have all the eyecandy I want. The User's Guide should tell you how to do all that, 'cept for the e17genmenu, go to [http://www.ubuntuforums.org/showthread.php?t=79155](http://www.ubuntuforums.org/showthread.php?t=79155) for that.

---

### Post by Whatthehello on 2005-11-02
if i installed using synaptic earlier today, which version would i have?

[http://www.get-e.org/](http://www.get-e.org/) does not have any info on E1.6. only E1.7

---

### Post by LittleReinhart on 2005-11-02
Hey,

[QUOTE=Whatthehello]if i installed using synaptic earlier today, which version would i have?

[http://www.get-e.org/](http://www.get-e.org/) does not have any info on E1.6. only E1.7[/QUOTE]

You will probably have version 0.16.6. Type "enlightenment -version" inside a terminal. This is my output:```
$ enlightenment -version
Enlightenment Version: 0.16.6
Last updated on: $Date: 2003/11/05 18:06:01 $
```

I learned about enlightenment by reading the helpfile that comes with it (click on your mouseweel (or both left and right mouse bottons at the same time) and then click "help").
To get you started, you can manually make your own usermenu by changing file.menu found in your .enlightenment dir.

This is how my menu looks like:
vi /home/*your_user_name*/.enlightenment/file.menu
```
"User Menus"
"Xterm" NULL exec "xterm"                    # this executes an xterminal
"FireFox" NULL exec "mozilla-firefox"        # if you like icons, just replace NULL by the icon path and file between two ""
"Konqueror" NULL exec "konqueror"

"Internet" NULL menu "internet.menu"         # this points to an other menu. Of course you have to make the file "internet.menu" the same way you make this file
"MultiMedia" NULL menu "multimedia.menu"
"Office" NULL menu "office.menu"
"System" NULL menu "system.menu"
"Scientific" NULL menu "scientific.menu" 
"Netwerk" NULL menu "netwerk.menu"
"Utilities" NULL menu "utilities.menu"

"The GIMP" NULL exec "gimp"
"Procesbeheer" NULL exec "gnome-system-monitor"
"QT Parted" NULL exec "qtparted"
"Netwerk tools" NULL exec "gnome-nettool"
"Run as different user" NULL exec "gksuexec"

"Debian menu" NULL menu "/home/reinhart/.enlightenment/debianmenus/debian.menu"

"Automatisch aangemaakt" NULL menu "auto.menu"
"Enlightenment Epplets" NULL menu "epplets.menu"
"Restart Enlightenment" NULL exec "/usr/bin/eesh -e 'restart'"
"Log Out" NULL exec "/usr/bin/eesh -e 'exit'"

```

Then you get to the menu by clicking on your left mousebutton anywhere on the desktopbackground.

An other thing I like about enlightenment... add a gnome-panel to it. (Personally I don't like the pager and iconbox that comes with enlightenment, so I use the gnome-pannel instead.)

Befor we go on, please note that I got some errors when I added or changed the gnome-pannel. I just ignored the errors, and at the next boot they were gonne (I'm not shure if this is bad, my compy works fine, so I'm not worried (if it is bad, please tell me! And how to fix it.))

And if you want the gnome-panel to start everytime you start your enlightenment, open the next file
vi /home/*your_user_name*/.xsession  <- this is your userstartupscript
First time it looks like this:
```
# Enlightenment inserted Execution string here
exec /usr/bin/enlightenment
```
And add "gnome-panel &" befor the last line
```
# Enlightenment inserted Execution string here
gnome-panel &
exec /usr/bin/enlightenment
```
For example, mine looks like this:
```
# Enlightenment inserted Execution string here
# esd &
xmms -fp &
xterm &
gnome-panel &
gaim &
mozilla-thunderbird &
kate /home/reinhart/Todo &
exec /usr/bin/enlightenment
```

See [http://www.enlightenment.org/](http://www.enlightenment.org/) for more nice things...

Greetings,
Reinhart

---

### Post by LittleReinhart on 2005-11-02
I've just been true this : [http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment](http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment) to put enlightenment on my laptop.

Damn, this comes in handy, thanks poofyhairguy, Stormy Eyes and Rasterman!

Greetings,
Reinhart

---

