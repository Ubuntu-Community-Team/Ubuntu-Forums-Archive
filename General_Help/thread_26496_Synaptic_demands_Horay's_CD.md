---
title: "Synaptic demands Horay's CD?"
date: 2005-04-13
forum: General Help
---

### Post by la-karaviro on 2005-04-13
Hi,

since yesterday synaptic on my Ubuntu Horay Hedgehog 5.04 demands the System CD, is there a Server problem around, or does something got wrong in my configurations? or does some packeges download from servers and some you need to get from the CD?

---

### Post by heimo on 2005-04-13
I got this same thing some time ago. For me the solution was to uncomment the line for that cd in /etc/apt/sources.list (at the beginning of file). I don't know if need to, but *sudo apt-get update* may be neccessary after that.


EDIT: Oh, and for those with new to editing configuration files and commenting out lines, what you do is open terminal window, type *sudo gedit /etc/apt/sources.list*, add # sign at the beginning of the line you don't need (that line probably begins with *deb*), save the file and you're done.


EDIT: line->file

---

### Post by accuser on 2005-04-13
Out of the box, APT is configured (see /etc/apt/sources.list) with a number of repositories, including the collection of packages on the installation CD-ROM. If you don't want to use the CD-ROM, just comment out that line in your sources.list file and then run the following at the command line:
```

$ apt-get update

```

---

### Post by la-karaviro on 2005-04-13
Thank you guys very much :)

just for information, did i change this, strange that it worked yesterday in the morning?!

how ever everything is fine now, (more or less :))

thanks and bye

---

