---
title: "'Unsupported Operation' when attempting to delete folder"
date: 2007-05-13
forum: General Help
---

### Post by voxman69 on 2007-05-13
Hi!

I'm trying to delete the "Documents and settings" folder (which is completely empty) from my sda1 where Windows used to live :) 
However, I get this (for me) mysterious error. Attached the error message.

Any ideas?

//Vox

[IMG]http://www.kompisportalen.net/images/Screenshot-nautilus.png[/IMG]

---

### Post by zvacet on 2007-05-13
Did you put sudo in front of command?

---

### Post by Wiebelhaus on 2007-05-13
Open term:
> sudo nautilus


be careful! lol

---

### Post by voxman69 on 2007-05-13
Thanks for the suggestion. Tried that, but I get the same error message...can't delete it, move it, rename it...anything...

---

### Post by zvacet on 2007-05-13
```
cd /media/sd1
```

and when you are in type** ls**

That will show you all files and folders there.you will see one you want to delete so 

```
sudo rm -r folder_of _your_choice
```

---

### Post by voxman69 on 2007-05-13
Hmmm....I get this:

rm: cannot remove `Documents': No such file or directory
rm: cannot remove `and': No such file or directory
rm: cannot remove `Settings': No such file or directory

So, obviously the spaces are a problem...how do I go about that?

---

### Post by voxman69 on 2007-05-13
Found the how-to on spaces, could use either quotation or backslashes...unfortunately that just meant I'm back to square one with the "Unsupported Operation" message....

---

### Post by zvacet on 2007-05-14
Install nautilus scripts.

[http://doc.gwos.org/index.php/Nautilus_Scripts]("http://doc.gwos.org/index.php/Nautilus_Scripts")

First two are what you looking for.

---

