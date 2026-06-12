---
title: "Bad icons arrangement in notification area when it's on a vertical panel"
date: 2008-04-29
forum: General Help
---

### Post by Alex Kay on 2008-04-29
Hello there,

I'm pretty new to Linux, hope I'm not asking something terribly obvious.

In XP and Vista I always docked my task bar vertically on the left. That makes sense when using a wide-screen monitor since the vertical space is limited and I want to give it to applications.

In this setup, the start menu button is in the top-left corner, then goes the quick launch tool bar, then the list of open programs, then the notification area with a dozen of icons, and finally the system clock.

I reproduced this in Ubuntu more or less successfully as shown in the first attachment. I did it by going to the panel properties, setting orientation to "Left" and size to 160 pixels.

As you can see the notification area looks rather icky. It doesn't arrange icons horizontally, all of them are stacked vertically which eats up the space.

In addition, the icons have different sizes, some of them are very big, up to 48px.

I tried to do the same in a Kubuntu VM and it worked out of the box by just dragging the bottom bar to the left side of the screen. The result is attached.

I could of course stop complaining and just install KDE, but:

1. Gnome seems to have more users and better support.
2. Other people probably have the same issue, and I'd rather it's fixed once and for all.
3. I quite like some of the Gnome applications and hate the idea of shopping around (again!) for their KDE counterparts.

Thanks for reading!

---

### Post by Alex Kay on 2008-04-30
KDE, here I come... ;)

---

### Post by Zorael on 2008-05-01
KDE is arguably larger than Gnome among **linux** users, but as it is the default in Ubuntu these forums are mostly gnomey. :>

I find KDE to be more "fleshed out" than Gnome (this being a good example), but the whole KDE-vs-Gnome discussion is likely to continue when the world ends.

Durandal is a hardcore KDE fan, see. And he totally changed his mind, choosing instead to stay alive. KDE wins!

---

### Post by Alex Kay on 2008-05-01
Thanks for your comment, Zorael!

I've been reading a lot of reviews/opinions last two days and testing various KDE distros. From what I tested I like the most Mandriva and openSuse. 

Fedora is not bad too, but I don't feel comfortable with their 'cuttin edge' philosophy. In particular, KDE 4.0 is very unstable and stubborn, alas I cannot even move the panels around!

I didn't like Kubuntu that much, Ubuntu is much more polished.

Damn, all this testing/research takes a lot of time but I hope it will pay in the end...

---

### Post by Andre-D on 2008-05-01
Now, back to the topic ... what about this bug ?

Same problem with "windows-list" - place it vertically, make it 120pixel wide, open 10-15 windows... and notice strange alignment.

---

### Post by Alex Kay on 2008-05-02
> **Andre-D said:**
> Now, back to the topic ... what about this bug ?

Same problem with "windows-list" - place it vertically, make it 120pixel wide, open 10-15 windows... and notice strange alignment.

Andre,

The only solution I could find is installing the panel from xfce as explained [in this thread](http://ubuntuforums.org/showthread.php?t=583908). HTH.

---

### Post by Andre-D on 2008-05-02
thanks :)

---

### Post by Alex Kay on 2008-05-03
This bug is already in Bugzilla database:
[http://bugzilla.gnome.org/show_bug.cgi?id=428943](http://bugzilla.gnome.org/show_bug.cgi?id=428943)

[Edit]
I added a new bug report which describes only the notification area behaviour:
[http://bugzilla.gnome.org/show_bug.cgi?id=531371](http://bugzilla.gnome.org/show_bug.cgi?id=531371)

---

