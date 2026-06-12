---
title: "Griffith Movie Database Manager not working after Upgrade"
date: 2014-04-29
forum: General Help
---

### Post by llong0415 on 2014-04-29
I upgraded recently to 14.04, and reinstalled Griffith. It shows in Unity, and in my lib folder. But, when i try to launch nothing happens. I can't seem to find any solutions on the web or here on the forums. I hope I'm not the only person still using Griffith, I'd really hate having to reload a couple of thousand movies manually. Any input would be appreciated. Thanks in advance.

---

### Post by kostkon on 2014-04-29
Try running it from the terminal. i.e.
```
griffith
```
see if you'll get any error messages.
Also, according to [its man page]("http://manpages.ubuntu.com/manpages/trusty/en/man1/griffith.1.html"), you can start it in debug mode, you may get a more verbose output
```
griffith -D
```
and also check for any missing dependencies
```
griffith --check-dep
```

Hope that helps.

---

### Post by llong0415 on 2014-04-29
Tried all three commands and got the same responseTraceback (most recent call last):
  File "/usr/bin/griffith", line 86, in <module>
    import add
  File "/usr/share/griffith/lib/add.py", line 31, in <module>
    import quick_filter
  File "/usr/share/griffith/lib/quick_filter.py", line 25, in <module>
    import db
  File "/usr/share/griffith/lib/db/__init__.py", line 30, in <module>
    from _objects import *
  File "/usr/share/griffith/lib/db/_objects.py", line 33, in <module>
    import validators
  File "/usr/share/griffith/lib/db/validators.py", line 26, in <module>
    from sqlalchemy.orm.interfaces import AttributeExtension, InstrumentationManager
ImportError: cannot import name InstrumentationManager
mongo@mongo-Aspire-5315:~$ griffith -D
Traceback (most recent call last):
  File "/usr/bin/griffith", line 86, in <module>
    import add
  File "/usr/share/griffith/lib/add.py", line 31, in <module>
    import quick_filter
  File "/usr/share/griffith/lib/quick_filter.py", line 25, in <module>
    import db
  File "/usr/share/griffith/lib/db/__init__.py", line 30, in <module>
    from _objects import *
  File "/usr/share/griffith/lib/db/_objects.py", line 33, in <module>
    import validators
  File "/usr/share/griffith/lib/db/validators.py", line 26, in <module>
    from sqlalchemy.orm.interfaces import AttributeExtension, InstrumentationManager
ImportError: cannot import name InstrumentationManager
mongo@mongo-Aspire-5315:~$ griffith --check-dep
Traceback (most recent call last):
  File "/usr/bin/griffith", line 86, in <module>
    import add
  File "/usr/share/griffith/lib/add.py", line 31, in <module>
    import quick_filter
  File "/usr/share/griffith/lib/quick_filter.py", line 25, in <module>
    import db
  File "/usr/share/griffith/lib/db/__init__.py", line 30, in <module>
    from _objects import *
  File "/usr/share/griffith/lib/db/_objects.py", line 33, in <module>
    import validators
  File "/usr/share/griffith/lib/db/validators.py", line 26, in <module>
    from sqlalchemy.orm.interfaces import AttributeExtension, InstrumentationManager
ImportError: cannot import name InstrumentationManager There seems to be a prob with sqlalchemy, the places I've checked online basically state that Griffith is dead as far as any support from the developer. I've already downloaded a different database manager and started to load all of my movies into it.

---

### Post by kostkon on 2014-04-29
Actually, there's [a bug report for that]("https://bugs.launchpad.net/ubuntu/+source/griffith/+bug/1212397"), and a proposed solution in the comments; you could give it a try.

---

### Post by llong0415 on 2014-05-03
Sorry for not answering earlier, but life goes on as they say. I tried the solution you recommended and still no Griffith. I've started using MeD's movie manager instead. I tseems to work well. Thanks again for your help and input.

---

### Post by kostkon on 2014-05-03
> **llong0415 said:**
> Sorry for not answering earlier, but life goes on as they say. I tried the solution you recommended and still no Griffith. I've started using MeD's movie manager instead. I tseems to work well. Thanks again for your help and input.
No problem.

And MeD's movie manager looks rather nice.

---

### Post by llong0415 on 2014-05-21
Well I tried the fix you suggested one more time. Mainly because I'm just a stubborn cuss, and it worked. Now I have both movie database managers working. Score one for our side. Thanks one more time for the help. MeD's is good but Griffith uses other sources than IMDB, and sometimes you need them. We can marked this solved.

---

### Post by coldcritter64 on 2014-05-21
> We can marked this solved. 				
You will need to do that from the Thread Tools drop down  menu at the top of your browser window as you are the OP. 
There is a  link in my signature line if you need a guide on how to mark solved,  cheers.

---

