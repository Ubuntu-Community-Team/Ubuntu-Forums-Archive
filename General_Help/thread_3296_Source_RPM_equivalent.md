---
title: "Source RPM equivalent???"
date: 2004-11-04
forum: General Help
---

### Post by salmankhilji on 2004-11-04
I was wondering what the source RPM equivalent is in Ubuntu.  I want to make a small change to the source of a package and rebuild the .deb file.  How do I do this?

Specifically, I am interested in rebuilding freetype and enabling the byte code interpreter.

Salman

---

### Post by oddabe19 on 2004-11-05
cd /home/username/anyfolder.you.want
sudo apt-get --compile source xxxxxxxxxxx

where xxxxxxx is the package name. then just install the .debs from the directory you're in when it's all done compiling, etc...

if you just want the source its

sudo apt-get source xxxxxxxxx

---

