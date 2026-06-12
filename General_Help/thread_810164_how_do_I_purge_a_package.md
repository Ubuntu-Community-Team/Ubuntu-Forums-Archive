---
title: "how do I purge a package?"
date: 2008-05-28
forum: General Help
---

### Post by DarkDancer on 2008-05-28
Earlier I was trying to get Skype  to work (no luck there) in 64 bit hardy. I ran into some instructions that included this command:

>  sudo dpkg -i –force-architecture skype-debian_2.0.0.68-1_i386.deb


I've tried:

> sudo apt-get purge skype-debian_2.0.0.68-1_i386.deb

and

> sudo apt-get purge skype

What have I done wrong?

---

### Post by sdennie on 2008-05-28
What error messages are you getting with those commands?  It will probably be:

```

sudo apt-get purge skype-debian

```

If that doesn't work, you should be able to figure out the package name with:

```

dpkg -S `which skype`

```

---

### Post by DarkDancer on 2008-05-28
ok, this:

> sudo apt-get purge skype-debian_2.0.0.68-1_i386

gives me:

> E: Couldn't find package skype-debian_2.0.0.68-1_i386

This:

>  apt-get purge skype

gives me:

> Package skype is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

this:

>  sudo apt-get purge skype-debian

gives me:

> E: Couldn't find package skype-debian

and this:

> dpkg -S `which skype`

gives me:

> skype: /usr/bin/skype

which I don't know what to do with it.

---

### Post by sdennie on 2008-05-28
How odd.  What does this show:

```

dpkg -l | grep skype

```

---

### Post by DarkDancer on 2008-05-28
ok, dpkg -l | grep skype gives:

> ii  skype                                      2.0.0.68-1                                         Skype - Take a deep breath


---

### Post by sdennie on 2008-05-28
I'm not sure what is going on but, does this work:

```

sudo apt-get remove --purge skype

```

---

### Post by DarkDancer on 2008-05-28
sudo apt-get remove --purge skype gives:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by sdennie on 2008-05-28
I'm at a complete loss.  The output of the commands you've typed seem almost impossible.  Sorry I can't help more.

---

### Post by DarkDancer on 2008-05-28
Well, thanks for trying.... ;)

---

### Post by jocko on 2008-05-28
Have you tried finding it in synaptic and purging it from there ("Mark for complete Removal")?

Another thing: To get a 32 bit package to work in 64 bit ubuntu, you probably need to install the package ia32-libs.

---

### Post by DarkDancer on 2008-05-28
It's not in synaptec. I installed it from a deb so synaptec has no clue it's there.

---

### Post by NikoC on 2008-05-28
According to the debian page on dpkg:
dpkg --list 
Gives you a list of all installed .deb packages
dpkg --list 'sky*'
Gives you a list of all packages starting with 'sky'
dpkg --remove packagename
Removes the packages but does not purge it
dpkg --purge packagename
Also removes the configuration files

Can't really try it out here, because I'm not on my linux machine...

---

### Post by DarkDancer on 2008-05-28
Thanks, that got it! ;)

---

### Post by jocko on 2008-05-28
> **DarkDancer said:**
> It's not in synaptec. I installed it from a deb so synaptec has no clue it's there.

Synaptic is a frontend for dpkg/apt, so it will see **all** **installed** debs, no matter how you installed them.
Just look in "Status" --> "Installed (local or obsolete)" to find all installed packages that are not available in the repos.
There you'll see everything you have installed directly from downloaded debs..

---

