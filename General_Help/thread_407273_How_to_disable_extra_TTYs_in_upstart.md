---
title: "How to disable extra TTYs in upstart"
date: 2007-04-11
forum: General Help
---

### Post by divisionbyzero on 2007-04-11
Hello everyone,

I'm trying to optimize my system by disabling extra TTYs in Ubuntu. 

I could easily do this by editing /etc/inittab and then commenting the extra TTYs there. With the new upstart mechanism in place for feisty fawn, i am only presented with a directory that has entries.

So the question is: How do I disable these extra TTYs from being run with upstart?

---

### Post by pointone on 2007-04-12
Rename the ttyX files in /etc/event.d/ to something else, such as disabledttyX.

---

### Post by divisionbyzero on 2007-04-13
I just tried that, renaming for example /etc/event.d/tty1 to /etc/event.d/disabled-tty1

I rebooted but I'm still getting terminals 1 to 6, when i press ctrl-alt-1 to ctr-alt-6

---

### Post by pointone on 2007-04-14
The system is still able to find the files somehow. I had the same problem when renaming mine disabled.ttyX. You need to change the name even more...

---

### Post by rajitsrinivas on 2007-04-21
You have to edit /etc/default/console-setup file. This file defines how many ttys should you get. Change ACTIVE_CONSOLES="/dev/tty[1-6]" to the number of consoles you want. Lets say, 2 ttys, then change it to "/dev/tty[1-2]".

And then goto /etc/event.d/ and change the ttyx files that you DONOT want. Edit them and comment lines starting with "start on runlevel". So, in this case, you'll comment the start line in tty3..tty6 files.

Rebooting shud minimize the number of consoles for you. Worked for me!!

Good luck,

NOTE: Even though you've reduced the tty number, X is still on Alt-F7.

---

### Post by divisionbyzero on 2007-04-21
I've been able to disable the extra TTY's by moving the TTY files somewhere but your method seem to be the "right way" of doing it.

Thanks for the help. I'll try it when I reformat to make way for Feisty.

---

### Post by kyfho23 on 2007-04-25
> **rajitsrinivas said:**
> You have to edit /etc/default/console-setup file. This file defines how many ttys should you get. Change ACTIVE_CONSOLES="/dev/tty[1-6]" to the number of consoles you want. Lets say, 2 ttys, then change it to "/dev/tty[1-2]".

And then goto /etc/event.d/ and change the ttyx files that you DONOT want. Edit them and comment lines starting with "start on runlevel". So, in this case, you'll comment the start line in tty3..tty6 files.

Rebooting shud minimize the number of consoles for you. Worked for me!!

Good luck,

NOTE: Even though you've reduced the tty number, X is still on Alt-F7.


I've also accomplished the same thing by renaming the excess tty's with a .bak extension. Seems to turn them off & speed things up. 
However, I'm still also going to edit the /etc/default/console-setup file. Drive a stake in their hearts, as it were. ::)

---

### Post by elect on 2008-04-11
Sry men, and if I cant see console by pressing ctrl-alt-Fx...what could it be?

---

### Post by Junglizer on 2008-04-11
Correct me if I am wrong isn't all of this located within **/etc/inittab**?

---

### Post by pointone on 2008-04-11
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by mali2297 on 2008-04-11
> **elect said:**
> Sry men, and if I cant see console by pressing ctrl-alt-Fx...what could it be?

I guess that you have encountered the same old bug as many others, see here
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

The bug is supposed to have been fixed in Ubuntu 8.04.

---

