---
title: "python3.3-dev on ubuntu 12.04 for blender"
date: 2013-06-03
forum: General Help
---

### Post by tilakrajsingh on 2013-06-03
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]               I want to install python3.3-dev on ubuntu 12.04... I installed python3.3 but still I am getting these errors
  
```
python3.3-dev depends on python3.3 (= 3.3.0-1); 
however:   Package python3.3 is not installed. 
 python3.3-dev depends on libpython3.3-dev (= 3.3.0-1); 
however:   Package libpython3.3-dev is not installed.
  python3.3-dev depends on libpython3.3 (= 3.3.0-1);
 however:   Package libpython3.3 is not installed.
 dpkg: error processing python3.3-dev (--install):  dependency problems - leaving unconfigured
```[/TD]
[/TR]
[/TABLE]

---

### Post by ohnonot on 2013-06-04
are you sure you installed *exactly* 3.3.0-1?

---

### Post by ohnonot on 2013-06-04
are you sure the python3.3 you installed is *exactly* 3.3.0-1, as the dev package demands?
also, sometimes a reboot can help. i know i shouldn't say that, but even in linux it helps, sometimes.

---

### Post by tilakrajsingh on 2013-06-05
yeah i installed python 3.3.2... its located at /opt/python3.3 ... but the prob is its not set as my default python...when i run python command on my system it shows the default version 2.7.3 ... to run 3.3 i have to issue the command /opt/python3.3/bin/python3.3 ........ i did set it to default once to when i run apt-get update it shows error that some files could not be updates successfully ... this may be due to incompatibility of python 2.X and python 3.X ...is there some way i could give apt-get install the path of python 3.3 to install python-dev library???

---

### Post by ohnonot on 2013-06-05
it seems to me that blender is a much used porgram in the linux world...
i think it should be possible to install it without any problem.
the kind of problems you're describing, maybe you have to take one more step back, to find the source of the problem.
...
why do you have python3.3.2 installed in /opt? seems weird. do you need that particular python version?
i have ubuntu 12,04 with both python 2.7 and 3.2 in /usr/..., and /usr/share/python/debian_defaults says 2.7.
it seems to me you did sth weird long before trying to install blender?! at least i read sth like that from your last post?

would completely uninstalling python and blender, and then reinstalling blender (which will then pull in all python dependencies) be something to try?
of course there is more subtle ways.

---

