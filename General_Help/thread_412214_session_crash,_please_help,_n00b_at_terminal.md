---
title: "session crash, please help, n00b at terminal"
date: 2007-04-17
forum: General Help
---

### Post by lyceum on 2007-04-17
-edit-

Solved! 

Every time I log in I get kicked out. After the first time I get a box that reads "Your sesion only lasted less than 10 seconds..." I have over 100 gis of disk space, so I am guessing that I did not set up something right, and the last thing I did was set up Beryl to start at startup. Here is my error:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/x11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/ytmp -x "/var/lib/gmd/:0,Xservers" -h " " -l ":0" "david"
/etc/gdm/PreSession/Default: Beginning session setup...
SESSION MANAGER=local/lyceam:tmp/.ICE-unix/6060
Window manager warning: " " found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension 
*** glibc detected *** x-session-manager: malloc ( ): memory corruption: 0x082fc6a0 ***
====== Backtrace: ======
 Then is has too much info to give (I cannot cut and paste it) but at the end it says there ar e3 ID errors"
update- notifier:6134
evolution-alarm-notif: 6150, 
gnome: session-properties:6153

Can anyone help? I can only work in terminal, but I am not very good at that. My other 2 logging sessions work fine, but have no admin rights. If I could just use terminal to create a new admin session, if nothing else, that would be great.

Thank you.

---

### Post by kornhead127 on 2007-04-17
when you are at the terminal type...
```
sudo nano /etc/X11/xorg.conf
```
you can enter this anywhere really but add a section like this...
```

Section "Extensions"
[INDENT]Option "Composite" "0"[/INDENT]
EndSection

```

---

### Post by lyceum on 2007-04-17
That did not seem to work. I can see that the info I entered is still there in terminal, but there is no new user session to add, nor does it seem that there was a way to add one when inputting that data into the terminal. Sorry if I was not clear in my first post. I was trying to add a new user session with asmin rights. I am no sure what what I was doing. Unless it is apt-get I really am clueless in the terminal. Could you give me more info as to what I am doing and how to do it? Thank you for you help.

---

### Post by skywalker___ on 2007-04-17
I cut and pasted your error you had and done a search in the advanced box and this is what it gave me

[http://ubuntuforums.org/search.php?searchid=18151036](http://ubuntuforums.org/search.php?searchid=18151036)

read others had same error

---

### Post by lyceum on 2007-04-17
> **skywalker___ said:**
> I cut and pasted your error you had and done a search in the advanced box and this is what it gave me

[http://ubuntuforums.org/search.php?searchid=18151036](http://ubuntuforums.org/search.php?searchid=18151036)

read others had same error

None of these are the same problem I am having and most do not have answers. Thanks though.

let me try to explain this again. I am not the best with words sometimes,

I have 3 users, myself, my wife, and "guest". I can use my wife's ID and the "guest" ID (which is what I have been using) but not my user session ("david"). I do not know how else to say that, sorry. The problem is only in my ID. It was not an update that messed me up, it was me. I tried to add something to start up and thought is was wrong, but forgot to fix it before I turned off my PC. Now I cannot log in to my user session, so the issue is only with my user name. My user name is the only one with admin rights. If I had a second user name with admin rights I would be fine. I would like to know how to go in to the startup area in terminal to stop the things I added from loading. That may be too much for me. I am great at Ubuntu, but not do good with Terminal. I thought it might be easier to create a new admin user name and use it to take the stuff I need from my opd admin ID and get rid of that ID. Sorry I was not as clear before. Thank you.

-edit-
or, if there is a way to do any of this with a live CD, that would be great too, actually better.

---

### Post by thephotoman on 2007-04-18
Okay, here's what I want you to do.  First, please try using the "failsafe terminal" option.  It's under the Options menu at the bottom left corner of the screen.  Select "select session", then "failsafe terminal".  Log in.

Do you get the same error?  If you do, then you can give one of the other accounts log in rights from the terminal and start over.  I don't exactly recommend doing what I do in these situations, which is to delete the ~/.gnome and ~/.gnome2 folders and letting the system rebuild those upon login.  You lose a lot of preferences this way, but since I don't mess with GNOME settings that much, it's not a problem for me.

Edited: Once in on the terminal above, try running gnome-session (this starts GNOME) and hitting ctrl+c at the right moment to kill the process that's giving you trouble.  I've had some luck with this in the past, when subversion builds of Beryl didn't exactly work, but it's all in the timing.  From there, I was able to get in and stop the process from loading at login in the usual way.  Honestly, I wish I knew of a more elegant and surefire way to stop things.

---

### Post by lyceum on 2007-04-25
> **thephotoman said:**
> Okay, here's what I want you to do.  First, please try using the "failsafe terminal" option.  It's under the Options menu at the bottom left corner of the screen.  Select "select session", then "failsafe terminal".  Log in.

Do you get the same error?  If you do, then you can give one of the other accounts log in rights from the terminal and start over.  I don't exactly recommend doing what I do in these situations, which is to delete the ~/.gnome and ~/.gnome2 folders and letting the system rebuild those upon login.  You lose a lot of preferences this way, but since I don't mess with GNOME settings that much, it's not a problem for me.

Edited: Once in on the terminal above, try running gnome-session (this starts GNOME) and hitting ctrl+c at the right moment to kill the process that's giving you trouble.  I've had some luck with this in the past, when subversion builds of Beryl didn't exactly work, but it's all in the timing.  From there, I was able to get in and stop the process from loading at login in the usual way.  Honestly, I wish I knew of a more elegant and surefire way to stop things.

I finally got a chance to try this and it worked! I could not get to sessions, but I was able to create a new admin account, which is just as good for me. Thank you!!!! 

:guitar:

---

