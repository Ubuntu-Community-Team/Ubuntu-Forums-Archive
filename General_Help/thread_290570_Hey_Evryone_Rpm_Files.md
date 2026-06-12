---
title: "Hey Evryone Rpm Files"
date: 2006-11-01
forum: General Help
---

### Post by Lukasz Tarkowski on 2006-11-01
Hey evryonene
How is evryone today.
my name is Lukasz I am Polish/Canadian
I was born in Poland and I live in Canada
I have a question?
How can I use rpm's files in ubuntu, cause it says archieve is not supported when I try to open the rpm hehe 
Thank You

---

### Post by taurus on 2006-11-01
You can use alien to convert it to .deb and install it...  Open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo aptitude update
sudo aptitude install alien
alien <filename>.rpm
sudo dpkg -i <filename>.deb

```

---

### Post by stalker145 on 2006-11-01
> **Lukasz Tarkowski said:**
> How can I use rpm's files in ubuntu

[How to install *anything* in ubuntu]("http://monkeyblog.org/ubuntu/installing/"):-D

---

### Post by aysiu on 2006-11-01
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Lukasz Tarkowski on 2006-11-01
Hey Evryone
How do I set and unset
You must set the environment variable CC to a working compiler.
Anyone know?

---

### Post by taurus on 2006-11-01
> **Lukasz Tarkowski said:**
> Hey Evryone
How do I set and unset
You must set the environment variable CC to a working compiler.
Anyone know?
I think you are confusing Gentoo with Ubuntu!!!  If you want to compile something from source, just install the build-essential and you are all set...

```
sudo aptitude install build-essential
```

---

### Post by Lukasz Tarkowski on 2006-11-01
Hey evryone
Does anyone know how to configure lostirc chat client hehe
Alternatively you may set the GLIBMMDEPS_CFLAGS and GLIBMMDEPS_LIBS environment variables

[http://lostirc.sourceforge.net/](http://lostirc.sourceforge.net/)
I tried glibmm installing that, the lostir client requires that

sorry Im a newb

If there is a documentation please post the link here or a guide on how to configure Ubuntu hehe :)
Cause Im a newb :p

---

