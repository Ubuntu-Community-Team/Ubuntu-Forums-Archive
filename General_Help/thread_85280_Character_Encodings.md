---
title: "Character Encodings"
date: 2005-11-02
forum: General Help
---

### Post by grinchy on 2005-11-02
Hi, I'v searched all over the web about this for quite a while now but nothing i'v found has helped me so far.

The problem I have is that gnome does not display certain characters properly, in the terminal, in nautalus and pretty much everywhere else
It replaces chars it doesn't recognize with a diamond with a ? in the middle

Also I frequently recieve emails that have characters which are displayed like this and then in mutt are displayed as \### where ### tends to be a number between 200 and 250

Any ideas, this is driving me mad!

$LANG=en_IE.UTF-8
$LANGUAGE=en_IE:en

---

### Post by matthias_k on 2005-11-02
Can you post the complete output from 'locale'?

---

### Post by grinchy on 2005-11-03
LANG=en_IE.UTF-8
LC_CTYPE="en_IE.UTF-8"
LC_NUMERIC="en_IE.UTF-8"
LC_TIME="en_IE.UTF-8"
LC_COLLATE="en_IE.UTF-8"
LC_MONETARY="en_IE.UTF-8"
LC_MESSAGES="en_IE.UTF-8"
LC_PAPER="en_IE.UTF-8"
LC_NAME="en_IE.UTF-8"
LC_ADDRESS="en_IE.UTF-8"
LC_TELEPHONE="en_IE.UTF-8"
LC_MEASUREMENT="en_IE.UTF-8"
LC_IDENTIFICATION="en_IE.UTF-8"
LC_ALL=en_IE.UTF-8

---

### Post by grinchy on 2005-11-04
Someone must have had the same problem as me

---

### Post by grinchy on 2005-11-08
sorry gotta bump again

---

### Post by 23meg on 2005-11-08
You should try adding "utf8" to the options string (the last part, before the numbers) of your drives in /etc/fstab.

---

