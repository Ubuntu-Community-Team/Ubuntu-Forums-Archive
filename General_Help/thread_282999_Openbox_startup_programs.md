---
title: "Openbox startup programs"
date: 2006-10-23
forum: General Help
---

### Post by recrispi on 2006-10-23
Hello!

I made a xubuntu server install and installed openbox following the instructions in this threads

[http://www.ubuntuforums.org/showthread.php?t=192106&highlight=openbox](http://www.ubuntuforums.org/showthread.php?t=192106&highlight=openbox)
[http://www.ubuntuforums.org/showthread.php?t=103806&highlight=openbox](http://www.ubuntuforums.org/showthread.php?t=103806&highlight=openbox)

Everything is running ok, but I can't make openbox run any programs on startup, no background image (using feh), no pypanel loaded.

I used the autostart.sh (~/.config/openbox/autostart.sh) file recommended in the first thread, made it executable and even modified it a little, but no result. Also I edited the file in /usr/share/xsession/openbox.desktop to point to my autostart.sh file but didn't work, so I tryied with .xinitrc and .xession in my home directory but didn't work either. ](*,) 

Now I don't know what else should I do to autorun some programs so I don't have to do it manually. Any ideas as to how to solve my problem? :confused: 

I'm using WDM as display manager and I'm avoiding any Gnome/KDE dependencies, because the PC is really slow.

Thanks for any help you could give me.

---

### Post by PriceChild on 2006-10-23
*moves*

---

### Post by paul6 on 2006-10-24
Could you post the contents of your autostart.sh and openbox.desktop file?

Also what session are you using, "Default session" or "Openbox"?

---

### Post by recrispi on 2006-10-25
Hello!
Sorry for the delay, but yesterday I was away from my office computer all day. My autostart.sh reads:

> #!/bin/sh 
# Auto-mounting drives 
# gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
exec eval `cat $HOME/.fehbg` &
#feh --bg-scale space-02.jpg &
#exec pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else exec pypanel && exec openbox 
fi
#exec openbox
#pypanel

the commented lines are the other chances I've tryied but didn't work either.
My openbox.desktop reads:

> [Desktop Entry]
Encoding=UTF-8
Name=Openbox
Comment=Use this session to run Openbox as your desktop environment
Exec=/home/rcrispieri/.config/openbox/autostart.sh
Icon=
Type=Application

I take a look at what session am I using and it was the "no change" session, then I tested the "default" and the "openbox" sessions and all were the same.

Any idea as to what to do? Thanks.

---

### Post by kerry_s on 2006-10-25
Just use .xsession
example:

[Desktop Entry]
Encoding=UTF-8
Name=Openbox
Comment=Use this session to run Openbox as your desktop environment
Exec=/home/rcrispieri/.xsession
Type=Application 


The .xsession, don't forget to make it executable.

#!/bin/sh

gnome-settings-daemon & 

sleep 5
pypanel &

exec openbox


The sleep 5 will make pypanel wait 5 seconds before loading, anything above sleep will load normal. so anything below sleep will pause for 5 seconds, you can adjust the time to your system speed.

---

### Post by recrispi on 2006-10-25
Thank you Kerry_s
I used this .xsession and made it executable:
> 
#!/bin/sh

#gnome-settings-daemon &
eval `cat $HOME/.fehbg` &
sleep 5
pypanel &

exec openbox
> 
-rw-r--r--  1 rcrispieri rcrispieri    11543 2006-10-23 17:25 .xscreensaver
-rwxr-xr-x  1 rcrispieri rcrispieri       94 2006-10-25 12:01 .xsession
-rw-------  1 rcrispieri rcrispieri    43289 2006-10-25 12:03 .xsession-errors

and made my openbox.desktop to look exactly as in your example:
> 
[Desktop Entry]
Encoding=UTF-8
Name=Openbox
Comment=Use this session to run Openbox as your desktop environment
Exec=/home/rcrispieri/.xsession
Icon=
Type=Application

but again I have to run pypanel and feh manually :-(

I don't know is this has anything to do about this, but this are the messages appearing in my .xsession-errors:
> 
Xsession: X session started for rcrispieri at mié oct 25 12:01:43 CLST 2006
I/O warning : failed to load external entity "/var/lib/openbox/debian-menu.xml"

(openbox:4290): ObParser-WARNING **: unable to find a valid menu file '/var/lib/openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/rcrispieri/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:4290): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'

(openbox:4290): Openbox-WARNING **: failed to grab keycode 12 modifiers 8

(openbox:4290): Openbox-WARNING **: failed to grab keycode 13 modifiers 8
I/O warning : failed to load external entity "/var/lib/openbox/debian-menu.xml"

(openbox:4290): ObParser-WARNING **: unable to find a valid menu file '/var/lib/openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/rcrispieri/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:4290): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'

why is this looking for a debian-menu.xml?

---

### Post by kerry_s on 2006-10-25
Did you install menu?->
sudo apt-get install menu

then in terminal->
update-menus
sudo update-menus

I think i had to also change the /.config/openbox/menu.xml to point to the one in the same folder cause it was pointing to /etc/X11/openbox/debian-menu.xml, i may have have even manually copied it to /home/-user-/.config/openbox/debian-menu.xml
from
/var/lib/openbox/debian-menu.xml

Sorry, i can't remember. I gave up openbox and went back to fluxbox.

"but again I have to run pypanel and feh manually"

How come you still have to run pypanel and feh manually? Is it the start up timing? Can you tell me more on the problem?

---

### Post by recrispi on 2006-10-26
Thank you. Your help is most welcome! :)

> **kerry_s said:**
> Did you install menu?->
sudo apt-get install menu

then in terminal->
update-menus
sudo update-menus

I think i had to also change the /.config/openbox/menu.xml to point to the one in the same folder cause it was pointing to /etc/X11/openbox/debian-menu.xml, i may have have even manually copied it to /home/-user-/.config/openbox/debian-menu.xml
from
/var/lib/openbox/debian-menu.xml

This made it stop asking for the debian-menu.xml. Now I have no error messages in my .xsession-errors file :D

> **kerry_s said:**
> 
Sorry, i can't remember. I gave up openbox and went back to fluxbox.

"but again I have to run pypanel and feh manually"

How come you still have to run pypanel and feh manually? Is it the start up timing? Can you tell me more on the problem?

When I start openbox I still have a blank screen, so I must open a terminal and run pypanel ans feh --bg-scale image.jpg. Just as if I hadn't followed your instructions from your previous message. :(  It looks to me like openbox isn't reading the configuration files, neither the .xsession file :confused:

---

### Post by moore.bryan on 2006-10-26
[I]your autostart.sh should look more like:
[/I]```
#!/bin/sh 
# Auto-mounting drives 
# gnome-volume-manager & 
# GTK themes... this is just one method 
# gnome-settings-daemon & 
# feh stores the last background in .fehbg 
exec eval `cat $HOME/.fehbg` &
pypanel & 
# This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else exec pypanel && exec openbox 
fi
```
*from there, you should only have to run ```
feh --bg-scale /DIR/OF/YOURPIC.PNG
``` once and never again until you want to change it.*

---

### Post by kerry_s on 2006-10-26
Are selecting openbox at the login in screen for session? It sounds like it's running the default instead which is a clean session each time. You have to select openbox at least once.

---

### Post by recrispi on 2006-10-27
> **kerry_s said:**
> Are selecting openbox at the login in screen for session? It sounds like it's running the default instead which is a clean session each time. You have to select openbox at least once.

Thanks, yes, this was my problem. Now I have it working ok. Thanks to all again :D

---

