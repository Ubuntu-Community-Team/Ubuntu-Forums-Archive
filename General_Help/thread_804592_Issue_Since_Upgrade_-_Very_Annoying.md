---
title: "Issue Since Upgrade - Very Annoying"
date: 2008-05-23
forum: General Help
---

### Post by Duffy on 2008-05-23
When I open most applications, I get a little pop-up windows that says "Could not find mime type Application/octet-stream" - what the heck is Kubuntu trying to find? I have restarted the system and it still occurs. When the system starts, I get about 10 of these little pop-up windows all saying the same thing. If I try to open a document in Open Office, it pops up.

Is there a file missing? I need some help as sometimes this has caused a lock up of the desktop requiring a restart of KDE.

---

### Post by Zorael on 2008-05-23
I got this after I accidentally deleted said mime type. :>

Try this. It'll spam error messages at every step but just bear with it and close them down.
[list=1][*]open up System Settings
[list][*]...via the kmenu
[*]...by running **systemsettings** via a run box (Alt+F2)[/list]
[*]pick Default Applications
[*]pick File Associations
[*]hit Add
[list][*]Group: application
[*]Type name: **octet-stream**
[*]Ok[/list]
[*]hit Apply
[*]log out and back in[/list]

---

### Post by Duffy on 2008-05-23
Thanks! That solved the problem. Very much appreciate the help.

---

