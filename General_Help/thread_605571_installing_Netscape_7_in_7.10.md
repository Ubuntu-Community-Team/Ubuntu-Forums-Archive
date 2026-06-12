---
title: "installing Netscape 7 in 7.10"
date: 2007-11-07
forum: General Help
---

### Post by Nutrition on 2007-11-07
Hi there, having to learn Linux fast to set up a work testing machine!

I'll start by mentioning that Netscape 7 is needed for testing reasons, no alternatives please, that's not the point ;)

If I double click the netscape-installer script a Terminal window flashes up then vanishes. Running in Terminal and executing the netscape-installer-bin gets -

```

fluent@ubuntu710desktop:~/Desktop/netscape7-installer$ ./netscape-installer-bin
./netscape-installer-bin: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

libgtk1.2 is installed as far as I'm aware:
apt-cache search libgtk
```

libgtk1.2 - The GIMP Toolkit set of widgets for X
libgtk1.2-common - Common files for the GTK+ library
libgtk1.2-dbg - Debugging files for the GIMP Toolkit
libgtk1.2-dev - Development files for the GIMP Toolkit
libgtk1.2-doc - Documentation for the GIMP Toolkit

```

The readme asks for:
[list]
[*] glibc - 2.2.4
[*] gtk+ - 1.2.0 (1.2.5 or later preferred)
[*] XFree86-3.3.6
[*] Glib 1.2.x
[/list]

But I always get stumped trying to work out how to install these things - trying to work out what apt-get package to type.

Can I get netscape 7 to work?

Thanks in advance.

---

### Post by mali2297 on 2007-11-08
Check 
```

ls -l /usr/lib/libgtk*

```
Is there a link called **libgtk-1.2.so.0**? If not, does it show any library with a similar name like libgtk-1.2.so.0.9.1? In that case, make a symbolic link yourself:
```

sudo ln -s /usr/lib/libgtk-1.2.so.0.9.1 /usr/lib/libgtk-1.2.so.0

```

..or might it be that you only need to use sudo? 
```

sudo ./netscape-installer-bin

```

As you can probably tell, I don't really have any clue whatsoever. :-)

---

### Post by Nutrition on 2007-11-08
Much appreciated anyway! Will have a look tomorrow. Can you briefly explain 'ln' and 'ls'? Link and list?

---

### Post by llamakc on 2007-11-08
You can use the "man" or "info" commands to read up on many other commands.

```

man ln

```

et cetera.

---

### Post by mali2297 on 2007-11-09
> **Nutrition said:**
>  Can you briefly explain 'ln' and 'ls'? Link and list?

Yes, exactly. The syntax is 
```

ln -s originalname linkname

```
where *-s* means that the link should be symbolic. (All links in Linux are chosen to be symbolic as it seems.)

```

ls -l directory/filena*

```
lists every file in the *directory* which name starts with *filena*. The *-l* option means that the list should be in a long format, i.e. give a lot of information like where links point to.

---

### Post by Nutrition on 2007-11-12
Still nothing. Sudo makes no difference.

```
ls -l /usr/lib/libgtk*
``` does list libgtk-1.2.so.0 as the first in the list.

What does a symbolic link actually do? I've done the linking as above (realise I don't need to now) so how do I remove it?

Anything else to try? :)

---

### Post by mali2297 on 2007-11-12
To investigate your problem, I downloaded Netscape 7.2 from here:
[ftp://ftp.netscape.com/pub/netscape7/english/7.2/unix/linux/](ftp://ftp.netscape.com/pub/netscape7/english/7.2/unix/linux/)

After installing libgtk1.2 from Synaptic, I made progress until I got an error about xpistub library. A solution to this:
```

cd path_to_where_you_have/netscape-installer
ln -s /usr/lib/firefox/libxpistub.so .
LD_LIBRARY_PATH=. ./netscape-installer-bin

```
I then chose to install netscape to a directory within my home directory.

I suggest you try the same installer as I, it should work.
.. or you don't run the 64-bit version of Ubuntu, do you?

---

