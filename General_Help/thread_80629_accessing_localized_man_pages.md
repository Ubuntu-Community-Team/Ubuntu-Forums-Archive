---
title: "accessing localized man pages"
date: 2005-10-22
forum: General Help
---

### Post by towsonu2003 on 2005-10-22
I just installed the turkish man pages, but I could not find a way to access them... Is there a command for that? I tried making up commands like man-tr and mantr but wasn't lucky.

---

### Post by darknuala on 2005-11-16
look at the file description in synaptic for that.  You should find something there, to help to see what you are looking for.

---

### Post by towsonu2003 on 2005-11-17
[QUOTE=darknuala]look at the file description in synaptic for that.  You should find something there, to help to see what you are looking for.[/QUOTE]

This is all it says:
-----
Turkish version of the manual pages
This package contains the Linux manual pages translated into Turkish.
The following sections are included:
 * 1 = User programs (e.g. ls, ln)
 * 2 = Linux system calls (e.g. exit, fork, open)
 * 3 = Library functions (e.g. malloc, printf)
 * 4 = Devices (e.g. hd, sd).
 * 5 = File formats and protocols, syntaxes of several system
       files (e.g. wtmp, /etc/passwd, nfs).
 * 6 = Games etc.
 * 7 = Conventions and standards, macro packages, etc.
       (e.g. nroff, ascii).
 * 8 = System administration commands.
----

???

package name is manpages-tr

:confused:

---

### Post by towsonu2003 on 2005-11-21
?

---

### Post by darknuala on 2005-11-21
package name is manpages-tr

do a search for manpages-tr.

---

### Post by towsonu2003 on 2005-11-23
Finally working... Here is what I did, for other dummies (like me) who could not make it work... 

sudo apt-get manpages-tr

sudo dpkg-reconfigure locales

choose the languages you want (such as us_US.UTF-8) and this one for the manpages-tr: tr_TR.UTF-8

then use this to open up the man pages in Turkish without permenantly changing your environment:

LC_ALL=tr_TR.UTF-8 LANGUAGE=tr_TR.UTF-8 GDM_LANG=tr_TR.UTF-8  LANG=tr_TR.UTF-8 man cp

(cp is an example command)

For a much nicer command, do this:

gedit ~/.bashrc

and add this one line to the end:

alias turkceman='LC_ALL=tr_TR.UTF-8 LANGUAGE=tr_TR.UTF-8 GDM_LANG=tr_TR.UTF-8  LANG=tr_TR.UTF-8 man'

doing this will allow you to see a turkish man page for cp (copy): 

turkceman cp

special thanks to ** Mr. Murat Demirten ** , who was very kind to help me via email. 

PS. I know you could just export all these variables, but I did not want to change my environment.

---

### Post by bernardfrancois on 2006-01-13
thanks!
I did the same for dutch man pages. Unfortunately they are full of spelling mistakes and aren't written very clearly :(

Note that you have to select *en_US.UTF-8* and not *en_IN.UTF-8*. I got warnings while executing 'man' (for english man pages)...
Maybe this can also be solved by choosing 'none' for the default locale...

---

