---
title: "Where are the desktop configuration files are?"
date: 2007-01-02
forum: General Help
---

### Post by mgarcia-val on 2007-01-02
Is there a way of locking access to desktop configuration files, meaning basically, screen resolution, desktop background, panels, fonts and so on? I really need to lock them for regular users to keep my computer going, allowing only the admin to make the relevant changes.

mgarcia-val

---

### Post by koenn on 2007-01-02
the gnome desktop configuration is saved in a large collection of xml files. If you're not familiar with xml, this is a bit of a problem because xml files are structured, and gnome uses a directory trees to organise them, so it can be like looking for a needle in a haystack. 
On top of that, you have system-wide settings and user-specific settings, and mandatory settings and default settings (defaults can be modified by the user). 
you'll find examples in the hidden directories in a user home, and in /etc/gconf. 

The whole system is documented on the gnome webstite, but even then it's not easy.

Luckily, there are some tools that can be used to change (and lock) these setings : look for

- gconf-editor
- pessulus
- sabayon
-gconf-tool2

 the first 2 are GUI apps where you can set settings, 
sabayon is very complete ; it works by showing you a desktop that you can customize, then saves all your changes in a "desktop profile" that you can apply to 1 or more users. You can lock down the changes you've made so users can't change them back. Works well but is still very much in an early stage of development (or so it was when i played with it about 6 months ago) so you 'll need to take your time to figure out how stuff works, and there will be bugs and tings you have to fix by "by hand"

I've experimented with those a while back, you can read my notes here :
[http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)
the page also has links to firther documentation

---

### Post by mgarcia-val on 2007-01-03
Thanks very much. It looks like there's plenty of information here.

Pessulus might do the job for what I want it and seems more GUI oriented. So I think I'll try it out  first, see if it can ban access to System > Preferences and System > Administration, and if this doesn't work, then go for Sabayon, which requires, if I'm not wrong, much more work.

Don't you think that Pessulus would be enough for it?

mgarcia-val

---

### Post by koenn on 2007-01-03
> **mgarcia-val said:**
> 
Don't you think that Pessulus would be enough for it?

depends on how much you want to configure and lock down. give it a try, it's fairly easy

---

### Post by mgarcia-val on 2007-01-04
I've tried Pessulus but that's definitely not what I'm looking for.

I want to lock down:

-panels
-desktop background
-fonts
-manu layout
-themes
-screen resolution
-screen saver
-about me (since this feature lets a user change his password!)

Would Sabayon lock all that?

mgarcia-val

---

### Post by koenn on 2007-01-04
as I said, Sabayon lets you design a deskyop the way you want it, save it as a "profile" , and apply it to users. You (the admin) will decide what will be locked and what not.

---

### Post by mgarcia-val on 2007-01-04
Thanks very much for your patience.

I've installed Sabayon and it is already running.

There's only one thing. You say in: 

[http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

that after you've finished, to be save you must uninstall alacarte. But that seems to me quite a drastic measure. I'm wondering whether you could use chmod to lock read and executing permissions for any other user than the root instead of uninstalling it. Problem: I don't know whether this can be safely done and where is the folder and file I should be looking for.

What do you think?

---

### Post by koenn on 2007-01-04
my approach was : if it 's not needed, it shouldn't be there ; then you're sure it will not be used. 

i suppose you can also set permissions so that only root / you can run it; you'll have to try.
you can find the location of programs in linux with 'which' - so if you type "which alacarte" at a command prompt (in a terminal), you'll see this :

```
t@x:/home/kn# which alacarte
/usr/bin/alacarte
```

---

### Post by mgarcia-val on 2007-01-04
Well, the funny thing is that after I find alacarte and set permissions this way:

```
sudo chmod go-rx /usr/bin/alacarte
```

I can still run alacarte right-clicking on the top-panel and clicking on 'Edit Menus'. 

I can't understand why. In principle, denying reading and executing permissions on /usr/bin/alacarte I myself shouldn't be able to run alacarte even without switching users.

That's the only I'd need to overcome: running alacarte right-clicking on the top.

---

### Post by koenn on 2007-01-04
yep; i see that too - 
I don't understand it either, but syspect gnome is doing something there to make it happen anyway. No idea what, though.

---

### Post by mgarcia-val on 2007-01-05
One gets the impression that Gnome is somehow cheating.

I've also tried to move /usr/bin/alacarte to another directory, but it looks as if Gnome has got a copy of it and easily run it when the system can't find alacarte in its place. All things considered, I resign myself to uninstall alacarte and install it again whenever I need it.

By the by, if running Sabayon you choose the menu you want for your user and block it, even if the user could run alacarte, could he restore the menus/icons you've taken away?

mgarcia-val

---

### Post by koenn on 2007-01-05
> if running Sabayon you choose the menu you want for your user and block it, even if the user could run alacarte, could he restore the menus/icons you've taken away?

don't know really - O expect not.
Then again, if you think in terms of locking down a deskop, you kinda  expect that sooner or later there will be a user that tries to circumvent the limitations you've imposed, and might find a loophole based on a combination of circumstances that you haven't anticipated. 
That's the main reason I like to remove stuff that is not needed : less chance that such a combination of circumstances can occur. 

As to your question : just try. Experiment. find out. You seem to be doing fine so far, and you'll get to understand so much more of what yiu've done and what the possibilities and limitations of your work are if you try and find out for yourself.

---

