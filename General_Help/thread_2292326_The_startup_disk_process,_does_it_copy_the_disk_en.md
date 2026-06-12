---
title: "The startup disk process, does it copy the disk entirely along with user settings ?"
date: 2015-08-27
forum: General Help
---

### Post by arunb on 2015-08-27
Hi,


Is it possible to make a installation image using the startup disk creator, that also stores the various custom user settings, also start-up programs, user data etc ?

I would like to provide an installation copy to my users, this will also serve as a rescue disk...Is this possible with the startup disk creator program ??

thanks
a

---

### Post by nerdtron on 2015-08-27
You can setup a persistence on your created startup disk. I think the limit on that is 4GB so if you have an 8GB flash drive, you can have the LIVE installer, plus 4GB of space where you can save your settings that survives on each reboot (including wallpaper, and some small programs).

---

### Post by Bucky Ball on 2015-08-27
Are you talking about creating your own custom ISO of your currently installed setup? If so, [Clonezilla]("https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/") might help.

---

