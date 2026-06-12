---
title: "Dolphin search can't find a simple file"
date: 2014-05-26
forum: General Help
---

### Post by scottbomb on 2014-05-26
I'm thinking of filing a bug but I don't know what package is at fault. I was searching for a .pdf file in my documents folder called "UNIX Hater's Handbook.pdf". I finally found it using my eyes but I was rather amazed that Dolphin couldn't find it given any of my search terms "unix" or "UNIX". I was even in the Documents directory, where the file is located.

Should I file a bug? And if so, against Dolphin or another package?

---

### Post by mastablasta on 2014-05-26
is baloo/nepomuk running?

---

### Post by Bashing-om on 2014-05-26
scottbomb; Hi !

Here be my thought. In linux a space is a delimiter, such that the file "UNIX Hater's Handbook.pdf" becomes 3 separate files Unix", "Haters", "Handbook.pdf".
For the system to see the file as one single file, those spaces need to the 'escaped'.
The '\' key will 'escape' the spaces.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by scottbomb on 2014-05-26
It appears that baloo is running, not nepomuk:
```
user@main-linux:~$ ps -A | grep baloo
 2435 ?        00:00:00 baloo_file
 2898 ?        00:00:00 akonadi_baloo_i
user@main-linux:~$ ps -A | grep nepomuk
user@main-linux:~$ 
```

In regards to the file name, does it expect me to enter the file name exactly as it appears? Using the example above, I've tried "unix", "UNIX", "unix*", and "UNIX*" - all to no avail. I also tried to see if it could find a different file, "Words of Wisdom.doc" using "words", "words*", "Words", and "Words*". Nothing found. I also tried some files using their full name, "Hanssen.pdf" and "earthman.pdf". Neither was found.

---

### Post by scottbomb on 2014-06-29
I did a fresh install of Mint 17 on two different machines and I'm suprised to see this problem still exists. Any ideas?? I guess my only choice is to file a bug against Dolphin. I just can't believe I'm the only one having this problem.

---

### Post by scottbomb on 2014-12-04
Problem still exists on 14.04 on 2 different machines. Even after fresh install. I googled this and there are multiple threads of this same issue in different forums going back to 2005! Does anyone here know what's going on and if it will ever get fixed?

---

### Post by nerdtron on 2014-12-04
Hhhhmm I haven't used the built in find tool on the file manager on thunar or dolphin or nautilus ages ago because I find them unreliable. I now usually use the the command line find on rare occasions I don't know the location of a file.

Not sure about KDE now but have you tried installing a standalone find program? [https://www.kde.org/applications/utilities/kfind/](https://www.kde.org/applications/utilities/kfind/)

Another alternative I use is an app launcher which not only launches apps but also launches documents or any recently accesses file. 
Check out Synapse or gnome-do: [http://askubuntu.com/questions/449285/is-synapse-application-launcher-available](http://askubuntu.com/questions/449285/is-synapse-application-launcher-available)

---

### Post by scottbomb on 2014-12-15
I'll check out some alternative applications, thanks. I'll check into filing a bug against KDE too. Dolphin is an otherwise excellent (and my favorite) file manager. Something like a search should be very simple. Perhaps a hashtable?

---

### Post by MrSteve on 2014-12-15
please try
system settings > desktop search
untick/disable desktop search, press apply

open dolphin, top menu > edit > find
see if the find/search function works now ...

---

### Post by scottbomb on 2014-12-15
That works! Thanks, Steve! There must be some bug in the search backend. Very interesting.

---

### Post by rybnik on 2015-05-31
I have the same problem as the OP, but I'm using Xubuntu, with Dolphin installed on top.  I tried installing the KDE settings manager to be able to follow the solution that Steve posted above, but after that installation, KDE settings just gave the error "System Settings was unable to find any views, and hence has nothing to display."

How can I get Dolphin to have search enabled?

---

### Post by scottbomb on 2015-05-31
I am the OP and have found this problem to be mysteriously resolved in Kubuntu. However to get it to work in Xubuntu, I had to install kdebase-apps.

---

### Post by rybnik on 2015-06-02
I installed kdebase-apps and now dolphin search works!  Thanks.

Perhaps kdebase-apps should be made a dependency of dolphin so that other users don't run into this issue in the future.

---

### Post by tk83 on 2015-11-10
I also had this problem in Kubuntu 14.04 and disabling Desktop Search also fixed it for me.

What's incredibly frustrating though is that having Desktop Search (Baloo) on was the default, **but this breaks one of the most basic functions of the file manager** - being able to search for files/folders! 

The people who write these semantic desktop/desktop search things (like Baloo) seem to want to foist it on all users as a default, when at best this stuff is always half-baked and often causes hard-to-debug problems for many users. In my experience (using KDE as my main desktop for over 10 years now) the semantic search stuff never works properly, is just a source of frustration and problems and should absolutely be **off by default!**

---

### Post by scottbomb on 2016-06-12
I wiped the OS drive and installed Kubuntu 16.04 and the problem is back. There is no more option to just "disable desktop search" (whatever that was).

System Settings has a whole section for Search now, but ZERO documentation.

When I'm in the file manager (Dolphin) and I click "Search" I expect it to search those files I'm looking at. Seriously, what gives?! Why is this STILL broken? Does anyone know of a fix?

---

### Post by scottbomb on 2016-06-12
I found the answer and oddly enough, the fix is NOT intuitive. In the "Search" section of the System Settings, I unchecked "Enable File Search" under the "File Search" section and search works again.

It sure would be nice to have some good Kubuntu documentation. I'd gladly help out if there is such an effort.

---

