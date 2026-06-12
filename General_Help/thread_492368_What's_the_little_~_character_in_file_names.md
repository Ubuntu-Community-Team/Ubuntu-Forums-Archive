---
title: "What's the little ~ character in file names?"
date: 2007-07-04
forum: General Help
---

### Post by sebast on 2007-07-04
Just a quick little curiosity:

When I open up a file with the GTKfileChooser widget from GTK, why do I see certain files doubled but with a ~ character appended?

---

### Post by christhemonkey on 2007-07-04
The ~ is a [Tilde]("http://en.wikipedia.org/wiki/Tilde")

It is appended to a document name if you have edited it with gedit, 
so it makes a backup of the original file with the ~ extension.

---

### Post by sebast on 2007-07-04
Thanks

And those backups stay there for a long time? Sometimes my file are deleted and this file is still there.

Also, Nautilus seem to treat them as hidden files, but not file chooser, I wonder if it's the desired thing to happen.

---

### Post by christhemonkey on 2007-07-04
They stay indeterminately (ie forever unless deleted).


I think the file chooser and Nautilus have seperate "Show Hidden Files" states.
So maybe your file chooser is set to display hidden files?

---

### Post by sebast on 2007-07-04
No, I don't see any of the files starting with a dot (.) in file chooser.

Weird, maybe a bug since I'm testing Gutsy (I don't remember if I had that in Feisty)

---

