---
title: "How to erase and burn data dvd?"
date: 2008-01-04
forum: General Help
---

### Post by Zdravko on 2008-01-04
I have a dvd and a folder on the computer. What must I do to erase the dvd and write the folder into it?

---

### Post by dannyboy79 on 2008-01-04
k3b can do this. it's a dvd authoring/erasing application. I am not sure about any gnome app that can do it but kde apps run fine in gnome, they just install a bunch of kde libraries which take up a little space but k3b is a very good app.

---

### Post by Zdravko on 2008-01-04
My internet connection is very slow and I must use it sparingly. Tell me a small but useful application that is capable of performing these tasks.

---

### Post by logos34 on 2008-01-04
Why not just use the nautilus cd/dvd creator?

---

### Post by dannyboy79 on 2008-01-04
i didn't think the nautilus cd/dvd creator can erase dvd's? i know it can create data dvd's/cd's as well as iso images but wasn't sure about erasing which is why I suggested k3b.

you could try growisofs which I believe is part of dvd+rw package. here it is:
[http://www.allynelectronics.com/debs/dvd+rw-tools_7.0-4_i386.deb](http://www.allynelectronics.com/debs/dvd+rw-tools_7.0-4_i386.deb)

the command once you get dvd+rw tools installed would be this

sudo growisofs -Z /dev/dvd=/dev/zero

IF /dev/dvd is thwe location of your rewritable dvd.

tehn to write a data dvd would be this as an example.

sudo growisofs -Z /dev/dvd=/home/jeff/books/

check out the man pages for growisofs, you can read it online for all the options. [http://linuxcommand.org/man_pages/growisofs1.html](http://linuxcommand.org/man_pages/growisofs1.html)

---

### Post by Craigus on 2008-01-04
It isn't necessary to erase rewritable DVD's - in fact if you tell K3b to erase a DVD it will tell you that it isn't necessary and won't do it.

---

### Post by logos34 on 2008-01-04
> **dannyboy79 said:**
> i didn't think the nautilus cd/dvd creator can erase dvd's? i know it can create data dvd's/cd's as well as iso images but wasn't sure about erasing which is why I suggested k3b.


yes, it can erase/format (if there is not enough room on dvd it will ask to do so).  Although k3b would certainly be the next thing to try.

> It isn't necessary to erase rewritable DVD's - in fact if you tell K3b to erase a DVD it will tell you that it isn't necessary and won't do it.

Yep.  (never have quite figured out why it does that, though--I format dvd's all the time in XP using Nero with no apparent damage to discs)

---

### Post by Zdravko on 2008-01-04
> **logos34 said:**
> Why not just use the nautilus cd/dvd creator?
Thanks, that was  it!

---

### Post by Gina on 2008-01-16
I haven't been able to erase DVDs with Nautilus.  It will write DVD-RWs fine as long as they're not already written to but re-using a DVD-RW for burning an ISO (for instanace) using Nautilus gives an error when you agree to Erase DVD :(  I have just committed the "mortal sin" of booting the dreaded Windows XP and Nero to erase some DVD-RWs.  Haven't had to do that for ages!  

I'll install k3b and try that - thanks for the suggestion :L)

---

### Post by Gina on 2008-01-16
k3b did the trick - thanks :)

---

### Post by Gina on 2008-01-16
> **dannyboy79 said:**
> k3b can do this. it's a dvd authoring/erasing application. I am not sure about any gnome app that can do it but kde apps run fine in gnome, they just install a bunch of kde libraries which take up a little space but k3b is a very good app.  Thank you :)  Just installed it and used it to write an ISO, on a pre-written DVD-RW - perfect.  Looks like a nice app :)

---

