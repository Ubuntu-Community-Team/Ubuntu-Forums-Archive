---
title: "Cinelerra Error"
date: 2006-10-29
forum: General Help
---

### Post by KayoLango on 2006-10-29
I am trying to install Cinelerra on Kubuntu Edgy.

I followed this tutorial:
[http://ubuntuforums.org/showthread.php?t=270037&highlight=cinelerra](http://ubuntuforums.org/showthread.php?t=270037&highlight=cinelerra)
(thank you Old Pink)

everything went well until I typed in "./configure"
I get this error
> _____@______-desktop:~/cinelerra-2.1$ ./configure
[: 24: ==: unexpected operator
[: 31: ==: unexpected operator
./configure: 47: Syntax error: Bad fd number


I did install nasm, yasm and looked at the official manual. What is wrong?

---

### Post by tregetour on 2006-10-31
I had the same problem.
[http://diveintomark.org/archives/2006/09/19/bad-fd-number](http://diveintomark.org/archives/2006/09/19/bad-fd-number) seems to have the answer of what's going on. Basically run "bash ./configure" instead of "./configure".

---

