---
title: "Is it possible to list all available commands in the terminal?"
date: 2006-08-10
forum: General Help
---

### Post by Dawnshadow on 2006-08-10
In the terminal, is it possible to output a list of all available commands (similar to what happens when you type a letter then push tab but for the whole alphabet)? Even better, is there a way to do this and export it to a text file automatically? I found a list of terminal commands, however, I know that I installed a few packages that make other things work at the command line (i.e, typing 'nethack' brings up Nethack) and I didn't think to write them all down....

Thank you.

---

### Post by calx on 2006-08-10
Just press TAB twice..

---

### Post by mlind on 2006-08-10
That's pretty huge list, just by hitting TAB key twice before writing any characters you get over 2000 hits.

Listing contents of /bin, /sbin, /usr/bin, /usr/sbin, /usr/local/bin, /usr/local/sbin (and possibly ~/bin, ~/sbin) shows you all the scripts and binaries you can execute (as root at least).

One of the most useful things is to learn use manual pages, and using search while browsing the manual. For nethack, you would type *man nethack* or for bried help: *nethack --help*.
To search a manual page, type '/' and then type in your search string. Use 'n' to find next search result, 'N' for previous.

---

### Post by Dawnshadow on 2006-08-10
Thanks. :) I knew about "man whatever," but not the other uses, nor the brief help option. Useful, as that's what I intended to do with the listing-- a DIY reference to everything by man-ing all the non-obvious ones. (I wonder if "man man" works.... [and I'll be trying it as soon as I'm done with this post, so no need to tell me.])

(Hitting tab *before* typing... who'd've thought....)

---

### Post by John.Michael.Kane on 2006-08-10
These may be of some use.

[**The Linux Terminal - a Beginners' Bash**]("http://linux.org.mt/article/terminal")
[**[COLOR="Blue"]An A-Z Index of the Linux BASH command line[/COLOR]**]("http://www.ss64.com/bash/")
[**[COLOR="Red"]Linux Shortcuts and Commands[/COLOR]**]("http://www.unixguide.net/linux/linuxshortcuts.shtml")
[Some Useful Linux Commands]("http://www.er.uqam.ca/nobel/r10735/unixcomm.html")
[**LINUX ADMINISTRATOR GUIDE **]("http://linux-newbie.sunsite.dk/")

---

