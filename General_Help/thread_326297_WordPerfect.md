---
title: "WordPerfect"
date: 2006-12-27
forum: General Help
---

### Post by ubergoods on 2006-12-27
I am having trouble opening wordperfect documents in orenoffice or abiword.  I installed libwpd from the synaptic packet manager but nothing happened.  I also tried running the program in wine but have had no luck so far.  Please help or direct me towards a support guide for either product.

---

### Post by angrykeyboarder on 2006-12-27
> **ubergoods said:**
> I am having trouble opening wordperfect documents in orenoffice or abiword.  I installed libwpd from the synaptic packet manager but nothing happened.  I also tried running the program in wine but have had no luck so far.  Please help or direct me towards a support guide for either product.

Try [wpd2sxw]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wpd2sxw")

```
$ sudo apt-get install wpd2sxw
```

wpd2sxw is a utility to convert WordPerfect documents to OpenOffice.org format.

---

### Post by ubergoods on 2006-12-27
> **angrykeyboarder said:**
> Try [wpd2sxw]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=wpd2sxw")

```
$ sudo apt-get install wpd2sxw
```

wpd2sxw is a utility to convert WordPerfect documents to OpenOffice.org format.

I just ran this, so now do I have to convert each document individually in the terminal?  Or is there a graphical interface I can do this in?  If I have to run it in the terminal can you elaborate the commands  I have to input a little more.  Sorry, I'm new to linux.

---

