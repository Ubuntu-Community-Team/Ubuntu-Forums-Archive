---
title: "admin user cant change date or wallpaper"
date: 2013-07-19
forum: General Help
---

### Post by daaatz on 2013-07-19
Hi,

my 1st ubntu ser ( with admin rights ) cant change date, wallpaper even remove icons from unity panel.
I've added second user jsu for test and for him everything works fine.

What do I have to do to give my admin user rights to change such things ? Dunno why it happens..
I know I can move my home files to that another user but I just dont want to.

Thanks

---

### Post by dino99 on 2013-07-19
[http://askubuntu.com/questions/84474/how-can-i-give-admin-permissions-to-my-account](http://askubuntu.com/questions/84474/how-can-i-give-admin-permissions-to-my-account)

---

### Post by daaatz on 2013-07-19
Does not work..

---

### Post by steeldriver on 2013-07-19
Those things shouldn't need admin (sudo) rights - perhaps it's an ownership / permissions problem in your old user's home dir e.g. ~/.config or ~/.config/dconf not owned by the user or not writeable (or - for directories - not executable)?

---

