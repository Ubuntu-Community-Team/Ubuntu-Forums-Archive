---
title: "rm -rf /etc/ ?????!!!!"
date: 2007-08-22
forum: General Help
---

### Post by raovq on 2007-08-22
all right. lets say hypothetically someone ran that command. this person presumed that it would do nothing, at least nothing damaging to the system as most folders should be permissioned to root only.

but anyway, obviously I (ahem, i mean, this person) was wrong, and it does damage the system. i am no unable to log in as any user or root. this makes it awkward to try and find out what other damage has been done.

i figure that a reformat will eventually be on the cards, but i don't really want to, and backing up my stuff is not working from a live cd (permission issues).

im wondering, i can't have deleted too many files, considering most should have been root only, so does anyone know of what file or folder, in /etc/ would cause all users to be removed and may be owned by a single user?

cheers for any help, its a pretty embarrasing situation.

---

### Post by leonardopsantos on 2007-08-22
Have you tried to use the live CD to re-install Ubuntu ? In the partition wizard, just don't format anything.

---

### Post by stchman on 2007-08-22
> **raovq said:**
> all right. lets say hypothetically someone ran that command. this person presumed that it would do nothing, at least nothing damaging to the system as most folders should be permissioned to root only.

but anyway, obviously I (ahem, i mean, this person) was wrong, and it does damage the system. i am no unable to log in as any user or root. this makes it awkward to try and find out what other damage has been done.

i figure that a reformat will eventually be on the cards, but i don't really want to, and backing up my stuff is not working from a live cd (permission issues).

im wondering, i can't have deleted too many files, considering most should have been root only, so does anyone know of what file or folder, in /etc/ would cause all users to be removed and may be owned by a single user?

cheers for any help, its a pretty embarrasing situation.

/etc is owned by root so that command would have no effect.  If they(your) ran this command:

_EDIT_ : Lets not post that type of code :) (the OP is bad enough) ~ bodhi.zazen

then you would be in trouble.

Linux has a way of keeping you from making mistakes like that.

---

### Post by bodhi.zazen on 2007-08-22
You should be able to get around the permissions issue with :

sudo cp -R <source> <destination>

Or 

gksu nautilus

Reinstalling will be less time consuming then trying to track down what you have deleted (and that may not be possible).

If you do not have a backup, I would pull your data and re-install

When you install you will overwrite /home (and any other directory for that matter) unless it is on a separate partition from / (root)

---

### Post by raovq on 2007-08-22
i see a reformat in my future. ill try the sudo nautilus to back up stuff, the only thing i really need to keep is my music, and thats available by everyone, so no real dramas.

thanks for the replies.

---

### Post by HermanAB on 2007-08-22
If you a recursive command runs away from you like that, then it is best and easiest, to re-install.  It only takes about an hour, while trying to fix it can take weeks.

I once wiped out a whole gawddamm web server (I had a backup!).  I guess it happens to everybody at least once, but few will admit to it...

Cheers,

Herman

---

