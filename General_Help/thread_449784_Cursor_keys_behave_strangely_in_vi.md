---
title: "Cursor keys behave strangely in vi"
date: 2007-05-20
forum: General Help
---

### Post by Nerdio on 2007-05-20
Just installed Ubuntu for the first time, and like it, but have found a strange behavior in vi (vim).

From bash I start vi by typing vi. When I am in insert mode, the cursor keys insert the letters  A, B, C, D each followed by a CR. Eg. cursor up prints an A <CR>.

My keyboard seems to behave normally otherwise, and the locale settings seem to be OK. It's a standard DELL keyboard, which works fine on XP, and worked fine on Fedora Core 5.

Any suggestions as to where I might start looking for clues?

Thanks

---

### Post by qix on 2007-05-20
Create the file:
 ~/.vimrc

Enter the line:
set nocompatible

And you should be all set!

---

### Post by rklauco on 2007-07-16
> **qix said:**
> Create the file:
 ~/.vimrc

Enter the line:
set nocompatible

And you should be all set!

Thanks, that really helped.

---

