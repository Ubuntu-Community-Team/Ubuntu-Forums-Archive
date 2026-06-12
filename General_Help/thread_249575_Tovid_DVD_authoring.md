---
title: "Tovid DVD authoring"
date: 2006-09-02
forum: General Help
---

### Post by skeff on 2006-09-02
Hi everybody!

First, thanks to grepper for helping me a bit :)
After a bit of searching and fiddling about, I eventually found my favourite DVD authoring program; Tovid

It's been mentioned here and there but hasn't been brought the proper glory it deserves yet I think.

In the Tovid suite there is a script called 'todisc', this is my favourite so far. It also has a "demo gui" called 'todiscgui' but I haven't tried it. With this script you can basically tell it what movie files you want on your DVD, feed it a menu background image and a bunch of other options, like animated submenus and 3d thumbnails, and it will transcode the movies and output a DVD structure, ready for image making. It creates pretty menus automatically.
[New Todisc commandline options]("http://tovid.wikia.com/wiki/Tovid_changelog/upcoming#todisc")

[Here's an example]("http://phebehouse.dyndns.org/tovid/outline.avi") of 3D buttons and showcase, with -wave and -rotate

Tovid or tovidgui is a user-friendly interface for authoring with videos or creating picture slideshows.

Tovid homepage:
[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")

IRC Channel on freenode.net: #tovid
(but remember to check the homepage for solutions and answers first, as is the community courtesy)

Ubuntu (edgy eft) installation:
---

You should download and compile from the **SVN** sources, follow the instructions on the homepage.
You will need **python-wxgtk2.6** and **txt2tags**, and of course **build-essentials**. There might be more dependencies, but they will most likely be found in the ubuntu repositories.

To avoid that python won't find some tovid files, you should use --prefix /usr when running ./configure:
```
./configure --prefix /usr
```

Also I discovered one problem with the Ubuntu system: dash (debian almquist shell) which is a minimalistic bash shell. The problem is that it's not bash and /bin/sh usually links to /bin/dash while most bash scripts expect to find bash when executing sh. So tovid won't actually work out of the box, until you;
```

sudo -s
cd /bin
rm sh
ln bash sh
exit

```

Have fun! :))

-skeff

---

### Post by user1397 on 2006-11-16
yes, tovid is awesome!
i have made a guide on how to use it (quite basic, but it does include an easy installation script which i made)

its the first link in my sig!

---

### Post by volksolwagen57 on 2007-10-05
i have two dvd drives and one of them is broken. i use:
> makedvd -burn DeathProof
and it searches for usable media in the broken dvd drive. How can I change the setting so it reads my working dvd drive. I don't really want to take remove the drive yet. Granted this will fix the problem, I would just like to know. Thanks in advance.

---

