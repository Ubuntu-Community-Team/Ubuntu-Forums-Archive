---
title: "recursive rm with an exclude option"
date: 2007-11-29
forum: General Help
---

### Post by JackRazz on 2007-11-29
I'd like to remove all files on a filesystem except for some specific excluded files (/backups/*). The filesystem isn't live as I'm running debian on a usb stick to do backups/restores on my ubuntu filesystem. 

Is there a way to do this somehow with the rm or another command?

Thanks - JackRazz

---

### Post by colo on 2007-11-29
Use `find`, part of the GNU findutils package. It's documentation is really good, you should be able to tailor a solutions for your problem after reading the manpage.

---

### Post by JackRazz on 2007-11-30
colo,
Thanks for the tip. I started looking at it last night. I see how can do it and started testing it on ubuntu just to get to echo out the results for testing.

JackRazz

---

