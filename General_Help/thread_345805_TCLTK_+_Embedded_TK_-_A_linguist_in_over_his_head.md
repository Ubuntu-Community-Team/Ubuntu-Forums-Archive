---
title: "TCL/TK + Embedded TK - A linguist in over his head"
date: 2007-01-24
forum: General Help
---

### Post by scott_b on 2007-01-24
I posted a similar question in "Absolute Beginners" without response.  I am hoping someone here can help me.  

I am working on my Thesis and there is some software that I simply MUST have.  
[http://www.coli.uni-saarland.de/projects/sfb378/negra-corpus/annotate.html](http://www.coli.uni-saarland.de/projects/sfb378/negra-corpus/annotate.html)

The darn thing seems to have been made in '99.  According to that site,

> Annotate runs under Solaris and Linux. It needs the GNU C-Compiler, Tcl/Tk 8.0, Embedded Tk, and an installation of MySQL.

From what I have been able to dig up (I spent all stinkin day on this), the problem at least has to do with the fact that 'et' (embedded TK) is no longer used.  See: 
[http://www.hwaci.com/sw/et](http://www.hwaci.com/sw/et)

According to that site, which was last updated in '98, 

> ET is no longer being actively developed. For new development work, please consider using mktclapp instead of ET.

I would gladly comply if I only knew how.  

What can I do?  I sent a note off to the distributors, but I doubt they'll be of much assistance.  They're passing this thing out.  I don't even know when the last time someone used this thing was.  But it is PERFECT for my research.  If it works, then I can use "TIGERSearch."  (Imagine Homer drooling over a donut).

[http://www.ims.uni-stuttgart.de/projekte/TIGER/TIGERSearch/screenshots-grammar.shtml](http://www.ims.uni-stuttgart.de/projekte/TIGER/TIGERSearch/screenshots-grammar.shtml)

I am on my knees begging for help. [-o<

---

### Post by bettlebrox on 2007-01-24
Have you tried e-mailing the author?

---

### Post by scott_b on 2007-01-24
Yes.  But I'm not hopeful.  I hope its just a language problem.  For example, the errors it gives are the following:

> swb@2laptop2:~/Desktop/Negra-Tools-3.7/et$ make
cc -O  -o et2c et2c.c
et2c.c: In function ‘SafeMalloc’:
et2c.c:252: warning: incompatible implicit declaration of built-in function ‘exit’
et2c.c: In function ‘SafeRealloc’:
et2c.c:266: warning: incompatible implicit declaration of built-in function ‘exit’
et2c.c: In function ‘WriteToDiversion’:
et2c.c:329: warning: incompatible implicit declaration of built-in function ‘strlen’
et2c.c: In function ‘ProcessTcl’:
et2c.c:546: warning: incompatible implicit declaration of built-in function ‘exit’
et2c.c: In function ‘ProcessIncludeMacro’:
et2c.c:738: warning: incompatible implicit declaration of built-in function ‘strlen’
et2c.c:741: warning: incompatible implicit declaration of built-in function ‘strcpy’
et2c.c:770: warning: incompatible implicit declaration of built-in function ‘strcpy’
et2c.c: In function ‘SanitizeName’:
et2c.c:993: warning: incompatible implicit declaration of built-in function ‘strlen’
et2c.c:994: warning: incompatible implicit declaration of built-in function ‘strcpy’
et2c.c: In function ‘ProcessDefineProc’:
et2c.c:1040: warning: incompatible implicit declaration of built-in function ‘strlen’
et2c.c:1041: warning: incompatible implicit declaration of built-in function ‘strcpy’
et2c.c: In function ‘main’:
et2c.c:1231: error: two or more data types in declaration specifiers
et2c.c:1251: warning: incompatible implicit declaration of built-in function ‘strlen’
et2c.c:1280: warning: incompatible implicit declaration of built-in function ‘exit’
et2c.c:1297: warning: incompatible implicit declaration of built-in function ‘exit’
et2c.c:1301: warning: incompatible implicit declaration of built-in function ‘exit’
et2c.c:1230: warning: return type of ‘main’ is not ‘int’
make: *** [et2c] Error 1

Line 252 reads:

>     exit(1);


Maybe this is as easy as a change in words or syntax.  But, I just made that up.  I don't know what I'm doing.

---

