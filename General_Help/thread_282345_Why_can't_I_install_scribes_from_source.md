---
title: "Why can't I install scribes from source?"
date: 2006-10-22
forum: General Help
---

### Post by paul6 on 2006-10-22
```
paul@ubuntu:~/scribes-0.2.9.88$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
paul@ubuntu:~/scribes-0.2.9.88$
```


Any idea what is going wrong? My guess is I need some sort of perl dependencies but I don't have a clue what to install :confused: :(

I already have the package "perl" installed from the repositories.

---

### Post by paul6 on 2006-10-22
*bump* I'm also fairly sure I have all the prereqs mentioned on the site. ](*,)

---

### Post by Buffalo Soldier on 2006-10-22
try installing the **libxml-parser-perl** module.

---

### Post by paul6 on 2006-10-22
> **Buffalo Soldier said:**
> try installing the **libxml-parser-perl** module.

Thanks! That fixed it... but the compiler is now getting stuck on something else.

```
Error: Version 2.10.0 or better of GTK needed.
```

Which package do I need now?

---

### Post by Buffalo Soldier on 2006-10-22
> **paul6 said:**
> Thanks! That fixed it... but the compiler is now getting stuck on something else.

```
Error: Version 2.10.0 or better of GTK needed.
```

Which package do I need now?

I'm sorry. I should have asked or checked first which version of Ubuntu are you running. Scribes is currently for Edgy only. Refering to [http://ubuntuforums.org/showpost.php?p=1626312&postcount=8](http://ubuntuforums.org/showpost.php?p=1626312&postcount=8)

> **Mystilleef said:**
> This release is targetted at testers, not users. I assume most testers are already on Edgy. It's unfortunate Ubuntu hasn't upgraded to GTK 2.10. Almost all other major distros have I believe. I'm still new to Ubuntu so I don't understand how the upgrade process works. I come from Gentoo were an upstream upgrade also means an upgrade for users. Plus GTK 2.10 has been out for months now. Does anyone know why it's not in Ubuntu? I have it here on Edgy, however.

---

### Post by paul6 on 2006-10-22
> **Buffalo Soldier said:**
> I'm sorry. I should have asked or checked first which version of Ubuntu are you running. Scribes is currently for Edgy only. Refering to [http://ubuntuforums.org/showpost.php?p=1626312&postcount=8](http://ubuntuforums.org/showpost.php?p=1626312&postcount=8)

My fault, I should have read into it more thoroughly before trying to install,

Do you have any recommendations for a lightweight text editor that isn't command line?

---

### Post by coder_ on 2006-10-23
> Do you have any recommendations for a lightweight text editor that isn't command line?

I ***highly*** recommend [Cream]("http://cream.sourceforge.net/").  I highly, highly, highly recommend it.  It's what got me from gedit to cream to vim/gvim.  And now I use cream with vim/cream modes together almost exclusively.  That way I have a GUI if I forget a text command for a second and I have the power of vi for speed and strength.

---

