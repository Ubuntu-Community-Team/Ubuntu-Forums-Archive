---
title: "swiftfox issues"
date: 2007-01-03
forum: General Help
---

### Post by fredster001 on 2007-01-03
Hi guys.

Just tried to download swiftfox by using
[http://getswiftfox.com/installer.htm](http://getswiftfox.com/installer.htm)

and installed it. When i went to open it, it just opened firefox (this isnt supposed to happen right)

so i uninstalled it and was going to try again, but then i realised it created a folder in my home folder which it wont let me delete.

I tried typing:

sudo rm /home/freddie/swiftfox
(the folder location) into the terminal and i gave this out:

rm: cannot remove `/home/freddie/swiftfox': Is a directory


So, two things:

1. How can i remove that folder.
2. What went wrong with my swiftfox installation and how shall i get it to work, if it's worth it?

Thanks again.

fredster001

---

### Post by angkor on 2007-01-03
1. rm -r /home/freddie/swiftfox (-r for recursive)
2. How did you start swiftfox? Did it say firefox in the Help -> about. Swiftfox is very similar to firefox and uses it's preferences (at least it did to some extent last time I tried it).

---

### Post by pissedoffdude on 2007-01-03
when you opened up swiftfox did you already have a firefox running? If you have firefox running it will open up another firefox instead of swiftfox

---

### Post by fredster001 on 2007-01-03
i went applications-->Internet--> Swiftfox
yes i did have firefox already open

i will install again and try opening it properly thanks.

---

### Post by evilc on 2007-01-03
Also  you can add to your panel Swiftfox. Just use custom application launch and link to the folder swiftfox is i.e.   /opt/swiftfox/swiftfox.

---

