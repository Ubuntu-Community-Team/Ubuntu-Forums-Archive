---
title: "Remove compiz"
date: 2008-06-22
forum: General Help
---

### Post by Kaneda187 on 2008-06-22
Hey people I just have a simple question for some one with the knowledge,

What do i type into the terminal to remove compiz? :confused:

---

### Post by pavlos_21 on 2008-06-22
it is so simple! just type:

 sudo apt-get remove compiz

but if you want to remove every package related to compiz,
like compiz-core, compiz-fusion-plugins-extra...
it is better (i mean easier because it is exactly the same thing, synaptic is just a graphic user interface of apt...) to open the synaptic package manager and make a search
with the keyword compiz, after that you can choise to remove every package related to compiz, and dont worry, if you want in the future to get compiz back, make a search with the keyword compiz, check just compiz and synaptic package manager will tell you which packages you need in order to run compiz and it will give you the choise to choose them automatically, so simple! synaptic package manager is at System->Administrator->Synaptic package manager, let me know if you managed to remove it, good luck!

---

### Post by Forlong on 2008-06-22
```
sudo apt-get purge compiz-core && sudo apt-get autoremove
```
Although I don't recommended doing that -- simply stop using it.

---

### Post by Forlong on 2008-06-22
> **pavlos_21 said:**
> it is so simple! just type:

 sudo apt-get remove compiz
That won't remove anything but compiz (the metapackage) and not Compiz itself.


edit: sorry for the double-post -- originally wanted to add this to the post above.

---

### Post by pavlos_21 on 2008-06-22
yes i agree, stop using it is the best solution, it does not need too muck hard disk space so if you just dont use it it will not annoy you!

---

### Post by pavlos_21 on 2008-06-22
yes forlong you are right, but if he works with the synaptic he can remove it, am i right?

---

### Post by Forlong on 2008-06-22
> **pavlos_21 said:**
> yes forlong you are right, but if he works with the synaptic he can remove it, am i right?
Yes of course. That's why I was only quoting that one command.

Sorry, if I wasn't clear enough.

---

### Post by pavlos_21 on 2008-06-22
forlong you are right, i was wrong about the command, no problem! i am sorry too for the misunderstanding, i hope that we helped our friend kaneda187! have a nice day!

---

### Post by pietjanjaap on 2008-06-22
If you do this then compiz will not start, and you have 2 buttons, 1 fot compiz start en 1 for compiz stop. The pc wil not start with compiz running, so you can fiddle around with it, even if it fails.


Monday, April 14, 2008
Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager

---

