---
title: "How do I uninstall realplayer?"
date: 2005-09-07
forum: General Help
---

### Post by linuxNewb on 2005-09-07
I installed RealPlayer as per the instructions at [http://ubuntuguide.org/4.10/index.html#realplayer](http://ubuntuguide.org/4.10/index.html#realplayer)

Now I want to uninstall it, but dpkg can't find realplayer, I guess it's not a package. I'm new to linux, and I still am clueless as to what files are placed where, when a package is installed. How should I uninstall RealPlayer? Thanks in advance.

---

### Post by mlomker on 2005-09-07
There's probably a /usr/realplay file and the rest of the files are /opt/realplayer...guessing from the link that you supplied.

open a command prompt:

su
updatedb
locate real | more

That will result in a list of all files with the word 'real' in them.  My guess is that it's just one link in /usr and the /opt directory, though.

---

### Post by linuxNewb on 2005-09-08
Thanks, I deleted all of them now. I was still thinking that I needed a windows type uninstaller. I love linux!

---

