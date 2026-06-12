---
title: "[SOLVED] 20Gb somewhere lost in the system"
date: 2008-01-22
forum: General Help
---

### Post by Boguz on 2008-01-22
Hey

i have a kind of strange situation here. Maybe someone can help me...

Yesterday i used for the first time the "Q"DVDAuthor to create a DVD. At some point it asked me what software i would use to burd the DVD: i chose K3b.

During this process i had to leave home.
When i came back it was ready.
The thing is, that now i have 20Gb less on my hard drive's free space.

I have been looking all over the temps folders and i cannot find where this 20Gb went...
:confused:

I've also used the search tool to look both for files created yesterday and for files over 500Mb and i cannot find a thing!

I have no clue about what happened
Any ideas?


(i am using Ubuntu 7.10)

Thanx for your help

---

### Post by forestpixie on 2008-01-22
there is a k3b temp folder - I'm on ubuntu and it's in a hidden folder in home

.kde/share/apps/k3b/temp
have you looked there, also check the hidden folder for DVDauthor

you could look in baobab as well, there are ways to check from terminal but I'm on the way out

---

### Post by Boguz on 2008-01-22
quando tento abrir a pasta .kde diz-me "*host .kde could not be found*".

andei a procura e a pasta mais parecida que encontrei foi a
/usr/share/apps/k3b
mas depois la dentro nao tem nenhuma outra pasta chamada "tmp", nem nada parecido...

ai, ai...

mais ideias?

---

### Post by fyo on 2008-01-22
If the previous advice doesn't help...

"du" is your friend.

```
du -h --max-depth=1
```

will give you the combined size of all the files stored in each top-level directory (relative to your position when you use the command).

I prefer running max-depth=1 when doing something like this and firing off many of them - as opposed to using a higher max-depth and manually going through them all. By using a depth of 1, I can zero in on suspicious directories pretty quickly and work my way down from there.

---

### Post by fyo on 2008-01-22
> **Boguz said:**
> quando tento abrir a pasta .kde diz-me "*host .kde could not be found*".

andei a procura e a pasta mais parecida que encontrei foi a
/usr/share/apps/k3b
mas depois la dentro nao tem nenhuma outra pasta chamada "tmp", nem nada parecido...

ai, ai...

mais ideias?

My Spanish isn't really that good, by try pre-pending your home folder (or using absolute path), e.g. "~/.kde/" instead of ".kde/".

That will work in Nautilus (the file browser), but I really would recommend command line interface for stuff like this.

---

### Post by Boguz on 2008-01-22
hey fyo, thanx, it worked... :)

i used that command and i discovered where the files where.

i am almost ashamed of saying it. I don't know why i didn't think about this place before...  It was so obvious... :confused:

ai, ai... the files where in the Trash Bin...     :S

Well, anyway, thank you so much. I discovered them there (and i think i would have discovered them anywhere else) thanx to you!
=)

---

### Post by forestpixie on 2008-01-22
knew someone would pitch in > du -h --max-depth=1 was what I was thinking of

can you mark thread solved

---

### Post by Boguz on 2008-01-22
yep, sure. thanx everyone...
:)

---

