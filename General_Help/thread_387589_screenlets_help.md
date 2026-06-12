---
title: "screenlets help"
date: 2007-03-18
forum: General Help
---

### Post by feest on 2007-03-18
Hi i've recently installed screenlets, but now i've added the mail check thing and everytime it loads the mail check  thing it locks up. how do i stop that thing from launching or where is the config file of screenlets saved so i can reset it?

---

### Post by danielduarte on 2007-03-19
happened the same thing to me... always lock up. It's so stupid =P. I already tried to remove it (actually, i removed screenlets) and installed it again. Nothing done. I dunno where the config file is.
Anybody knows? Please?

tks...

---

### Post by feest on 2007-03-21
if you wan't to solve this rename the folder of the mail screenlet (i.e. checkmail to checkmaildontuse) in this way you can use screenlets again.

---

### Post by FaceLeg on 2007-03-23
> **feest said:**
> if you wan't to solve this rename the folder of the mail screenlet (i.e. checkmail to checkmaildontuse) in this way you can use screenlets again.

Still doesn't work!  

So far my screenlets experience has been: 

```
screenletsd start
screenletsd add control
```

Right Click Control > Add > Mail Checker

Freeze...

```
faceleg@faceleg-desktop:~$ screenletsd stop
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Screenlets-daemon stopped.
```

Stopped?  Really?

```
faceleg@faceleg-desktop:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Screenletsd is already running - stop the running daemon first.
```

Ad infinitum...

---

### Post by FaceLeg on 2007-03-23
Try this:

```
sudo gedit ~/.config/Screenlets/screenletsd.ses
```

Didn't work for me though...

Though following the relevant parts of this thread did:

[http://ubuntuforums.org/showthread.php?t=356314&page=13&highlight=screenlets]("http://ubuntuforums.org/showthread.php?t=356314&page=13&highlight=screenlets")

Just don't try the MailChecker again!

---

### Post by stickx911 on 2007-05-17
sudo gedit ~/.config/Screenlets/screenletsd.ses

That command worked for me. Just remove the line for mailchecker.

Thanks guys!

---

### Post by lajja on 2007-05-27
Thanks, worked great :)

---

