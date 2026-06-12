---
title: "gcalcli errors"
date: 2014-11-04
forum: General Help
---

### Post by avery4 on 2014-11-04
I've been fiddleing around with gcalcli and conky for a few hours and haven't been able to get it working. Here's what I'm currently getting when trying to run gcalcli ```
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

If anyone has experienced the same errors or can help in some way, it would be very much apperciated.

---

### Post by avery4 on 2014-11-19
Seeing as I got no response on my previous post, I figured this is a better place to post this. I've been trying to get gcalcli running on my system for a while and have been unsuccessful in making it work. Here's what I'm getting when I run the agenda command ```

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
If anyone can help in any way it would be greatly appreciated.

---

### Post by matt_symes on 2014-11-19
Hi

How did you install it ? Where did you install it from ?

Kind regards

---

### Post by slickymaster on 2014-11-19
Threads merged.

Please do not create duplicate threads, it dilutes community effort. Bumping your thread if you receive no answer is acceptable.

---

### Post by icactus on 2014-11-24
Had same problem.  It is a two part solution. About a week ago Google stopped supporting the old way it used to use to handle your login creditials through Gcalcli. Separately, you need parsedatetime version 1.3 or higher.

PART 1:

1. Assuming you have pip for python, In terminal type "pip list" and see what version of parsedatetime you are running. If it isn't above 1.3 type 'sudo pip install parsedatetime --upgrade'

That should fix the error you see but then create a new problem with logging in unless you have already done part 2. 

PART 2:

1. You need to delete the ~/.gcalclirc file you were using to store your username and password.

2. In terminal type : "gcalcli list" and it will explain where your login creditials will be stored and automatically open a browser window for you to type in username and password.

3. After logging in click the "ok" box or whatever it says about letting Gcalcli access your info and links and what-not. That's it.

---
This is the place to look if you are having issues in the future: [https://github.com/insanum/gcalcli/issues](https://github.com/insanum/gcalcli/issues)

---

### Post by joshua38 on 2014-11-25
I am getting the same error as above, for "gcalcli list". According to pip list, parsedatetime is version (1.2). Any ideas?

---

### Post by icactus on 2014-11-25
I just went back and realized I had not actually fixed the problem but rather used a hack to skip the parsedatetime/PyICU problem. I also would still get the error message without this hack.

The hack is posted here: [https://github.com/insanum/gcalcli/issues/142](https://github.com/insanum/gcalcli/issues/142)

Just edit the gcalcli file here (needs permission to save) : /usr/local/lib/python2.7/dist-packages/gcalcli-3.1-py2.7.egg/EGG-INFO/scripts/gcalcli

- self.pdtCalendar = parsedatetime.Calendar()
+ self.pdtCalendar = parsedatetime.Calendar(parsedatetime.Constants(usePyICU=False))

EDIT:

For future reference I just discovered my problem was that I actually had multiple versions of parsedatetime install at once so when I was upgrading it was still using the old 1.2 version.  After deleting the duplicate old versions I have no problem with 1.3 or newer.

To see if you have more than one version hanging around type in terminal:

ll /usr/local/lib/python2.7/dist-packages/ | grep parsedatetime

You should see someting like this:

drwxr-sr-x  3 root staff    4096 Dec 19 23:24 parsedatetime/
drwxr-sr-x  2 root staff    4096 Dec 19 23:24 parsedatetime-1.4.dist-info/

If instead you see something like:

drwxr-sr-x  3 root staff    4096 Dec 19 23:24 parsedatetime/
drwxr-sr-x  2 root staff    4096 Dec 19 23:24 parsedatetime-1.4.dist-info/
drwxr-sr-x  2 root staff    4096 Jan 22 20:12 parsedatetime-1.2-py2.7.egg-info/

then you just need to manually delete the phantom version that is hanging around:

sudo rm -r /usr/local/lib/python2.7/dist-packages/parsedatetime-1.2-py2.7.egg-info/


Now the fixes that should have showed up in 1.3 and 1.4 are properly working on my machine.

---

