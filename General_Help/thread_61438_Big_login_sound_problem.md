---
title: "Big login sound problem"
date: 2005-08-31
forum: General Help
---

### Post by Warren on 2005-08-31
After disabling all sounds in the sound events menu, a few sounds still played, one being the sound as I login, when I press enter after typing my password.  I made a WAV file using the default sound recorder in ubuntu...about 1 second of silence.  Then I set that as my login sound.  Now, when I go to try to login, I get an error and can't get into ubuntu.  I can get as far as when that sound should try to play.  If needed, I can restart my computer and get the error message for anyone who might be able to help.

I feel dirty having to use windows XP to get online.  :(  Please help

---

### Post by arnieboy on 2005-08-31
[QUOTE=Warren]After disabling all sounds in the sound events menu, a few sounds still played, one being the sound as I login, when I press enter after typing my password.  I made a WAV file using the default sound recorder in ubuntu...about 1 second of silence.  Then I set that as my login sound.  Now, when I go to try to login, I get an error and can't get into ubuntu.  I can get as far as when that sound should try to play.  If needed, I can restart my computer and get the error message for anyone who might be able to help.

I feel dirty having to use windows XP to get online.  :(  Please help[/QUOTE]
yes please post the error message and also tell me where u saved the wav file and/or what it was called.

---

### Post by Warren on 2005-09-01
Alright, then.  First the easy part: The sound file is /home/warren/blank.wav

The first error message that popped up appeared in the top left corner:

> The GNOME Session Manager (process 6657) has crashed due to a fatal error (Aborted).
When you close this dialog, all applications will close and your session will exit.
Please save all your files before closing this dialog.

It had three buttons.  "Restart Application," "Close," and "Inform Developers" from left to right.  The close button took me back to the login screen.  Inform developers brought up a bug reporting system that was a little hard to use.  I didn't know which program to pick in the list.  Restart Application gave me another error message:

> Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

This error had a checkbox labeled "View details (~/.xsession-errors file)"  Clicking that showed this text:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -a "" -l ":0" "warren"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Warren: /tmp/.ICE-unix/6858
GLib-ERROR **:gmem.c:141 failed to allocate 2147483604 bytes

Hope all that helps.  Thanks.

---

### Post by arnieboy on 2005-09-01
[QUOTE=Warren]Alright, then.  First the easy part: The sound file is /home/warren/blank.wav

The first error message that popped up appeared in the top left corner:



It had three buttons.  "Restart Application," "Close," and "Inform Developers" from left to right.  The close button took me back to the login screen.  Inform developers brought up a bug reporting system that was a little hard to use.  I didn't know which program to pick in the list.  Restart Application gave me another error message:



This error had a checkbox labeled "View details (~/.xsession-errors file)"  Clicking that showed this text:



Hope all that helps.  Thanks.[/QUOTE]
ok try this:
from terminal type the folllowing in your home folder:
```
sudo rm -f $HOME/.ICE*
```
and restart your comp.

---

### Post by Warren on 2005-09-01
How do I get to the terminal when I can't login and what does that command do?

---

### Post by arnieboy on 2005-09-01
[QUOTE=Warren]How do I get to the terminal when I can't login and what does that command do?[/QUOTE]
when it gets to the login screen press ctrl-alt-F1 to get into console mode and hide your GUI.

---

### Post by Warren on 2005-09-01
If the .ICE* file mentioned in the error message is /tmp/.ICE-unix/6858 why would deleting all .ICE* files in /home help?

---

### Post by arnieboy on 2005-09-01
[QUOTE=Warren]If the .ICE* file mentioned in the error message is /tmp/.ICE-unix/6858 why would deleting all .ICE* files in /home help?[/QUOTE].ICE* is the ".ICEauthority" file. I can give u a complete tutorial later when I get back from work, but please follow my instructions for now if u want your system up and working again. dont worry. u wont screw it up by deleting that file.

---

### Post by Warren on 2005-09-01
The command made no change that I could tell.  Any other suggestions?

---

### Post by arnieboy on 2005-09-01
[QUOTE=Warren]The command made no change that I could tell.  Any other suggestions?[/QUOTE]
did u restart your comp after deleting $HOME/.ICEauthority ?

---

### Post by Warren on 2005-09-01
Yes

---

### Post by arnieboy on 2005-09-01
[QUOTE=Warren]Yes[/QUOTE]
have u tried deleting the wav file that u tried to make the sound server play? if not, try deleting that in the same way as u deleted the iceauthority file and see if it makes any difference.

---

### Post by Warren on 2005-09-01
Well, I'm finally back in Ubuntu (thanks bunches) but it still plays that annoying sound when I login.  So I've tried going into the sound preferences, sound events tab and removing the "log in" sound from the list, but, clearly, it still plays.  Setting it to another file screws my computer.

How do I disable that?

---

### Post by arnieboy on 2005-09-01
[QUOTE=Warren]Well, I'm finally back in Ubuntu (thanks bunches) but it still plays that annoying sound when I login.  So I've tried going into the sound preferences, sound events tab and removing the "log in" sound from the list, but, clearly, it still plays.  Setting it to another file screws my computer.

How do I disable that?[/QUOTE]
**uncheck** "enable sound server startup" in system-->preferences-->sound
take a look at the following HowTo if u wanna make your Ubuntu sound system super-sexy:
[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

---

