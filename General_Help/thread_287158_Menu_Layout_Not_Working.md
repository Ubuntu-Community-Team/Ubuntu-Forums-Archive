---
title: "Menu Layout Not Working"
date: 2006-10-28
forum: General Help
---

### Post by Sethro on 2006-10-28
Hello,

I just installed Ubuntu 6.10 and Iam running into some problems with the "Menu Layout" located in 

System- Preferences- Menu Layout

The thing is that I cant modify the names of any programs and I cant make them dissapear from the menu like I could with the Alacate Menu Editor in Ubuntu 6.06. Its not reponding at all.

I tried reinstalling through synaptic, but it wont work.

Also how do I stop ubuntu from restarting by pressing backspace and shift. In other words how do I make it stop. 


Thanks

---

### Post by Sethro on 2006-10-28
Anybody?... Guys...

---

### Post by PriceChild on 2006-10-28
Ok... Menu Layout IS Alacarte with a different name.

Try```
sudo chown <<your username>>:<<your username>> -R /home/<<your username>>
``` To sort out alacarte.

You've neglected to tell us that you are running xgl/compiz... that information might be handy for me to fix your shift+backspace "feature"

Fix shift+backspace with:```
xmodmap -e “keycode 22 = BackSpace BackSpace”
```

---

### Post by Sethro on 2006-10-28
Yes sorry about that iam running XGL Berly.

I tried that code for the backspace problem but I get :

sethro@sethro-laptop:~$ xmodmap -e &#8220;keycode 22 = BackSpace BackSpace&#8221;
xmodmap:  unknown command on line commandline:1
xmodmap:  unable to open file '22' for reading
xmodmap:  unable to open file '=' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  unable to open file 'BackSpace&#8221;' for reading
xmodmap:  5 errors encountered, aborting.
sethro@sethro-laptop:~$

---

### Post by Sethro on 2006-10-29
The werid thing with alacate is that I cant edit any of my options it just wont respond

---

