---
title: "Update killed window decoration in Compiz/XGL sessions"
date: 2006-07-12
forum: General Help
---

### Post by ericesque on 2006-07-12
I haven't noticed anyone else mention it so far, but after I did an update today, my session based XGL has gone borderless.

That is to say, that I have no window decorations anymore.  I have to assume that it was the update seeing as how things worked right up until the update. Things are working fine in a regular gnome session too.

Any thoughts?

---

### Post by WakkiTabakki on 2006-07-12
Hi
You may have better luck with the compiz forums:
[http://www.compiz.net/]("http://www.compiz.net/")

Cheers
/N

---

### Post by ericesque on 2006-07-12
right on.  I forgot about the compiz forums because the whole compiz thing has been floating around for a while now and I just jumped on the wagon.  Thanks for the reminder!

---

### Post by mrgnash on 2006-07-12
I performed a fresh install of Dapper 6.06 AMD64 today and am having the same trouble after xgl + compiz worked fine on my old Dapper 6.06 LTS i386 system. I've tried both the universe repos (which I prefer since I don't like messing around with 3rd-party repos) and the beerorkid/compizinfo/whatever repositories; all to no avail. At the moment I've removed xgl+compiz, and downgraded everything back to the official Dapper versions... after all, the Universe ones *should* work.. there just seems to be something screwy with the whole compiz --replace gconf thing at the moment :confused:

---

### Post by shlomi on 2006-08-30
hello,
the update killed my decoration too! did anyone get it to work again??
I WANT MY COMPIZ.... ooooff...:-? :-?

---

### Post by hollaburoo on 2006-08-30
what does your compiz startup script look like? (should be something like "startcompiz" or "thefuture" in /usr/bin

---

### Post by monkeyhelper on 2006-08-31
The aiglx package layout has been changed (at least for aiglx), this may be your problem - see this thread for which packages to remove and to install :

[http://www.compiz.net/topic-3675-window-invisible-upgrade-compiz-20060824](http://www.compiz.net/topic-3675-window-invisible-upgrade-compiz-20060824)

---

### Post by dannyboy79 on 2006-08-31
all you wold have to do is type in metacity in a terminal and you'll get your normal borders back. As far as a permenent fix, you'll have to go back to the guide you used to set xgl and compiz up and go backwards so that you can be back to normal Gnome etc. Good Luck.  As someone else has stated, [www.compiz.net](www.compiz.net) is going to be the best place for you to go for help.

---

