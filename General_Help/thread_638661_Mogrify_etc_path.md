---
title: "Mogrify etc path"
date: 2007-12-12
forum: General Help
---

### Post by jonpwatson3 on 2007-12-12
Hi All,

I hope someone can help me here.

i am using a php script called Dolphin ([www.boonex.com](www.boonex.com))
I upload the stuff to my host and all i get is blank pages, so i decided to create myself a ubuntu machine with apache2 on it etc and create my own local host to test this script on, with interesting results.

With dolphin, you have to input:
MOGRIFY PATH
COMPOSITE PATH
CONVERT PATH
PHP BINARY PATH

I asked my host and they told me /usr/bin/xxx (Replacing xxx with name, i.e. /usr/bin/mogrify)

The paths were the same on my server machine, BUT, when i opened the dolphin install page it auto-detected something different!
Dolphin says the path is /usr/X11R6/bin/xxx

When i fired up dolphin everything worked first time no problems.

In the ubuntu shell, if i type whereis i get: mogrify: /usr/bin/mogrify /usr/share/man/man1/mogrify1.gz

So meaning the path is actually /usr/bin/mogrify
So what on earth is the X11R6 all about?

Any ideas?????
Thanks
Jon

---

