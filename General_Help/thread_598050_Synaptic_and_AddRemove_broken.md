---
title: "Synaptic and Add/Remove broken"
date: 2007-10-31
forum: General Help
---

### Post by arqmdq on 2007-10-31
Following the instructions to install Ubuntu 7.10 I found at [www.howtoforge.com](www.howtoforge.com) The Perfect Desktop - Ubuntu 7.10, I opened the terminal and enter two lines to add the medibuntu repository:

... import the repository ...

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

... import the gpg-key and update your package-list.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Now Synaptic and Add/Remove don't work. 

I don't know how to fix the problem. It's my first day with Ubuntu (and Linux).

Any advice?

Thanks

Pablo

---

### Post by Mothinator on 2007-10-31
Any error messages?

Try "sudo apt-get update" Any error messages there?

---

### Post by Maestro23 on 2007-10-31
Try:

> sudo apt-get update

sudo apt-get upgrade


If that doesn't work:

Open a terminal and type:

> cat /etc/apt/sources.list

Copy/Paste the output here.

---

### Post by arqmdq on 2007-10-31
I fixed the problem reinstalling the repository following the instructions at Medibuntu and now it's OK. 

Thanks.

---

### Post by Maestro23 on 2007-10-31
> **arqmdq said:**
> I fixed the problem reinstalling the repository following the instructions at Medibuntu and now it's OK. 

Thanks.

Good deal. Please mark this SOLVED using Thread Tools.

Thanks.:)

---

