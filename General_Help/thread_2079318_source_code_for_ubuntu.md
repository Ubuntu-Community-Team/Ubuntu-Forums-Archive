---
title: "source code for ubuntu"
date: 2012-11-01
forum: General Help
---

### Post by shahnitrr on 2012-11-01
i want full source code for ubuntu
how can i get it

---

### Post by oldos2er on 2012-11-01
Make sure source code repositories are enabled (gksudo software-properties-gtk) then choose which package you want the source for ```
apt-get source <package>
```

---

### Post by shahnitrr on 2012-11-01
can i get it as atxt file or something i can download...

---

### Post by localhost8080 on 2012-11-01
there isnt a single file that you can download, rather each compiled binary package has its own source package available

the source code for the linux kernel for example - which you can download from kernel.org - can be downloaded inside ubuntu by typing 'apt-get source --only-source linux' in a terminal (bash prompt)

---

### Post by MG&amp;TL on 2012-11-01
> **shahnitrr said:**
> can i get it as atxt file or something i can download...

What are you trying to do? You seem to have some misconceptions:

1) It's a single program ("a [single] txt file"). Ubuntu is made up of hundreds of programs and libraries working in harmony. If you want a particular bit, get that bit's source code.

2) It's a small piece of data ("or something I can download"). The source code packages for the default release of ubuntu would easily fill a couple of GB, the entire repositories several hard drives.

---

### Post by Slim Odds on 2012-11-01
> **MG&TL said:**
> What are you trying to do? You seem to have some misconceptions:

1) It's a single program ("a [single] txt file"). Ubuntu is made up of hundreds of programs and libraries working in harmony. If you want a particular bit, get that bit's source code.

2) It's a small piece of data ("or something I can download"). The source code packages for the default release of ubuntu would easily fill a couple of GB, the entire repositories several hard drives.
I agree with some of that, but I think that you have a misconception about how big hard drives are today.

---

### Post by Cheesemill on 2012-11-01
> **Slim Odds said:**
> I agree with some of that, but I think that you have a misconception about how big hard drives are today.
True.

The entire Ubuntu repository is around 548GB (as of 14/06/2012).

---

### Post by lisati on 2012-11-01
> **shahnitrr said:**
> can i get it as atxt file or something i can download...

You've probably figured out by now that the idea of downloading the source code for Ubuntu can mean different things to different people, and that it *can* result in a [SIZE="4"]big[/SIZE] download.

What I recommend is that you decide which part of Ubuntu that you would like to concentrate on, and let us know. We can then offer suggestions on where to begin.

Another place to start would to be to see if there are any good [books]("http://ubuntuforums.org/showthread.php?t=1660822") around.

---

### Post by oldos2er on 2012-11-01
> **shahnitrr said:**
> can i get it as atxt file or something i can download...

The command I gave you downloads the source for which ever package you choose.

---

### Post by MG&amp;TL on 2012-11-02
> **Slim Odds said:**
> I agree with some of that, but I think that you have a misconception about how big hard drives are today.

True. I have some ancient hardware around, my biggest HDD is 80GB. :P

---

### Post by Slim Odds on 2012-11-02
> **MG&TL said:**
> True. I have some ancient hardware around, my biggest HDD is 80GB. :P

Are you running the 16 bit version of Ubuntu? :lolflag:

---

### Post by nothingspecial on 2012-11-02
[SIZE="3"][COLOR="Red"]Don't actually do this[/COLOR][/SIZE]

but

```
for f in $(dpkg --get-selections); do apt-get source "$f"; done
```

would probably do it.

---

