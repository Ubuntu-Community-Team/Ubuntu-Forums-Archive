---
title: "Newbie in Ubuntu Made a Dumb Potentially Fatal Mistake"
date: 2020-05-30
forum: General Help
---

### Post by kspjohndoe501 on 2020-05-30
So I'm fairly new to Ubuntu and was installing some packages in a server that was given to me for my project. 
But I encountered that some of the pre-existing packages are in conflict with the packages that I'm trying to install.
Long story short I typed in the terminal **sudo apt purge ... **
Which Deleted all the packages in the server.
My question is, will the real data in this server be any way affected,deleted or modified because of this command?
Real data like images, texts, saved models and etc.  since we're doing machine learning.
This because this server is used by multiple people and I fear I may have affected their data.

---

### Post by deadflowr on 2020-05-30
> My question is, will the real data in this server be any way affected,deleted or modified because of this command?
Unknown, but in general apt never touches anything in the home directory.
I cannot say that same for anything outside the home directory though.

Worst case, leave the drive/disk untouched and use a recovery tool like testdisk to try and recover the data before doing anything else.

---

### Post by Bashing-om on 2020-05-30
kspjohndoe501; Hello - Welcome to the forum

The command's result depends on where you were located in the file system when the command was executed ( ... directs two levels up).

What file system is in use ? As there may be tools to help recover.
For instance ext4 ?
see:
```

apt show extundelete

```


[INDENT]these things happen
[/INDENT]

---

### Post by Impavidus on 2020-05-30
sudo apt purge [something] removes some software, including configuration. It shouldn't touch any documents. It will run the removal scripts belonging to the packages it removes, which, if well-behaved, will only cleanly remove the software, but if the software is not from the official repos, that can't be guaranteed.

---

### Post by TheFu on 2020-05-30
It also removed config files in the /etc/ directory structure which were installed as part of the package.
Data that was added while running a desktop or some server shouldn't be touched.  Anything in $HOME should be 100% fine.

If you are new, please learn to use the manpages.  What any command does should be spelled out there. Obviously, it won't say what it doesn't do. The apt command is/was a wrapper around apt-get, so check both manpages.  Sorry, but when working at the level you are working, reading manpages is mandatory.

Linux does what you ask it to do, not necessarily what you want it to do.

---

### Post by HermanAB on 2020-05-30
Hmm, I can understand how this is 'potentially fatal'.  Someone just might want to revenge his data loss with a nerf gun if you are lucky, or a cattle prod if you are not so lucky. Either way, you probably need to go and buy a few boxes of doughnuts.

As mentioned above, if the important data is in /home, then it should still be there, but if it was anywhere else, then it may now be in lalaland.  You should therefore look around for backups.

---

### Post by dragonfly41 on 2020-05-30
I looked around briefly for .. reverse sudo apt purge .. and found a few threads which might help you.

[https://askubuntu.com/questions/522712/undo-apt-get-remove-purge](https://askubuntu.com/questions/522712/undo-apt-get-remove-purge)

and as I though .. try the history command to see what actions were run.

---

### Post by deadflowr on 2020-05-30
I kind of wonder how far it actually got, since at some point something that was to be removed would have caused the package management system to halt.
Not to say the system isn't totaled, it most likely is.
Just kind of have to wonder where it stopped itself.

---

### Post by TheFu on 2020-05-30
This is where someone needs to ask ... how are your backups?  There are over 1000 uses for backups. This is one.

---

### Post by dragonfly41 on 2020-05-30
[COLOR=#000000]> ... since we're doing machine learning

this is a good learning exercise.[/COLOR]

---

### Post by mc4man on 2020-05-30
> **kspjohndoe501 said:**
> 
Long story short I typed in the terminal **sudo apt purge ... **
Which Deleted all the packages in the server.
...
My question is, will the real data in this server be any way affected,deleted or modified because of this command?
.
I suspect maybe you've found a way forward. 
Taking you verbatim I can't see where that "command" would do anything, doesn't here..

If .. meant some package name(s) then mention, if you somehow managed to remove apt and or dpkg then you're in a bit of a bind.

---

