---
title: "Software for burning video to DVD's"
date: 2007-04-14
forum: General Help
---

### Post by Error47 on 2007-04-14
Hello all, I am looking for a something that can help me easily burn any video file to work on a DVD player. Right now, I have an .avi file that I need to  burn. I do have a DVD burner.

---

### Post by taurus on 2007-04-15
You can use DeVeDe.

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by martinw89 on 2007-04-15
I remember the Gentoo Wiki had something on the subject ([http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode](http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode)).  Of course some things are different, like we use Debian based package management and not Portage, but everything else should be the same.

---

### Post by Error47 on 2007-04-15
I downloaded and extracted devede, but I have no clue on how to install it. 

And Martinw89's link doesn't work.

---

### Post by taurus on 2007-04-15
There is an install.sh which allows you to install it on your machine.

```
sudo ./install.sh
```

---

### Post by Error47 on 2007-04-15
It didn't work. 

It's on my desktop. 

So I ran in the terminal:  "  sudo /home/andrew/Desktop/devede-2.12/install.sh " without quotes. It asked me for a password, then it did nothing.

---

### Post by Error47 on 2007-04-15
Since that didn't seem to work for me, I tried synaptic. That worked. Exept the program doesn't open. 

devede in the terminal gives me this

"Failed to load modules 2. Exiting"

---

### Post by martinw89 on 2007-04-15
If you still would like to try some of the software mentioned in the Gentoo Wiki I fixed the link (it automatically included the ")" in the link)

---

### Post by viciouslime on 2007-04-15
Isn't devede in the repos on edgy.... i'm sure I used to use it

Edit: Thought so: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=devede&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=devede&searchon=names&subword=1&version=edgy&release=all")

Just enable the multiverse and install from there.

---

### Post by Error47 on 2007-04-15
I did enable multiverse, and I installed it from the synaptic packet manager the first time. It won't start. I tried installing tovid, but their .deb thing is messed up. So I tried from the tarbel thing and I think I messed up so much stuff.

---

### Post by DrtBikDave on 2007-05-05
I know that this wasn't my post but I appreciate The effort spent by all of you because I was able to make it work. Again I want to thank all of you.

---

