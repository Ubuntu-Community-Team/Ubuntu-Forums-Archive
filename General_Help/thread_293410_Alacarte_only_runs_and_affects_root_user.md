---
title: "Alacarte only runs and affects root user"
date: 2006-11-05
forum: General Help
---

### Post by Old Pink on 2006-11-05
Hi. 

Basically the problem is that when running alacarte, I must use sudo/su/gksudo/gksu in order to give it permission to run. Otherwise, it just complains of incorrect permissions and exits. 

This is fine, and everything works well, but when editing menus it only affects the root account. ](*,)

Any help?

---

### Post by Unknowndeepness on 2006-11-05
What happends if you do "chmod +x" on the "alacarte"-bin file?
(Im guessing its in /usr/bin)

---

### Post by Old Pink on 2006-11-05
I'd already tried that, no success. What I did do, however was run nautilus as root, then make the alacarte bin file unable to run, and that worked. :| Strange, but thanks for the insight.

---

### Post by Old Pink on 2006-11-05
Ok, now it will run as a regular user, all good, but I can't add items. :|

---

### Post by Unknowndeepness on 2006-11-05
"locate alacarte"
then you'll probably catch some folder, like "usr/local/alacarte/" or anything, then do a "chmod 755 *" inside that folder

?

---

### Post by Old Pink on 2006-11-05
Nope. Now, when running alacarte as regular user, I have no option to add menus etc. When running as sudo, I have options but they don't affect anything on my home account. :(

---

### Post by Unknowndeepness on 2006-11-05
:/

How did you install the software?

---

### Post by Old Pink on 2006-11-05
Installed in dapper, all fine. Updated to edgy, installed/upgraded via edgy update and worked well for like 2 weeks, then just randomly started happening after alacarte crashed.

I've tried reinstall through terminal and through synaptic, as well as removing and re-installing, no luck. :(

---

### Post by Unknowndeepness on 2006-11-05
Can it be your sources.list that still has dapper repos?
Mabie you have alacarte for dapper?

---

### Post by Old Pink on 2006-11-05
> **Unknowndeepness said:**
> Can it be your sources.list that still has dapper repos?
Mabie you have alacarte for dapper?

I did a GUI update, the sources list was changed automatically, without any input from me, and I did check afterwards and there's no sign of any dapper related repos. 

This wasn't caused by an upgrade or a weird install, it was caused by a crash.

---

### Post by CatKiller on 2006-11-05
What are the permissions on your ~/.config/menus and ~/.config/menus/applications.menu?

Just a thought.

---

### Post by melyadon on 2006-11-12
I had exactly the same problem on my computer, due to ~/.local being owned by root (I don't know why). Solved with :
```
sudo mv ~/.local/ ~/.local_back
```

---

### Post by techweenie on 2006-11-14
I have a similar problem.  After I installed something as root, Alacarte failed to run as a "normal" user.  After changing permissions on the ~/.local folder it will run, but any changes I make are not saved.  I can't figure out what I need to do to get this thing to work right.

EDIT: I guess I lied.  After moving/renaming the ~/.local folder I can make changes and all just fine.  However, I can't seem to move doom3 from "Other" to "Games", or rename it to Doom 3...

---

### Post by kerber0s on 2006-12-27
> **Old Pink said:**
> Hi. 

Basically the problem is that when running alacarte, I must use sudo/su/gksudo/gksu in order to give it permission to run. Otherwise, it just complains of incorrect permissions and exits. 

This is fine, and everything works well, but when editing menus it only affects the root account. ](*,)

Any help?

I don't know if you've solved this problem already, but the problem here is that you don't have the correct permissions  on your ~/.config/menus and ~/.config/menus/applications.menu (just like CatKiller thought).
Just change the ownership (or permissions) on the menu directory, and the problem should be fixed. 

sudo chown "username":"username"  -R /home/"username"/.config/menus

---

### Post by barney_1 on 2007-01-03
This thread fixed my alacarte menu editor.  I used the following commands as suggested above:

```
sudo mv ~/.local ~/.local_back
sudo mv ~/.local_back ~/.local
sudo chown "username":"username" -R /home/"username"/.config/menus
```

Of course I changed the "username" part to reflect my username.  I'm not certain moving the ~/.local directory was necessary.  You could try running the third line first if you want.

---

