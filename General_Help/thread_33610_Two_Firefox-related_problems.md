---
title: "Two Firefox-related problems"
date: 2005-05-11
forum: General Help
---

### Post by MrMunson on 2005-05-11
Right... This is my first post ever in this forum so I hope I get it all right.

Just moved from Fedora to Ubuntu 5.04 Hoary (used Linux for quite some time). After the install i used the ZIP-archive available to install the various bits and pieces of nice things that one must have. This all worked like a charm so great work!

I do have two problems with Firefox though:
[list=1]
[*]Trying to install extensions unexpectedly leaves me with the "save or open with.."-dialog for some strange reason (as opposed to the expected "install/cancel" dialog. Seem like Firefox deosn't recognice my install attempt from any other download off the Net.
[*]During administration of one of my websites, I use the TinyMCE editor to edit content. This does not work with the Firefox install that comes with Ubuntu. I have used this editor with success on every other Linux-install/Firefox-installation i have every tried (app. 6-8 total) and there has never been an issue before.
[/list] 

Any suggestions as to what can be causing me so much headache would be appreciated.

---

### Post by harryc on 2005-05-11
1.) Download the extension to a directory. Go into file, open file,  in firefox and point it to the downloaded file....open it.

---

### Post by MrMunson on 2005-05-11
[QUOTE=harryc]1.) Download the extension to a directory. Go into file, open file,  in firefox and point it to the downloaded file....open it.[/QUOTE]

Harryc, thanks a bunch for the helped! Needless to say, that did the trick just fine. Now I can finally surf without getting all those annoying ads everywhere.

As far as problem two (using the editor) I tried to downgrade to Firefox (FF) version 1.0.2, any wehaa(!), it works. I had a look in the repositories in my package manager and it turned out I had a bunch of "unstable" and backport reps in there. Probably a consequence of me running that ZIP-package with stuff without haveing 100% control over what I am doing(?). I think I need a crash-course in the world of apt-get/repositories/Debian-isch stuff. Only used to Fedora-stuff and using Yum. The previous version of FF that I had installed was 1.0.3somethingsomething and now I am down to the old 1.0.2 and it doesnt complain. Could it be that I was having some unstable/tested version since I had all those "less-stable-sounding" repositories in my setup?

---

### Post by harryc on 2005-05-11
AFAIK, the latest stable version of Firefox for Ubuntu is 1.02, so it's hard to say what consequences an untested 1.03 might have. Glad you got everything working. ;). Unless you have a need for a specific package/s(like when you are running the zip-package), it's best to stay away from backports and debian-marillat repos. Comment them out in your  /etc/apt/sources.list.

---

### Post by nocturn on 2005-05-12
[QUOTE=harryc]AFAIK, the latest stable version of Firefox for Ubuntu is 1.02, so it's hard to say what consequences an untested 1.03 might have. Glad you got everything working. ;). Unless you have a need for a specific package/s(like when you are running the zip-package), it's best to stay away from backports and debian-marillat repos. Comment them out in your  /etc/apt/sources.list.[/QUOTE]

Actually, backports seem to be pretty stable.
For FF, Jdong (backports) is weeks ahead with security patches...

---

### Post by harryc on 2005-05-12
[QUOTE=nocturn]Actually, backports seem to be pretty stable.
For FF, Jdong (backports) is weeks ahead with security patches...[/QUOTE]Good to know, thanks. How long would you wait before installing FF 1.04 for instance...as soon as it's in backports?

---

### Post by shakin on 2005-05-12
[QUOTE=harryc]Good to know, thanks. How long would you wait before installing FF 1.04 for instance...as soon as it's in backports?[/QUOTE]

Yes. In fact, I have backports staging enabled so I can get it ASAP. Worst case scenario is that it breaks and I have to downgrade. Best case is that I will be patched quicker, so it's worth it.

---

### Post by nocturn on 2005-05-12
[QUOTE=harryc]Good to know, thanks. How long would you wait before installing FF 1.04 for instance...as soon as it's in backports?[/QUOTE]

Backports has a staging area, so I would wait until it comes out of that into the main (for backports).
You can install it at that point.  Jdong has been doing the backports since Warty, and there haven't been major problems that I know of.

---

