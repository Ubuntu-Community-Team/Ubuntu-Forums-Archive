---
title: "Katapult doesn't open bookmarks in right program."
date: 2007-09-16
forum: General Help
---

### Post by Goda on 2007-09-16
Hi, I use Gnome on Feisty Fawn. I really like the idea of launcher programs like Katapult. Whenever I try to open a bookmark it opens the page in a html editor instead of Firefox. Is this because I'm not using KDE and Konqueror? I couldn't find any options to change what program it launched.

---

### Post by prince_niceguy on 2007-09-17
install kcontrol and change hte default application browser to firefox..

---

### Post by Goda on 2007-09-20
Ok thanks, but when I try to install it in Synaptic, it comes up with this "kcontrol: Depends: kdebase-data (<4:3.5.7) but 4:3.5.7-0ubuntu1~feisty1 is to be installed".

---

### Post by prince_niceguy on 2007-09-20
before installing try doing

sudo apt-get update

sudo apt-get install kcontrol

that should work.

---

### Post by Goda on 2007-09-20
That didn't work. Maybe it has to do with "-0ubuntu1~feisty1" being on the end of the version.

---

### Post by alter-eebo on 2007-10-08
I do have the kcontrol, but I could not find "hte" in the program. could you please provide more detailed instructions (as to what to do after launching kcontrol). I am really new to ubuntu, so please be nice to me. Thanks a bunch.

---

### Post by prince_niceguy on 2007-10-08
no problem..

here you go...

open kcontrol. there would be search box on the top left. put the search term i.e. default and it will display default application in keyword. select the same. now, use click on default applications in result section (i know it is annoying but cannot help that)... select web browser and change it to "in following browser". type firefox in the same and you are all set.

Let me know if this does not work out.

---

### Post by alter-eebo on 2007-10-08
Thanks for the reply prince_niceguy. However, when I type "default" in the search box, it does not return any topics - so, still no solution to my problem.  My configuration is:

KDE version: 3.5.6
Release: 2.6.20-16-generic
Machine: i686

I am running Compiz Fusion

---

### Post by prince_niceguy on 2007-10-09
Ok. in that case install kde-systemsettings from synaptic or adept. then the default application should come. then follow the steps mentioned above.

hope that helps.

---

