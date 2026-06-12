---
title: "Is this a python 2.7 or linux/ubuntu bug?"
date: 2015-01-31
forum: General Help
---

### Post by Zarkopafilis on 2015-01-31
[https://github.com/Zarkopafilis/Random-Notes/tree/master/PythonUbuntuBug](https://github.com/Zarkopafilis/Random-Notes/tree/master/PythonUbuntuBug)

runbug.sh is the output of the terminal when you execute the python file:

If you run a bash file via python and this bash file tries to execute another bash file there is a file not found error. (ME:MAD)

---

### Post by SeijiSensei on 2015-01-31
Does the first bash script reference the second with a complete path, e.g., /path/to/my/program?

---

### Post by Holger_Gehrke on 2015-01-31
Sorry, but I can't reproduce the behaviour you describe. 
Ubuntu 12.04, Python 2.7.3, bash 4.2.25(1).
I put all three files in one directory (which is not on the $PATH) and changed to that directory, executed 'python code.py' and got 
```

Im file 1
Im file 2

```

---

### Post by Zarkopafilis on 2015-02-01
No, its just ./file.extension

---

### Post by Zarkopafilis on 2015-02-01
Im using ubuntu 14.04

---

### Post by Zarkopafilis on 2015-02-01
Idk if this is a vmware workstation issue too...

---

### Post by SeijiSensei on 2015-02-01
No, it's nothing complicated like that. You just need to use the complete path. Replace ./something with /path/to/something.

---

