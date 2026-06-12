---
title: "Unable to configure Samba4?"
date: 2016-08-01
forum: General Help
---

### Post by madisonverger613 on 2016-08-01
I have recently been having issues with my Samba shares and thought it best to just reinstall the whole program, since it was working well from the time it was first installed. I had issues installing with apt-get, so I resorted to installing from source and that is the method I prefer. Now as to the problem: cding into samba-4.4.5 and running ./configure, it gets all the way to the point where it looks for python, and it finds python for the most part.
[HTML]
 Checking for program xsltproc                                                     : /usr/bin/xsltproc 
Checking for program python                                                       : /usr/local/bin/python 
Checking for program python                                                       : /usr/local/bin/python 
Checking for program python                                                       : /usr/local/bin/python 
Checking for Python version >= 2.6.0                                              : ok 2.7.10 
Checking for library python2.7                                                    : yes 
Checking for program python2.7-config                                             : /usr/local/bin/python2.7-config 
Checking for custom code                                                          : Could not find the python development headers 
/home/maddogserver/Desktop/samba-4.4.5/wscript:106: error: the configuration failed (see '/home/maddogserver/Desktop/samba-4.4.5/bin/config.log')


[/HTML]

It finds everything except for the python development headers, and I know that they are in /usr/include/python2.7. 

[HTML]ls /usr/include/python2.7
abstract.h         errcode.h       object.h        pystate.h
asdl.h             eval.h          objimpl.h       pystrcmp.h
ast.h              fileobject.h    opcode.h        pystrtod.h
bitset.h           floatobject.h   osdefs.h        Python-ast.h
boolobject.h       frameobject.h   parsetok.h      Python.h
bufferobject.h     funcobject.h    patchlevel.h    pythonrun.h
bytearrayobject.h  genobject.h     pgen.h          pythread.h
bytes_methods.h    graminit.h      pgenheaders.h   rangeobject.h
bytesobject.h      grammar.h       pyarena.h       setobject.h
cellobject.h       import.h        pycapsule.h     sliceobject.h
ceval.h            intobject.h     pyconfig.h      stringobject.h
classobject.h      intrcheck.h     pyctype.h       structmember.h
cobject.h          iterobject.h    py_curses.h     structseq.h
codecs.h           listobject.h    pydebug.h       symtable.h
code.h             longintrepr.h   pyerrors.h      sysmodule.h
compile.h          longobject.h    pyexpat.h       timefuncs.h
complexobject.h    marshal.h       pyfpe.h         token.h
cStringIO.h        memoryobject.h  pygetopt.h      traceback.h
datetime.h         metagrammar.h   pymacconfig.h   tupleobject.h
descrobject.h      methodobject.h  pymactoolbox.h  ucnhash.h
dictobject.h       modsupport.h    pymath.h        unicodeobject.h
dtoa.h             moduleobject.h  pymem.h         warnings.h
enumobject.h       node.h          pyport.h        weakrefobject.h[/HTML]

So any ideas as to what packages I might need, or how to include the headers which I presume I already have?

---

