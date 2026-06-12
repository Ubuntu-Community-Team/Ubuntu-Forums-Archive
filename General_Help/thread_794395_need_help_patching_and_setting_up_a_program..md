---
title: "need help patching and setting up a program."
date: 2008-05-14
forum: General Help
---

### Post by jessika-kaos on 2008-05-14
I am trying to install [Anki]("http://ichi2.net/anki/"), with a patch applied because the version I have installed from the provided .deb has a serious bug.

I downloaded the source, and the patch from [here]("http://repose.ath.cx/tracker/anki/issue533"). 

Now, what folder would I put the patch into? How should I apply it? 

And also, since the program installs with setup.py instead of .configure > make > checkinstall, it wont be managed by synaptic?

This probably isn't as hard as I'm making it, sorry.

---

### Post by mc4man on 2008-05-14
Take the patch file and put it in anki-0.9.5.7/ankiqt/ui then cd to ui and run patch -i closing.patch  
ex. (assuming anki-0.9.5.7 is in home dir. )
```
doug@doug-desktop:~$ cd anki-0.9.5.7/ankiqt/ui
doug@doug-desktop:~/anki-0.9.5.7/ankiqt/ui$ patch -i closing.patch
patching file addcards.py
patching file cardlist.py
patching file deckproperties.py
patching file displayproperties.py
patching file exporting.py
patching file graphs.py
patching file importing.py
patching file modelchooser.py
patching file modelproperties.py
doug@doug-desktop:~/anki-0.9.5.7/ankiqt/ui$ cd ../..
doug@doug-desktop:~/anki-0.9.5.7$ 

```
i think you can build a package using fakeroot debian/rules binary or dpkg-buildpackage -rfakeroot -uc -b.   Would have to ck. on hardy (on gutsy atm and the are ver. issues with a couple of libs, solvable but easier just to try hardy)
see here for dep issues on gutsy - if applicable
[http://ubuntuforums.org/showthread.php?t=726606](http://ubuntuforums.org/showthread.php?t=726606)

---

### Post by jessika-kaos on 2008-05-14
Thanks!! I will try this now.

---

### Post by jessika-kaos on 2008-05-14
Awesome, the second command worked perfectly, and the patch fixed the problem. Thanks again!

---

