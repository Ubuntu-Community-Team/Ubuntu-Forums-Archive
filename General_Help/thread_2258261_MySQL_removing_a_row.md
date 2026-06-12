---
title: "MySQL removing a row?"
date: 2014-12-26
forum: General Help
---

### Post by johnnybgoode on 2014-12-26
LPI Linux certification           | Jeffrey Dean                    | computer    |
| Practical Python                  | Magnus Lie Hetland              | computer    |
| kuifje                            | HergÃ©                          | strip       |
| MySQL                             | Zak Greant                      | computer    |
+-----------------------------------+---------------------------------+-------------+
67 rows in set (0.00 sec)

I tried to remove MySQL , Zak Greant, computer  record with
Detelte from boeken where Titel = MySQL & Auteur = Zak Greant & Aard = computer without result.
What do I wrong?

---

### Post by steeldriver on 2014-12-26
A couple of things: (1) you will probably need to quote varchar (string) values like "Zak Greant"; and (2) the logical operator is && or AND e.g.

```

DELETE FROM boeken WHERE Titel = "MySQL" AND Auteur = "Zak Greant" AND Aard = "computer"

```

(the capitalization is optional I think - but helps to distinguish commands and arguments)

---

### Post by johnnybgoode on 2014-12-27
Hallo Steeldriver,
It was indeed  the quoting that was missing.
Thanks!

---

### Post by mörgæs on 2014-12-27
Please mark the thread 'solved'.

---

### Post by johnnybgoode on 2014-12-27
Sorry I forgot the "SOLVED"

---

### Post by mörgæs on 2014-12-27
Yes, it's better to do with Thread Tools.
Fixed that now.

---

