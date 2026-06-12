---
title: "umm... guys i think i broke linux(ubuntu)..."
date: 2013-05-12
forum: General Help
---

### Post by Saluq on 2013-05-12
I haven't loaded up my Ubuntu OS in a while when i did this morning the Software Center kept crashing and said something was wrong so i tried sudo apt-get update and it said that the headers were missing here is the error from Terminal
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

I apologise in advance if this is a simple fix but I'm a total noob when it comes to Linux.
Thank you for your time.
Saluq

---

### Post by oldos2er on 2013-05-12
Open a terminal (Ctrl-Alt-t) and run the following commands one at a time 
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by alan9800 on 2013-05-12
try this code```
sudo apt-get install -f
```

---

### Post by Saluq on 2013-05-12
fails at first step here is the error
sudo rm /var/lib/apt/lists/* -vf
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

---

### Post by Saluq on 2013-05-12
> **alan9800 said:**
> try this code```
sudo apt-get install -f
```

and it works you sir are a god thank you very much

---

### Post by oldos2er on 2013-05-12
Oops, that should've been ```
sudo rm -rf /var/lib/apt/lists/* -vf
```

---

