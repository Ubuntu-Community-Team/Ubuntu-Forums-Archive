---
title: "let command not working in /bin/sh shell"
date: 2007-05-01
forum: General Help
---

### Post by 00coday on 2007-05-01
I had scripts that ran under 6.06 just fine, but they won't run under 7 without changing the shell to bash.  Part of the code I am trying to execute is:
```
   case $x in
    [A,G,H,I,L,M,S,T,V,W]*)
	  category=`grep "CAT I" $x.Result`
	  case "$category" in
	    'Finding Category: CAT I'  ) outfile=CAT.I;   let "cati += 1"   ;;
	    'Finding Category: CAT II' ) outfile=CAT.II;  let "catii += 1"  ;;
	    'Finding Category: CAT III') outfile=CAT.III; let "catiii += 1" ;;
	    'Finding Category: CAT IV' ) outfile=CAT.IV;  let "cativ += 1"  ;;
	    *) outfile=CAT.OTH; let "cato += 1" ;;
	  esac

```
It fails on the let command and the variables are set to 0.  I used the /bin/sh shell so that this script can also run on HPUX/AIX without modification.

Any Thoughts?

---

### Post by girishv on 2007-05-01
Recently, the sh is changed to dash and this is the reason for breaking of several programs. It is much liter than sh and hence, do not have many features as well. If you see
ls -l /bin/sh
you can find that it is actually a soft link to dash 

You can re-link /bin/sh to /bin/bash or simply replace the shell to bash

Girish

---

