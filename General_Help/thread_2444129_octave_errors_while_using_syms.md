---
title: "octave errors while using syms"
date: 2020-05-25
forum: General Help
---

### Post by mm1379 on 2020-05-25
[SIZE=3]Hello,
When I want to use e.g. syms x these two errors appear.
[/SIZE]
```
[COLOR=#000000][FONT=&amp]>> syms x[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]error: 'python_ipc_popen2' undefined near line 62 column 15[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]error: called from[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    python_ipc_driver at line 62 column 13[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    pycall_sympy__ at line 163 column 9[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    valid_sym_assumptions at line 38 column 10[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    assumptions at line 82 column 7[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    syms at line 97 column 13[/FONT][/COLOR]
```  

```
[COLOR=#000000][FONT=&amp]>> syms x[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Traceback (most recent call last):[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  File "<stdin>", line 4, in <module>[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  File "<stdin>", line 12, in octoutput_drv[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  File "<stdin>", line 55, in octoutput[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  File "/home/smhk/.local/lib/python3.6/site-packages/sympy/__init__.py", line 677, in __getattr__[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    return getattr(self.mod, name)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]AttributeError: module 'sympy.core.compatibility' has no attribute 'integer_types'[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]error: Python exception: AttributeError: module 'sympy.core.compatibility' has no attribute 'integer_types'[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    occurred while copying variables to Python.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    Try "sympref reset" and repeat your command?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    (consider filing an issue at https://github.com/cbm755/octsympy/issues)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]error: called from[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    pycall_sympy__ at line 191 column 5[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    valid_sym_assumptions at line 38 column 10[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    assumptions at line 82 column 7[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]    syms at line 97 column 13[/FONT][/COLOR]
```

---

### Post by monkeybrain20122 on 2020-05-25
From your output
> Python exception: AttributeError: module 'sympy.core.compatibility' has no attribute 'integer_types' 

Apparetly sympy breaks backward compatibility, so try to install an earlier version that works.
```
sudo pip3 install sympy==1.4
```

Now in octave
```
>> pkg load symbolic
>> sym x
Symbolic pkg v2.9.0: Python communication link active, SymPy v1.4.
ans = (sym) x
>>



```

Ubuntu20.04, octave 5.2.0

P.S.  I presume you are using Ubuntu 20.04, octave 5.2.0 (it is a good idea to tell people your ubuntu and software versions when you ask for help) and you installed sympy from the repo, which is version 1.5.x. You don't need to remove sympy from repo as it maybe a dependency of other things you installed with apt. pip installs sympy in /usr/local/lib which take precedence over the one installed by apt in /usr/lib at run time.

---

### Post by mm1379 on 2020-05-25
Thanks a lot.+1
It is working well know

P.S I am using octave4.2.2 and ubuntu18.04

---

### Post by monkeybrain20122 on 2020-05-25
I have tested that symbolic works with sympy 1.5 as well but not 1.6. Since you are in 18.04 so your repo's sympy may be too old rather than too new.

If your problem is solved please go to thread tools and mark the thread as solved.

---

### Post by chessbucket on 2020-07-07
This solved my issue.

> **monkeybrain20122 said:**
> From your output
 

Apparetly sympy breaks backward compatibility, so try to install an earlier version that works.
```
sudo pip3 install sympy==1.4
```

Now in octave
```
>> pkg load symbolic
>> sym x
Symbolic pkg v2.9.0: Python communication link active, SymPy v1.4.
ans = (sym) x
>>



```

Ubuntu20.04, octave 5.2.0

P.S.  I presume you are using Ubuntu 20.04, octave 5.2.0 (it is a good idea to tell people your ubuntu and software versions when you ask for help) and you installed sympy from the repo, which is version 1.5.x. You don't need to remove sympy from repo as it maybe a dependency of other things you installed with apt. pip installs sympy in /usr/local/lib which take precedence over the one installed by apt in /usr/lib at run time.

---

