---
title: "Wine not working"
date: 2007-07-05
forum: General Help
---

### Post by VEGAMO on 2007-07-05
Hi

I am a new Ubuntu user, however I am having problems with wine.

For some reason, after I download the package and double click on it to install,  it tells me *Error: Conflicts with the installed package 'wine-doc'*

Where can I find wine-doc so I can remove it??? I searched every where and didn't find anything.

---

### Post by PatrickMay16 on 2007-07-05
Whoa, slow down there. Instead of installing wine that way, install wine using the instructions from here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

It will work much better. I assume you're using ubuntu "feisty".
Basically, these are the instruction from that page for "feisty":

Open a terminal and copy-paste these commands in.
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```

And enter your password when prompted.

With that method, it will install without problems, I expect.

---

### Post by bapoumba on 2007-07-05
Thread moved out of the "community Cafe" to "General Help".

---

