---
title: "How do you rename one single file?"
date: 2007-04-21
forum: General Help
---

### Post by beachreader on 2007-04-21
Please help I want to rename one single a file. i.e. ename /usr/lib/wine/winearts.drv.


 to this:  /usr/lib/wine/winearts.drv.so.old

thanks very much. you are very kind.

---

### Post by total wormage on 2007-04-21
you can just move the one file to the other with

```
mv /usr/lib/wine/winearts.drv /usr/lib/wine/winearts.drv.so.old
```

---

### Post by beachreader on 2007-04-21
I tried:

           mv <old file name>  <new file name>

and I got permission denied. 

any thoughts?

---

### Post by mhansen on 2007-04-21
That file is owned by root, so you have to do:

sudo mv etc,etc,



Regards,
Mike

---

### Post by beachreader on 2007-04-21
how do I give my self permission. anyone? 

beachreader@beachreader:~$ mv /usr/lib/wine/winearts.drv.so /usr/lib/wine/winearts.drv.so.old
mv: cannot move `/usr/lib/wine/winearts.drv.so' to `/usr/lib/wine/winearts.drv.so.old': Permission denied

---

### Post by Swab on 2007-04-21
> **beachreader said:**
> how do I give my self permission. anyone? 

beachreader@beachreader:~$ mv /usr/lib/wine/winearts.drv.so /usr/lib/wine/winearts.drv.so.old
mv: cannot move `/usr/lib/wine/winearts.drv.so' to `/usr/lib/wine/winearts.drv.so.old': Permission denied

Use sudo as suggested, you don't really want to give permission to a regular user.

---

### Post by beachreader on 2007-04-21
thanks a lot now I know how to change a file name. unfortunately that did not solve my problem....thanks again!!!:)

---

### Post by JackandJohn on 2008-01-30
note: sudo gives you permission, basically no matter what you are doing.

Typically it goes like this:

```
mv /usr/lib/wine/winearts.drv /usr/lib/wine/winearts.drv.so.old
```
Permission Denied.
"Doh"
```
sudo mv /usr/lib/wine/winearts.drv /usr/lib/wine/winearts.drv.so.old
```
Successful

See also:

[http://xkcd.com/149/](http://xkcd.com/149/)

---

