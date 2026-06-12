---
title: "How to make a terminal automatically run commands upon launch?"
date: 2007-06-18
forum: General Help
---

### Post by hypersire on 2007-06-18
Hi all - I am launching an aterm from my .xinitrc file as follows:

aterm -tr +sb &

Is there anyway to append commands so that they are automatically run when the aterm is launched? I would like to automatically run ifconfig and netstat when the terminal starts.

Thanks.

---

### Post by Anonii on 2007-06-18
> **hypersire said:**
> Hi all - I am launching an aterm from my .xinitrc file as follows:

aterm -tr +sb &

Is there anyway to append commands so that they are automatically run when the aterm is launched? I would like to automatically run ifconfig and netstat when the terminal starts.

Thanks.
You can launch ifconfig in the startup with this command (since you like aterm):
**aterm -e ifconfig**
I guess that you can follow the patern for netstat, too.

---

### Post by hypersire on 2007-06-18
> **Anonii said:**
> You can launch ifconfig in the startup with this command (since you like aterm):
**aterm -e ifconfig**
I guess that you can follow the patern for netstat, too.

Thanks for the reply Anonii -

When I add the -e commandname flag, it appears to work except now the terminal won't stay open - it flashes briefly (with what appears to be the results of the command on the screen) but then it's gone. 

Any ideas on how to make the terminal stay open after it finishes executing the command?

Thanks!

---

### Post by Anonii on 2007-06-18
**ifconfig > ~/ifconfig.txt && gedit ~/ifconfig.txt** should do that, but this is by no means the best way. Unfortunately, tho, I don't remember the switch to do it. Someone else will probably give you a better answer. (Notice that it will open a txt file with gedit for you to check the output.)

Also, you just created a question in my tiny mind. The ifconfig in my command above will be executed as root or as the normal user? Also, if I didn't add the ~/ before it, where would ifconfig.txt be saved? If someone can answer this, I'd be grateful.

---

### Post by kerry_s on 2007-06-18
Well if i'm reading the man page right, you would use -C to capture the output.

xterm you would use> xterm -hold -e ifconfig

[http://www.die.net/doc/linux/man/man1/aterm.1.html](http://www.die.net/doc/linux/man/man1/aterm.1.html)

---

### Post by hypersire on 2007-06-18
> **kerry_s said:**
> Well if i'm reading the man page right, you would use -C to capture the output.

xterm you would use> xterm -hold -e ifconfig

[http://www.die.net/doc/linux/man/man1/aterm.1.html](http://www.die.net/doc/linux/man/man1/aterm.1.html)

Hmm, it works for xterm but not aterm (using -e ifconfig and the -C flags). The aterm terminal window doesn't stay.

Dang... and I need to use aterm too (using transparency).

---

### Post by kerry_s on 2007-06-18
As far as terminal's go, that's a pickle. ;)
Have you tried using conky for those commands?

i see a option in the man pages that looks like it would work, i think i used something similar for viewing the logs some time back, anyways i think it's something you should look at/try->

exec command 
Executes a shell command and displays the output in conky. warning: this takes a lot more resources than other variables. I'd recommend coding wanted behaviour in C and posting a patch.

man page-> [http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

---

### Post by jayanth on 2008-02-14
Hi,

**xterm -hold -e *<command>*** holds the display all right, but the terminal remains unusable as far as running further commands is concerned. Could anyone please tell me how to make sure a command like **xterm -hold -e ls** displays the contents of the current directory, *and also* makes the command prompt available for running further commands?

Thanks,

Jayanth

---

### Post by Mothinator on 2008-02-14
Try putting an & at the end. This will background the process.

---

### Post by jayanth on 2008-02-14
That doesn't seem to help; it just sends xterm into the background.

---

### Post by jayanth on 2008-02-18
Anyone?

---

