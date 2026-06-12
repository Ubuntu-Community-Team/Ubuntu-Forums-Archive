---
title: "compiz and other things just stopped working"
date: 2008-01-14
forum: General Help
---

### Post by alexander.forster on 2008-01-14
hi,

So yesterday a bunch of things stopped working.

i think it had something to do with a fix that i was using to get totem "unstuck" from fullscreen. whenever totem got stuck i would close it then type
```

metacity --replace
```

which turned off all effects and i was able to un-maximise totem and turn my effects back on and totem would work for a while.

but in any case, the problems i am having now include

this is the output of ccsm
```

$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

i found a fix here [http://ubuntuforums.org/showthread.php?t=594893](http://ubuntuforums.org/showthread.php?t=594893) , which recommends editing my /usr/bin/ccsm, and commenting out a line.

this lets ccsm run but there is a tab missing and i cannot chance the actions, (ie: alt+tab =flip thru windows) and none of the effects work.

also i cannot install emerald which just dissapeared for no obvious reason.

and my audio in totem is out of sync.

i have tried re-installing ccsm and emerald.

here is the output of trying to install emerald
```

$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
           Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages
```


well any help would be appreciated, perhaps i should just re-install ubuntu? i'd rather not, but it is an option.

thank you very much in advance

Alexander

---

### Post by mccorkle on 2008-01-14
The first thing I'd suggest is to backup and files that you want to keep, because a re-install might be the final solution (depending on how much time you want to spend fixing this issue without a re-install).

Now, if you can re-install things with apt, that's the first and best method.  Do the following:
sudo apt-get update
sudo apt-get -f install

And pay close attention to what it says its about to do before you say (Y)es to anything.  It might try to remove all of Gnome or something silly like that (yes, its happened to me).  

Assuming that apt-get does a good job of fixing its own packages, then apt-get remove all of the packages that are acting up (ccsm and emerald in this case).  If apt can't deal with the files, you may be able to force remove them with dpkg or dselect and then re-install them with apt in a graceful manor.  

Let me know if none of that resolves the issue.  

::Mark McCorkle

---

### Post by alexander.forster on 2008-01-14
hey,

apt-get -f install did this

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and like i said in my first post i cannot install emerald, and removing and re-installing ccsm  still doesn practically nothing.

thank you for your interest in my issue! any further advice would be appreciated thanks!

---

### Post by benthegreat on 2008-02-04
I'm having the same sort of problems.

sudo apt-get -f install brings this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by alexander.forster on 2008-03-30
yeah i never got anywhere kind of just ignored the issue, i plan on doing a complete wipe of my computer anyway when 810 is released

---

