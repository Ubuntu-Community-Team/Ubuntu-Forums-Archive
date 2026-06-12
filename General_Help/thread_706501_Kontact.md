---
title: "Kontact"
date: 2008-02-24
forum: General Help
---

### Post by LOBONCA on 2008-02-24
In Kontact I am getting an error:
"Cannot load part for feeds.
Library files for libakregatorpart.la
not found in paths."

How do I correct this?

---

### Post by der_joachim on 2008-02-25
It sounds like either some library was not installed (or misconfigured somehow) or Akrekator was not installed at all.

You can try either of these two things. Open a konsole (or other X terminal) and issue the following command:
```

sudo aptitude -f install

```
This will automatically restore any missing dependencies. 

Another option is to reinstall both Kontact and Akrekator. From the terminal:
```

sudo aptitude reinstall kontact
sudo aptitude reinstall akrekator

```
Any missing dependencies should be restored. 

Good luck.

---

