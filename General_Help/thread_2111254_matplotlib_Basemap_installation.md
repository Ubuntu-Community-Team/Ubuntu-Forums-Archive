---
title: "matplotlib Basemap installation"
date: 2013-02-01
forum: General Help
---

### Post by Singularity64 on 2013-02-01
Hi
I am running Ubuntu 10.04 and have already installed python and matplotlib. I wanted to plot data on maps and tried to install the basemap package from matplotlib for this purpose.  I followed the instructions that are given here: 
[http://matplotlib.org/basemap/users/installing.html](http://matplotlib.org/basemap/users/installing.html)

When I completed the installation and, as suggested in the guide, I typed 'from mpl_toolkits.basemap import Basemap' at the python prompt I get the following error:
  ```
 File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python2.6/dist-packages/mpl_toolkits/basemap/__init__.py", line 30, in <module>
    from mpl_toolkits.basemap import pyproj
ImportError: cannot import name pyproj
```

What is surprising is that, I repeat the same command, and I sometimes get an error that is different but of a similar form: an import error that says 'cannot import X' 

Any help to resolve this would be highly appreciated.  
Thanks.

---

### Post by raja.genupula on 2013-02-01
are you sure about installation of the required libraries ?

---

### Post by Singularity64 on 2013-02-01
> **raja.genupula said:**
> are you sure about installation of the required libraries ?

Thanks for the response. I installed python-dev and GEOS, the latter according to the instructions on the matplotlib website.   I think the error has something to do with a different directory being named pyproj but I am not sure how to fix it.

---

### Post by raja.genupula on 2013-02-02
open your terminal and do as 
```
sudo apt-get install python-pyproj
```

then try again.
hope that helps.

---

### Post by Singularity64 on 2013-02-02
> **raja.genupula said:**
> open your terminal and do as 
```
sudo apt-get install python-pyproj
```

then try again.
hope that helps.

Thanks. I actually got into a much bigger mess trying to figure this out. I just started a new thread on that. 
 


[http://ubuntuforums.org/showthread.php?t=2111728]("http://ubuntuforums.org/showthread.php?t=2111728")

---

