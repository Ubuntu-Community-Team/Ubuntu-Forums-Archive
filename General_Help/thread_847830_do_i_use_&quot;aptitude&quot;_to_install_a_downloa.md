---
title: "do i use &quot;aptitude&quot; to install a downloaded .deb package?"
date: 2008-07-02
forum: General Help
---

### Post by bluepowder7 on 2008-07-02
seeing as i've installed everything on the new OS using the terminal and typing "sudo aptitude install <program_name>", there are times when the program isn't in the repos, so i need to download a .deb package.

now, as far as i know, using 'aptitude' makes it keep a complete log of what's installed, what the dependencies are, and all that - which neither apt-get nor synaptic do.  so, i wanna keep all the benefits of using 'aptitude'.  but, if i download the .deb package, do i need to run:

```

sudo aptitude install <path_and_name_of_downloaded_deb_package_on_my_pc>

```

or do i need to run

```

sudo dpkg -i <path_and_name_of_downloaded_deb_package_on_my_pc>

```

and if i do the second one (dpkg), will aptitude know what i did the next time i use it (aptitude) to install some other stuff?  or will it at some point in time try to blow the installed stuff (or portions of it) away since it (aptitude) didn't install it in the first place?

in a nutshell - given that i've been using 'aptitude install' from the beginning, what do i do to keep the system 'together'?

---

### Post by Bubba64 on 2008-07-02
You can download some debi packages to open with gdebi package installer for a easy install. This cannot be done from the terminal as far as I know which isn't much, but from safe download sites

---

### Post by bluepowder7 on 2008-07-02
right, that part i know since i used to do that when i had gutsy running.  but with hardy, some software that i want isn't in the hardy repos (specifically, xmms, NOT xmms2).

my main concern, though, is - i've been using 'sudo aptitude install ____' specifically to keep a nice thoroughly detailed log of what's in, what needs what, etc - so that if i UNinstall a certain piece of software, it'll clean out all the dependencies that aren't used by OTHER software (unlike apt-get or synaptic, which just leaves them floating around, taking up space, being useless, etc)

so, if i just run the .deb package, will the aptitude log get updated with whatever i do, or will it say "hey, i didn't install that, i dunno what it is, dunno who needs it, let's blow it away"?

or - plan B - should i just enable the gutsy repos and use aptitude to install the gutsy version onto hardy?  that would keep my aptitude log going nicely, but would have me using a gutsy package on a hardy system.  is that an OK thing to do?

---

### Post by 16777216 on 2008-07-02
Yeah gdebi makes it real easy to install non repo deb packages.
And yes they will show up in synaptic for easy uninstall as if they were installed the normal way.
Uninstalling works fine with this method.

```
sudo apt-get install gdebi
```

---

### Post by Vivaldi Gloria on 2008-07-02
> **bluepowder7 said:**
> and if i do the second one (dpkg), will aptitude know what i did the next time i use it (aptitude) to install some other stuff?  or will it at some point in time try to blow the installed stuff (or portions of it) away since it (aptitude) didn't install it in the first place?

You can install a deb package by double clicking on it or using dpkg in the terminal. In any case you will see it in installed packages in synaptic and aptitude. The only problem with deb packages is that you don't get automatic updates unless they are in some repo.

---

### Post by bluepowder7 on 2008-07-02
well, i don't want to use synaptic or apt-get, and want to use aptitude exclusively because of the whole logging thing (cuz quite honestly i just don't want oodles of unused supporting programs or libraries hanging around if i remove a particular main program).

so, i know that i can remove stuff using either the nice GUI'd synaptic, or apt-get, or probably aptitude.  BUT - if i didn't use aptitude to INSTALL it, what happens when i get to REMOVING it (using aptitude)?  will it remove ONLY the program, or will it seek out the unused dependencies as well and blow them away?

AND - if i'm doing some other repo install using aptitude, and it sees a package that it didn't install, will it tell me "hey, this doesn't show up in my log, i'm gonna blow it away for you", thereby making my initially installed .deb package useless (or broken)?

---

### Post by cariboo on 2008-07-02
Aptitude is just one to the frontends to dpkg. Using aptitude, apt-get, synaptic, or adept, the installed package info gets stored by dpkg. If you look in /var/lib/dpkg/status you will see a list of all the packages you have installed.

Jim

---

### Post by 16777216 on 2008-07-02
They all use the exact same backend (dpkg).
So all of the methods will get the exact same results.
The difference between the frontends ( apt-get, aptitude, gdebi, synaptic, etc,..) is the way they open this back end to the user which all comes down to user preference.

They all allow the user to install and uninstall with dependency resolution.
And, yes if you install with one you can uninstall with another with correct dependency handling.

Thanks Jim you beat me to it.

---

### Post by bluepowder7 on 2008-07-02
oh, well that changes things a bit.  :P

i was under the understanding that aptitude is able to sort out unused dependencies (like, prog A requires prog G, and if nothing else uses G, when removing A it removes G as well), and that apt-get and synaptic wer not able to determine that G isn't needed anymore and would therefore just leave it alone.

edit - and therefore, using something other than aptitude to install a package would have caused aptitude's log to be missing the info it would need later on to sort out what i can blow away and what it has to leave alone.

---

### Post by 16777216 on 2008-07-02
Aptitude uses tags to help find and sort packages so the user can find and install packages easier.
I used to use a installer in KDE that did this as well but can't remember the name.
But yeah, they all give the same end result.

---

### Post by bluepowder7 on 2008-07-02
ok, that's good to know.

so, as a subquestion - is it OK to enable gutsy repos for my hardy OS?  for example, XMMS is not in the hardy repos, but it's in the gutsy repos.  what would happen (now and down the road) if i enabled the gutsy repo and used aptitude to install XMMS from there onto my hardy system?

---

### Post by 16777216 on 2008-07-03
That is usually a very bad idea.
I will see if I can find a deb for you.

---

### Post by 16777216 on 2008-07-03
Couldn't find a pre-made package for you but [this blog]("http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html") gives instructions on how to compile XMMS from source for Hardy.

---

### Post by bluepowder7 on 2008-07-03
thanks to all for your VERY quick clarifications!  that blog's instructions look long and convoluted, but i DID love XMMS...

---

### Post by kevdog on 2008-07-03
The reason you should not install gutsy packages in hardy is that each version has a different kernel.  Packages are compiled against the header files for each respective kernel.  These header files and kernels change between versions, so although a package compiled against a later kernel may work in the current kernel, it might also break something.  It would be interesting however to see if it would work in this case, however odds are -- it will not!

---

### Post by jocko on 2008-07-03
**Bluepowder7**:
You are right about aptitude, it remembers which dependencies were installed with every package, and will try to remove them when the main package is uninstalled.
None of the other dpkg frontends will do that.
Using another package manager may end up causing aptitude to break packages or remove packages you need.

Let's say you have these packages installed:
Package A, installed with aptitude, requires package B.
Package B, installed by aptitude as a dependency for package A.
Package C, requires package B, installed with dpkg, apt-get, gdebi or synaptic.
Now you decide to remove package A with aptitude.
This will try to remove package B, which will either result in breaking or removing package C, or perhaps that aptitude will be unable to remove package A at all.

So if you want to use aptitude, it's best not to install packages any other way.

Xmms is very old, which is why it is not included in the hardy repos anymore.
I use audacious, which is a a fork of bmp, which is a fork of xmms.
It is very similar to xmms, but it's still being activelly developed. Try it out:
```
sudo aptitude install audacious
```

---

### Post by bluepowder7 on 2008-07-03
well, i found a deb package of xmms for amd64 (took a while), and got it installed.  sort of.  i think this calls for another thread:

[http://ubuntuforums.org/showthread.php?p=5311957](http://ubuntuforums.org/showthread.php?p=5311957)

oh, i also installed audacious.  i got them both installed late last night, so haven't had a chance to run either of them yet to see which i like better...

---

