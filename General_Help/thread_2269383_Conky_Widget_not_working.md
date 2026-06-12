---
title: "Conky Widget not working?"
date: 2015-03-15
forum: General Help
---

### Post by DarkSapphire on 2015-03-15
So I have Conky installed with the manager, and its working great.  The default themes and widgets work great, but a theme I got from devian art is not working.  I may be using it wrong, thats why i'm asking.  When I select the widget in the manager nothing happens.   The widget/theme has a readme that I followed, but still doesn't work.  If you have the time to test it out, it would be great.  If you managed to get it installed, its a great theme.  Thanks!  Here is the link: [http://beslayed.deviantart.com/art/Steamy-Conky-on-Ubuntu-11-04-214491083](http://beslayed.deviantart.com/art/Steamy-Conky-on-Ubuntu-11-04-214491083)  The creator did a great job!

---

### Post by CantankRus on 2015-03-16
Conky manager is a recent application that will only manage conkyconfigs that have been 
specifically designed to work with it.
The conky you linked to has not.

The weather section and clementine conky wont work as both rely on packages from the **conky-companions** PPA
which hasn't been updated since Quantal.

You can start the conky by specifying a config to use with the "-c" option ...
```
conky -c [COLOR="#FF0000"]/path/to/conkyconfig[/COLOR]
```

eg I downloaded the **Steam Conky** and extracted it to **~/.conky/steamconky**
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] ls -A ~/.conky/steamconky
aural.png  clementine.conky  conkyClementine.template  **.conkyrc**  fonts-to-install  README.txt  start_conky.sh
```
So the command to run the conkyconfig for me is...
```
conky -c [COLOR="#FF0000"]~/.conky/steamconky/.conkyrc[/COLOR]
```

PS The conky config is usually named conkyrc but can be named anything really.
When you just run the command "conky" by itself it looks for and uses the hidden config file  @ **~/.conkyrc**

---

### Post by DarkSapphire on 2015-03-16
Thanks man!  I really appreciate it!

---

