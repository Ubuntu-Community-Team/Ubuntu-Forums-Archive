---
title: "How can i reset GRUB to origonal menu.lst file?"
date: 2007-12-22
forum: General Help
---

### Post by thenetduck on 2007-12-22
Hi

I would like to know if there is a command like "grub-update" that will reset your existing GRUB menu.lst to what it's original (original being what it looked like when you first installed Ubuntu on the machine). 

Is there such a command? Reason I am asking is because I would like to use it for a program I am writing. 

The Net Duck

---

### Post by viking777 on 2007-12-22
You probably need to read this:

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

---

### Post by nick_h on 2007-12-22
> I would like to know if there is a command like "grub-update"

Almost! the command is update-grub - it will re-generate the automatically generated list of Ubuntu kernels, but won't touch anything extra added outside the generated list.

---

### Post by thenetduck on 2007-12-22
> **nick_h said:**
> Almost! the command is update-grub - it will re-generate the automatically generated list of Ubuntu kernels, but won't touch anything extra added outside the generated list.

Wow I think that is what I was looking for and I didn't even know I was looking for it. Thanks

---

### Post by StephX on 2007-12-22
i just tried this and had some issues...

first i needed to login as "su" in the terminal (just type su)

  (if you don't have an su password you may have to create on using "sudo passwd" in the terminal and then entering a password)

after loging in as su i was able to run "update-grub"

-al

---

