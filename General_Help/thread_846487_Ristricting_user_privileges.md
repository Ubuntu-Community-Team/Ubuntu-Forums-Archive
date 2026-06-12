---
title: "Ristricting user privileges"
date: 2008-07-01
forum: General Help
---

### Post by kemo_dk on 2008-07-01
Hallo, I am trying to create a "party user" for my computer as i am sick of people screwing around with my settings every time i throw a party. the user should be allowed to do nothing but playing media-files, and such basic actions. the most important thing is that the user can't change any settings at all! 
i have no idea how to ristrict a users access to applications, settings, etc. 

thanks, Kemo

---

### Post by soccerboy on 2008-07-01
hey they are about to add guest account abilities in the next version of ubuntu!!  If you want, you could wait till october.

---

### Post by kemo_dk on 2008-07-01
sweet, guest account sound nice. but still, if anybody have a solution that would do the trick now instead of October please post here,

---

### Post by sdennie on 2008-07-01
You should be able to create a new user with System->Administration->Users and Groups.  If you click on the user and then Properties you can get User Privileges.  Remove everything except access to audio devices and CD devices.  Then, once logged in as the user, hit Alt-F2 and type gconf-editor.  Navigate to /desktop/gnome/lockdown and lock the machine down.  Drag your media player of choice to the panel, remove everything else (specifically, the Applications Places System menu) and then, again in gconf-editor, navigate to /apps/panel/global and click locked_down.  

That should get you started with having a fairly restricted user.  It's not fail-proof to be sure but, it's a good start.

---

