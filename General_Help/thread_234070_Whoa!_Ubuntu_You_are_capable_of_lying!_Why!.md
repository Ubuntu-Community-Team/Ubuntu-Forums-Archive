---
title: "Whoa! Ubuntu? You are capable of lying?! Why!"
date: 2006-08-10
forum: General Help
---

### Post by UltraSonicSite on 2006-08-10
[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/odd.jpg[/IMG]
Soo ubuntu, you don't even trust your own files?

A lil help please.

libasound2 is at the newest version along with everything else. I have no idea what the problem could ever be? Only that ubuntu lies:shock:

The deb package is of a game called 'Sturmbahnfahrer'
It is a physics based game that I'm really interrested in. Only one post came up when I searched for it and it suggested I edited the .deb file. I have no Idea how to edit any .deb file, or any type of anything written in something other than simple

fullscreen = yes

format. :P

---

### Post by RAOF on 2006-08-10
Where did you get this deb from?  It probably has something like "Depends: libasound2 (>= 1.0.11)" as one of it's dependencies.  Since the latest version of libasound in the Ubuntu repositories is 1.0.10-2ubunut4, it can't satisfy the dependency.

You could manually edit the dependency, but it may very well not work.

Where did you get the .deb from.  Is the deb source available?

---

### Post by Doytch on 2006-08-11
Interesting.  I ran into this error today also.  I tried getting ScummVM to run on Ubuntu with the Debian Sarge package and it told me I don't have libasound2, when like the OP, I do.

EDIT: For those interested, ScummVM's packages, binaries and sources can be found [here.]("http://www.scummvm.org/downloads.php")

---

### Post by RAOF on 2006-08-11
Debian is not Ubuntu, no matter how close they may appear.  A debian package will often have such problems (packages with a newer Debian version than Ubuntu version, or a just plain **different** version).

A generic solution is to download the source package from debian instead, and build that*.  Then it will either fail to build (because it depends on a new feature of the package) or will build with the right Ubuntu dependencies :).

* A quick tutorial (commands get run from the terminal):  
0) Make sure you have the **build-essential** and **fakeroot** packages installed.
1) Download the files from the source package (they'll generally be at least a .tar.gz & a .dsc)
2) Unpack them with **dpkg-source -x *packagename.dsc***
3) cd into the new directory (generally *packagename-version*
4) run **dpkg-buildpackage -rfakeroot**.

Either 4) will work, or it will say "missing build-dependencies: ...".  Each of the names after that will be a package you need to install in order to build the deb.

---

### Post by UltraSonicSite on 2006-08-11
> **RAOF said:**
> Where did you get this deb from?  It probably has something like "Depends: libasound2 (>= 1.0.11)" as one of it's dependencies.  Since the latest version of libasound in the Ubuntu repositories is 1.0.10-2ubunut4, it can't satisfy the dependency.

You could manually edit the dependency, but it may very well not work.

Where did you get the .deb from.  Is the deb source available?

From here: [http://www.sturmbahnfahrer.com/](http://www.sturmbahnfahrer.com/) I believe tere is a source available, but the make command just spits out a short error.

---

### Post by Perfect Storm on 2006-08-11
You should really use the official .deb(s) from Ubuntu to avoid dependency hell and for safty. Or using the source Code.

---

### Post by UltraSonicSite on 2006-08-11
> **Artificial Intelligence said:**
> You should really use the official .deb(s) from Ubuntu to avoid dependency hell and for safty. Or using the source Code.

You mean like the ones in synaptic Package Manager? I wouldn't know, but if thats what you mean, there are no packages for the game there :P

---

### Post by Perfect Storm on 2006-08-11
Then use the sorce code package.

---

### Post by UltraSonicSite on 2006-08-11
> **Artificial Intelligence said:**
> Then use the sorce code package.

> **"source"]ultrasonicsite@ubuntu:~/Desktop/sturmbahnfahrer-1.2$ sudo make
g++ -c -I/usr/include -I/usr/include -O2 -g -Wall staticworldobject.cxx
In file included from staticworldobject.cxx:8:
staticworldobject.h:8:22: error: plib/ssg.h: No such file or directory
worldobject.h:9: error: variable or field ‘MakeDisplayLists’ declared void
worldobject.h:9: error: ‘MakeDisplayLists’ declared as an ‘inline’ variable
worldobject.h:9: error: ‘ssgEntity’ was not declared in this scope
worldobject.h:9: error: ‘e’ was not declared in this scope
worldobject.h:10: error: expected ‘,’ or ‘ said:**
>  Error 1

It seems as though the game files have a problem and not me?

---

### Post by Perfect Storm on 2006-08-11
Okay and I guess the configure went well (if it use one)?

---

### Post by UltraSonicSite on 2006-08-11
Well I downloaded the most up to date unstable version of libasound2 and now the requirments for that file are met, of course there are other files I have to download. But first, I need to figure out a solution to all these "broken package" errors I'm getting.
[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/Screenshot-1.jpg[/IMG]

---

Soo ubuntu, we meet again. Oh, what's this? I could fix these broken pakages! OMG Really?! Tell me how!

[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/ubuntu.png[/IMG]"Delete me. All the programs these files depend on. Everything! Burn 'em, BURN 'EM!!!"

Ah, I see you also have xterm in this "to delete" list of yours. Gnome Desktop as well. *Gasp* Not my gnome screensaver! Nooo please! Don't delete my electric sheep!!! Please I beg of you!

[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/ubuntu.png[/IMG]"Useless I say, USELESS! DELETE THEM ALL!!!1!1!1"

Whoa..not even windows is this suicidal...

[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/ubuntu.png[/IMG]'You *DARE* compare me with **WINDOWZ**?!?! Why you son of a"-explicitly deleted

Soo, how can I stop my "friend" here from committing computerized suicide?...

[I swear the list actually contains every program from a to z]

---

### Post by Perfect Storm on 2006-08-11
No need of sarcasm if you want help.

Find the package at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and downgrade the troublesome package.

---

### Post by UltraSonicSite on 2006-08-11
Ok ok so I might had over done it a bit, but I find it very silly for ubuntu to do that. I mean come on now =P These dependencies seem a little to strict if you ask me.

---

### Post by Perfect Storm on 2006-08-11
There's a good reason for the dependency. If it wasn't people would start complain why didn't this or this application get that lib, for without it it wouldn't work. Also when it comes to version of the diffrent libs.

That's the reason  why you should download important files from the official repo. ;)

---

### Post by UltraSonicSite on 2006-08-11
Meh, makes sense. For me though the problem always arises when I want to delete something that everything depends on. Well at least you've tought me one of the solutions, thanks =P

Lets see if I can repair these things.

---

### Post by UltraSonicSite on 2006-08-11
Ok well all the broken files have been erm, replaced/downgraded. Now we're just where we left off on page one =P

---

### Post by Perfect Storm on 2006-08-11
Okay :)

If you solved the problem with libasound, I can show how to remove the dependency of the .deb file of the game, though there's no guarentee the game will work. (and if the compiling just wont)

---

### Post by UltraSonicSite on 2006-08-11
On a positive note, we can see what the dependency problems with the deb file is.

> ultrasonicsite@ubuntu:~/Desktop$ sudo dpkg --install sturmbahnfahrer_1.2-1_i386.deb
Selecting previously deselected package sturmbahnfahrer.
(Reading database ... 120368 files and directories currently installed.)
Unpacking sturmbahnfahrer (from sturmbahnfahrer_1.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of sturmbahnfahrer:
 sturmbahnfahrer depends on libasound2 (>> 1.0.11); however:
  Version of libasound2 on system is 1.0.10-2ubuntu4.
 sturmbahnfahrer depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 sturmbahnfahrer depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 sturmbahnfahrer depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing sturmbahnfahrer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sturmbahnfahrer


Is it meant to run on a future ubuntu or what? =D

---

### Post by UltraSonicSite on 2006-08-11
> **Artificial Intelligence said:**
> Okay and I guess the configure went well (if it use one)?

Yes the configuration went off without a hitch.

---

### Post by Perfect Storm on 2006-08-11
Move your game.deb to the Desktop.
Then:

```
cd Desktop
mkdir Sturmbahnfahrer
dpkg-deb --extract XXXXXXXX.deb Sturmbahnfahrer
dpkg-deb --control XXXXXXXX.deb Sturmbahnfahrer/DEBIAN
nano  Sturmbahnfahrer/DEBIAN/control

```

Remove the the libs it complains about from the depends list.
save and exit. Just remember to install the depending libs before removing them (though they are of another version).
```
dpkg --build Sturmbahnfahrer
sudo dpkg -i Sturmbahnfahrer.deb

```

It might work or it might work not. The optimal will be building it from scratch from the source :)

---

### Post by UltraSonicSite on 2006-08-11
Thanks alot for all the help, I'll remember my new technique for years to come, or at least I'll try to =)

The game works flawlessly. (At a pretty good framrate too) It was probably the creator that accidently set the requirnments too high. But seriously, thanks for your time, next time I get problems with ubuntu, I know who to bug ;) 

j/k

---

### Post by Perfect Storm on 2006-08-11
My pleasure ^_^

```
It was probably the creator that accidently set the requirnments too high.
```

No, the package was made on Debian unstable version. That's why it had some other version dependency :KS

---

### Post by UltraSonicSite on 2006-08-11
You created this. =D  

Warning big pic.

[IMG]http://img.photobucket.com/albums/v64/ultrasonicsite/Screenshot-1.png[/IMG]

---

### Post by Perfect Storm on 2006-08-11
If you wanna try to compile some of the games with the latest version check my sig ^^. More will be added continuesly (depending on how much time I have).

---

### Post by UltraSonicSite on 2006-08-11
Ah okay, sure.

---

