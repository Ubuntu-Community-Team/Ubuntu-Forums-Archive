---
title: "Finding applications installed - OOo specifically, but in general as well..."
date: 2007-05-27
forum: General Help
---

### Post by southernman on 2007-05-27
I am wanting to add some templates into OO however, I can NOT seem to find the right place to put them.

I've tried using find, which and dpkg but am apparently not using the write program name. I've tried it nine ways to Sunday including google.

OO's site says *These files should be placed in your %OpenOffice.org%/user/template directory* and for the life of me, I can't find it... [-X

Please help.... Many thanks!

---

### Post by LPomfrey on 2007-05-27
I believe the directory they go in is "/home/YOUR_USERNAME/.openoffice.org2/user/template"

If you're using Nautilus you'll need to press Ctrl+H to view hidden files.

---

### Post by southernman on 2007-05-27
> If you're using Nautilus you'll need to press Ctrl+H to view hidden filesThank you LPomfrey!

Had looked using both Nautilus and a terminal. Couldn't see it atall in Nautilus, didn't know about the Ctrl+H trick! Could see all that in a terminal but couldn't open it. Kept getting a "not a directory" when doing a cd /.openoffice.org2 /home/<username>

---

### Post by LPomfrey on 2007-05-27
> **southernman said:**
> Thank you LPomfrey!

Had looked using both Nautilus and a terminal. Couldn't see it atall in Nautilus, didn't know about the Ctrl+H trick! Could see all that in a terminal but couldn't open it. Kept getting a "not a directory" when doing a cd /.openoffice.org2 /home/<username>
There's also an option in Edit > Preferences > Views to always show Hidden and System files if you ever need it.

Using the terminal the correct command to enter that directory would have been:
```
cd ~/.openoffice.org2/
```

Or if you was already in your home folder:
```
cd ./.openoffice.org2/
```
Or:
```
cd .openoffice.org2/
```

If you don't put the period (meaning that the directory you want to move to is relative to the current directory) or the tilde (meaning that the directory you want to move to is in your home folder) in front of the directory it is assumed it is in the top level directory / (i.e. where /etc, /var, /bin, /usr, etc. are.) Unless, of course, you don't put the first / in as in the last example.

---

### Post by southernman on 2007-05-27
The ole commercial for m&m's comes to mind... "sometimes you feel like a nut..."

I wasn't putting the trailing slash in my commands.

Thanks again!

---

