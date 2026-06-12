---
title: "Restricted Extras Install error"
date: 2019-03-01
forum: General Help
---

### Post by Redalien0304 on 2019-03-01
Trying to Install Ubuntu Restricted Extras Codecs
Getting E: Unable to locate package ubuntu-restricted-extras

Using sudo apt-get install ubuntu-restricted-extras

---

### Post by logix2 on 2019-03-01
ubuntu-restricted-extras is in the Ubuntu multiverse repository, which is probably disabled on your machine. To enable it, launch "Software & Updates" from the applications menu, and enable the Software restricted by copyright or legal issues (multiverse)" option:

[IMG]https://i.imgur.com/YHzRijU.png[/IMG]

---

### Post by Redalien0304 on 2019-03-01
k Thanks that Did it. Is that Check box something new? Do not remember it?

---

### Post by logix2 on 2019-03-08
No, it's been there for years and years... You probably disabled it by accident somehow.

---

