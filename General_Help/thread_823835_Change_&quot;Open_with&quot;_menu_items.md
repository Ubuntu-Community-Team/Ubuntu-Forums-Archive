---
title: "Change &quot;Open with&quot; menu items"
date: 2008-06-09
forum: General Help
---

### Post by decipher on 2008-06-09
Hi There
I have been trying to change the menu items that are suggested for opening a file when you right click on it and select the "open with" sub-menu.

If I right-click the file and select properties, then select the "open with" tab, that gives me the default preferred application, and it's the same when I select System >> Preferences >> Preferred application, but this is not what I want, I basically want to be able to change the list of applications suggested to open with file with.

The reason why I ask this, is because recently I installed a text editor, then decided I didn't like it and removed it from my system, but the application still exists as a suggested "open with" application. 

Secondly, for example, I have a Javascript file, and the selected "open with" application is Text Editor, which is what I want. But the application Text Editor does not come up in the "open with" menu, and when I double click on the Javascript file, it gives some "C Source Code" editor, so in order for me to actually open this file, (although the default app for opening this file is Text Editor), I need to right-click it, select "open with", select "open with another application", and search for Text Editor, do you see my frustration?

Any suggestions would be greatly appreciated :)

---

### Post by tom66 on 2008-06-09
On the right-click menu there should be an option - 'Open With Other Application', then when you select the other application, it'll be the default.

---

### Post by decipher on 2008-06-09
Thank you for your reply. As mentioned in my first post, my preferred app is the default. But that is still useless to me.

What I am sayig is, I need to edit the "open with" application list, to add the default app to the list, and to remove apps that don't exist on my system anymore.

---

### Post by fooman on 2008-06-09
right click on file > properties > open with

then use the add/remove buttons to change the list of suggested applications.

---

### Post by decipher on 2008-06-09
I have tried that, unfortunately it won't allow me to remove any of the apps. Why is this? The remove button just stays disabled.

A quick solution I found to get my default app in the "open with" menu, is to select a default app that I don't actually want to open the file with, and so now "Text Editor" (my previous default app) is in my "open with" menu, I guess I can work with this workaround. ;)

---

### Post by fooman on 2008-06-09
> **decipher said:**
> I have tried that, unfortunately it won't allow me to remove any of the apps. Why is this? The remove button just stays disabled.


when you choose which app to remove, you need to click on the actual *name* of the app,  so that it is highlighted.  then the remove button should be accessible.  if you are only putting a "tick" in the circle in front of the name....the remove button will remain grayed out.

does that help?

---

### Post by decipher on 2008-06-09
> **fooman said:**
> does that help?
Even with it is ticked and the name selected, the remove button still remains disabled :(

---

### Post by ieee488 on 2009-11-08
> **decipher said:**
> Even with it is ticked and the name selected, the remove button still remains disabled :(

I have the same problem in Ubuntu 9.10.

Anyone know what is going on?

Because I upgraded from 8.04, I have some items that appear twice in the Open With selection box. I want to delete the duplicate.

---

### Post by celem on 2009-11-08
fooman - thanks - it was really eluding me as to how to get rid on an action in the Open With right click dialog.

---

### Post by Marcel-X on 2009-11-24
I have the same problem. But it is even worse!
Almost every wine application is listed 20 to 30 times.

What I like to know is which config file I have to edit?
The click, remove trick does not work.

---

### Post by Marcel-X on 2009-11-24
Found the solution here:
[http://ubuntuforums.org/showthread.php?t=1273296](http://ubuntuforums.org/showthread.php?t=1273296)

I removed 170 wine entries from ~/.local/share/applications

---

