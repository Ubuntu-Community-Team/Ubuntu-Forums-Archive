---
title: "How to create custom docklets for docky"
date: 2017-03-15
forum: General Help
---

### Post by skanger on 2017-03-15
Multiple searches revealed that the methods used to create custom docklets or launchers for the docky dock menu system are now dated and don't apply to Ubuntu 16.04 or later. Most of them suggest right-clicking on the docky dock panel to access a menu selection for creating a new docklet. Others are similar but reference right-clicking on the desktop to access the 'create a launcher' menu selection. None of these easy options exist at this point.

I would like to create several very simple docklets, such as one for reverting to desktop view (the included docklet does not function - a well known bug) - all of which are nothing more than a simple key sequence: ctrl - windows key (or super key) - d, for example for reverting to desktop view. In fact I would like to eliminate most or all of the key sequences I use and replace them with docklets. This would make best use of docky for me (and maybe many others) who are tired of remembering a lot of key strokes.

Thank you for any suggestions or information about this.

Sk.

---

### Post by skanger on 2017-03-18
Anyone?

---

### Post by skanger on 2017-03-21
One more time...

---

### Post by dragonfly41 on 2017-03-22
Since you've had no replies I'll add some suggestions.

I use Docky on Ubuntu 14.04 but have not found a need to write custom docklets.

Since you wish to automate a library of key sequences I think that you could achieve your needs by launching an Actionaz automation script in Docky.

In an Actionaz script you can define a series of procedures.

So instead of creating an indefinite number of docklets (as you seem to envisage), you have just one running script in Docky.

Another approach would be to run a script which executes xdotools perhaps in python or bash script.
[http://manpages.ubuntu.com/manpages/trusty/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/xdotool.1.html)

While searching around I found this tip for launching the main menu from Docky icon.

[https://www.gnome-look.org/content/show.php/Docky+Main+Menu?content=138187](https://www.gnome-look.org/content/show.php/Docky+Main+Menu?content=138187)

That works nicely.

So to conclude I suggest using either Actionaz or xdotool from Docky to generate key sequences or launch applications or scripts.

In Ubuntu 14.04 I could not find a context menu to &#8220;create launcher&#8221; so just try Alt+F2 and navigate using key sequences such as arrow down, tab etc or xdotool to type text (name of application).

More here ... [http://askubuntu.com/questions/23816/how-to-make-use-launcher](http://askubuntu.com/questions/23816/how-to-make-use-launcher)

I believe that Ubuntu Tweak allows &#8220;create launcher&#8221;.

[http://askubuntu.com/questions/451887/cant-create-application-launcher-in-lubuntu-14-04](http://askubuntu.com/questions/451887/cant-create-application-launcher-in-lubuntu-14-04)

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

I still have much to learn myself about using Docky.

---

