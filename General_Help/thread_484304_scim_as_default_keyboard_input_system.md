---
title: "scim as default keyboard input system"
date: 2007-06-25
forum: General Help
---

### Post by mainalisuyog on 2007-06-25
Well, i'm in a bit of a mess here. I was trying to enable nepali language support on gnome, and followed some tutorials to make scim the default input system for gnome. But it seems to have messed up my amsn. And now i don't remember what change i made :-( What is the default keyboard input system for ubuntu, and how do i revert back to it? Please help. Thank you.

---

### Post by lieuhon on 2008-05-16
Hi, I am also trying to make scim default and not quite successful. I am using 8.04.  I managed to get scim work in gedit but not in Firefox and Openoffice that are more important to me.

The following is come from a page in the Community Docs.  For more go to the Community Docs in Ubuntu site and type in scim to search. you will find a few docs.

Reverting changes

There are several ways to revert the changes performed above:

    *

      Use im-switch to set the input method for your locale to "default", for example:

      im-switch -z en_GB -s default
    *

      Remove the file in your ~/.xinput.d directory corresponding to the appropriate locale:

      rm ~/.xinput.d/en_GB
    *

      Remove the SCIM package from your system (this should not be needed, and isn't the cleanest method, but should do the job if nothing else does):

      apt-get remove scim

Good luck

---

### Post by carfield on 2008-05-20
I also interested about having SCIM as default, plz post if any finding...

---

### Post by lieuhon on 2008-05-23
When I was using 7.10.  The scim worked fine but once upgrade.  It does not work at all and as said I managed to made it work in gedit but not in the firefox and the OpenOffice.  I tried to change the settings in OpenOffice but it does not work.  At the moment just too busy to make any progress on this matter.  I hope someone can tell me something about this.  This must be something related to the upgrade.

---

### Post by lieuhon on 2008-05-28
I have found a way to make the scim works.  I select Chinese as default language in the System/Administration/language Support/.  I can input Chinese in most applications but, of course, all the menus become Chinese.

---

