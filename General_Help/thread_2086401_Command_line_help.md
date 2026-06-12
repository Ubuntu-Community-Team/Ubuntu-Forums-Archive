---
title: "Command line help"
date: 2012-11-20
forum: General Help
---

### Post by Hex9 on 2012-11-20
Hi all,
Pretty easy question.

At the command line how do you get it to 'guess' the rest of the filenames (i've seen it done before but unsure the shortcuts. For example:

I want to run the command : ```
sudo dpkg -i peazip_4.7.3.LINUX.GTK2-2_all.deb
```

I am quite likely to make a mistake typing it all out, instead you could type part of the filename and it would select it for example: ```
sudo dpkg -i peazip_4.7.3
```

Thanks, John:)

---

### Post by syerges on 2012-11-20
not the answer you are looking for but copy/paste with the right click.

---

### Post by gerowen on 2012-11-20
I usually just type enough of the filename to make it unique, then stick an asterisk in for the rest of it.

For example let's say you also had a similarly named deb for peazip that was version 3 something, and so that one was the only one you have that has the version number 4 in the filename, I would run this to install that one.

```

sudo dpkg -i peazip_4*.deb

```

---

### Post by Impavidus on 2012-11-20
Command and file name completion works with <tab>. Type part of the name, hit <tab> and the shell will add what it can guess (it's even smart enough to understand that some commands will be used for certain file types, xdvi stor<tab> will be completed as xdvi story.dvi, even if story.tex is also present). If it cannot guess, hit <tab> again and it will display a list of possibilities.

---

### Post by Hex9 on 2012-11-20
> **Impavidus said:**
> Command and file name completion works with <tab>. Type part of the name, hit <tab> and the shell will add what it can guess (it's even smart enough to understand that some commands will be used for certain file types, xdvi stor<tab> will be completed as xdvi story.dvi, even if story.tex is also present). If it cannot guess, hit <tab> again and it will display a list of possibilities.

Exactly what i was looking for, Thanks!

---

