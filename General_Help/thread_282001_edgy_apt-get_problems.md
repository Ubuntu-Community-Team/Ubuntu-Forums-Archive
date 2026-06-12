---
title: "edgy: apt-get problems"
date: 2006-10-22
forum: General Help
---

### Post by wyldeone on 2006-10-22
I'm having some trouble with apt-get in edgy. For some reason, when downloading in apt-get, the speeds vary radically from 100KB/s to about 5KB/s (spending most of their time at 5KB/s). This is not my connection, as things downloaded through firefox stay at a constant rate and don't drop down. I also don't think this is the repository, since these files are from the official ubuntu repos. Does anybody have any clue what's going on? At 5Kb/s it's a little painful to download anything.

---

### Post by teet on 2006-10-22
If you're in the United States...

Go to a terminal and type 'sudo gedit /etc/apt/sources.list'

Then, remove the 'us.' part in all of the repos.  For example,

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

would become

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

Save the file, exit gedit.  Then try your updates again.  It's worth a shot at least :)

-teet

---

### Post by taurus on 2006-10-22
Actually, if you plan to use gedit, better use gksudo instead of old plain sudo.  ;)

---

### Post by wyldeone on 2006-10-22
All of the repositories in my sources.list file lack the us prefix already, so I don't think that's the problem.

---

### Post by teet on 2006-10-22
> **taurus said:**
> Actually, if you plan to use gedit, better use gksudo instead of old plain sudo.  ;)

sudo works just fine.  Notice I said to do this from a terminal.  You would only need gksudo if you were doing this from the "Run Application" (Alt + F2) dialog box.

Anyway, removing the 'us.' is really the only trick I have up my sleeve.  Sorry :(

-teet

---

### Post by wyldeone on 2006-10-22
I see now that this is not a problem with apt. I just tried wget-ing a file from archive.ubuntu.com and it shows similar fluctuations. Downloading from us.archive.ubuntu.com is somewhat better, (it tends to go from 10Kb/s to 150KB/s), but still hardly optimal. Are there other mirrors available? It's odd because I haven't experienced this from my other Ubuntu machines.

---

### Post by taurus on 2006-10-22
> **teet said:**
> sudo works just fine.  Notice I said to do this from a terminal.  You would only need gksudo if you were doing this from the "Run Application" (Alt + F2) dialog box.

-teet
I am not going to argue with you since I have better things to do with my time but you should use gksudo with gedit either from a terminal or from <Alt>F2.

---

