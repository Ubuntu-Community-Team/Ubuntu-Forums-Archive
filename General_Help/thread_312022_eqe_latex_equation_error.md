---
title: "eqe latex equation error"
date: 2006-12-03
forum: General Help
---

### Post by norman_ on 2006-12-03
Hi everyone, 

I recently installed the eqe latex equation editor to be able to visualize the equations when I write them. However, it is completely unusable as it gives errors.

Both equations come out fine in a normal *.tex file. 

Wondering if anyone has any idea what the problem is.

For example:
e + 1 + 5 will output perfectly fine, but e_2 + 4 will generate the following error:
```
(/usr/share/texmf-tetex/tex/latex/psnfss/times.sty)
No file temp_eqedit_M0VXd.aux.
(/usr/share/texmf-tetex/tex/latex/psnfss/ot1ptm.fd)
! Missing $ inserted.
<inserted text> 
                $
l.27 e_
       2 + 4
? 
! Emergency stop.
<inserted text> 
                $
l.27 e_
       2 + 4
No pages of output.
Transcript written on temp_eqedit_M0VXd.log.
!!! error: command 'latex /tmp/temp_eqedit_M0VXd.tex' failed with error code 256 

```

---

### Post by norman_ on 2006-12-26
stupid problem...

I just forgot to wrap the equation in $...$

What threw me off was that simple equations worked and the huge text you get when you open the program rendered fine without the dollar signs.

---

