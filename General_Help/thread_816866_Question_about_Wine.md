---
title: "Question about Wine"
date: 2008-06-03
forum: General Help
---

### Post by Kinnza on 2008-06-03
hi,
im using ubuntu for about a month now, maybe less, and im pretty happy
thing is i have this small program (language learning) that doesnt have a linux version .

i tried to use Wine to run it

when it installed, the installation process seems kinda stuck.. i mean it seems like it ended... all is at 100% but it wont close the setup window and i cannot close it either... it doesnt really respond.

now when i try to run the application, at first site it seems like its running, but when i try to activate the main feature (lesson) it abends.

im guessing that it has something to do with it trying to activate the microphone.

so here are my questions:
1) how can i check if the mic works? it wasnt in the ubuntu driver check.
2) are there any logs that you suggest i will look in?
3) any other ideas?

thanks for all your help

Kinnza

---

### Post by dracayr on 2008-06-03
hi,

have you searched the web for other people's experiences with that program under wine? If wine doesn't work, there's not much you can do...

dracayr

---

### Post by kpkeerthi on 2008-06-03
Not all windows applications run in wine. You can check how well your application is expected to run in wine here [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by dmizer on 2008-06-03
it would also help if you gave the name of the language learning program.

---

### Post by Kinnza on 2008-06-03
ok i will check that
and i know that not everything should run on it, but its a really really simple program... i dont think it does anything special but access the mic and speakers...

the program's name is : "Talk Now!" and the specific CD is: "Learn to Speak ESTONIAN Language From EuroTalk" 

what about checking the mic? and the logs?

---

### Post by dmizer on 2008-06-03
searcing in google with the following:
> linux wine audio mic
i found this forum post that looks to be potentially helpful:
[http://forums.worldofwarcraft.com/thread.html?topicId=2200220013&sid=1](http://forums.worldofwarcraft.com/thread.html?topicId=2200220013&sid=1)

also searched with
> "talk now!" site:winehq.org
which returned several potentially helpful links:
[http://www.winehq.org/pipermail/wine-users/2006-March/020850.html](http://www.winehq.org/pipermail/wine-users/2006-March/020850.html)
[http://bugs.winehq.org/show_bug.cgi?id=8594](http://bugs.winehq.org/show_bug.cgi?id=8594)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1182](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1182)

audio input functionality isn't something i would consider "simple" for wine.

---

### Post by Kinnza on 2008-06-03
yeah i guessed so
i will read those and see what i come up with
thanks :D

---

### Post by Kinnza on 2008-06-03
ok i found the audio specification in the Wine config
it doesnt really work... 
when i go to the audio tab it issues a message:

"there is no audio drive currently specified for the registry"

then it gives me a list of drivers... i tried them all

any suggestions?

---

### Post by dmizer on 2008-06-04
try this:
[http://ubuntuforums.org/showthread.php?p=4816491](http://ubuntuforums.org/showthread.php?p=4816491)

i'm really only googling here, i have never had a use for wine or configuring wine audio.  you might also get more assistance if you post/search at the winehq forums: [http://forum.winehq.org/](http://forum.winehq.org/)

---

### Post by Kinnza on 2008-06-05
thanks for trying :) i will read and do some more search

---

