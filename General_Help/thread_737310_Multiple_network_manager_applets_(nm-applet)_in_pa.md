---
title: "Multiple network manager applets (nm-applet) in panel."
date: 2008-03-27
forum: General Help
---

### Post by sancho panza on 2008-03-27
I have been running Gutsy from before it was released, and I have had no real problems with the networking. Since last week, everytime I login, there are two instances of the nm-applet in the panel instead of one. All the settings incl. sessions manager have only one instance listed. I also have the remember current processes checked in session manager and I always kill one of the nm-applets from process manager after login. So, the process manager should be remembering just one nm-applet...not two.
Any ideas?

---

### Post by sancho panza on 2008-03-28
bump! Maybe i should move this to the general help section?

---

### Post by bapoumba on 2008-04-01
Moved and bumped.

---

### Post by sancho panza on 2008-04-03
Bump...Anyone?

---

### Post by brianw on 2008-04-03
I just came across it, fixed it. Now I can not recreate the problem... At any rate, this is how I fixed it...

You need to edit this file:** ~/.gnome2/session**

Look for as many instances of the following that you have extra "nm-applet" icons in your panel. So if you have (2) extra icons, you will look for (2) instances in your session file.

Each section starts with a line like this:

**0,id=...A very long number...**

and ends with a line like this:

**0,RestartCommand=...A command...**

All the lines starting with **"0"** are the same section....

You need to look for one that has the restart command something like: 

**3,RestartCommand=nm-applet --sm-client-id "a long number"**

Delete all lines with **"3"** at the beginning.

Hope it helps...

brianw

---

### Post by sancho panza on 2008-04-16
Thanks for the suggestion, but it didnt work. I'm guessing that editing the file *~/.gnome2/session* is the same as changing the settings in system>prefs>sessions.
And those settings too have the Network manager box UNchecked.

I'm clueless.

---

### Post by brianw on 2008-04-16
Well sorry about that, but do just one test for me;

```

grep "nm-applet --sm-client-id" ~/.gnome2/session

```

If that produces any output, then edit **~/.gnome2/session** and delete the section('s) it/they is/are in. 

Explained further;

If your output to the previous command is **19,RestartCommand=nm-applet --sm-client-id (a long number)**, then edit the file, whilst deleting all the lines that start with **19**. If you see **2,RestartCommand=nm-applet --sm-client-id (a long number)**, then delete the section starting with **2**.  If you see **2,RestartCommand=nm-applet --sm-client-id (a long number)** and **3,RestartCommand=nm-applet --sm-client-id (a long number)**, then delete the sections starting with **2 and 3**. 

brianw

---

### Post by sancho panza on 2008-04-18
Out of the blue, its back to normal once again, without me having done anything about it off late. So I'll leave it at that for now.

Thanks all

---

