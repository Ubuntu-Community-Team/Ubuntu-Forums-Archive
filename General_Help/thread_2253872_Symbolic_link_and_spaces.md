---
title: "Symbolic link and spaces"
date: 2014-11-23
forum: General Help
---

### Post by michael235 on 2014-11-23
what * instead of one
this is what i run ln -s home/michael/swtor_settings  /home/michael/Desktop/Star Wars - The Old Republic/wineprefix/drive_c/users/michael/Local Settings/Application Data/SWTOR/swtor/


this is what it tells me
ln: target &#8216;Data/SWTOR/swtor/&#8217; is not a directory: No such file or directory
what am i doing wrong it is a directory

---

### Post by michael235 on 2014-11-23
I also want it to be the symbolic link to be in my home folder
this is one complicated process thatis confusing for me :(
i hope someone can help me
swtor_settings points to the target i specified

---

### Post by ian-weisser on 2014-11-23
Try:
```
ln -s swtor_settings /home/michael/.local/share/wineprefixes/SWTOR/drive_c/users/michael/Local\ Settings/Application\ Data/SWTOR/swtor/
```

A space ' ' has a specific meaning to the shell as a separator. Spaces inside a path must be escaped (/foo\ baz/bar) or quoted ("/foo baz/bar").
The shell is interpreting your path to be three different instructions due to the spaces in the path.

---

### Post by michael235 on 2014-11-23
Ok i added the quotes i ran  ln -s /home/michael/swtor_settings "/home/michael/Desktop/Star Wars - The Old Republic/wineprefix/drive_c/users/michael/Local Settings/Application Data/SWTOR/swtor/"


why does it say broken link :(

---

### Post by michael235 on 2014-11-23
Oh never mind got it working :D

---

### Post by coldcritter64 on 2014-11-23
> **michael235 said:**
> Oh never mind got it working :D

Can you say how ? May help others searching for answers to similar problems who look at this.

Also could you please mark the thread as [SOLVED] please ? There is a link in my sig to a guide, if needed. Cheers, coldcritter64

---

### Post by michael235 on 2014-11-23
how i solved it
i ran it the other way around
i ran the u know where the link is going to go to
than i did where the synlink was going be placed
ln -s (directory to be linked) (directory where to place)

---

