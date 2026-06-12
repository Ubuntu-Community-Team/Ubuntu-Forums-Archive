---
title: "creating package and add/remove apps"
date: 2007-04-01
forum: General Help
---

### Post by kritzikratzi on 2007-04-01
Hello! 

When creating my own debian package, how can i make the application show up in the add/remove applications list? 
My package shows up nicely in synaptic, but is missing in add/remove. 

Anyone has an idea? 


hansi.

---

### Post by zvacet on 2007-04-02
In menu layer first select in wich section you want your app to show(games,internet...)>new item and that will start launcher.Type this
1.name =app name
2.command =usr/bin/app_name (in most cases)
3. icon 0 usr/share/pixmaps

---

### Post by kritzikratzi on 2007-04-02
@zvacet
this will create a launcher for the menu, right? 

but i'm looking for some mysterious file i have to include in my .deb package, so that the application will be installable / removeable from the add/remove app, and not just from synaptic. 

hansi.

---

### Post by zvacet on 2007-04-02
Every program you can install have option to uninstall,so I don´t know what are you looking for.In case you are not only person using comp you will be administrator and nobody but you will be in position to uninstall it.

---

### Post by charlie763 on 2007-12-02
I'm in the same situation. I'd like to package up [Gladex]("https://launchpad.net/gladex") and stick it in a Launchpad PPA. I'd like for people to add my PPA repository and install/remove Gladex from "Add/Remove Applications." What do I need to add to the Gladex .deb file to make this happen? Is there something that needs to be added to the repository package list?

---

