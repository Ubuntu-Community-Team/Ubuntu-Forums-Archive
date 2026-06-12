---
title: "Removal of a LAMP Server."
date: 2015-06-03
forum: General Help
---

### Post by BlinkinCat on 2015-06-03
Hi all,

At present I have WordPress set up on a LAMP Server.

Without any need to go into the reasons why, I now wish to completely remove the installation.

I came across the following commands.

1.```
sudo apt-get remove --purge apache2 php5 mysql-server-5.0 phpmyadmin
```

2.```
sudo tasksel remove lamp-server
```

Which do I need to apply to achieve what I require? I noticed that taskel at present does not appear to be installed. Should I install taskel first?
Are there any further needs?

```
sudo apt-get install tasksel
```

Thanks for any help offered - :)

Edit : Do I need to remove Wordpress first and if so with which command ?
        The installation has not been added to in any way.

---

### Post by BlinkinCat on 2015-06-04
Added Edit.

---

### Post by BlinkinCat on 2015-06-04
Hi,

I ran all of the above commands and all now appears to be good.

I also ran -

```
sudo apt-get update && sudo apt-get upgrade -y
```

I have also taken steps to open an account with a hosting service and will then install Wordpress from their Control Panel.

As everything now appears to be O.K. I will mark this thread as solved.

Thanks - :)

---

