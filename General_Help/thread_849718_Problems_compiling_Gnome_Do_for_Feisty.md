---
title: "Problems compiling Gnome Do for Feisty"
date: 2008-07-04
forum: General Help
---

### Post by PC_load_letter on 2008-07-04
I followed the instructions on the WIKI: [https://wiki.ubuntu.com/GnomeDo/Installation]("https://wiki.ubuntu.com/GnomeDo/Installation")

I installed all the dependencies, but still got the following error when I ran ./autogen.sh:
```
No package 'gnome-desktop-sharp-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_SHARP_20_CFLAGS
and GNOME_DESKTOP_SHARP_20_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details
```
I then performed:
```
sudo apt-get install gnome-sharp2
``` 
Ran ./autogen.sh again, only to get the same error above. What I think is the culprit (but I'm no expert) is that the package in question has gone through a name change. The pkg with the old name, as mentioned in the error message, no longer exists. 
So, anyone knows how to fix this situation? 

Thanks in advance.

---

### Post by PC_load_letter on 2008-07-05
bump.

---

### Post by AlesUbu123 on 2008-07-05
> **PC_load_letter said:**
> 
I then performed:
```
sudo apt-get install gnome-sharp2
``` 


I think the error output said you should actually perform this:
```
sudo apt-get install gnome-**desktop**-sharp2
```
Or did you just make a typo?

---

### Post by PC_load_letter on 2008-07-05
Did you even read my post?  To answer your question in any case, upon entering the code you suggested I get an error message that says gnome-desktop-sharp2 can not be found. What I think is happening is that "gnome-desktop-sharp2" is the old name for "gnome-sharp2".Anyone can confirm?

So my question really is, how do I direct the installation script to the new version of this package? Would a symbolic link work in such a case?
I even tried to edit "./autogen.sh" but to no avail since the pkg "gnome-desktop-sharp2" is not mentioned anywhere in the script.

---

### Post by simoncullen on 2008-08-30
bump.

I have the same problem here.  I'd like to use the latest version of Do with Gutsy -- but i can't compile from source:

```
checking pkg-config is at least version 0.9.0... yes
checking for LIBDO... yes
checking for GCONF_SHARP_20... yes
checking for GLADE_SHARP_20... yes
checking for GLIB_SHARP_20... yes
checking for GNOME_DESKTOP_SHARP_20... configure: error: Package requirements (gnome-desktop-sharp-2.0) were not met:

No package 'gnome-desktop-sharp-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_SHARP_20_CFLAGS
and GNOME_DESKTOP_SHARP_20_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@aristurtle:/usr/bin/gnome-do# 
```

---

### Post by PC_load_letter on 2008-09-02
Oh, Gnome-do will not install under Feisty no more. According to the dev in another post here on this forum, he told me this is due to the lack of support of the Mono library under Feisty; if I recall correctly. Sorry.

---

### Post by PC_load_letter on 2008-09-02
Here it is: [http://ubuntuforums.org/showthread.php?t=381039&page=31](http://ubuntuforums.org/showthread.php?t=381039&page=31)

Scroll down to read deuce868's reply #308.

---

