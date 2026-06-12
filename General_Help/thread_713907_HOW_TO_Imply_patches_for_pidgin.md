---
title: "HOW TO Imply patches for pidgin?"
date: 2008-03-03
forum: General Help
---

### Post by avdzm on 2008-03-03
Hey all,

I want to ask, 
how can i imply the patches for pidgin?

I found this patch, that adds a nudge button on the conversation window.
[http://developer.pidgin.im/ticket/2788](http://developer.pidgin.im/ticket/2788)

although it doesn't say how to use it and where.

I have tried adding the patches to,
/usr/lib/pidgin

and running is command
patch < file

and i get this

can't find file to patch at input line 4
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Nurp old_pidgin-2.3.1/pidgin/gtkconv.c new_pidgin-2.3.1/pidgin/gtkconv.c
|--- old_pidgin-2.3.1/pidgin/gtkconv.c  2007-12-07 14:37:11.000000000 +0000
|+++ new_pidgin-2.3.1/pidgin/gtkconv.c  2008-02-06 12:27:04.000000000 +0000
--------------------------

so either the command is wrong, or i'm misusing the patches.
is the patch supposed to be used when compiling the source code.

thanks for any help.

---

### Post by kuja on 2008-03-03
Yes, it's a source code patch. So, you'll need to get the source code, apply the patch (I've no idea which file it's meant to patch), then compile it.

---

### Post by avdzm on 2008-03-03
ah....

I was afraid of that...

if i compile and make install the source code, 
the debian package, would still exist, right?

So i guess i have to uninstall the deb version first and compile the source.

does any1 know, if it will automatically be added to the gnome-menu or do i have to add it my self?

or can i compile it in /usr/lib/pidgin?

---

### Post by kuja on 2008-03-03
Yeah, the debian package will still exist. It'd probably be easiest to uninstall the package first. It depends where you install it whether or not it will be in your menu ..... it should have a file that gets put somewhere like $PREFIX/share/applications. You can compile it anywhere you want by specifying the prefix when running ./configure (ie: "./configure --prefix=/opt" or similar).

You might want to run "sudo apt-get build-dep pidgin" to grab the dependencies before you try to build it.

Oh, and though it recieves quite a lot of scorn, you might want to try using checkinstall to make a makeshift package for it, so you can remove it easily later before installing for example another pidgin deb.

---

### Post by kevdog on 2008-03-03
If you specify anything on the command line, it will be default be placed in /usr/local/lib.  Its possible to keep both copies on the machine as well.  One in /usr/bin and the other in /usr/local/bin.

---

