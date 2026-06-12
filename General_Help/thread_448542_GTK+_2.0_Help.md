---
title: "GTK+ 2.0 Help"
date: 2007-05-19
forum: General Help
---

### Post by Browzilla on 2007-05-19
I was trying to install the new version of Pidgin, the predecessor to Gaim today, and since it wasn't in Add/Remove yet, I had to go get the source.  I extracted all the files, and while "./configure"-ing, got the message 

"configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure."

Could anyone help me fix this?

---

### Post by 3rdalbum on 2007-05-19
```
sudo apt-get build-dep gaim
```

Should get everything you need to compile Gaim/Pidgin. After that command is finished, run the ./configure again.

---

### Post by Browzilla on 2007-05-19
After sudo apt-get build-dep gaim:

```
browzilla@masashi:~$ sudo apt-get build-dep gaim
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```|



EDIT: Nevermind, I think I've solved that part.

---

### Post by Browzilla on 2007-05-19
Apparently the ./configure worked fine, but when I tried "make" it gave me:

```
gtkrange.c:1153: internal compiler error: in extract_insn, at recog.c:2084
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[4]: *** [gtkrange.lo] Error 1
make[4]: Leaving directory `/home/browzilla/Desktop/gtk+-2.10.9/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/browzilla/Desktop/gtk+-2.10.9/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/browzilla/Desktop/gtk+-2.10.9/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/browzilla/Desktop/gtk+-2.10.9'
make: *** [all] Error 2

```

---

### Post by Browzilla on 2007-05-19
Any help would be appreciated, I'm still new to linux and somewhat lost...

---

### Post by ethana2 on 2007-08-23
I'm in the same boat.  Someone see if you can get pidgin into the Ubuntu repositories, please.  That would make this a lot easier, needless to say.

---

### Post by GISJason on 2007-11-14
> **Browzilla said:**
> After sudo apt-get build-dep gaim:

```
browzilla@masashi:~$ sudo apt-get build-dep gaim
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```|



EDIT: Nevermind, I think I've solved that part.


Care to share with us how you solved that part? I'm having the same prob here :)

Oh well I solved it too :lol:  It was the synaptic manager being open / running  just had to kill it then it worked fine

---

### Post by GISJason on 2007-11-14
> **GISJason said:**
> Care to share with us how you solved that part? I'm having the same prob here :)

Oh well I solved it too :lol:  It was the synaptic manager being open / running  just had to kill it then it worked fine

try sudo make instead of just make  worked for me... I guess I need to add my acct to sudoers to build it successfully

it worked but no protocols prolly cuz I installed with plugins disabled  So Im gonna give it another shot with plugins enabled then maybe protocols will show up  :lol:

Also I ran it from where it installed the compiled dir  w/ app and it wouldnt run unless i did sudo ./pidgen then it worked and opened up a add acct option and all that.. But again.. was missing the protocols  like MSN / GTalk / AIM etc..

---

