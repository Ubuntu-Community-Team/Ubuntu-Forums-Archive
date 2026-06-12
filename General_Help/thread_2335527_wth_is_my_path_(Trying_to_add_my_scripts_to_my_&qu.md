---
title: "wth is my path? (Trying to add my scripts to my &quot;command list&quot;)"
date: 2016-08-29
forum: General Help
---

### Post by Delupara on 2016-08-29
I'm trying to modify my $PATH so it can read scripts command I made as a command. Not only it doesn't work but the path is... well weird. Take a look at this:

> /home/delupara/scripts:/home/delupara/bin:/home/delupara/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin


^this is my path

> /home/delupara/scripts:....

^my scripts are in there. But I want you to take a look at this

> /home/delupara/bin

^this doesn't exist on my system. I'm gonna assume it's normal. But in case it isn't let me know.

So in any case, why won't any of my scripts get called?

---

### Post by 1clue on 2016-08-29
$HOME/bin is a typical addition to $PATH.
$HOME/scripts is atypical, you probably added that yourself from the sounds of it.
$HOME/.local/bin I've never heard of.  Is something there? If so what is it?
/snap/bin is atypical
The rest of that is something you would expect on a Linux box.

---

### Post by Delupara on 2016-08-29
The only thing I've added is $HOME/scripts The rest was auto generated.

---

### Post by &amp;KyT$0P# on 2016-08-29
Are your scripts **directly** in [FONT=Courier New]/home/delupara/scripts[/FONT] (not in a subdirectory) and do you have execute permission on the files?

---

### Post by Delupara on 2016-08-29
apparently I had to restart my bash command. thanks everyone.

However if people wants to figure out what $HOME/.local/bin and /snap/bin is, because I haven't put them there

---

### Post by Keith_Helms on 2016-08-30
$HOME/bin is the usual place for a user's scripts.  The directory may not exist after a new user is created, but the default path created for that user will include that directory.  I'd get rid of the "scripts" directory and use bin instead.

If you didn't create $HOME/.local/bin or /snap/bin then something you installed probably added them to your path.

---

### Post by 1clue on 2016-08-30
I found this: [http://snapcraft.io/](http://snapcraft.io/)

Did you install this software? That might explain /snap/bin

---

