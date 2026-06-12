---
title: "SU path not found..."
date: 2007-08-25
forum: General Help
---

### Post by mrbones on 2007-08-25
I am not too sure how this happened but I ahve an update on my comp, went to try and update and I get an error telling me the Program su is nowhere to be found...

> Error text:
The program 'su' is not found;
make sure your PATH is set correctly.
_
Anyone possibly know how I may be able to correct the path? or perhaps reverse whatever has happened here?

Your help is appreciated.

---

### Post by ozorba on 2007-08-25
here is my PATH

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

just copy paste it in a terminal and check if your su works.

If you are successful then just add it to /etc/environment file.

---

### Post by bettlebrox on 2007-08-25
This will show what your PATH is set to. 

[INDENT]echo $PATH [/INDENT]

su should be in /bin: 

[INDENT]$ which su
/bin/su
[/INDENT]

You didn't change or remove any of your .bash files?

---

### Post by mrbones on 2007-08-26
I would love to do that but Konsole gives an error too!

> Konsole is unable to open a PTY (pseudo teletype). It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write access to the PTY devices.

and as far as I know I didnt mess with any of the other files (BASH) at all... I was however attempting to get another HDD recognised and mounted.
(Edited for spelling)

---

