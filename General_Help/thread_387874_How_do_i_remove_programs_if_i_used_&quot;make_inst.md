---
title: "How do i remove programs if i used &quot;make install&quot; to install it?"
date: 2007-03-18
forum: General Help
---

### Post by minirx7 on 2007-03-18
Hi all,

I have rapidly learned Ubuntu in the past few weeks and I came to a bit of a situation.

I downloaded the SVN latest release for mythtv, and i compiled from source using:
./configure
sudo make
sudo make install

However, i want to uninstall it completely.  I read that i should have installed Checkinstall so that it will create a *.deb and i can remove with syanptics, but its too late for that.

what can i do to completely remove mythtv and its associated packages?

ED

---

### Post by Mr. C. on 2007-03-18
You have to manually remove the items installed via **make install**.

You could do a make install again, and capture the output into a file, and remove the files/directories you see updated/installed.

MrC

---

### Post by SishGupta on 2007-03-18
> **Mr. C. said:**
> You have to manually remove the items installed via **make install**.

You could do a make install again, and capture the output into a file, and remove the files/directories you see updated/installed.

MrC

This is very untrue.

When you compile from source you can use the same makefile (which is what you use when you do make and make install) to uninstall

To uninstall mythtv
from the command line
cd to the source directory and do 
sudo make uninstall

this will rm -rf the installed files

additionally you can open up the makefile and see the actions that are taken for each command (install, uninstall, clean) and which actions are available

---

### Post by minirx7 on 2007-03-18
Thanks for the speedy response.

So if its just a case of deleting directories, then there shouldnt be an issue.

What i was planning to do was reinstalling Mythtv via APT-GEt as a opposed to compiling at source, so i just wanted to ensure there will be no issues

Thanks again!

---

### Post by Mr. C. on 2007-03-18
> **SishGupta said:**
> This is very untrue.

I'm afraid you are incorrect.  You need to look at more makefiles, and understand the uninstallation problem better.  It is very rare for makefiles to contain uninstall targets.  There are several reasons for this, the first primarily is that the installation procedure is expected to be one way.  Existing binaries are often overwritten.  There are not saved copies laying around Unix systems.

> **SishGupta said:**
> 
When you compile from source you can use the same makefile (which is what you use when you do make and make install) to uninstall

While some software may include specific uninstall, the vast majority does not.  If you care to challenge this, you're going to have to use data, not your opinion.


> **SishGupta said:**
> 
additionally you can open up the makefile and see the actions that are taken for each command (install, uninstall, clean) and which actions are available

As a rule of thumb, it is not a simple matter of removing some files or directories installed.  Many installations irretrievable overwrite existing binaries, or they perform operations that adds information to, or rebuilds database files, overwrites required system files, etc.

One should not perform a make install on a system without understanding the consequences and havnig a backup plan in the event of unexpected problems.

MrC

---

### Post by SishGupta on 2007-03-18
Every  makefile I have ever used has had an uninstall. Forgive me for giving the assumption that the entire compiling *nix world is based on that. I have never thought that, but i did assume that an application such as mythtv would indeed have an uninstall (and it does)...and I doubt that it overwrites anything that a previous installation hasn't put there.
I even hinted at the fact that all applications might not have an uninstall when I added in the last line there showing that he can see the available makefile commands.
I have yet to find a linux application that overwrites files that are not directly involved with it (ie. from an installation of a previous version). I am not saying these don't exist, as literally anything could exist and I am sure it does often enough.

Your second to last comment seems a little hypocritical as you say it isn't a simple matter of removing files, yet those were your exact instructions in your original post. Look at the output and remove the installed/updated files.

At least we both agree on your last comment.

Anyway, thanks for taking me so literally. I wish I had more friends like you where they took what I said as fact instead of everyone else that understands that broad based things that I say are merely generalizations.:lolflag:

---

### Post by 454redhawk on 2007-03-19
A simple solution would be to use checkinstall (instead of make install) next time you install from source.

Synaptic is then aware of the program and can uninstall it for you.

to get checkinstall 

```
sudo apt-get install checkinstall
```

then you would install a program by
 ./configure
make
checkinstall

A *.deb will be created and installed for you.

---

### Post by Mr. C. on 2007-03-19
If you are going to challenge a statement, be prepared to back it up with data.

There was no contradiction in my statements.  I indicated to the OP that manual steps were required and indicate that files and directories can be removed.  I did not promise or guarantee system functionality.

When you are trying to teach or help someone, literal statements are imperative.

Many makefiles created with autoconf create dummy rules such as:

uninstall: uninstall-recursive

where no uninstall-recursive target is defined.  They are no-ops.

NrC

---

### Post by minirx7 on 2007-03-19
Awesomeness!!!

Yes.. i need to use Checkinstall from now on.

I tried the remove feature and recompiled again from the SVN without any issues and did a make install.  There was no version differences so i believe that it did cleanly get removed.

But thanks guys for all your help.!!

---

