---
title: "Delete /var/cache/apt/archives"
date: 2017-08-16
forum: General Help
---

### Post by raleigh3 on 2017-08-16
> If you'd like to free up drive space, a useful and safe command is...

sudo apt-get clean

That removes the aptitude cache in /var/cache/apt/archives

You'd be amazed how much is in there! You don't need to keep it, and the  only drawback is that the packages would have to be downloaded again if  you wanted to reinstall them.

I have 1.7 Gb in that directory. 

Is it ok to run that command ?

---

### Post by Bashing-om on 2017-08-16
raleigh3; Hello;

Yes - is safe . 'clean' is a part of the general housecleaning tools .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by raleigh3 on 2017-08-18
thanks.

---

