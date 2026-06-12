---
title: "GIMPShop on Ubuntu?"
date: 2005-05-03
forum: General Help
---

### Post by adam.b on 2005-05-03
Arr! I have tried to get GIMPShop up and running on Ubuntu and I can't do it. Is there anyone who has been successful who might be able to write a comprehensive howto? 

Please?  :)

---

### Post by chard on 2005-05-05
From: Cron

"I've put up the deb here:

[http://www.imageafter.com/temp/lex/....2.4-2_i386.deb](http://www.imageafter.com/temp/lex/....2.4-2_i386.deb)

and the libc, in case you need it here:

[http://www.imageafter.com/temp/lex/....3.4-2_i386.deb](http://www.imageafter.com/temp/lex/....3.4-2_i386.deb)
edit: (careful! may cause problems!)

Also, here is the menurc config file which lets Gimp use PS shortcuts:

[http://www.imageafter.com/temp/lex/...hop_debs/menurc](http://www.imageafter.com/temp/lex/...hop_debs/menurc)

Copy it to ~/.gimp-2.2/ (but rename your old menurc file before you do)

Use at your own risk ofcourse (I'm installing Hoary on tuesday so I'm a bit more reckless at the moment )"

---

### Post by chard on 2005-05-05
[QUOTE=adam.b]Arr! I have tried to get GIMPShop up and running on Ubuntu and I can't do it. Is there anyone who has been successful who might be able to write a comprehensive howto? 

Please?  :)[/QUOTE]
 From [http://www.macewan.org/index.php?m=200504](http://www.macewan.org/index.php?m=200504)

So you were reading about Gimpshop on codemills & got excited, installed it & the libc6 .deb only to discovered that Hoary is now screwed.

wget [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.2.ds1-13ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.2.ds1-13ubuntu2_i386.deb)
sudo dpkg -i libc6_2.3.2.ds1-13ubuntu2_i386.deb
sudo apt-get install -f

---

### Post by ow50 on 2005-05-05
There are a couple Ubuntu packages posted at codemills. Try this one:
[http://codemills.com/blog/?p=4#comment-142](http://codemills.com/blog/?p=4#comment-142)

---

### Post by radhaz on 2005-05-08
[QUOTE=ow50]There are a couple Ubuntu packages posted at codemills. Try this one:
[http://codemills.com/blog/?p=4#comment-142](http://codemills.com/blog/?p=4#comment-142)[/QUOTE]

That worked for me (so far without breaking anything) using```

dpkg -i --force-overwrite {package name here}

```

---

### Post by Myrtti on 2005-06-03
[QUOTE=ow50]There are a couple Ubuntu packages posted at codemills. Try this one:
[http://codemills.com/blog/?p=4#comment-142](http://codemills.com/blog/?p=4#comment-142)[/QUOTE]
Too bad the domain has expired...

---

### Post by radhaz on 2005-06-09
[QUOTE=Myrtti]Too bad the domain has expired...[/QUOTE]

I got it to work from the source code and posted a [Howto](http://www.ubuntuforums.org/showthread.php?p=205361) for other people to use. If you're interested in trying GimpShop compiling from the source seems to be the safest way at the moment.

---

