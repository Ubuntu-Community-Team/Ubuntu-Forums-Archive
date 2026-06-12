---
title: "Problems installing Sun JDK on Hoary"
date: 2005-04-10
forum: General Help
---

### Post by Anonymouslemming on 2005-04-10
Hi all,

I'm trying to use make-jpkg to install the Sun j2sdk on Hoary. I've downloaded j2sdk-1_4_2_08-linux-i586.bin from sun, but this is what happens when I try and build a package:

--- OUTPUT ---
Creating temporary directory: /tmp/make-jpkg.XXXX0JXmWb
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
--- OUTPUT ---

Can anyone advise how I build a package for this j2sdk release on hoary please ?

---

### Post by Hinko on 2005-04-10
as root user: ```
pico  /etc/apt/sources.list
```

and add ```
deb ftp://ftp.tux.org/java/debian/ sarge non-free
```

Save it, update your sources and you can add it using synaptic.

---

### Post by bihe on 2005-04-10
another easy way is described at[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by remkio on 2005-04-10
can you show me what command you are using to build the file?

it should be:

```
$ fakeroot make-jpkg j2sdk-1_4_2_08-linux-i586.bin
```

---

