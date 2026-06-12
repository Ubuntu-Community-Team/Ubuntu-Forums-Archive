---
title: "installing file from local drive"
date: 2006-10-19
forum: General Help
---

### Post by dolphin_1 on 2006-10-19
I have a .deb file I want to install so I placed it in /files/deb directory 
I added the following to the sources.list file
```
deb file://files/deb/ ./
```
then did a apt-get update

(doesn't appear to ba any problems at this point)

But I get an error saying the file is not there when I try to perform a "apt-get install filename"

I know this is an easy one but .....I must be misssing something.
Don't assume I know the obvious.

thanks

---

### Post by aysiu on 2006-10-19
Have you considered double-clicking the .deb? Or just doing this? ```
cd /files/deb
sudo dpkg -i *.deb
```

---

### Post by dolphin_1 on 2006-10-19
worked like a charm.
what document should I read tso as to know things like this?

---

### Post by aysiu on 2006-10-19
> **dolphin_1 said:**
> worked like a charm.
what document should I read tso as to know things like this?
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

