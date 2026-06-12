---
title: "iPhone &amp; synchronizing contacts and calendar"
date: 2007-11-30
forum: General Help
---

### Post by chikko on 2007-11-30
after reading a little bit about [COLOR="Orange"][ubuntu and iphone]("http://ubuntuforums.org/showpost.php?p=3659182&postcount=15")[/COLOR] i managed to sync my music into it, using amarok and ssh connection.

unfortunately, there are two main things that i still miss out concerning my kubuntu Feisty and my iphone:

1. my music collection is build as folders with a folder.jpg inside each of them - how can i "tell" my iphone to use a specific photo as an art cover?

2. my contacts and meetings are extremely important to me.  i feel very comfortable around Kontact and don't want to even consider moving back to windows (where which iTunes magically arranges stuff) - how can i sync my information?..
i took a little peak inside iPhone's folders and realized that it uses SQLITE databases for saving the addressbook & calendar ..
now, i don't really know how to read those files, but whan i DO know, is that the package sqlite was already installed on my kubuntu - but it's a console command, with no UI.
so i was thinking, maybe if i could open those databases i could find a way to convert it somehow into a .cal file or anything else that Kontact could read from..
any help with that? :)
btw:
in order to check out your iphone's Library files via your computer, simply follow the above link's directions, goto a console and type:

```
sudo sshfs root@<your iphone's IP>:Library /media/iphonelib/ -o allow_other
```

(and that's, ofcourse, after creating a directory named "/media/iphonelib" (or whatever) and chowning it)

any help would be much appreciated! :)

---

### Post by lokimon on 2007-12-11
i am also very interested in hearing of ways to sync contacts and calendars from ubuntu (in my case gutsy) to an iphone.

---

### Post by ntetreau on 2007-12-16
So far, you can only sync your contacts with evolution through the Scheduleworld webserver, check out my [howto]("http://ubuntuforums.org/showpost.php?p=3956447&postcount=198")

---

### Post by dent_a on 2007-12-17
I too would love a sync tool or plug-in for Evolution or Kontact.  I ran a cross this and sounds like the makings of with we need, just a like to ICal output via Evolution and to automate the whole thing.  Of course the contacts are not mentioned in this. 
[http://wayetender.spawnpoint.com/](http://wayetender.spawnpoint.com/)

---

### Post by ntetreau on 2007-12-18
Thanks dent_a, I gave it a try and could sync my google calendar ---> iphone, not the other way around yet.  You can take a look at the howto I wrote [there]("http://ubuntuforums.org/showpost.php?p=3972806&postcount=217")

---

