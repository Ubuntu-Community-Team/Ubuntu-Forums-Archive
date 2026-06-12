---
title: "folder permissions?"
date: 2007-08-11
forum: General Help
---

### Post by stlouis1 on 2007-08-11
this might be a sort of dumb question....but i installed deus ex earlier, and it works, but everytime i reopen it, it starts back up with default settings

now im attributing this to it being installed to the /usr/local/games folder. and that it doesnt have permission to write a new file to keep my settings.

now i know in windows you can use the cacls command to change folder permissions. 

i was wondering if theres a command like that in linux that i could set the permissions on that games folder so that any user can read and write to it?

---

### Post by jynyl on 2007-08-11
There is an article on file permissions over on the wiki ...

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

HTH

Peter

---

### Post by stlouis1 on 2007-08-11
well, that explains a few things. i've used that command before......never knew what it was for. thanks, ill give it a go when i get home.

so if i type "sudo chmod -rwxrwxrwx /usr/local/games"  it should allow everyone access to that folder?

---

### Post by aysiu on 2007-08-11
Aren't application settings usually stored in your home folder?

---

### Post by stlouis1 on 2007-08-12
deus ex runs under wine, 

the executable for the game itself is at /usr/local/games/deusex/system, which is where it keeps its settings. it does use the unreal engine, but its older and like i said, running under wine, so im guessing its trying to save its settings in that path, not the home folder like native games would

thats just my 2 cents, i've always been a windows guy, got my certs, working in IT for several years now, and currently supporting vista

i've been using linux though for the last month, used FC4 a couple years ago, and FC6 about 6 months ago, and started using FC7 a month ago, and kubuntu 7 a week ago now, and im really liking kubuntu, i kept ditchin fedora because i found it kept crapping out on me, dont find it that stable....but kubuntu....i've got everything working that i want/need....liking it enough that im going to ditch windows on my desktop next pay when i get a new hard drive

but anyway, aside from the technical knowledge, this stuffs all new to me, but same principles i guess when it comes down to it. thats why im thinking folder permissions. anyway, that command i posted above, should do the trick right?

---

### Post by stlouis1 on 2007-08-12
well, i ended up just runnong konqeror as root and changed the folder permissions....sure enough, when i ran deusex and set my resolution, it kept that setting when i restarted it

:D

---

