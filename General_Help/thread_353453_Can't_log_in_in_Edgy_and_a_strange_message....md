---
title: "Can't log in in Edgy and a strange message..."
date: 2007-02-04
forum: General Help
---

### Post by milagre23 on 2007-02-04
When I was trying to log in my Ubuntu Edgy I was blocked and get this strange message:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator"

It is possible that I'm out of disk space, but how can free some space if I can't get in the system? I don't know how to do it in recovery mode. I've also tried with a live-cd like Knoppix but it wont let me erase from the partition.

I'm desperate. Can anyone help me please?

Thanks for your attention

---

### Post by gradedcheese on 2007-02-04
You can switch to a text shell by hitting Control+Alt+F1 (actually F1 through F6 are text shells).  Now see how much disk space you have:

df -h

If you're really out of space, delete some files.  Otherwise, check the permissions for your home directory by using "ls -al" to list directories... you can switch back to the first graphical shell with Control+Alt+F7 when you are done.

---

### Post by Ramses de Norre on 2007-02-04
First: when following my instructions you can always press ctrl-alt-F7 to get back to your graphical screen when you get stuck in the console.

Press ctrl-alt-F1, log in and type this:
```
sudo aptitude clean
```
Which will remove all archives of already installed apps, this will give you back some space.
Beware that the error probably return soon if you don't make additional space later and this method wont work when /home is not on the same partition as /, in that case you'll need to use rm -r to delete files from /home, or mv to move them somewhere else.

---

### Post by milagre23 on 2007-02-04
> **Ramses de Norre said:**
> First: when following my instructions you can always press ctrl-alt-F7 to get back to your graphical screen when you get stuck in the console.

Press ctrl-alt-F1, log in and type this:
```
sudo aptitude clean
```
Which will remove all archives of already installed apps, this will give you back some space.
Beware that the error probably return soon if you don't make additional space later and this method wont work when /home is not on the same partition as /, in that case you'll need to use rm -r to delete files from /home, or mv to move them somewhere else.


The "sudo aptitude clean" Worked. 
Thank you very much.

---

