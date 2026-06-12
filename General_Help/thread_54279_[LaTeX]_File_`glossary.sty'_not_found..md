---
title: "[LaTeX] File `glossary.sty' not found."
date: 2005-08-04
forum: General Help
---

### Post by alegomes on 2005-08-04
I'm using Kile to edit and compile my .tex files.

What do you do when you get the "File `glossary.sty' not found." error ? I've already looked at Synaptic, but could not find any package that could meet my needs.

I followed instructions posted at [1] but that didn't work for me.


[1] [HTML]http://www.tug.org/tex-archive/macros/latex/contrib/glossary/[/HTML] 

thanks

---

### Post by kalle314 on 2005-08-04
I&#12288;dont think I can help you very much - I too have had some trouble installing new LaTeX packages, so I am also interested in any reply to your question.

This is as much I can say: 
Since LaTeX do not find the file (check this by typing "kpsewhich glossary.sty" in the terminal) , you will probably have to put it somewhere where it can be found, or tell LaTeX the path to it (I am not sure how that should be done.). 
What is the path to glossary.sty on your system?

edit: Did you do "mktexlsr" to update the search paths list?

---

### Post by alegomes on 2005-08-05
Hey, after booting Ubuntu, Kile could find glossary.sty

Now I got another problem: 

Unknown option `style=altlist' for package `glossary'. \usepackage
Unknown option `toc=true' for package `glossary'. \usepackage

Gonna search for that.

[QUOTE=kalle314]
This is as much I can say: 
Since LaTeX do not find the file (check this by typing "kpsewhich glossary.sty" in the terminal) , you will probably have to put it somewhere where it can be found, or tell LaTeX the path to it (I am not sure how that should be done.). 
What is the path to glossary.sty on your system?[/QUOTE]

glossary.sty is at /usr/share/texmf/tex/latex/glossary/glossary.sty   I put it there following the instructions found at that link I posted before. But it was found only after rebooting.


[QUOTE=kalle314]
edit: Did you do "mktexlsr" to update the search paths list?[/QUOTE]

No, I didn't. From man page 

       "mktexlsr  is  used  to generate the ls-R databases used by the kpathsea
       library.  It will create them for the specified directories, or  for  a
       default list if no directories are specified."

but what do it do ?


regards

---

