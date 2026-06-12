---
title: "abcde config file"
date: 2006-11-17
forum: General Help
---

### Post by paul6 on 2006-11-17
Does anyone know how I would increase the OGG encoding quality level to 5? I believe abcde defaults to 3, and I would like to change it.

---

### Post by mazirian on 2006-11-17
Find the following in your .abcde.conf

```

# Ogg:
#VORBIZEOPTS=
#OGGENCOPTS=

```

and set oggencopts to add whatever you want.  See man oggenc for the options, but probably:

```

# Ogg:
#VORBIZEOPTS=
OGGENCOPTS="-q 5"

```

or something like that.

---

### Post by paul6 on 2006-11-17
Thank you mazirian! Worked perfectly.

---

