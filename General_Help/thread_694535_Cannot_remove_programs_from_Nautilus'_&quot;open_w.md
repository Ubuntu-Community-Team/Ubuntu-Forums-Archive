---
title: "Cannot remove programs from Nautilus' &quot;open with&quot; list"
date: 2008-02-12
forum: General Help
---

### Post by svivian on 2008-02-12
When I right-click on a file in Nautilus and go to *Properties > Open With*, it lists various apps that appear in the open with cascaded menu. However, I can only remove some of them!

For example, XML files list Bluefish, Firefox, Kate, Konqueror, Kwrite, Opera and Text editor, but I can only remove Konqueror and Opera - the Remove button is grayed out for the rest. *How can I remove the others?!*

---

### Post by zvacet on 2008-02-12
Why do you want to remove them?You are supose to choose between them wich one you want to use for some app.

---

### Post by svivian on 2008-02-12
Well, that's not really the point... but it's because I know for some file types I'll only ever want to open them with one of two or three apps, and it's quicker if they're the only ones listed.

There are probably hundreds of apps available that are capable of opening text files. If they were all installed on my system it would be a bit ridiculous to list them all in the menu! (I doubt they would all be, but still.)

It's silly that I can remove some apps from the list but not others. I should be able to choose what I want in my menus!

---

### Post by zvacet on 2008-02-12
If that is all you have easy fix for that.If you want to open all text files with same app choose wich one will it be and every time you try to open text files you will see that app as default.

---

### Post by svivian on 2008-03-10
I already have apps set as default for my files. But I want to be able to choose the "extra" options.

Take this example of HTML files. I have the default set as Opera. But I also want Firefox on there (for testing purposes). And I want my text editor of choice, too, which is Kate.

OK so I have these apps all there. Opera is the default and the other two are in the "Open with >" submenu. Except there are several other programs listed here too: Kwrite, Bluefish, Text Editor (gedit), Konqueror. I don't need these listed and they just get in the way when I want to open a file.

But I can't remove them when I go to the "Open with" tab of the file properties. When I get round to it I'll submit a bug report to whoever, but in the meantime, is there another way to edit this list? Is it stored in a config file somewhere?

---

### Post by mat28590 on 2008-06-12
I too would like to remove programs from this list.
I've specified to open some file types with "custom commands".
Sometimes I've entered the command wrong.
Now the "open with" menu has got lots of programs / commands I don't want in the list.

---

### Post by mat28590 on 2008-06-12
~/.local/share/applications

Delete the applications you don't want from there.
They don't seem to show up again

---

