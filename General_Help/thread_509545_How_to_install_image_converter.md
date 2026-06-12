---
title: "How to install image converter"
date: 2007-07-25
forum: General Help
---

### Post by alexmidd on 2007-07-25
Hi, I'm pretty new so I hope I am posting this in the right place. I have seen instructions for installing an image resizer to the right-click menu by installing nautilus-image-converter using Synaptic. However, the package is not in Synaptic and I am not sure how to go about getting it. Any ideas?

---

### Post by rax_m on 2007-07-25
Hi 

Nautilus image converter is in the repos (Synaptic) but it is in the Universe repository. So first you have to enable the Universe by going to System->Administration->Software sources and ensuring you have the community / universe repo ticked. 
Then open Synaptic and search for "nautilus image" and it should show up. 

Rax

---

### Post by FunkyJack on 2007-07-25
In terminal:

```
sudo apt-get install nautilus-image-converter
```

---

### Post by alexmidd on 2007-07-25
> **FunkyJack said:**
> In terminal:

```
sudo apt-get install nautilus-image-converter
```
I've tried that but it said it can't find the package.

@ rax_m I thought I had enabled the Universe repo but I will check again.

Thanks for the replies.

:)

---

### Post by alexmidd on 2007-07-25
Just checked. I have the "Community maintained Open Source software (Universe)" box ticked. :confused:

---

### Post by rax_m on 2007-07-25
Just to make sure (sorry if it seems obvious).. 
you are searching for the package through "synaptic" and NOT "Add or Remove Programs" ?

Also, have you tried reloading the Synaptic packages after enabling the repos?

---

### Post by FunkyJack on 2007-07-25
Try this:

```
sudp apt-get update
sudo apt-get install nautilus-image-converter
```

---

### Post by mcduck on 2007-07-26
> **FunkyJack said:**
> Try this:

```
sudp apt-get update
sudo apt-get install nautilus-image-converter
```

That won't work. It's not in Edgy's repositories, only in Feisty and Gutsy.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nautilus-image-converter&searchon=names&subword=1&version=all&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nautilus-image-converter&searchon=names&subword=1&version=all&release=all")

Anyway, you can get the .deb package from here: [http://www.getdeb.net/app.php?name=nautilus-image-converter]("http://www.getdeb.net/app.php?name=nautilus-image-converter")

---

