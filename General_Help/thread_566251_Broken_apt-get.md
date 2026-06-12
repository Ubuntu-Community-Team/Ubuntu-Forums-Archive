---
title: "Broken apt-get"
date: 2007-10-03
forum: General Help
---

### Post by LokeTheDog on 2007-10-03
I was trying to install a printer and tried installing some driver package.

And now apt-get tells me: (translated from swedish) "I could not localize the package for z600cups. This might mean you have to manually repair this package."

And refuses to do anything else. I want to tell apt-get "just forget about it" since I don't care about this package anmore and just want to get on with life.

I tried "apt-get remove z600cups", but It says it has to be reinstalled but can't find the archive for it.

---

### Post by trippinnik on 2007-10-03
did you try apt-get -f remove <packagenamge> ?

---

### Post by LokeTheDog on 2007-10-03
Tried it now, still tells me it needs to be reinstalled. Also tired -m, which also gave the same message.

---

### Post by por100pre1 on 2007-10-03
Try these commands:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If that doesn't work try [this]("http://ubuntuforums.org/showpost.php?p=2879828&postcount=2").

---

### Post by LokeTheDog on 2007-10-03
Yep, what that other post explained is exactly what I have done, and I have tried doing it again. But the problem now is that when I try to run the .deb files, i get a message saying I don't have the rights to run it, or its damaged.

The deb files created by alien are owned by root, but using sudo doesn't help, nor does creating new files with alien.

---

### Post by por100pre1 on 2007-10-03
Please give [this tutorial]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters") a try if you have not done so yet. I don't think you need to be superuser to use alien.

---

### Post by LokeTheDog on 2007-10-04
That probably istalled the neccesary stuff to get the printer working. But the main issue remains.

---

### Post by acadiansteph on 2007-10-04
Some people, including myself,have problems accessing repositories or updating through Update Manager. It seems to be a repository issue. I have counted 3 so far with fatal error: 404 or you do not have permission

[http://ubuntuforums.org/showthread.php?t=567021](http://ubuntuforums.org/showthread.php?t=567021)

---

### Post by LokeTheDog on 2007-10-04
Well, that does not appear to be the problem in my case.

---

### Post by LokeTheDog on 2007-10-09
Doesn't anyone have some other idea? There's gotta be a way for ubuntu to just forget about this package.

---

### Post by forestpixie on 2007-10-09
have you tried to purge it

```
sudo apt-get remove --purge z600cups
```

Edit - if that gets nowhere you could try this one

```
sudo dpkg --remove --force-remove-reinstreq z600cups
```

and of course if z600cups isn't the name of the package change that bit.

---

### Post by LokeTheDog on 2007-10-12
The first command just gave the usual error message.

The second command gave the following, but didn't seem to fix anything:

dpkg - varning, ignorerar problem då --force använts:
 Paketet är i ett väldigt dåligt inkonsistent läge - du bör
 ominstallera det innan du försöker ta bort det.
(Läser databasen ... 162838 filer och kataloger installerade.)
Tar bort z600cups ...
/var/lib/dpkg/info/z600cups.postrm: 2: /etc/init.d/cups: not found
dpkg: fel vid hantering av z600cups (--remove):
 underprocess post-removal script gav felkod 127
Fel uppstod vid hantering:
 z600cups

Sorry it's in swedish, I haven't figured out how to change languge. Don't think me translating it would do any good either, its just gibberish to me :P

---

### Post by zvacet on 2007-10-12
```
locate z600cups
```

You will see where package is and then remove it manualy.Go to every directory with  z600cups and 

```
sudo rm -r packagename
```

---

### Post by LokeTheDog on 2007-10-12
Finally! At first I thought it didn't work, but then i used the "dpkg --remove --force-remove-reinstreq z600cups"-command, and that did it. 

Thanks a lot, I was almost considering doing a clean reinstall :)

---

