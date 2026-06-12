---
title: "&quot;Login last less than 10 secunds&quot;"
date: 2007-06-02
forum: General Help
---

### Post by Ub1476 on 2007-06-02
Yes, I tried to login in to every session, none works.. Except the terminal session.. 

Here's my error message: (Show details (~/.xsession-errors file)

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default. runnning: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0,Xservers" -h " " -l ":0" "myusername"

/etc/gdm/Xsession: Beginning session setup

gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

```

_Last thing I did with Ubuntu OS:_

*I opened my notebook, it's in locked screen. I choose cancel, come to the login screen and shutdown.*

Hope this is a small problem:)

Thanks,
Ub

---

### Post by bapoumba on 2007-06-02
From the grub menu, log in recovery mode (you'll be root with a # prompt):
```
chown <your_user> /home/<your_user>/.ICEauthority
chmod 600 /home/<your_user>/.ICEauthority
reboot
```
replace <your_user> with your actual login, without the <>.
If this does not work, just delete the .ICEauthority file (a new one will be created upon next login).

---

### Post by Ub1476 on 2007-06-03
Thanks for the reply, but it didn't work.:(

I deleted the .ICEauthority file too, still I can't login.

---

### Post by Ub1476 on 2007-06-03
Actually I think it has something to do about the sound drivers (Realtek HD) I just installed, unsuccessful I guess..

Found a similar thread here: [Link]("http://ubuntuforums.org/showthread.php?p=2736969") and here.. [Link]("http://ubuntuforums.org/showthread.php?t=168371")

How can I undo what I have done? Anyone, please help!#-o

---

### Post by Ub1476 on 2007-06-03
Bump

---

### Post by bapoumba on 2007-06-03
Other than the suggestion I previously had, are you on a 64-bit kernel ?

---

### Post by Ub1476 on 2007-06-03
Nope.

---

### Post by Ub1476 on 2007-06-04
bump

---

### Post by bapoumba on 2007-06-04
Would you happen to read italian ?
[http://www.dacciola.it/?p=10]("http://www.dacciola.it/?p=10")

Do you have ubuntu-desktop installed ?

---

### Post by engla on 2007-06-04
Seemingly something is wrong with the library "libasound.so.2" have you tried to reinstall this file? Are you using prelink, it can corrupt libraries sometimes (it did that to me a while ago..)

At least try something like 'apt-get install --reinstall libasound2' to reinstall the library file to fix it if it was corrupt.

---

### Post by Ub1476 on 2007-06-04
> Would you happen to read italian ?
[http://www.dacciola.it/?p=10](http://www.dacciola.it/?p=10)

Nope, I came across that one too, actually;)

> 
Do you have ubuntu-desktop installed ?
Yes

> Seemingly something is wrong with the library "libasound.so.2" have you tried to reinstall this file? Are you using prelink, it can corrupt libraries sometimes (it did that to me a while ago..)

Nope, haven't tried to reinstalled it, honestly I don't know how to:p Neither am I using a prelink, but thanks for the warning.

> At least try something like 'apt-get install --reinstall libasound2' to reinstall the library file to fix it if it was corrupt.


Yes, that did it! Thank you very much! Now I just have to figure out how to successfully install the sound drivers without screwing it up again:p

---

### Post by si_harp on 2007-06-15
Thanks engla!

Solved my problem too!  I'll post this solution in other unanswered threads about this too.

Thanks again

Si

---

