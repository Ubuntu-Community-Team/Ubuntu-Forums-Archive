---
title: "Where is the mail program"
date: 2007-02-16
forum: General Help
---

### Post by ethan@xmlstandards.org on 2007-02-16
Hi there all,

I am learning how to use Unix in general and am constantly coming across a command line mail program called "mail".

Where is this program located (or installed from).

Thanks

---

### Post by llamakc on 2007-02-16
Open a Terminal.

sudo apt-get install mailx

How did I figure which package provided that file?

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=%2Fusr%2Fbin%2Fmail&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=%2Fusr%2Fbin%2Fmail&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

---

### Post by ethan@xmlstandards.org on 2007-02-16
Thanks,

Already found after making this post.

Installs Postfix also though so not good for me.

Thanks anyway

---

### Post by Arisna on 2007-02-16
The "mail" command is for mail on the local system, sort of like one of those big inter-office delivery envelopes.  If you want a command line tool to get into e-mail on an Internet server, that's a different case.  You'd probably want something like mutt.

---

