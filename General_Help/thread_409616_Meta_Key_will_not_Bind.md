---
title: "Meta Key will not Bind"
date: 2007-04-14
forum: General Help
---

### Post by thimble on 2007-04-14
Using bash, I'm trying to bind Meta-w to do a history search of text typed on the command line by doing the following:

bind '"\M-w"':"\"\C-k\C-ahistory | grep '^ *[0-9]* *\C-e.'\C-m\""

It doesn't work on my Ubuntu box. (It works on all my other linux boxes (Fedora, Debian) with bash.) Binding Meta-o, or any other letter following Meta doesn't work either. However, binding Control-o works:

bind '"\C-o"':"\"\C-k\C-ahistory | grep '^ *[0-9]* *\C-e.'\C-m\""

Has anyone else successfully bound a meta-letter key combination in bash (using Ubuntu)? Why won't Meta-w work?


Thanks!

---

### Post by thimble on 2007-04-26
No one knows why Meta won't bind in bash? :(


Even doing something like:

>> bind "\M-w":magic-space

...in order to bind Alt-w to the magic-space function (which expands bangs in bash) doesn't work.


No one has tried binding the Alt key to anything in bash?

---

