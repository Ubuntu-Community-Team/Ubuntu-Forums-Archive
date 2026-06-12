---
title: "[SOLVED] get rid of sudo"
date: 2007-08-25
forum: General Help
---

### Post by Chymera on 2007-08-25
My system freezes after i introduce my password in a graphical dialog (like you get with gksudo....). It does not freeze when i introduce it in a terminal (like with sudo...).

I tried to get this problem solved but it seems nobody has the faintest idea.

So in order to be able to do stuff on my comp (updates administrative tasks etc) i need to get rid of sudo, PERMANENTLY. I read up how you can disable it session-wise but i dont want to repeat that process every time i reboot. So how do i get permanent root permissions?

---

### Post by kerry_s on 2007-08-25
confusing.

you don't need to get rid of sudo. i think what your asking is how to turn on root. in terminal run> sudo passwd root
once you give root a password, you use "su" for administrative functions. if you don't want your user using sudo at all(not good idea) just remove from the admin group(su gedit /etc/group).

also instead of using gksudo, use gksu instead.

---

### Post by Chymera on 2007-08-26
I read your sugestion somewhere else but it seems to only impact my rights while  im am in a terminal. which isnt of any help pecause entering the password there would not give me any trouble.

I need to get rid of sudo because otherwise i would have to run every administrative task from the terminal, like typing "sudo synaptic", instead of just clicking it. In the case of synaptic this may not be a problem, but i cannot remember the name of every aplication that requires root privileges.

---

### Post by kerry_s on 2007-08-26
removed unsafe suggestion. :) please try the 1 below

---

### Post by Dark Star on 2007-08-26
Nice tip there kerry :) Thanks :D

---

### Post by Chymera on 2007-08-26
> **kerry_s said:**
> i just don't understand how you graphical can be messed up, but than again it's ubuntu, they hack all kinds of stuff instead of doing it the right way.
Neither does anybody else, its so annoying, not to mention i lost unsaved info about 4 times before realizing that the graphic dialog was behind the crashes...

What do you mean by "they hack it instead of doing it properly"?

---

### Post by eentonig on 2007-08-26
So, in stead of resolving your problem, you preffer to use a dangerous workaround?

Don't come complaining how insecure linux is when you get hacked.

---

### Post by kerry_s on 2007-08-26
okay that was easier than i thought.
so here go's
in terminal

sudo mv /usr/bin/gksu /usr/bin/gksu.old
sudo gedit /usr/bin/gksu
put>

```
#!/bin/sh
xterm -g 30x0+0+0 -e sudo "$@" &

```

then, make it executable>
sudo chmod +x /usr/bin/gksu


try that out and let me know if it works for you, mind you i don't even have gksu installed on my system and that works for me.

hmm, not elegant is it. added set size and shoved it into the top left corner.

---

### Post by Chymera on 2007-08-26
> **eentonig said:**
> So, in stead of resolving your problem, you preffer to use a dangerous workaround?

Don't come complaining how insecure linux is when you get hacked.
If you would be kind enough to read through my entire first post you may come across a point where i state that i have already tried solving the problem but it seems nobody has the slightest idea of what the cause could be.

Furthermore, if you cannot help please refrain from posting and maybe think twice about what you say (you may not have noticed it but your last phrase implies that all linux distributions not implementing sudo are insecure, which is total bullcr@p)

---

### Post by Chymera on 2007-08-26
> **kerry_s said:**
> okay that was easier than i thought.
so here go's
in terminal

sudo mv /usr/bin/gksu /usr/bin/gksu.old
sudo gedit /usr/bin/gksu
put>

```
#!/bin/sh
xterm -g 30x0+0+0 -e sudo "$@" &

```

then, make it executable>
sudo chmod +x /usr/bin/gksu


try that out and let me know if it works for you, mind you i don't even have gksu installed on my system and that works for me.

hmm, not elegant is it. added set size and shoved it into the top left corner.

what is that little black box i get?

---

### Post by kerry_s on 2007-08-26
that's the xterm used to put in your password,  before it launches the application, it's like if you opened a xterm and typed sudo app-name, this is just automating it for you, you just put your password. i haven't figured out how to make it close after the application is launched, it stays till you close the application, that's why i put it out of the way. if you prefer it in a different spot(30x0+0+0=width x height + across +down)

well enough for me tonight, got to hit the sack. if you have a way you want it let me know, we can even add a title if you want> xterm -g 50x0+0+0 -T "Please enter your Password" -e sudo "$@"

---

### Post by Chymera on 2007-08-26
woah 10x a lot... i dont think i got any support of this kind since i first came to the forums :)

The strange thing is that i can do whatever i want to do without entering any password in the box :confused: furthermore, i wenmt to usergroups and saw 2 accounts, mine, and "root" is this normal? i thought there was no root account in ubuntu? maybe i created it while implementing that solution that worked only in terminal sessions... is it safe to delete it?

It seems we're on opposite sides of the atlantic if its time for you to hit the sack..

---

### Post by kerry_s on 2007-08-26
> **Chymera said:**
> woah 10x a lot... i dont think i got any support of this kind since i first came to the forums :)

The strange thing is that i can do whatever i want to do without entering any password in the box :confused: furthermore, i wenmt to usergroups and saw 2 accounts, mine, and "root" is this normal? i thought there was no root account in ubuntu? maybe i created it while implementing that solution that worked only in terminal sessions... is it safe to delete it?

It seems we're on opposite sides of the atlantic if its time for you to hit the sack..

no don't delete root, there is a root account it's just disabled but is still needed.

did you already do the no password thing, you don't need that if your going to use the gksu replacement. you can put that back the way it was and it will make you type in the password.

yeah it's 1 am here in hawaii

---

### Post by aidanr on 2007-08-26
are you using compiz/compiz fusion/beryl/desktop effects?

---

### Post by Chymera on 2007-08-26
yes, Iam using compiz fusion...

---

### Post by aidanr on 2007-08-26
[http://forum.compiz-fusion.org/showthread.php?t=2250](http://forum.compiz-fusion.org/showthread.php?t=2250)

---

### Post by por100pre1 on 2007-08-26
> **kerry_s said:**
> no don't delete root, there is a root account it's just disabled but is still needed.

did you already do the no password thing, you don't need that if your going to use the gksu replacement. you can put that back the way it was and it will make you type in the password.

yeah it's 1 am here in hawaii

Gnome saves superuser settings in root folder, if you delete it many programs won't load with su, gedit for example.

---

### Post by Chymera on 2007-08-26
> **aidanr said:**
> [http://forum.compiz-fusion.org/showthread.php?t=2250](http://forum.compiz-fusion.org/showthread.php?t=2250)

The link seems to be broken

---

### Post by aidanr on 2007-08-26
it's working for me

> I have had this issue since one of the Beryl versions. You can avoid this situation by going to the System menu -> Preferences -> Accessibility -> Assistive Technology Preferences and enabling Password dialogs as floating windows. This disables the screen-darkening fade effect, the drawback being that the focus isn't locked to the password dialog (so you need to be careful not to type your password into the wrong window).

Also, I never found a hard reset to be necessary to escape this problem. Although the screen stopped updating, the system wasn't stalled. Aiming blindly at things was too much work, though, so I just hit Ctrl + PrintScreen (SysRq) + K and waited a few seconds for GDM to reload.
> Thank you, I use xubuntu (different menus), so I found the best way to do this is to enter this in Alt+F2:

gconf-editor

then click "apps", then click "gksu"...and then check the box to "disable-grab".

I found that it is the "grab" that I was having problems with...so if anyone knows how to fix that with out "disabling" it, then please let me know.
Reply With Quote
> in CCSM > General Options, disabling "Unredirect Fullscreen Windows" should fix this problem.

those were the suggestions posted, i'd also recommend try a newer version of cf such as [trevino's git repo]("http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/"), it may be fixed already

---

### Post by Chymera on 2007-08-27
> **kerry_s said:**
> okay that was easier than i thought.
so here go's
in terminal

sudo mv /usr/bin/gksu /usr/bin/gksu.old
sudo gedit /usr/bin/gksu
put>

```
#!/bin/sh
xterm -g 30x0+0+0 -e sudo "$@" &

```

then, make it executable>
sudo chmod +x /usr/bin/gksu


try that out and let me know if it works for you, mind you i don't even have gksu installed on my system and that works for me.

hmm, not elegant is it. added set size and shoved it into the top left corner.

how do i undo all that?

---

### Post by Chymera on 2007-08-27
> **aidanr said:**
> i'd also recommend try a newer version of cf such as [trevino's git repo]("http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/"), it may be fixed already

I am using that repo.... and i think it may be the cause of [some other trouble]("http://ubuntuforums.org/showthread.php?t=535365") im getting recently... could you link me to a repo which only has stabel official releases

---

### Post by kerry_s on 2007-08-27
> **Chymera said:**
> how do i undo all that?

**sudo mv /usr/bin/gksu.old /usr/bin/gksu**

---

### Post by Chymera on 2007-08-27
10x... all well now thanks to your precautions and that irish dude :P

---

### Post by Zootropo on 2007-08-27
Some time ago I wrote an article on how to edit the sudoers file so that sudo doesn't ask for a password. This may help you.

It's in spanish, so you will have to use google translator, babelfish or something like that
[Cómo hacer que sudo no nos pida contraseña y otros trucos relacionados]("http://mundogeek.net/archivos/2007/05/14/como-hacer-que-sudo-no-nos-pida-contrasena-y-otros-trucos-relacionados/")

---

### Post by Chymera on 2007-08-27
no need 10q, the problems already solved

---

