---
title: "Update manager is broken"
date: 2007-03-19
forum: General Help
---

### Post by HugoRune on 2007-03-19
(System: Ubuntu edgy 64bit with kubuntu-desktop installed)

My update manager is broken. Adept just gives starnge error messages( "database locked by another process", even thought it isn't)

Synaptic is somewhat more helpfull, saying I should run "dpkg --configure -a"

Running "sudo dpkg --configure -a" yields the follwoing error:
```

Setting up update-manager (0.45.2) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 482 strings at 20 - 2810
Wrote aliases at 2810 - 29c4
Wrote parents at 29c4 - 3398
Wrote literal globs at 3398 - 33fc
Wrote suffix globs at 33fc - 6804
Wrote full globs at 6804 - 6828
Wrote magic at 6828 - beb4
Wrote namespace list at beb4 - bec4
***
Compiling /usr/lib/python2.4/site-packages/mcf/scripts/vrml/test_on_file.py ...
  File "/usr/lib/python2.4/site-packages/mcf/scripts/vrml/test_on_file.py", line 3
    def check( filename, resultfile='z:\\temp\\testout.wrl', index ):
SyntaxError: non-default argument follows default argument

Compiling /usr/lib/python2.4/site-packages/mcf/walker/commonidioms.py ...
  File "/usr/lib/python2.4/site-packages/mcf/walker/commonidioms.py", line 64
    for rawcontent and rawcontent_ci, just use the functions as your triggers,
                     ^
SyntaxError: invalid syntax

Compiling /usr/lib/python2.4/site-packages/mcf/walker/compile.py ...
Sorry: IndentationError: ('expected an indented block', ('/usr/lib/python2.4/site-packages/mcf/walker/compile.py', 78, 0, "'''\n"))
Compiling /usr/lib/python2.4/site-packages/mcf/walker/engine.py ...
SyntaxError: ('Invalid syntax.  Assignment to None.',)

Compiling /usr/lib/python2.4/site-packages/mcf/walker/mappedlist.py ...
SyntaxError: ('Invalid syntax.  Assignment to None.',)

dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 update-manager
```

neither adept or synaptic can succesfully install updates.

Any idea?

---

### Post by Kateikyoushi on 2007-03-19
Try the following in terminal.
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by HugoRune on 2007-03-19
neither of those made the error dissapear, but I managed to solve it by manually deleting /usr/lib/python2.4/site-packages/mcf/, which belonged to a python library I installed recently. 

Sorry for the confusion.

---

### Post by Kateikyoushi on 2007-03-19
Those weren't really meant to solve it just wanted the output to go further.

---

### Post by HugoRune on 2007-03-20
ah, sorry about that, aptitude update seemed to hang at [99% waiting for headers], and aptitude upgrade stopped with the same error as above.

I am still not sure how exactly I caused this, but since it works now that is ok

---

