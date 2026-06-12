---
title: "file permissions, what if laptop gets stolen, will they be able to access files?"
date: 2007-05-10
forum: General Help
---

### Post by olavjunior on 2007-05-10
I was wondering about the file-permissions in ext3. If my laptog should get stolen, will they be able to access (read) my files without my password?

What if I make my files completely private, not readable for others. What if I install another version (I have a seperate home-partition), will my home be unreadable?? Or will they be readable as long as I use my old username? (Will my files then be unreadable if I change my username?)

---

### Post by Rinzwind on 2007-05-10
Yes they can.

1. Grub (the bootloader) will let people have access if they are physically at that system; even when they do not know the root password: it's a failsafe in case you forget your root-account.
2. If someone knows your root-password or is able to change it (via Grub or otherwise) they can access anything on your system.

What you can do is make your system n00b-protected. EXT3 allows for encrypting your filesystem. 
It's not easy to setup though.
Here's our resident topic on this: [http://ubuntuforums.org/showthread.php?t=120091](http://ubuntuforums.org/showthread.php?t=120091)

---

### Post by ikonia on 2007-05-10
anyone can boot from any linux live cd and mount your hard disk despite the permissions. So yes anyone can see your files if they steal your laptop in your current example.

---

### Post by starcraft.man on 2007-05-10
Google truecrypt both on the forums and google, its a great software for encryption. :)

---

### Post by olavjunior on 2007-05-10
Thanx alot guys! This was what I wanted to know :)

I'm already using trucrypt for my most sensetive files, great app!

I just started wondering about the saftey of my files after learning about this app: [http://www.thelaptoplock.com/]("http://www.thelaptoplock.com/")

Would be nice if anyone with the competanse would make this for ubuntu :)

---

