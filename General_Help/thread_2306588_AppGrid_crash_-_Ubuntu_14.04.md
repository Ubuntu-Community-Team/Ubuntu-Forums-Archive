---
title: "AppGrid crash - Ubuntu 14.04"
date: 2015-12-16
forum: General Help
---

### Post by TheBane on 2015-12-16
Hey everyone! Good evening to all the Ubuntuphiles! ):P

Just tried to use AppGrid and I keep getting this error and I can't figure it out. I'm curious if anyone ran across this.

```
Traceback (most recent call last):  File "/usr/share/appgrid/appgrid.py", line 55, in <module>
    sc.show_home()
  File "/usr/share/appgrid/widgets/sc.py", line 21, in show_home
    from widgets.home import Home
  File "/usr/share/appgrid/widgets/home.py", line 5, in <module>
    from appdata.helpers import request
  File "/usr/share/appgrid/appdata/helpers.py", line 13, in <module>
    downloads_dir = dd + '/appgrid/'
TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'



```

I thought it might be using an older version of python, but I don't think it is. I have both 2.7.6 and 3.4.3 on this machine. 

Any thoughts?

---

