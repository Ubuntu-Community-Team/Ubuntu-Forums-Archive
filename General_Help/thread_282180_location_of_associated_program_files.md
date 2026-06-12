---
title: "location of associated program files?"
date: 2006-10-22
forum: General Help
---

### Post by jbu311 on 2006-10-22
Hi all,
I recently installed amarok 1.4 and it asked me to select my media library and I think I accidentally selected some corrupt files.  Consequently, everytime I open up amarok it will get stuck in the "building library" screen and the screen will go gray (compiz).  I've tried to reinstall amarok but even when I do, it goes straight to the "building library" screen without even asking me where my media is this time.  So I thought I could find some files that I could delete to tell amarok to stop looking at those particular files because I can't use Amarok.

Any help is greatly appreciated.

Thanks,
jbu

ubuntu 6.06 32bit

---

### Post by CatKiller on 2006-10-22
I've not used Amarok, but you'll probably have a configuration directory in your Home folder - possibly called .amarok or something similar - that includes all the stuff that you've told Amarok since you installed it. If you delete or rename this directory, you should get back to the way it was when you used it for the very first time.

---

### Post by jbu311 on 2006-10-22
actually i dont have that hidden file

---

### Post by CatKiller on 2006-10-22
> **jbu311 said:**
> actually i dont have that hidden file

> I've not used Amarok ... or **something similar**

I have no idea what it's called. But it's definitely there, and it's definitely called **something**.

Have a look around, or just hope that someone who **has** used it comes along.

---

### Post by bsussman on 2006-10-22
It can be challenging to track down the config files.

try renaming /home/**yourlogin**/.kde/share/apps/amarok

It might help

Assuming you do not have much time invested in the install and that you used synaptic to install, you could try mark for complete removal, apply and then install, apply which does an apt-get purge and then a complete install.

---

### Post by jbu311 on 2006-10-22
CatKiller,
You were right.  I misinterpreted and thought you meant just /home/myUserName and not all of its subdirectories.  I found it about 3 folders deep into myUserName and deleted it.  Everything worked out.

Thanks everyone.

---

