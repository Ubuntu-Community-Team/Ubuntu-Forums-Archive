---
title: "[SOLVED] Trouble Installing PyXML on Hardy Heron"
date: 2008-06-28
forum: General Help
---

### Post by Kaneda on 2008-06-28
Hi, I just upgraded to Hardy Heron, and I can't get PyXML working for some reason.  I had no problems with it in Gutsy Gibbon.  A few internet searches, and all I found was [this]("http://gnuradio.utah.edu/trac/wiki/GNURadioCompanion?format=txt"):
> '''Notes for Ubuntu Hardy Heron users:''' Ubuntu removed the xml.dom.ext package from their repositories. GRC 0.70 and below require this package. Solution: download the [[http://pyxml.sourceforge.net/topics/download.html](http://pyxml.sourceforge.net/topics/download.html) pyxml source]. Unpack the source, and run "sudo python setup.py install" from the source directory. This issue has been fixed in the trunk and in future releases.


I've downloaded the source from the pyxml sourceforge site and both "sudo python setup.py install" and "sudo python setup.py build" have failed, bringing up a long list of errors that look like this:
```
extensions/pyexpat.c: &#12488;&#12483;&#12503;&#12524;&#12505;&#12523;:
extensions/pyexpat.c:1676: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Xmlparsetype’
extensions/pyexpat.c:1719: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
extensions/pyexpat.c:1766: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
extensions/pyexpat.c:1778: error: &#37197;&#21015;&#12398;&#22411;&#12364;&#19981;&#23436;&#20840;&#35201;&#32032;&#22411;&#12434;&#25345;&#12387;&#12390;&#12356;&#12414;&#12377;
extensions/pyexpat.c:1779: error: expected ‘}’ before ‘pyexpat_ParserCreate’
extensions/pyexpat.c:1781: error: expected ‘}’ before ‘pyexpat_ErrorString’
extensions/pyexpat.c:1797: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
extensions/pyexpat.c: In function ‘initpyexpat’:
extensions/pyexpat.c:1835: error: ‘PyObject’ undeclared (first use in this function)
extensions/pyexpat.c:1835: error: ‘m’ undeclared (first use in this function)
extensions/pyexpat.c:1835: error: ‘d’ undeclared (first use in this function)
extensions/pyexpat.c:1835: &#35686;&#21578;: &#12459;&#12531;&#12510;&#28436;&#31639;&#23376;&#12398;&#24038;&#20596;&#12398;&#24335;&#12395;&#21177;&#21147;&#12364;&#12354;&#12426;&#12414;&#12379;&#12435;
extensions/pyexpat.c:1836: error: ‘errmod_name’ undeclared (first use in this function)
extensions/pyexpat.c:1836: &#35686;&#21578;: implicit declaration of function ‘PyString_FromString’
extensions/pyexpat.c:1837: error: ‘errors_module’ undeclared (first use in this function)
extensions/pyexpat.c:1838: error: ‘modelmod_name’ undeclared (first use in this function)
extensions/pyexpat.c:1839: error: ‘model_module’ undeclared (first use in this function)
extensions/pyexpat.c:1840: error: ‘sys_modules’ undeclared (first use in this function)
extensions/pyexpat.c:1848: error: ‘Xmlparsetype’ undeclared (first use in this function)
extensions/pyexpat.c:1848: error: ‘PyType_Type’ undeclared (first use in this function)
extensions/pyexpat.c:1851: &#35686;&#21578;: implicit declaration of function ‘Py_InitModule3’
extensions/pyexpat.c:1855: error: ‘ErrorObject’ undeclared (first use in this function)
extensions/pyexpat.c:1856: &#35686;&#21578;: implicit declaration of function ‘PyErr_NewException’
extensions/pyexpat.c:1862: &#35686;&#21578;: implicit declaration of function ‘PyModule_AddObject’
extensions/pyexpat.c:1866: error: expected expression before ‘)’ token
extensions/pyexpat.c:1868: &#35686;&#21578;: implicit declaration of function ‘get_version_string’
extensions/pyexpat.c:1869: &#35686;&#21578;: implicit declaration of function ‘PyModule_AddStringConstant’
extensions/pyexpat.c:1889: &#35686;&#21578;: implicit declaration of function ‘PySys_GetObject’
extensions/pyexpat.c:1890: &#35686;&#21578;: implicit declaration of function ‘PyModule_GetDict’
extensions/pyexpat.c:1891: &#35686;&#21578;: implicit declaration of function ‘PyDict_GetItem’
extensions/pyexpat.c:1893: &#35686;&#21578;: implicit declaration of function ‘PyModule_New’
extensions/pyexpat.c:1918: error: ‘list’ undeclared (first use in this function)
extensions/pyexpat.c:1921: &#35686;&#21578;: implicit declaration of function ‘PyErr_Clear’
extensions/pyexpat.c:1926: error: ‘item’ undeclared (first use in this function)
extensions/pyexpat.c:1933: &#35686;&#21578;: implicit declaration of function ‘PyList_Append’
extensions/pyexpat.c:1996: &#35686;&#21578;: implicit declaration of function ‘PyModule_AddIntConstant’
extensions/pyexpat.c: In function ‘clear_handlers’:
extensions/pyexpat.c:2023: error: ‘PyObject’ undeclared (first use in this function)
extensions/pyexpat.c:2023: error: ‘temp’ undeclared (first use in this function)
extensions/pyexpat.c:2027: error: ‘xmlparseobject’ has no member named ‘handlers’
extensions/pyexpat.c:2029: error: ‘xmlparseobject’ has no member named ‘handlers’
extensions/pyexpat.c:2030: error: ‘xmlparseobject’ has no member named ‘handlers’
extensions/pyexpat.c:2032: error: ‘xmlparseobject’ has no member named ‘itself’
error: command 'gcc' failed with exit status 1

```

Any help would be appreciated!  Thanks in advance!

---

### Post by Kaneda on 2008-06-28
Sorry everyone!  I guess I should have looked a little bit more before posting.  Anyway, I found [this post]("http://ubuntuforums.org/showthread.php?t=772259&highlight=pyxml") that got everything worked out.

---

