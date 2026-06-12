---
title: "grub2-set-default for nested systems?"
date: 2013-02-06
forum: General Help
---

### Post by Jonnycat5000 on 2013-02-06
Hello, When using grub2-set-default, it is an easy matter to set the default OS  by number, but how do I select a nested OS?  These are the OSs listed  under the various "advanced options" listings. 

I saw this information on a webpage last week, but of course I can't  find it now.  IIRC, it was something like "grub2-set-default x,y" (but  of course that's not it). 

Anyone know what the correct syntax is for the nested systems, using the number starting from "0"?

Thanks!

---

### Post by oldfred on 2013-02-06
Welcome to the forums.

drs305 suggests using the title (exactly) as one way.

[https://help.ubuntu.com/community/Grub2/Submenus](https://help.ubuntu.com/community/Grub2/Submenus)

[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)

---

### Post by Jonnycat5000 on 2013-02-06
Thanks Fred, it looks like the correct syntax is as follows:

grub2-set-default "x>y"

BTW: The quotation marks are required for this to work.

---

