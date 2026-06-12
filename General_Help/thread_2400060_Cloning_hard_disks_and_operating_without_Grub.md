---
title: "Cloning hard disks and operating without Grub"
date: 2018-09-02
forum: General Help
---

### Post by webmiester on 2018-09-02
Hi guys,

I wanted to share my experience and ask your opinions regarding this case...

I was setting up several PCs with ubuntu mate 16.04...

So I setup one computer and we cloned  its Hard Disk for all the other computers...  One good thing about ubuntu is that it appears that there is no problem even if the cloned computers have a different specifications with the original one (Unlike in Windows where this process will fail if the specs are different).

When I bootup the cloned computers, Grub doesn't appear (It still loads in the original computer), the clones instead load directly into Ubuntu. I find this really cool, but will I have any problems with this for day-to-day use?  I did have a problem when I upgraded one computer through the terminal, but If I just hold the setup, they seems to work fine.  Should I expect any long term problems with this setup?

Thank you so much.

---

### Post by sudodus on 2018-09-02
At the following link you find ways to make the system show the grub menu.

[Configuring GRUB 2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

In new systems you should use

```

sudo nano /etc/default/grub

```

because gksu is no longer there and it is complicated to run graphical programs with elevated permissions.

```

GRUB_HIDDEN_TIMEOUT=

    No value entered after the = sign
    The menu will be displayed for the number of seconds designated by GRUB_TIMEOUT. 

```

- Save /etc/default/grub after editing

- Run

```

sudo update-grub

```

makes the change active. (It is transferred to grub.cfg.)

---

### Post by webmiester on 2018-09-02
Thank you Sudodus.  Come to think of it, it was elevated permissions that I had problems with after I upgraded the system.

I really like the idea though that Grub doesnt show up and it loads directly into Ubuntu.  Can I still do that if I fix up grub as what your link shows?

---

### Post by sudodus on 2018-09-03
You can make the grub menu appear, and you can make it not appear according to the settings, that are described in that link.

---

