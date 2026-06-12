---
title: "Terminal and firefox not picking site up, but it exsits?"
date: 2008-05-16
forum: General Help
---

### Post by Swinkid on 2008-05-16
Hey,
I want to download cheese... but i cant, terminal is timing out, and so is firefox..

URL: [http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.22.1-0ubuntu1_i386.deb]("http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.22.1-0ubuntu1_i386.deb")

I know this exsits because, well its on Ubuntu's server!

Thanks, if you can get me a working link or something. please tell me

thanks again, swinkid.

:guitar:

---

### Post by Bakon Jarser on 2008-05-16
> **Swinkid said:**
> Hey,
I want to download cheese... but i cant, terminal is timing out, and so is firefox..

URL: [http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.22.1-0ubuntu1_i386.deb]("http://gb.archive.ubuntu.com/ubuntu/pool/main/c/cheese/cheese_2.22.1-0ubuntu1_i386.deb")

I know this exsits because, well its on Ubuntu's server!

Thanks, if you can get me a working link or something. please tell me

thanks again, swinkid.

:guitar:

Use the synaptic packe manager.

System > Administration > Synaptic Package Manager

Do a search for cheese.  It'll be right on top of the list.  Click the box next to it and click mark for installation.  Hit the apply button in the toolbar and it will download and install.

---

### Post by Swinkid on 2008-05-16
Tryed it, but thanks. but it it didnt work..

:guitar:

---

### Post by Bakon Jarser on 2008-05-16
What do you mean it didn't work?  Did you get an error message or something?  I just installed it through synaptic 5 seconds ago so if it's failing for you then you may have a problem with apt.

---

### Post by Swinkid on 2008-05-16
I think ive got a problem then..

---

### Post by rlcomstock3 on 2008-05-16
Try...

$ sudo apt-get install cheese (or whatever the package name is)

Post the output

---

### Post by Swinkid on 2008-05-16
> **rlcomstock3 said:**
> Try...

$ sudo apt-get install cheese (or whatever the package name is)

Post the outputd

Thanks, tryed it didnt work

---

### Post by Bakon Jarser on 2008-05-16
> **Swinkid said:**
> d

Thanks, tryed it didnt work

Yes, we see it didn't work but can't figure out why it didn't work unless you post the output.

---

### Post by Swinkid on 2008-05-16
> **Bakon Jarser said:**
> Yes, we see it didn't work but can't figure out why it didn't work unless you post the output.

How do i get that? the erorror i got from terminal or..

---

### Post by Bakon Jarser on 2008-05-16
go to the terminal. type

```
sudo apt-get install cheese
```

wait for it to finish.  highlight everything it printed on the screen and copy it.  Paste it here.

---

### Post by Swinkid on 2008-05-17
> **Bakon Jarser said:**
> go to the terminal. type
 

wait for it to finish.  highlight everything it printed on the screen and copy it.  Paste it here.

Meh its fine now, dno what it was..

---

