---
title: "Trouble setting PATH"
date: 2007-04-29
forum: General Help
---

### Post by erikcw on 2007-04-29
Hi,

I'm trying to add ~/bin to my path.

I've added
> 
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
    export PATH
fi

to my ~/.bash_profile but it is not being included in my path when a launch a new shell.

Any idea what I'm doing wrong?

Thanks!

---

