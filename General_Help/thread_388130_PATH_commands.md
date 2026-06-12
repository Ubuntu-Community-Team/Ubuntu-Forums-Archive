---
title: "PATH commands"
date: 2007-03-19
forum: General Help
---

### Post by woland on 2007-03-19
I need to manage my $PATH variable during my working session.

Is there any good manual to the PATH?
How do I edit my default PATH values?
How do I revert to default after I made changes?
How do I remove a value from PATH?

Thanks in advance!

---

### Post by denver on 2007-03-19
you can try reseting your PATH variable. Basically to set a variable you just type

> export VARIABLE=value

in this case its something like

> export PATH=$PATH:/aditional/path

the above command will add to your current path an extra folder ( /additional/path ).

 If you execute the command
> echo $PATH

you will be able to see which folders are in your current path. 
You could also just type

> export PATH="/home/<user>/bin:/home<user2>/bin"
and replace the whole thing with those 2 folders.

Keep in mind that you export that variable only for the current terminal session. If you wish to keep those settings you need to export it in your ~/.bashrc file.


NOTE!

folders are delimited by a semicolon ( : ).


to revert to your old PATH variable just source your bashrc file
> source ~/.bashrc

---

### Post by woland on 2007-03-19
Thanks!

I couldn't find manual for this anywhere...

---

