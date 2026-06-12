---
title: "I'm not i386, am I?"
date: 2008-05-17
forum: General Help
---

### Post by jpoRS on 2008-05-17
I "know" my computer isn't i386, but ever since I upgraded to Hardy, I can't add many applications, citing the fact that my system is i386.  Now I am questioning myself.  My computer is a three year old hp, it can't be i386, can it?  Is there any way I can check (I lost all of my paperwork long ago, and information from hp is cloudy at best) short of opening up my laptop?

Assuming I'm not i386, how do I "prove" it to Ubuntu?

Thanks,
jim

---

### Post by chrisccoulson on 2008-05-17
What does:
```
uname -a
```
say?

This will tell you what kernel you're running, and whether it is i386 or x86-64

---

### Post by mardawi on 2008-05-17
what's the output of
```
uname -a
```

---

### Post by scxtt on 2008-05-17
what's the output of:

**cat /proc/cpuinfo; uname -a**

maybe you're just using a strictly i386 kernel for some reason ... the -generic kernel should be working fine.

---

### Post by Joeb454 on 2008-05-17
Instead of ```
uname -a
``` you can always run ```
uname -m
``` Which will just give you the exact bit of info you are after :)

Also to the O.P i386 is usually a 32 bit install

---

### Post by Sleaka J on 2008-05-17
Are you sure you're not confusing i386 with x86 ?

---

### Post by Frak on 2008-05-17
If you are running an Intel Pentium 3 or above, you run an i386 compatable processor.

If you are running an AMD Sempron or Athlon or above, you run an i386 compatable processor.

If you run a VIA Cyrix III or above, you run an i386 compatable processor.

---

### Post by storm99999 on 2008-05-18
> **Frak said:**
> If you are running an Intel Pentium 3 or above, you run an i386 compatable processor.

If you are running an AMD Sempron or Athlon or above, you run an i386 compatable processor.

If you run a VIA Cyrix III or above, you run an i386 compatable processor.

Hmm, I believe that the VIA C3, Amd Athlon/Sempron, and Pentium Pro were the minimum to have the i686 instructions, and anything newer than an actual 386 were 386 compatible.

Anyways, back to the point.  So, apt-get won't install packages because you're i386?  What, specifically (or anything, for analysis purposes), fails, and how does it fail?  Does it state that you're trying to install a package that is <insert something not i386 here> architecture and that won't work?

---

### Post by Frak on 2008-05-18
> **storm99999 said:**
> Hmm, I believe that the VIA C3, Amd Athlon/Sempron, and Pentium Pro were the minimum to have the i686 instructions, and anything newer than an actual 386 were 386 compatible.
Anything below those won't run Ubuntu period.

---

### Post by jpoRS on 2008-05-18
uname -a:

```
Linux Alfred 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
```


So i686, that is what I thought.

As for what is failing, when I apt-cache search anything, i get no response, just a newline.  Example:

```
owner@Alfred:~$ apt-cache search hydrogen
owner@Alfred:~$
``` 

When I apt-get install hydrogen, i get the following:

```
owner@Alfred:~$ sudo apt-get install hydrogen
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hydrogen
owner@Alfred:~$
``` 

When I go to Applications>Add/Remove and search for hydrogen, the program shows up, but comes with this disclaimer:

This application is provided by the Ubuntu community.
Hydrogen cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

I am just using hydrogen as an example, it is the same story for any application I try, unless I already have the program installed.  For example, Amarok shows up fine everywhere.

It is also probably important to note that I didn't have this problem before I upgraded to Hardy a few days ago.

Thanks,
jim

---

### Post by storm99999 on 2008-05-18
Try going into Synaptic ([System]-[Administration]-[Synaptic Package Manager]) and go to [Settings]-[Repositories] and make sure that on the first page that at least the first is checked, possibly the next two or three if, for the second one, you want community packages, for the third one, you need restricted drivers, or for the fourth one, you live in an area that the legal liability of some of the software there does not apply.

It appears that there's no data for your repositories, and apt-get is spazzing out about it.  That is farily likely for the first two problems, and for the last one, maybe it just can't find the i386 package...

---

### Post by jpoRS on 2008-05-19
Bingo!

Thanks storm.  I have been in and out of my repositories since the problem began, but I was vim-ing instead of going through Synaptic.  I guess I just glazed over it.

Muchas gracias!

jim

---

