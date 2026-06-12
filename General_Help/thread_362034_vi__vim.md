---
title: "vi / vim"
date: 2007-02-15
forum: General Help
---

### Post by aliyanage on 2007-02-15
Hi all,

I was using now the dapper version for quite a while and thought I might as well just upgrade to edgy, which I did now.

One of the things that was funny for me was that the vi editor didn't function as it usually did. Like if I would type vi and then press the I key for insert it would come up and in general nothing really worked, until I found out that there was no alias made to connect to vim, I didn't have this after I installed the dapper version.

how comes you have to use vim instead of vi, was that done on purpose or is it something that just got forgotten?

regards
aliyanage

---

### Post by Stephen Howard on 2007-02-15
My Edgy has vi linked to vim:

[FONT="Fixedsys"][INDENT]**$ stat /usr/bin/vi**
  File: `/usr/bin/vi' -> `/etc/alternatives/vi'

**$ stat /etc/alternatives/vi**
  File: `/etc/alternatives/vi' -> `/usr/bin/vim.full'[/INDENT][/FONT]

---

### Post by h.mehdi on 2007-02-15
Hey,

Just install vim ;)

sudo apt-get install vim

---

