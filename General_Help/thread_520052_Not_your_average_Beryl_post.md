---
title: "Not your average Beryl post"
date: 2007-08-07
forum: General Help
---

### Post by Aesir09 on 2007-08-07
so i installed beryl with add/remove and i open up the settings manager and wow so many cool choices!

hmm yep so i do what i want and...

ctrl+alt+directional keys do nothing.

there is no sign of beryl even installed

why wont it work?

PS: i did install my nvidia drivers today to play FPS games and the quailty got even worse.

...?

---

### Post by hikaricore on 2007-08-07
You need to run **beryl-manager**.

Then there should be an icon in your "system tray" that allows you to turn beryl off an on.

Be aware you need Direct Rendering working properly for Beryl/Compiz/Compiz-Fusion to work properly.  ^_^

---

### Post by Aesir09 on 2007-08-07
how do i get direct rendering and thanks man

---

### Post by hikaricore on 2007-08-07
Direct rendering has to do with your video drivers being installed and working properly.

Upon closer inspection it looks like you've already accomplished this: [http://ubuntuforums.org/showthread.php?p=3149416](http://ubuntuforums.org/showthread.php?p=3149416)

---

### Post by kulturloseramerikaner on 2007-08-07
To get it running right now, open a terminal and type in "beryl" at the prompt and hit enter, then "beryl-manager," without the quotes of course.  That should bring it right up.  To get it running everytime you log in, go to System . Sessions and choose "add."  Under name, type beryl, command: beryl and click OK.  Do the same for beryl-manager: name beryl-manager, command beryl-manager and OK.

---

### Post by hikaricore on 2007-08-07
> **kulturloseramerikaner said:**
> To get it running right now, open a terminal and type in "beryl" at the prompt and hit enter, then "beryl-manager," without the quotes of course.  That should bring it right up.  To get it running everytime you log in, go to System . Sessions and choose "add."  Under name, type beryl, command: beryl and click OK.  Do the same for beryl-manager: name beryl-manager, command beryl-manager and OK.

Just FYI, **beryl-manager** negates the need for the **beryl** command itself.

beryl-manager is just that, it manages beryl.  It launches it and switched back to metacity/kwin through menus.

---

