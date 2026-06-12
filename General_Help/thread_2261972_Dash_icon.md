---
title: "Dash icon"
date: 2015-01-22
forum: General Help
---

### Post by nefeli2 on 2015-01-22
Hello, I have a problem with the Dash icon. It used to show me all  applications and files but now it is only for Search without showing  anything. How can I access applications and programs without it? Any  help please?

---

### Post by deadflowr on 2015-01-22
Simple method would be to open Files(the file manager, which is usually located in the launcher)
Go to the left side pane area at click on Computer.
Then go to the folder, usr.
then to the folder share.
then to the folder applications.
In this folder most program launchers can be found, and a simple click will launch them.
Once an app ;launches from here, it'll set a launcher icon in the launcher sidebar.
You can then right click on the launcher icon and set it to stay by clicking on the Lock to Launcher selection.
Otherwise when you close the app, the icon will go away.

This, of course, is a rather roundabout way, but it works(for the most part)

All that aside, do you remember doing anything recently that might have caused the odd behavior you now see?

---

### Post by nefeli2 on 2015-01-24
ok i can do that. is there a way to make a shortcut of this file to my desktop?


Recently i tried to unistall firefox, install chrome and reinstall firefox. I deleted a firefox file but i think it contained only firefox data. i dont remember doing anything else

---

### Post by deadflowr on 2015-01-24
> ok i can do that. is there a way to make a shortcut of this file to my desktop?

Right click on the file in /usr/share/applications and choose copy.
The go to your desktop and select paste. Or navigate back to your Home folder and go to the Desktop folder and paste it there.
Either way you need to copy to Desktop. No move, though; only copy.

---

### Post by nefeli2 on 2015-01-25
hmm that is not working. i did paste the file to desktop but it doesn't have the applications in it anymore

---

### Post by deadflowr on 2015-01-25
Does it still look like the app icon or does it look like a weird text file?

---

### Post by nefeli2 on 2015-01-26
yes the icons look like text files, with .desktop ending or .index

---

### Post by nefeli2 on 2015-01-31
I think this command fixed dash
rm -rf ~/.local/share/zeitgeist

ty

---

