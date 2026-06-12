---
title: "permissions problem - cant change apache2 config scripts"
date: 2007-06-02
forum: General Help
---

### Post by Xanderfoxx on 2007-06-02
I'm trying to change a text configuration script, but I can't get permissions to do so.

How am I supposed to sudo this?

media:/sda2/etc/apache2/sites-available/default

change using Kate


What I'm really trying to do is change the root directory for the server, and I'm not having any success, as you can tell.

Help, please?

](*,)

---

### Post by statictonic on 2007-06-02
sudo kate /etc/apache2/sites-available/default

That should do it, if I read right.

---

### Post by Xanderfoxx on 2007-06-03
Thank you so much!

If I could learn to sudo, I wouldn't have to bother you guys so much, but as it is....

I appreciate it!

=D>

---

### Post by Xanderfoxx on 2008-01-04
> **statictonic said:**
> sudo kate /etc/apache2/sites-available/default

That should do it, if I read right.

This simple advice was a lifesaver.

Thank you! :lolflag:

---

### Post by Blindraven on 2008-01-04
> **maurin.alex@gmail.com said:**
> This simple advice was a lifesaver.

Thank you! :lolflag:

Can I just say that your nick is extremely malicious bot crawlable. You should get an admin to change it for you dude :)

---

