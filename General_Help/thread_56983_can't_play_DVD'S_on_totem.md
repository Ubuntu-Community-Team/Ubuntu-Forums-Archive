---
title: "can't play DVD'S on totem"
date: 2005-08-14
forum: General Help
---

### Post by randlieb on 2005-08-14
my first time with linux!

installed ubuntu from installation disc in dual boot mode with windows. everything worked out real good. followed excellent step by step instructions i found on this forum. can boot to both windows and ubuntu....and they both work!

i would like to go fully to linux but my first attempt at opening TOTEM came up with an error message (sorry, i didn't write it down). tried to follow various threads, added something via the terminal and now totem opens but is frozen (must 'force' it to close). can't get it to do anything.

my problem is i don't know all the jargen for fixing these problems and so get lost trying to read the threads. it's like greek to me!!!!!

how can i fix the problem if i don't understand the language??

i want to watch DVD's on ubuntu......HELP!!!

---

### Post by Ubunted on 2005-08-14
For DVD's - 

```
sudo apt-get install libdvdcss2
```

I also reccomend xine

```
sudo apt-get install xine-ui
```

---

### Post by randlieb on 2005-08-14
[QUOTE=Ubunted]For DVD's - 

```
sudo apt-get install libdvdcss2
```

I also reccomend xine

```
sudo apt-get install xine-ui
```[/QUOTE]
 so what exactly do i do with the 2 pieces of code you show?

---

### Post by Donshyoku on 2005-08-14
Open the Terminal by going to your Applications Menu, going to the System Tools category and selecting Terminal.  Type the lines of code as he wrote them, and it should automatically download, install, and configure your computer for DVD playback.

---

### Post by wellery on 2005-08-14
[QUOTE=randlieb]so what exactly do i do with the 2 pieces of code you show?[/QUOTE]

Those are commands which you type into the terminal. Use the menu to open it.

Applications->systemTools->terminal

The guide is the best way to do these things:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) 

To add dvd playback follow this:

[http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback) 

(make sure you add the extra repositories)

Then if you want to play things like divx/xvid then it's a good idea to install the codecs:

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) 

Then install xine-ui:

[http://www.ubuntuguide.org/#xine-ui](http://www.ubuntuguide.org/#xine-ui)

---

