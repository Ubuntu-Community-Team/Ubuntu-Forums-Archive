---
title: "an error message in synaptic"
date: 2008-02-06
forum: General Help
---

### Post by axman1971 on 2008-02-06
if i try to run synaptic or update this happens, it comes up in an error box.

E: Type 'deg' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


any help would be appreciated
max

---

### Post by drs305 on 2008-02-06
Make a backup, then check your sources.list file
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksu gedit /etc/apt/sources.list
```

Look at line 60, "deg" is probably a typo that is supposed to be "deb"
If you can't seem to see an error in line 60, you might just want to comment it out with a # symbol, see if it then works, and go back later to fix the line.

---

### Post by accatagon on 2008-02-06
feel free to post the text of the file as well if you feel unsure

---

### Post by axman1971 on 2008-02-07
Sigh, I feel so dumb, Thanks, after taking the time to see what you posted and really LOOK at that error message it seem so obvious!
it was a typo, it works...thanks again.

---

### Post by kesman on 2008-02-07
It's not the first time when somebody posts here an error message which clearly states the reason for the error :D In Windows, all you could do was to click "ok" to an error, but in linux there's always something to do about it.

---

