---
title: "gksudo problem"
date: 2008-02-05
forum: General Help
---

### Post by EmoDx on 2008-02-05
Hey, I am having a problem using wifi radar. When I try opening it from the K menu, the app won't load. So I tried to fool Kubuntu by loading as a panel app, then opening it. When I do that, I get this error:

```

KDEinit could not launch 'gksudo'.:
Could not find 'gksudo' executable.

```

So I thought I was smarter than I actually am, and typed this and got this response in the terminal:

```

emodx@Micron-GX:~$ sudo apt-get install gksudo
[sudo] password for emodx:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gksudo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gksudo has no installation candidate
emodx@Micron-GX:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
emodx@Micron-GX:~$

```

Also, when I installed gbindadmin, I got the same thing, the app would not load from the K menu. I am running Kubuntu 7.10 I386. Thanks in advance.

-Emo

---

### Post by yabbadabbadont on 2008-02-05
I believe that it is provided by the "gksu" package.

---

### Post by bodhi.zazen on 2008-02-05
kde uses kdesu, try editing your launcher changing the command from "gksu ...." to kdesu

Else you could make a link, 

ln -s /usr/bin/kdesu /usr/bin/gksudo

---

### Post by EmoDx on 2008-02-05
Hi, my name is Emo, and I am a point and click abuser... LOL. Can you dumb it down for me? I can navigate to the gksudo file, right click to edit it as root, then what do I do to make it work? Thanks for the help.

-Emo

---

### Post by bodhi.zazen on 2008-02-05
Well, you do not want to edit the file.

I assume from your post you are using kde, and from your terminal it does not appear gksu (gksudo) is installed.

I am advising you edit your KDE menu or the launcher. In the command box there is a command 

something like gksudo bla bla bla

change it to kdesu bla bla bla

If that fails, in a terminal, enter :

```
sudo ln -s /usr/bin/kdesu /usr/bin/gksudo
```

That creates a symbolic link, linking gksudo to kdesu, so when you enter :

gksudo you will run kdesu. Kind of a work around.

---

### Post by EmoDx on 2008-02-05
Ok, I ran the command line first. I got an icon on the task bar stating wifi was loading. THen it went away w/o actually starting the app. Then I make the change in the command swapping out gksudo for kdesu. Same thing. Any ideas?

Second, should I be running the latest version of Kubuntu? The only reason I am running it right now is because I like the way the dektop feels vice the plain old Ubuntu desk top. But, if I get better compatibility from Ubuntu w/ no headaches of a desk top that hasn't worked out the bugs, I am going with works great all the time. What do you think?

-Emo

---

### Post by EmoDx on 2008-02-06
^^^Top^^^

---

