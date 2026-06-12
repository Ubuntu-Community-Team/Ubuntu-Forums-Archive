---
title: "Can't input Korean on a laptop"
date: 2007-01-31
forum: General Help
---

### Post by snowboard975 on 2007-01-31
I use Edgy. I freshly installed Edgy a few days ago but still can't input Korean into it. When press Hangul key, it doesn't toggle between Korean and English.
I went to the SCIM Input Method Setup and added several other keys such as Ctrl+Alt+] or Ctrl+g to trigger SCIM, but it didn't solve the problem. 

Any suggestions?

---

### Post by snowboard975 on 2007-02-03
I solved it using the following method.
```
sudo gedit /etc/X11/xinit/xinput.d/default
```

I edited it as follows:
```
XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS='-d'
GTK_IM_MODULE=scim
DEPENDS=
XMODIFIERS=@im=SCIM

```

This solution is from 
[http://ubuntu.or.kr/wiki.php/InstallingInputMethods#s-1.3](http://ubuntu.or.kr/wiki.php/InstallingInputMethods#s-1.3)

---

