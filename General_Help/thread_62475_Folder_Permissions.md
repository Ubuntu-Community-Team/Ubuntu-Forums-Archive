---
title: "Folder Permissions"
date: 2005-09-04
forum: General Help
---

### Post by L1nVx on 2005-09-04
Hey i took a few things from my windows partition to my linux through root now... how do i make them so the user (me) kmalik can do anything he wants toe'm (fuill acces) there foldres... i got the main folder to let me open it but then everything under it is locked and going thruogh and permissioning everything to kmalik is crazy.... what is a shortcut (WAHOO THANKS GUY THIS IS FIXED NOW I NEED THE REST)

 how do i make a shortcut on my desktop to the folder kmalik

i downlaoded tar.bz2 for gdesklets and i extracted it and then did ./configure but it didn't work... is there a special way to do it?

i tried to get the darwinia linux demo file but it's a.sh and i don't know what to do with it..... what do i do..

thank you in advance!

---

### Post by serzz on 2005-09-04
Try following:

$sudo chown -R kmalik:kmalik FOLDER_NAME

---

### Post by L1nVx on 2005-09-04
well i right lcicked them went to properties and then changed permissions... ... will the way your doing it do everything under that folder??

---

### Post by serzz on 2005-09-04
Yes, it changes owner for all sub-files/folders recursively.

---

### Post by L1nVx on 2005-09-04
thanks for that now i just have to get the rest fixed :) as you can tell i'm a nub linux user... :-/

---

### Post by Lambert on 2005-09-04
[QUOTE=L1nVx]

i downlaoded tar.bz2 for gdesklets and i extracted it and then did ./configure but it didn't work... is there a special way to do it?

[/QUOTE]


Is there a reason you're trying to install from source rather then the using apt-get or synaptic. The latest gdesklet is in the repositories.

Not knowing your experience, you may want to take a moment and read these.

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://wiki.ubuntu.com/AptGetHowTo](https://wiki.ubuntu.com/AptGetHowTo)

I wonder if gdesklets will run on kubuntu as I believe it's an application for gnome. It may run on kubuntu but will need some gnome libraries to function? I'm not real sure, someone with more experience could maybe clear that.

---

### Post by L1nVx on 2005-09-04
i think the problem is i don't have updated repositiories... i'm a total newb btw

becuase i looked in synaptic and i will need to read those howtos etc. and update my repositories i guess.

---

### Post by Lambert on 2005-09-04
[QUOTE=L1nVx]i think the problem is i don't have updated repositiories... i'm a total newb btw

becuase i looked in synaptic and i will need to read those howtos etc. and update my repositories i guess.[/QUOTE]
 If you're a newb  then the whole wiki is a good place to spend some time reading along with [www.ubuntuguide.org](www.ubuntuguide.org)

---

