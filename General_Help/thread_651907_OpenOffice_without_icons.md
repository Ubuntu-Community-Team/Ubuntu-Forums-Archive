---
title: "OpenOffice without icons"
date: 2007-12-28
forum: General Help
---

### Post by hraposo on 2007-12-28
I did the installation of ubuntu 7.04, and appens a strage tingh:

When I open the OpenOffice, the menu bars, have no icons only text.

How can I solve this problem?

---

### Post by DjBones on 2007-12-28
(assuming your in gutsy)
have you checked to make sure that in System > Preferences > Appearance .. > Interface (tab)
that the box reads 'icons with text' or 'icons' or whichever configuration you prefer?
Edit: ah well nevermind, you said you're feisty haha..
but it should be the same thing but the menu tree should be something like System > Preferences > Windows .. think so

if not.. then make sure in OpenOffice (Writer) that in View > Toolbars > Customize .. > Toolbars (tab)
you'll see a drop down menu and make sure the bubble is over the 'icons' ..
check the pick if your confused lol

---

### Post by forestpixie on 2007-12-28
check in tools >options > openoffice.org >view

look to see if icons in menu is checked

you might also need to install the styles, open synaptic and search for 
openoffice.org-style-tango


Edit - although DjBones has probably got it :)

---

### Post by martwine on 2007-12-28
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=278773](http://ubuntuforums.org/showthread.php?t=278773) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi I had this problem too on upgrading to Gutsy. Only just noticed it as I don't use OO on this machine very often. Caused a real problem because as well as icons missing, handles on drawing objects (the frame of little squares around an object in e.g. Impress which allow you to transform the object) were missing, which made OO for drawing pretty much inoperable. The solution is the same as for this Edgy bug [http://ubuntuforums.org/showthread.php?t=278773](http://ubuntuforums.org/showthread.php?t=278773)

In short, install openoffice.org-style-default and openoffice.org-style-crystal and all will be back to normal (at least it was with me).

Cheers,

Martin

---

### Post by x1um1n on 2008-01-11
I had this problem too, by default ubu installs its own "human" style and no other, OO needs to be told to use it tho..

just go to Tools->Options select View and change the style to human, or install a different one..

Hope this helps

---

### Post by strabes on 2008-01-11
I believe you could install the package openoffice.org-style-human as well.

---

