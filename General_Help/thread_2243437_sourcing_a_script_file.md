---
title: "sourcing a script file"
date: 2014-09-08
forum: General Help
---

### Post by Silvernail on 2014-09-08
In gnome Ubuntu 12.04 & before, I was told  that if I wanted to source a script I could put it in a folder, '/home/dave/bin'.

Since I upgraded to 14.04, I do not find this options.
1. Has this option been depricated?
2. Can I create this folder and what do I export to environment?

Thanks for any light you can shed on this subject.
Dave

---

### Post by TheFu on 2014-09-08
So - you were lied to previously. Sorry.

"sourcing" and "running" a script are different.  You can place a script into any directory inside your PATH (echo $PATH).  It is extremely common to have a personal ~/bin/ directory and adding that to your PATH so they are available.  Of course, the file will need read + execute permissions set as you like - probably just the owner, if it is you, but perhaps the group and others as well.  Scripts must be readable to be run.

To learn more: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - just skim the first 100 pgs. It should clear up some misconceptions that may have been assumed.

---

### Post by steeldriver on 2014-09-08
The default ~/.profile file (copied from /etc/skel when you create a user account using adduser) should have a section in it like

```

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

This means that all you need to do is create a ~/bin directory and it will automatically be added to your PATH next time you login.

---

### Post by Silvernail on 2014-09-08
> **steeldriver said:**
> The default ~/.profile file (copied from /etc/skel when you create a user account using adduser) should have a section in it like

Worked perfectly...  Thankss

---

