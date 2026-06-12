---
title: "how to make a (desktop) shortcut for java application"
date: 2014-08-29
forum: General Help
---

### Post by quina on 2014-08-29
hello!
I would like to have a shortcut/launcher for one aplication. I use this aplication almost everyday! I know how to make shortcut for standard applications.
I get this app from local authority and instruction how to start it.
App is located in directory:  /home/quina/Pulpit/eUPO  (Pulpit=Desktop in polish).
To start this app from terminal I use this command:
```
quina@quina-PC:~/Pulpit/eUPO$ sudo java -classpath .:lib/bcmail.jar:lib/bcprov.jar:lib/bctsp.jar com.coig.esp.upo.Main

```

Can anyone could help me?

---

### Post by dave131 on 2014-08-29
I make no promises here, but I *think* you could do the following:

open an editor and put the following text in:

#$bin/bash
cd /home/quina/Pulpit/eUPO
java -classpath .:lib/bcmail.jar:lib/bcprov.jar:lib/bctsp.jar com.coig.esp.upo.Main
read -p "Press enter to close this window" nothing

save that file as (for example) ~/mytest.sh

then in a terminal:

cd ~
chmod +x mytest.sh

Now try to execute it in the terminal:

sudo ./mytest.sh 
- it should ask for your password since you are using "sudo"

What I couldn't do is make it an actual desktop launcher as it appears it opens a new shell or something such that it doesn't interact with the screen.  What I was able to make work was putting the shell file itself in the Desktop folder - as an example:  cp ~/mytest.sh ~/Desktop, then just clicking on the mytest.sh on the desktop.  But then I also had to select "run in terminal" when the question pops up when I click on the mytest.sh file.

So, I'm not sure exactly what you need.  Someone can probably help you more as I'm at the end my knowledge right now.

---

### Post by quina on 2014-08-29
It's works!
thank You very much!

---

### Post by dave131 on 2014-08-29
I'm glad it worked for you.

---

