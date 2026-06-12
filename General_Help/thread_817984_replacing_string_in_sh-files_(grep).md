---
title: "replacing string in sh-files (grep)"
date: 2008-06-04
forum: General Help
---

### Post by p.becks on 2008-06-04
Hello,

I need some help with this problem:

I have a folder called "scripts" in this folder i have more folder which contain all sorts off scripts i wrote. I need to search all these sh-files in all the folders for the occurrence of the string "sudo" and replace it with "sudo -c" ("sudo su" / "gksudo" should be ignored!)

I am trying to sed it but without success.

Can you help?:confused:

---

### Post by sdennie on 2008-06-04
Sounds like you want something like this:

```

sed -i -e 's/^sudo/sudo \-c/g' `find ~/scripts -name "*.sh"`

```

Don't actually type that (I didn't try it) but, that's the general idea.

---

