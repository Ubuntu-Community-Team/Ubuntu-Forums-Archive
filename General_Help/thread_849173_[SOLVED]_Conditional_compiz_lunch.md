---
title: "[SOLVED] Conditional compiz lunch"
date: 2008-07-04
forum: General Help
---

### Post by OmaDessala on 2008-07-04
Hello everyone, 

It's not a problem I have, just a question : 
I have compiz installed and working on my laptop (ubuntu hardy heron).

It lunch at startup, but I'm trying to find a way for a conditional lunch.

In my mind, it would be a shell-script or something, executed at startup that depending on a test (like what kernel version I am actually running) would make compiz start or not.

I think I have found the file that tells gnome what window manager to start : ~/.gconf/desktop/gnome/applications/window_manager~>%gconf.xml, 

But I know nothing about xml or the way gnome use this file...

Anyone, any idea?

---

### Post by OmaDessala on 2008-07-04
up...

Someone?

---

### Post by Kevbert on 2008-07-04
Have you had a look at [[COLOR="Red"]compiz-switch[/COLOR]]("http://forlong.blogage.de/article/pages/Compiz-Switch").  You can turn compiz on and off as you please.

---

### Post by OmaDessala on 2008-07-05
Thanks for the link, interesting stuff, I will try it later as I'm not on my Ubuntu right now.

However, reading the blog I am not sure it would permit to make an automatic choice at stratup... we'll see

---

### Post by sayakb on 2008-07-05
Make up a script that looks like this:
```
#!/bin/bash
STR=`uname -r`
if [ "$STR" = "2.6.24-19-generic" ]; then
  compiz --replace &
else
  metacity --replace &
fi

```

And save it as compizscript.sh in, for example, **/home/Documents**
Now do:
```
sudo chmod u+x /home/Documents/compizscript.sh
```

Now goto **System->Preferences->Sessions**, click **Add** button. Enter the **Name** as *Compiz Scipt* or whatever you like. Enter the **Command** as:
```
sh /home/Documents/compizscript.sh
```
Press **OK** button and close the Session Properties window.
Restart X to check if it works (Press Ctrl+Alt+Backspace)

---

### Post by OmaDessala on 2008-07-06
I was a bit afraid that I wouldn't work, but I was wrong!

Thanks for the help

((My initial "problem"  was that my second kernel is patched to run RTAI and this one really dislike compiz...))

---

### Post by sayakb on 2008-07-06
Glad I could help!
Please mark the thread as solved :)

---

