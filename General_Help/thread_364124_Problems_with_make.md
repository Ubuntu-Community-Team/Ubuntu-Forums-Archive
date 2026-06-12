---
title: "Problems with make"
date: 2007-02-17
forum: General Help
---

### Post by jpe2000 on 2007-02-17
Sorry for this really long list. I'm trying to compile beryl-settings-bindings or whatever there called.

Here it is:

```
berylsettings.c:7881: error: array type has incomplete element type
berylsettings.c:7882: error: syntax error before '__pyx_f_13berylsettings_keytos tring'
berylsettings.c:7883: error: syntax error before '__pyx_f_13berylsettings_modsto string'
berylsettings.c:7884: error: syntax error before '__pyx_f_13berylsettings_button tostring'
berylsettings.c:7885: error: syntax error before '__pyx_f_13berylsettings_edgeli sttomask'
berylsettings.c:7886: error: syntax error before '__pyx_f_13berylsettings_edgeto list'
berylsettings.c:7887: error: syntax error before '__pyx_f_13berylsettings_send_r eload'
berylsettings.c:7888: error: syntax error before '__pyx_f_13berylsettings_Backen ds'
berylsettings.c:7894: error: syntax error before 'initberylsettings'
berylsettings.c:7894: warning: data definition has no type or storage class
berylsettings.c:7895: error: syntax error before 'initberylsettings'
berylsettings.c: In function 'initberylsettings':
berylsettings.c:7896: error: 'PyObject' undeclared (first use in this function)
berylsettings.c:7896: error: '__pyx_1' undeclared (first use in this function)
berylsettings.c:7897: error: '__pyx_2' undeclared (first use in this function)
berylsettings.c:7898: error: '__pyx_3' undeclared (first use in this function)
berylsettings.c:7899: error: '__pyx_4' undeclared (first use in this function)
berylsettings.c:7901: error: 'PYTHON_API_VERSION' undeclared (first use in this function)
berylsettings.c:7901: warning: assignment makes pointer from integer without a c ast
berylsettings.c:7903: warning: assignment makes pointer from integer without a c ast
berylsettings.c:7909: error: syntax error before ')' token
berylsettings.c:7912: error: syntax error before ')' token
berylsettings.c:7914: error: request for member 'tp_free' in something not a str ucture or union
berylsettings.c:7914: error: '_PyObject_GC_Del' undeclared (first use in this fu nction)
berylsettings.c:7916: error: syntax error before ')' token
berylsettings.c:7918: error: request for member 'tp_free' in something not a str ucture or union
berylsettings.c:7920: error: syntax error before ')' token
berylsettings.c:7922: error: request for member 'tp_free' in something not a str ucture or union
berylsettings.c:7924: error: syntax error before ')' token
berylsettings.c:7926: error: request for member 'tp_free' in something not a str ucture or union
berylsettings.c:7928: error: syntax error before ')' token
berylsettings.c:7930: error: request for member 'tp_free' in something not a str ucture or union
berylsettings.c:7932: error: syntax error before ')' token
berylsettings.c: At top level:
berylsettings.c:8136: error: syntax error before '*' token
berylsettings.c: In function '__Pyx_ArgTypeTest':
berylsettings.c:8137: error: 'type' undeclared (first use in this function)
berylsettings.c:8138: error: 'PyExc_SystemError' undeclared (first use in this f unction)
berylsettings.c:8141: error: 'none_allowed' undeclared (first use in this functi on)
berylsettings.c:8141: error: 'obj' undeclared (first use in this function)
berylsettings.c:8141: error: 'Py_None' undeclared (first use in this function)
berylsettings.c:8143: error: 'PyExc_TypeError' undeclared (first use in this fun ction)
berylsettings.c:8145: error: 'name' undeclared (first use in this function)
berylsettings.c: At top level:
berylsettings.c:8149: error: syntax error before '*' token
berylsettings.c:8149: error: syntax error before '*' token
berylsettings.c: In function '__Pyx_GetName':
berylsettings.c:8150: error: 'PyObject' undeclared (first use in this function)
berylsettings.c:8150: error: 'result' undeclared (first use in this function)
berylsettings.c:8151: error: 'dict' undeclared (first use in this function)
berylsettings.c:8151: error: 'name' undeclared (first use in this function)
berylsettings.c:8153: error: 'PyExc_NameError' undeclared (first use in this fun ction)
berylsettings.c: At top level:
berylsettings.c:8157: error: syntax error before '*' token
berylsettings.c:8158: error: syntax error before '*' token
berylsettings.c: In function '__Pyx_CreateClass':
berylsettings.c:8160: error: 'PyObject' undeclared (first use in this function)
berylsettings.c:8160: error: 'py_modname' undeclared (first use in this function )
berylsettings.c:8161: error: 'result' undeclared (first use in this function)
berylsettings.c:8163: error: 'modname' undeclared (first use in this function)
berylsettings.c:8166: error: 'dict' undeclared (first use in this function)
berylsettings.c:8168: error: 'bases' undeclared (first use in this function)
berylsettings.c:8168: error: 'name' undeclared (first use in this function)
berylsettings.c: At top level:
berylsettings.c:8174: error: syntax error before '*' token
berylsettings.c: In function '__Pyx_Raise':
berylsettings.c:8175: error: 'type' undeclared (first use in this function)
berylsettings.c:8176: error: 'value' undeclared (first use in this function)
berylsettings.c:8177: error: 'tb' undeclared (first use in this function)
berylsettings.c:8179: error: 'Py_None' undeclared (first use in this function)
berylsettings.c:8183: error: 'NULL' undeclared (first use in this function)
berylsettings.c:8184: error: 'PyExc_TypeError' undeclared (first use in this fun ction)
berylsettings.c:8195: error: 'PyObject' undeclared (first use in this function)
berylsettings.c:8195: error: 'tmp' undeclared (first use in this function)
berylsettings.c:8215: error: syntax error before ')' token
berylsettings.c:8215: error: 'PyInstanceObject' undeclared (first use in this fu nction)
berylsettings.c:8215: error: syntax error before ')' token
berylsettings.c: At top level:
berylsettings.c:8236: error: syntax error before '*' token
berylsettings.c: In function '__Pyx_GetExcValue':
berylsettings.c:8237: error: 'PyObject' undeclared (first use in this function)
berylsettings.c:8237: error: 'type' undeclared (first use in this function)
berylsettings.c:8237: error: 'value' undeclared (first use in this function)
berylsettings.c:8237: error: 'tb' undeclared (first use in this function)
berylsettings.c:8238: error: 'result' undeclared (first use in this function)
berylsettings.c:8239: error: 'PyThreadState' undeclared (first use in this funct ion)
berylsettings.c:8239: error: 'tstate' undeclared (first use in this function)
berylsettings.c:8245: error: 'Py_None' undeclared (first use in this function)
berylsettings.c: At top level:
berylsettings.c:8266: error: syntax error before '*' token
berylsettings.c: In function '__Pyx_InternStrings':
berylsettings.c:8267: error: 't' undeclared (first use in this function)
berylsettings.c: At top level:
berylsettings.c:8276: error: syntax error before '*' token
berylsettings.c: In function '__Pyx_InitStrings':
berylsettings.c:8277: error: 't' undeclared (first use in this function)
berylsettings.c:8286:21: error: compile.h: No such file or directory
berylsettings.c:8287:25: error: frameobject.h: No such file or directory
berylsettings.c:8288:23: error: traceback.h: No such file or directory
berylsettings.c: In function '__Pyx_AddTraceback':
berylsettings.c:8291: error: 'PyObject' undeclared (first use in this function)
berylsettings.c:8291: error: 'py_srcfile' undeclared (first use in this function )
berylsettings.c:8292: error: 'py_funcname' undeclared (first use in this functio n)
berylsettings.c:8293: error: 'py_globals' undeclared (first use in this function )
berylsettings.c:8294: error: 'empty_tuple' undeclared (first use in this functio n)
berylsettings.c:8295: error: 'empty_string' undeclared (first use in this functi on)
berylsettings.c:8296: error: 'PyCodeObject' undeclared (first use in this functi on)
berylsettings.c:8296: error: 'py_code' undeclared (first use in this function)
berylsettings.c:8297: error: 'PyFrameObject' undeclared (first use in this funct ion)
berylsettings.c:8297: error: 'py_frame' undeclared (first use in this function)
make[2]: *** [berylsettings.lo] Error 1
make[2]: Leaving directory `/home/josh/Desktop/beryl-settings-bindings-0.1.9999. 2/python'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/josh/Desktop/beryl-settings-bindings-0.1.9999. 2'
make: *** [all] Error 2
```

---

### Post by jpe2000 on 2007-02-17
*sigh* Can anyone please help me?

---

### Post by jpe2000 on 2007-02-18
Why do I never get help?

---

### Post by dexter on 2007-02-18
Seems to be a problem in the source code. If you want to compile Beryl yourself, try to get the latest version of the code. If you want Beryl, you dont have to compile it yourself, you can download binaries (precompiled packages) and use those.

---

### Post by highneko on 2007-02-18
There's some information under the words "Beryl Developer's Documentation" on the following page that might be useful:
[http://wiki.beryl-project.org/wiki/Main_Page](http://wiki.beryl-project.org/wiki/Main_Page)

---

