---
title: "babytrans"
date: 2005-05-28
forum: General Help
---

### Post by flashdog on 2005-05-28
Hello,
I try to install BABYTRANS, but I get a fault:

```

sudo apt-get install babytrans
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  babytrans: Depends: babytrans-common but it is not installable
E: Broken packages


``` 

How can I intall Babytrans?

---

### Post by Xian on 2005-05-28
You just have a dependency issue whereas the package babytrans-common isn't available. 
What pkg repository is this application babytrans in?

---

### Post by flashdog on 2005-05-28
Babytrans [http://fjolliton.free.fr/babytrans/](http://fjolliton.free.fr/babytrans/) is a Babylon für Linux. Babytrans translate words i.e. from english to german.

I think it is in [http://packages.ubuntu.com/hoary/text/babytrans](http://packages.ubuntu.com/hoary/text/babytrans)

Where can I find babytrans-common?

---

### Post by Xian on 2005-05-28
[QUOTE=flashdog]Where can I find babytrans-common?[/QUOTE]
Looks like it's on the /dists/stable/main/binary-i386 marillat repos.
It is an [unmet dep](http://www.ubuntulinux.org/wiki/UniverseUnmetDeps) in Universe.

```
deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
```

---

### Post by rwabel on 2005-05-28
[QUOTE=Xian]Looks like it's on the /dists/stable/main/binary-i386 marillat repos.
It is an [unmet dep](http://www.ubuntulinux.org/wiki/UniverseUnmetDeps) in Universe.

```
deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
```[/QUOTE]
 works fine for me. You need then to copy the dic files to /usr/lib/babytrans I guess. I've not yet tried that

but the dic files are old and babytrans doesn't support the new format...it's too bad

---

### Post by go_beep_yourself on 2008-05-08
Can Babytran use Babylon dictionaries? I haven't found any good dictionaries to translate from spanish to english and english to spanish yet, so I am looking for a way to use Babylon dictionaries in Linux.

---

### Post by marciowb on 2008-07-17
There is [Stardict]("http://stardict.sourceforge.net"). Try it and love it! It's fantastic! Better than Babylon. Belive me.
If you need some help to full install it or its TTS or glossaries, see tips at: [http://www.marciowb.net/blog/2008/07...a-linux-para-o](http://www.marciowb.net/blog/2008/07...a-linux-para-o)

Regards,
Marcio Wesley Borges
[http://www.marciowb.net/blog/](http://www.marciowb.net/blog/)

---

