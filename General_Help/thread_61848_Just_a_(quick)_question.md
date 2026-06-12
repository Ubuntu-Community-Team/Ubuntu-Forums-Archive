---
title: "Just a (quick) question"
date: 2005-09-02
forum: General Help
---

### Post by Havoc on 2005-09-02
So, I have a question to ask you.
How can I, when running "make install", have the program register itself in synaptic, or whatever (Or APT in general)?  :? 
Meaning, when I e.g compile wine, I then have to keep the whole 700 MB folder for one sleazy "make uninstall" session.And I can't do that any longer.  :^o 
I don't mean building a package from compiled sources, mind you.I just want an option which registers the files added to /usr through "make install", so that I can uninstall them using something (synaptic, dpkg, whatever).
I know it can be done cause I read it somewhere in these forums, but I can't remeber where!

Thanks!  :grin:

---

### Post by KingBahamut on 2005-09-02
Havoc, I dont think there is a way to link compiled binaries or sources to synaptic or apt get without there being created a deb for it, if for no other reason, the fact that apt's database is whats used to compare whats installed vs not installed vs upgradeable.

---

### Post by Havoc on 2005-09-02
Uhhhh,crap.

Yes, but what's the difference between "make install" and "dpkg -i ..."?
They both create the program folders,scattered somewhere in the filesystem (such as /usr/share, /usr/bin, /usr/lib, and so on...), the only difference is (I guess...) that when installing a .deb file, the system also keeps track of what folders and what files and what configurations (Whatever, you know what I mean) were done in the process.That's what I'm looking for.A way for the system to keep track of everything related to the program, through Synaptic (or anything else).Upgrades through normal packages could be done by deleting all previous' versions' files, and replacing with the newer versions' ones.Or not, anyways.   :roll: 

I would thank you for any additional feedback.
Also, thank you KingBahamut.I hope you become Tiamat, one day.  ](*,)

---

### Post by mlomker on 2005-09-02
I'd recommend that you apt-get install checkinstall

It's a script that creates a .deb file after you'd compiled the source.  Once it is a .deb you can use dpkg to install it and it'll be listed in synaptic like everything else.  It's *not* going to automatically figure out dependencies and whatnot for upgrades, but it'll allow you to remove the old version in synaptic before installing a new one.

---

### Post by Havoc on 2005-09-02
Hey, thanks!!!  :wink: 

I guess that will work!

Do the packages work as usual (Well, with no info on dependancies, no description, no nothing), or are they just for use on my system?

Anyways, this could work as a nice workaround till I get off my but and learn how to make proper packages.

THANK YOU

---

### Post by az on 2005-09-02
[QUOTE=mlomker]I'd recommend that you apt-get install checkinstall

It's a script that creates a .deb file after you'd compiled the source.  Once it is a .deb you can use dpkg to install it and it'll be listed in synaptic like everything else.  It's *not* going to automatically figure out dependencies and whatnot for upgrades, but it'll allow you to remove the old version in synaptic before installing a new one.[/QUOTE]


Checkinstall is installed by default, as far as I know.

This is what you need.

"Yes, but what's the difference between "make install" and "dpkg -i ..."?
They both create the program folders,scattered somewhere in the filesystem (such as /usr/share, /usr/bin, /usr/lib, and so on...), the only difference is (I guess...) that when installing a .deb file, the system also keeps track of what folders and what files and what configurations "

There is a big difference.  Make install runs a script which copies files ont your system.  A deb package is an archive of the files to be copied as well as preinstall, postinstall, preremove and postremove scripts.  It is also part of a system of dependancies which ensure that the package you are installing will not break your syste,  It will also not remove another package's file.  
It also means that someone very well qualified (a debian developer, or similar) has taken the time to work out any problems with the application installing and running on your system.  The debian policy manual is an intricate set of rules to follow which are made to ensure top quality packages.

You do not get this with make install.

So, checkinstall will make your make-install into a deb package which is of marginal quality.  That is, it will install and be removed from your system and show up in synaptic, but it is not guaranteed to work:  For example, if the package tries to overwrite a file that is alread in your system, the installation of that packages will fail.

What app are you trying to install from source?

---

### Post by Havoc on 2005-09-02
Well, I installed checkinstall, and it's quite unusable (At least for me).It messes up, and can't install the packages it made because it's gonna overwrite (random) files, not connected to the package I'm installing, such as Skype documentation when installing advancemame.duh.  :???: 

As for your question, azz, I'm not *trying* to compile anything.It's just that, I' need a better way to keep record of my stuff, and since most stuff in hoary repos are a little bit outdated (I'm the kinda guy that can't sleep right if he's not getting the latest and greatest), and the backports aren't complete yet,so I compile most of the (non essential) programs I use.So, in order to uninstall all the crap I've amassed over the millenia, I have to keep the whole folders of compiled source.And I have to tell you, It's not pretty.So, that's what I need, pretty much.  :wink:

---

### Post by az on 2005-09-02
[QUOTE=Havoc]Well, I installed checkinstall, and it's quite unusable (At least for me).It messes up, and can't install the packages it made because it's gonna overwrite (random) files, not connected to the package I'm installing, such as Skype documentation when installing advancemame.duh.  :???: 

As for your question, azz, I'm not *trying* to compile anything.It's just that, I' need a better way to keep record of my stuff, and since most stuff in hoary repos are a little bit outdated (I'm the kinda guy that can't sleep right if he's not getting the latest and greatest), and the backports aren't complete yet,so I compile most of the (non essential) programs I use.So, in order to uninstall all the crap I've amassed over the millenia, I have to keep the whole folders of compiled source.And I have to tell you, It's not pretty.So, that's what I need, pretty much.  :wink:[/QUOTE]


Well, it's good that you know that installing skype will clobber files from another package.  These sort of things may be benign, but they may also bork your system.

As for what you are trying to compile, I was only asking because a lot of users bang their heads trying to install one particular application from source and they do not realise that it is already available in synaptic...

---

