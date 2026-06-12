---
title: "Problems with mercury and IBM JRE"
date: 2007-11-15
forum: General Help
---

### Post by alexander.forster on 2007-11-15
I tried installing mercury messenger since it has a lot of the features that pidgin lacks, and it installed very nicely, but when i try to run it all i get it a blank grey window, i read somewhere that installing the IBM JRE instead of the SUN one might fix this issue, but i cannot seem to install the IBM JRE.

ive been trying to do some research and have spent hours and have come up with nothing... so im not just being lazy by asking for help here :)

does anyone know how to fix the grey window issue?
or atleast install the IBM JRE?

id be more than happy to post any needed  info, im just not sure what someone would need to know in order to help me.


thank you very much in advance :D

---

### Post by odiseo77 on 2007-11-16
Hi. The latest mercury-messenger version only runs with Sun JVM, so you need it. The reason why you're getting a blank window is because you're probably using compiz/beryl/etc, and Sun JVM doesn't get along with composited managers. Luckily, Gutsy has this problem solved with the latest version of Java (1.6), so, if you're on Gutsy, try this:

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

(You'll have to enable the canonical repository in order to install java 1.6)

After the packages are installed, type:

```
sudo update-alternatives --config java
```

And select the number for java 1.6 at the menu prompt.

You should be able to run mercury after that (even with compiz enabled).

Now, if you're on Feisty, or an older Ubuntu release, you'll have to install java 1.6 and apply a patch in order to make it work.

Regards.

---

### Post by alexander.forster on 2007-11-16
:D:D:D

wow. thank you very much sir. your advice worked perfectly, im only 17 and the gutsy release is my first linux os, so i dont know a whole lot, but hopefully someday ill be able to give advice like that.

thank you!

---

### Post by odiseo77 on 2007-11-16
> **alexander.forster said:**
> :D:D:D

wow. thank you very much sir. your advice worked perfectly

You're welcome (btw, only 'odiseo' is fine ;))

> **alexander.forster said:**
> im only 17 and the gutsy release is my first linux os, so i dont know a whole lot, but hopefully someday ill be able to give advice like that.

thank you!

At least you know how to explain things and follow some basic instructions; I've met people using linux for ages and wouldn't be capable of following these -very basic- instructions ;)

Greetings!

---

### Post by Skorzen on 2007-11-17
> **odiseo77 said:**
> Hi. The latest mercury-messenger version only runs with Sun JVM, so you need it. The reason why you're getting a blank window is because you're probably using compiz/beryl/etc, and Sun JVM doesn't get along with composited managers. Luckily, Gutsy has this problem solved with the latest version of Java (1.6), so, if you're on Gutsy, try this:

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

(You'll have to enable the canonical repository in order to install java 1.6)

After the packages are installed, type:

```
sudo update-alternatives --config java
```

And select the number for java 1.6 at the menu prompt.

You should be able to run mercury after that (even with compiz enabled).

Now, if you're on Feisty, or an older Ubuntu release, you'll have to install java 1.6 and apply a patch in order to make it work.

Regards.

Thanks a lot, mate. This was very useful to me.

---

### Post by alexander.forster on 2008-04-29
:) i just used this again with 8.04, very helpful!

---

