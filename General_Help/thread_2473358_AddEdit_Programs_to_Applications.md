---
title: "Add/Edit Programs to Applications"
date: 2022-04-01
forum: General Help
---

### Post by Hacker Agio on 2022-04-01
Hello to all. 
I would like to add an program to my applications.  Let me apologize up front, I will very likely be using the wrong nomenclatures.  When I click the 'square of dots' where I can access 'Show Applications' I would like to add a program to that. It's a third party piece of software and right now I have to type out in terminal the whole command line.  This is not overall difficult and I have condensed it down to a link but I would live to just be able to 'click on an icon' and be on my way.

Also, my apologies if I have not done my due diligence, as I don't really know what exactly to look for when I'm "googling"

Any help and/or guidance is greatly appreciated.

Thank you in advance

---

### Post by deadflowr on 2022-04-02
This should give you a general idea of what to do: [https://www.maketecheasier.com/create-desktop-file-linux/]("https://www.maketecheasier.com/create-desktop-file-linux/")

---

### Post by vanadium on 2022-04-02
You can also install either Menulibre or Alacarte to create such entries .

---

### Post by Hacker Agio on 2022-04-02
> **vanadium said:**
> You can also install either Menulibre or Alacarte to create such entries .

Thank you very much for the information, this provides pretty much what I needed.  Is there a way to manually edit the menu via terminal using something like VIM, also where the menu information is stored?

---

### Post by GhX6GZMB on 2022-04-02
Of course there is.
The .desktop files can be found in:
/usr/share/applications or $HOME/.local/share/applications for the Main (sudo) user, or
$HOME/.local/share/applications for all other users.

For correct operation, the "Categories=" line in the file is important. You'll find a listing here:
[https://specifications.freedesktop.org/menu-spec/latest/apa.html](https://specifications.freedesktop.org/menu-spec/latest/apa.html)

For suitable icons look in /usr/share/pixmaps.

I find it easiest to copy one of the existing .desktop files to a new file and edit that using some text editor. Mostly deleting all the irrelevant Comment, GenericName and Name lines that do not appy to my locale.

Remember to check permissions (compare to existing .desktop files).

---

### Post by GhX6GZMB on 2022-04-02
On rereading the question, this stuck out:
> **Hacker Agio said:**
> also where the menu information is stored?

You're going through the same loops that I did once, and probably searching for a "menu content" file somewhere.
You can stop doing that, it doesn't exist.

The Application Menu is created new every time someone logs in.
It's built from the "Main Categories" that I linked to (built into the GUI), plus the .desktop files and their "Categories=" entries.

---

### Post by Hacker Agio on 2022-04-02
Thank you very much! This is exactly what I needed to know.

---

