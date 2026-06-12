---
title: "[edgy-desktop] Why Evolution?"
date: 2006-10-27
forum: General Help
---

### Post by cataenry on 2006-10-27
Hi all,
i would like to know why the ubuntu-desktop in edgy depends over Evolution..
Here there is a discussion where it's easy to see how people prefers Thunderbird.

[http://www.ubuntuforums.org/showthread.php?t=190461&page=21](http://www.ubuntuforums.org/showthread.php?t=190461&page=21)

But even if the staff prefers Evolution, isn't better a virtual package like
email-client wich depends in one of them so that removing evolution doesn't remove ubuntu-desktop?

This is not a critic but a discussion, thanks!

Bye

---

### Post by skymt on 2006-10-27
Evolution is (a) more than an email client, and (b) integrated into Gnome. Until Gnome 3 arrives, with the universal back-ends we're promised, we're stuck with Evolution for integration.

---

### Post by cataenry on 2006-10-27
What i meant was that i'm not free to replace evolution with TB without remove also ubuntu-desktop. It would be great to have a vpackage to avoid this situation.. To have evolution has a default email client is one thing, "if you wanna have ubuntu-desktop u must have evolution" has nothing to do with integration...

---

### Post by Choad on 2006-10-27
he means that the ubuntu-desktop meta package you install with ubuntu is *not* responsible for depending on evolution. it is the gnome project it's self that depends upon it, so unless they fork the whole gnome project and unlink the dependencies, they are stuck with it

i think thats what hes saying anyway

---

### Post by skymt on 2006-10-27
ubuntu-desktop is a metapackage that depends on all the default packages Ubuntu installs. You can safely remove it, and Evolution, if you want to.

---

### Post by cataenry on 2006-10-27
Ah, ok, now i see... i didn't get gnome dependency with it..
Thanks a lot for the explanation!

Bye

---

