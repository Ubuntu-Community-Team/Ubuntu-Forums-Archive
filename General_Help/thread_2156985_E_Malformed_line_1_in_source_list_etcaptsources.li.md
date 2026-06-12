---
title: "E: Malformed line 1 in source list /etc/apt/sources.list (dist parse)"
date: 2013-06-23
forum: General Help
---

### Post by Signaidy on 2013-06-23
Hello, i updated some security packages, and reboot the system after it finalized (just to make sure everything whent well) but i got this error after using apt-get update:

> E: Malformed line 1 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I dunno what to do. Can someone help me please, thanks before hand.

P.S.

I went to check the /etc/apt/sources.list file, and this is all of what was in there:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-proposed

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]Signaidy; Hi ! Welcome to the forum !...

I am stupefied that the /etc/apt/sources.list file could get in that condition. Please check again:
```

cat /etc/apt/sources.list

```
else: we will have to work on generating you a new 'list !
[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by Signaidy on 2013-06-24
Okay, I run the terminal and wrote the comand you told me, but only this is shows :
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-proposed

---

### Post by Bashing-om on 2013-06-24
Signaidy; Hey,

uhh, not good !.. ok ..go to this site:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
and insert your data in the required fields to generate a new updated sources.list file
Then, terminal codes:
```
sudo apt-get update
sudo apt-get upgrade

```

Post back with any difficulties encountered.

---

### Post by Signaidy on 2013-06-24
Thanks, that did ti, everything seems to be fine!
Thanks for your help :KS

---

### Post by Bashing-om on 2013-06-24
[COLOR=#000000]Signaidy; Hey ,

Pleased to be of some assistance.

[/COLOR]Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=2]
Ain't ubuntu wonderful

[/INDENT]

---

