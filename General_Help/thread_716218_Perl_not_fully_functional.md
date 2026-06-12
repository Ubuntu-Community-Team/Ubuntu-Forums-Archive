---
title: "Perl not fully functional?"
date: 2008-03-05
forum: General Help
---

### Post by mrz on 2008-03-05
I'm not sure that perl is correctly installed and fully enabled. If I give a command like
$ perl  myscript.pl
it works. But if I just use the filename
$ myscript.pl
I get a "command not found" error. Isn't this supposed to run?

Also, if I have a web page with an embedded script, when I load the page it doesn't run. Is that the same problem?

Help on how to fix this would be appreciated. Am running ubuntu 6.06 with Apache2 installed.

---

### Post by wirelessmonkey on 2008-03-05
Have you set your script as executable?  sudo chmod +x myscript.pl


Also, you need to specify the file's location, so rather than $ myscript.pl try $ ./myscript.pl

If your embedded script doesn't run after that, post back.

---

### Post by munkyeetr on 2008-03-05
And if you want to be able to run it no matter what your current working directory is, copy it into /usr/bin and make sure you have permissions to run.

Then from any terminal just type myscript.pl (you can actually even remove the .pl from the name and just type myscript)

---

