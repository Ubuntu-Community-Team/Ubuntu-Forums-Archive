---
title: "How to get Celtx 2.9.7 to work in 14.04"
date: 2014-10-27
forum: General Help
---

### Post by davy jones on 2014-10-27
Celtx worked perfectly well for me in 12.04, but I just  upgraded to 14.04 in a way that my /home folder and therefore my  settings were preserved, but the / folder was formatted. I downloaded  Celtx 2.9.7, and followed all the instructions to extract it to  /usr/local. Since my settings were preserved, there was already a Celtx  shortcut in the Applications menu. I removed that and followed the  instructions here - [http://askubuntu.com/a/414425/178834](http://askubuntu.com/a/414425/178834) - to create a fresh shortcut, but when I click on it, nothing happens. I don't know why this is happening. 

  Just to provide information, in the permissions of this celtx folder,  I see myself, not root as the owner, and on the celtx file inside it,  'Allow executing file as program' is unchecked, but checking it also  didn't yield any results.

  Can anyone explain how to get this to work? I need it very urgently.  If not this, then can anyone tell me how to get the latest version of  Celtx from the repositories. The one that is there is an old version  with an awful and buggy interface.

---

### Post by mc4man on 2014-11-07
Run this in a terminal,  what is the result?
```
/usr/local/celtx/celtx
```

---

### Post by davy jones on 2014-11-07
Running it with sudo says "command not found". Without it says "permission denied"

---

### Post by mc4man on 2014-11-07
Well I don't use this but see no issue with it opening, whether 'installed'  locally or to /usr/local/

What's this return?
```
ls -l /usr/local/celtx |grep celtx
```

Ex. here -  (extracted in $HOME, then mv'ed to /usr/local/ 
> $ ls -l /usr/local/celtx |grep celtx
-rwxr-xr-x 1 doug doug     3893 Mar 30  2012 celtx
-rwxr-xr-x 1 doug doug 21218448 Mar 30  2012 celtx-bin

or extracted as root directly to /usr/local/
> $ ls -l /usr/local/celtx |grep celtx
-rwxr-xr-x 1 root root     3893 Mar 30  2012 celtx
-rwxr-xr-x 1 root root 21218448 Mar 30  2012 celtx-bin


Both methods work & celtx opens fine...

---

### Post by davy jones on 2014-11-08
This was the output -

```
-rw------- 1 bhaskar bhaskar     3893 Mar 30  2012 celtx
-rw------- 1 bhaskar bhaskar 21218448 Mar 30  2012 celtx-bin
```

---

