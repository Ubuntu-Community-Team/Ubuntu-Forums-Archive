---
title: "Getting a packages files that go in /etc"
date: 2006-12-30
forum: General Help
---

### Post by Stephen-I-M on 2006-12-30
If I do:

sudo apt-get remove apache2
sudo rm -rf /etc/apache
sudo apt-get install apache2

I don't see the /etc/apache directory restored.

How can I get the default files that go there installed? Thanks.

Stephen

---

### Post by taurus on 2006-12-30
```
sudo apt-get --purge remove apache2
sudo apt-get update
sudo apt-get install apache2
```

---

### Post by Stephen-I-M on 2006-12-30
Anyone?

---

### Post by Stephen-I-M on 2006-12-30
Thank. That worked (the file I wanted turned out to be in apache2-common).

---

