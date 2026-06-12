---
title: "some questions on zim desktop wiki and tomboy"
date: 2008-03-18
forum: General Help
---

### Post by pedrotuga on 2008-03-18
I use my own online wiki for notes so i never realy gave a try to aplications like tomboy, tiddly wiki or zim.

But recently since they are comming with so cool features I decided to guive them a try and i am quite impressed.

First of all... a dummy question that doesn't relate directly do tomboy... how do i set it to start when my system starts up?

Now about zim... i'm quite impressed, the coolest feature is that it comes with txt2tags output.
that basically makes it one of the most efficient documentation tools since one can export the content to latex, man pages, html, wiki format and others...

I want to try zim's equation editor. On zim's website it says that i need to have latex installed in order to use that plugin. In fact the plugin doesn't show in the plugin list in zim... but i haven't install latex.
Does anybody uses that feature?
Does the version available on the repos has the equation editor plugin?
I thought i would ask before installing tons of packages that i might not need.

EDIT:
also, another question on tomboy.
What's with the pins? they just change state... i can't find any difference in behavior between pinned and non pinned notes...

---

### Post by Xzenome on 2008-04-12
I'm experiencing the same problem. The root cause seems to be that 0.19 (the version in the ubuntu repositories) does not come with the plug-in. Simply substituting in the plug-in file doesn't seem to work. The latest version (available from a third party but linked to on the Zim website does contain the formula plugin though).

Install the following packages in order:
[http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-basedir-perl_0.03-0kv0_all.deb](http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-basedir-perl_0.03-0kv0_all.deb)
[http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-desktopentry-perl_0.04-0kv0_all.deb](http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-desktopentry-perl_0.04-0kv0_all.deb)
[http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/zim_0.23-0kv3_all.deb](http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/zim_0.23-0kv3_all.deb)

It looks like there may be some bugs, but from my quick test it seems to work fine. Ignore any notices about older versions in the repository.

---

### Post by nanotube on 2008-05-10
> **Xzenome said:**
> I'm experiencing the same problem. The root cause seems to be that 0.19 (the version in the ubuntu repositories) does not come with the plug-in. Simply substituting in the plug-in file doesn't seem to work. The latest version (available from a third party but linked to on the Zim website does contain the formula plugin though).

Install the following packages in order:
[http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-basedir-perl_0.03-0kv0_all.deb](http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-basedir-perl_0.03-0kv0_all.deb)
[http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-desktopentry-perl_0.04-0kv0_all.deb](http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/libfile-desktopentry-perl_0.04-0kv0_all.deb)
[http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/zim_0.23-0kv3_all.deb](http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/zim_0.23-0kv3_all.deb)

It looks like there may be some bugs, but from my quick test it seems to work fine. Ignore any notices about older versions in the repository.

thanks for the links! an update: the zim package up there is now 0.24:
[http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/zim_0.24-0kv0_all.deb](http://www.tu-harburg.de/~vkv/gutsy/zim/binary-i386/zim_0.24-0kv0_all.deb)

---

