---
title: "Compiz-start restarts xserver"
date: 2006-09-06
forum: General Help
---

### Post by crhall on 2006-09-06
No errors or anything.
Just type 'compiz-start' and x restarts itself.

Any ideas? 

(I'm not sure what data to provide.)
New install of Dapper this morning.
Nvidia card. 
All suggested components are the latest and greatest.

---

### Post by ayoli on 2006-09-06
have you got errors in /var/log/Xorg.log ?
in ~/.xsession-errors ?

---

### Post by crhall on 2006-09-06
Please see attached logs.
I don't think there are any in xorg... but may be some in xsessions.
But I don't know what they mean. =(

---

### Post by ayoli on 2006-09-06
hmm cant see any errors concerning compiz in your logs.

---

### Post by crhall on 2006-09-06
The following, typed in the terminal causes x to restart.
```
cgwd --replace
```

Uninstalled and reinstalled cgwd but no love.](*,)

---

