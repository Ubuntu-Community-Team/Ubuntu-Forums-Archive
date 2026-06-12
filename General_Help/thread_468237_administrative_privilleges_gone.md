---
title: "administrative privilleges gone"
date: 2007-06-08
forum: General Help
---

### Post by rakeshdx on 2007-06-08
All of a sudden my eclipse quit working and i was no longer bale to so any administrative stuff. I cannot get to add/remove programs, or update manager. if i get to the update manager its giving 

failed to run /usr/bin/synaptic '--hide main window''-- non interactive''--parent-window-id''56623107''--update-at-startup' as user root.

The underlying authorization mechanism does not allow you to run this program. Contact the system administrator.


welll, i am the administrator here. Its my home pc. How do i login as root??



any help would be appreciated

---

### Post by Emerzen on 2007-06-08
I'm not sure what caused the problem, so it's difficult to trouble shoot.  But, you can try this ->[ Login as root w/o password]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_gain_root_user_access_without_login") -> from there try to create a new administrator account.

Did you fireup a GUI application from the command line using sudo by any chance?  If so, there's a good possibility you need to rewrite your ICE authority file.  While logged in as root go into your Home directory, view hidden files folders and look for an .ICEauthority file and delete.  When you reboot and try to login the proper file will be rewritten.  Obviously, if this isn't the case don't bother with it.  If it is, use gksudo instead of sudo at command line to open GUI's in the future.

---

### Post by rakeshdx on 2007-06-08
i just figured what i did... I accidentally removed all the permissions to me. I did that by going into system/ users and groups. 

There were 2 users there. One was by the name root and other was my name. i did not create the root username. It was already there. I dont know the password for the root. Is there a default password that is set for ubuntu (fiesty).

---

