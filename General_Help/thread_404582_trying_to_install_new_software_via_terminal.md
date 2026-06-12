---
title: "trying to install new software via terminal"
date: 2007-04-08
forum: General Help
---

### Post by beachreader on 2007-04-08
Hello this is my second day on ubuntu...still trying to remember how to spell it...
in any case I am trying to install new software that is I guess is debian/ubuntu based

1) I go to open terminal and I paste: 

/etc/apt/sources.list 

I get : permission denied

basically I am trying to install this link: deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main

ok I am loser...any help I would appreciate.

Many thanks
MM

---

### Post by yabbadabbadont on 2007-04-08
```
sudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get install <whatever software you need from that source>
```
:D

---

### Post by beachreader on 2007-04-08
very kool!!

fyi: [http://wiki.slimdevices.com/?DebianPackage](http://wiki.slimdevices.com/?DebianPackage) 

thats what i am trying to do..

many thanks!!

---

### Post by beachreader on 2007-04-08
wow I did that and I got a long program did not make it to step 1...I also got terminal servier client...can you refer me to a link before I messy everything up...sorry to bother you again.

'thanks

---

### Post by ardchoille42 on 2007-04-08
It is a very bad idea to add debian sources, it can quickly break your system.
Stick to the following rules for safety:

1. Install only from official repos, or
2. Look for a .deb package made for Ubuntu, or
3. Compile the app yourself, or
4. Look for a different app to do the job

---

### Post by beachreader on 2007-04-08
ok let see/:

sudo gedit /etc/apt/sources.list
( i did this and it took me to word file named sources.list. Do I save this?

sudo apt-get update
next did this

sudo apt-get install <whatever software you need from that source>
did this as:

sudo apt-get install deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main

then got nothing....

a sterling for your thoughts!

PS: this code is made for debian and ubuntu?
thks

---

### Post by beachreader on 2007-04-08
is there any way to install software other then open terminal. any thoughts are greatly appreciated. 

thanks

---

### Post by happymellon on 2007-04-08
> **beachreader said:**
> is there any way to install software other then open terminal. any thoughts are greatly appreciated. 

thanks

Yes there is, if you go to:

System>Administration>Software Sources

This is the nice way of editing your sources.list!

The second tab should be 3rd Party Sources and you can click on the +add button to add your new repository. In this case you paste "deb [http://debian.slimdevices.com](http://debian.slimdevices.com) stable main" in there.

Once this is done it should auto update your list and you can then run:

System>Administration>Synaptic Package Manager

If you choose the "origin" option in the bottom left to show all the repositories you've added and select your newly added server to view all the packages available on it.

---

### Post by beachreader on 2007-04-08
that is amazing but I do donot have "System>Administration>Software Sources"...do I need to add something to get that menu...btw I am running 6.06 if that makes the difference. thanks !!!

---

### Post by Maestro23 on 2007-04-08
> **beachreader said:**
> that is amazing but I do donot have "System>Administration>Software Sources"...do I need to add something to get that menu...btw I am running 6.06 if that makes the difference. thanks !!!


Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by beachreader on 2007-04-08
Once that's all done you should now have the Synaptic package manager on your screen. On the menu of this screen you will want to click on Settings -> Repositories

 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


Now hit Close. From the main Synaptic window, hit Reload. Once this finishes, you will now be able to get packages from the Canonical commercial repositories using the Synaptic Package Manager.

does anyone know how to access packages from  "canonical" in Synaptic window

further once you add software via Synaptic...where do you find it./....add /remove does seem to show it in the database...


sorry..

thanks

---

### Post by beachreader on 2007-04-08
ok I have the package install via Synaptic window now how do i install....please!

---

