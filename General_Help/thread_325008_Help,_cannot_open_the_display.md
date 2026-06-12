---
title: "Help, cannot open the display"
date: 2006-12-24
forum: General Help
---

### Post by punkybouy on 2006-12-24
I have an installation of 6.06 LTS that itself was an upgrade from a previous version.  Its been working good for 6 months ( probably because I have not messed with it) until today when I was trying to fix a problem with the Mozilla acrobat reader snapin.  I had no page controls when I viewed a document in the browser.  I un-installed Evince, thinking that might help, and now I have no desktop.  I get a graphical login screen but after entering my user name and password all I see is a black screen and the mouse cursor.  Otherwise it works fine.  I connected my Ubuntu 6.06 laptop and copied all my important files and then tried to do an upgrade on the broken desktop but the gksu "update-manager -c" failed with three errors about not being able to set the locale and not being able to open the display.  I was running the upgrade command from a terminal crtl-alt-f2.
I think the repositories on the broken desktop are from verson 5 as they mention breezy as well as dapper... I think.  Any help would be appreciated.

---

### Post by cilynx on 2006-12-24
Not really an answer to the question, but to do an upgrade from a terminal w/o the GUI:
```

sudo pico /etc/apt/sources.list

```
make sure that all lines reference a single version.  If you're upgrading, you're probably looking for Edgy as Feisty isn't really ready yet.

```

sudo apt-get update
sudo apt-get dist-upgrade

```

That'll update your sources then do a distribution upgrade.

---

### Post by punkybouy on 2006-12-25
Thanks for the speedy reply but according to the documentation here I should not be using apt-get.
[https://help.ubuntu.com/community/EdgyUpgrades#head-083dba9cd00350371c1a27ce7c1df6](https://help.ubuntu.com/community/EdgyUpgrades#head-083dba9cd00350371c1a27ce7c1df6)

I will try your method.  I am thinking now I must have somehow un-intalled the Gnome desktop since everything else works.

---

### Post by punkybouy on 2006-12-25
I fixed it by copying sources.list from my dapper laptop to the broken dapper desktop then doing an aptitude update from a recovery console as root which did quite a lot of updating.   Then I did a apt-get install ubuntu-desktop and that brought my desktop back plus with the "new" sources.list many packages were updated.  When I deleted Evince yesterday it must have deleted my desktop since during the install I saw references to Evince.
I suspect my upgrade to Dapper last summer resulted in some issues with sources.list keeping its Breezy references.  Thanks again for your help.

---

### Post by punkybouy on 2006-12-25
For those interested,  the reason why I had no page controls for Acrobat Reader in my browser , it was because I lacked the nppdf.so plugin in the plugin directory for Firefox.  With that installed it works just fine

---

### Post by cilynx on 2006-12-25
The documentation warns against apt-get because apt-get doesn't hold your hand like update manager or aptitude.  It also doesn't problem solve as well.  Since you were just installing packages and not resolving conflicts, it doesn't matter which you used.  Glad you got it up and running again.

---

