---
title: "Uninstall Wesnoth"
date: 2008-05-04
forum: General Help
---

### Post by Oreo Priest on 2008-05-04
I recently installed Battle for Wesnoth using what I think were packages, and now I want to uninstall it, but I don't see it listed in Synaptic. I find this odd, for one because it does show up in the "start menu" (sorry, but I don't know what it's properly called) under games.

How can I get rid of it?

Thanks

---

### Post by Monicker on 2008-05-04
When you run this command from a terminal, is it listed?

```
dpkg --get-selections|grep wesnoth
```


I see that there are several wesnoth packages in the repos.  If you used one of those, then do =:


```
sudo apt-get remove wesnoth
```


You may have to change the package name in the remove command, depending on the results from the dpkg command.

---

### Post by Oreo Priest on 2008-05-05
The second one worked. Thanks!

---

