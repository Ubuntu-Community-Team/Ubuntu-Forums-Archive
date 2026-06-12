---
title: "Need help installing gnucash 2.0.2"
date: 2006-10-11
forum: General Help
---

### Post by zeeone on 2006-10-11
I downloaded GNUCash 2.0.2 from their website, because the one in the Dapper repository is a much older version.

I run ./configure but it returns the following error:

```

checking for gconf-2.0 >= "2.0"... Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (gconf-2.0 >= "2.0") not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

I did a locate gconf-2 and I didn't see gconf-2.0.pc, the only two files I see are:

/usr/lib/libgconf-2.so.4.1.0
/usr/lib/libgconf-2.so.4

Can anyone help?

---

### Post by mjpoetic on 2006-10-15
Do you have the libgconf2-dev package installed?  I was able to compile it last night myself.  So far no problems I have noticed.  A rule of thumb for compiling is to have the dev packages installed for the dependencies the program has.

But I am still new at linux myself and trying to unbrainwash my microsoft windows mind.  ;)

---

### Post by zeeone on 2006-10-15
Thanks for your reply! I was not able to compile gnucash or any of the libraries it required, but I found a .deb file for gnucash 2.0 here in ubuntuforums.org

Problem solved.

---

### Post by mjpoetic on 2006-10-15
Do you remember which thread?  I was looking last night before I decided to compile.  And compiling took forever for some reason.  If you could zip it and post it here that would be cool. :mrgreen:

---

### Post by Cable on 2006-10-15
Compiling programs like that will take a bit, you just have to be patient and let it finish.  If you're trying to compile something and it's complaining about missing specific files, you can use apt-file to search for the package that the file is in (you must install apt-file first), then install that package with apt-get/aptitude/Synaptic.

---

### Post by mlavikai on 2006-11-01
I have managed to compile gnucash 2.0.2 after troublesome searching. There are some notes in thread about the problems I found when trying to compile, and trying to match development packages for the needs of compiling.

[http://www.ubuntuforums.org/showthread.php?t=290322]("http://www.ubuntuforums.org/showthread.php?t=290322")

This post is not a howto, just notes about my struggle

So, when i run 
```
./configure
```
in the gnucash2-source-directory, I got some errors about missing packages. 

I went to synaptics and searched for corresponding dev-packages. If the installed binary package had higher version than what was offered for the dev-package I needed to install dev-package manually.

While doing the manual install, new dependencies emerged one after another, and I needed to solve them too. Then I run the ./configure again and again to find new dependencies until configure finished. 

Next are the packages I needed to install manually. For you these packages are not probably same, so I strongly suggest you to check them through synaptics or whatever you like.

```

http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-dev_1.12.3-0ubuntu3_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/libxfixes-dev_4.0.1-0ubuntu1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-dev_2.14.1-0ubuntu3_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-dev_2.14.2-0ubuntu1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-dev_2.12.1-3ubuntu2_i386.deb

```

If I remember correctly, for next dependencies dev-packages were at the same version as binary ones.

```

libgnomeprintui
libgtkhtml (3.6)
```

So the above was for compiling. Below is another dependency for actually running the program
```
guile-g-wrap
```

I Hope my explanation was not too confusing and it helps you ;)

---

### Post by zeeone on 2006-11-01
Sorry for the delay in my response. I don't know how to attache files here. It seem the gnucash files are too big for this forum.

---

### Post by altonbr on 2008-03-31
Is there a repo for GnuCash 2.0+ in Ubuntu 6.06 (Dapper)??

---

### Post by Oldsoldier2003 on 2008-03-31
> **mlavikai said:**
> I have managed to compile gnucash 2.0.2 after troublesome searching. There are some notes in thread about the problems I found when trying to compile, and trying to match development packages for the needs of compiling.

[http://www.ubuntuforums.org/showthread.php?t=290322]("http://www.ubuntuforums.org/showthread.php?t=290322")

This post is not a howto, just notes about my struggle

So, when i run 
```
./configure
```
in the gnucash2-source-directory, I got some errors about missing packages. 

I went to synaptics and searched for corresponding dev-packages. If the installed binary package had higher version than what was offered for the dev-package I needed to install dev-package manually.

While doing the manual install, new dependencies emerged one after another, and I needed to solve them too. Then I run the ./configure again and again to find new dependencies until configure finished. 

Next are the packages I needed to install manually. For you these packages are not probably same, so I strongly suggest you to check them through synaptics or whatever you like.

```

http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-dev_1.12.3-0ubuntu3_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfixes/libxfixes-dev_4.0.1-0ubuntu1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-dev_2.14.1-0ubuntu3_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-dev_2.14.2-0ubuntu1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeprint/libgnomeprint2.2-dev_2.12.1-3ubuntu2_i386.deb

```

If I remember correctly, for next dependencies dev-packages were at the same version as binary ones.

```

libgnomeprintui
libgtkhtml (3.6)
```

So the above was for compiling. Below is another dependency for actually running the program
```
guile-g-wrap
```

I Hope my explanation was not too confusing and it helps you ;)

did you try ```
sudo apt-get build-dep gnucash
``` getting the build deps this way helps a lot.

---

### Post by Oldsoldier2003 on 2008-03-31
> **altonbr said:**
> Is there a repo for GnuCash 2.0+ in Ubuntu 6.06 (Dapper)??

if gnucash is available in the Dapper repos its very likely to be an older version. Your best bet would be to either compile from source or use [getdeb]("http://www.getdeb.net/").

---

