---
title: "gcalcli run issue"
date: 2014-08-30
forum: General Help
---

### Post by Chrison999 on 2014-08-30
Forgive me if this has already been asked and answered, but I've been searching for a couple of hours now and can't find the solution....

I'm trying to instal gcalcli on Ubuntu 14.04 and have tried both methods - using apt-get install and also pulling it from [https://github.com/insanum/gcalcli](https://github.com/insanum/gcalcli).  In both cases, when I try and run gcalcli from a terminal prompt I get this output:

```

Traceback (most recent call last):
  File "/usr/local/bin/gcalcli", line 5, in <module>
    pkg_resources.run_script('gcalcli==3.1', 'gcalcli')
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 528, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1401, in run_script
    exec(script_code, namespace, namespace)
  File "/usr/local/lib/python2.7/dist-packages/gcalcli-3.1-py2.7.egg/EGG-INFO/scripts/gcalcli", line 369, in <module>
    
  File "/usr/local/lib/python2.7/dist-packages/gcalcli-3.1-py2.7.egg/EGG-INFO/scripts/gcalcli", line 388, in gcalcli
    
  File "/usr/local/lib/python2.7/dist-packages/gcalcli-3.1-py2.7.egg/EGG-INFO/scripts/gcalcli", line 321, in __init__
    
  File "/usr/lib/python2.7/dist-packages/parsedatetime/__init__.py", line 216, in __init__
    self.ptc = Constants()
  File "/usr/lib/python2.7/dist-packages/parsedatetime/__init__.py", line 1733, in __init__
    self.locale = pdtLocales['icu'](self.localeID)
  File "/usr/lib/python2.7/dist-packages/parsedatetime/pdt_locales.py", line 151, in __init__
    self.icu = pyicu.Locale(localeID)
icu.InvalidArgsError: (<type 'icu.Locale'>, '__init__', (None,))



```

As anyone come across this and found a solution?

Thanks for any and all help provided!

Regards,

Chris

---

