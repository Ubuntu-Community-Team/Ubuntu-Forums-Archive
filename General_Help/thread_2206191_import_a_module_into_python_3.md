---
title: "import a module into python 3"
date: 2014-02-17
forum: General Help
---

### Post by historyb on 2014-02-17
Hello,

I have looked all over the net for answers and I can not seem to find any. I am using Ubuntu 13.10. I need to import a module (graphics.py) into python 3 and I put the module in /usr/lib/python3/dist-packages and when I type import grapics.py (the module) I get this error:

   ```
 Traceback (most recent call last):
      File "<frozen importlib._bootstrap>", line 1519, in _find_and_load_unlocked
    AttributeError: 'module' object has no attribute '__path__'

    During handling of the above exception, another exception occurred:

    Traceback (most recent call last):
      File "<pyshell#0>", line 1, in <module>
        import graphics.py
    ImportError: No module named 'graphics.py'; graphics is not a package

```


can anyone help?

---

### Post by historyb on 2014-02-17
Any help would be appreciated I don't want to use windows :(

---

### Post by dragonfly41 on 2014-02-18
Well I'll chip in .. but at the moment I'm only starting to learn python .. and in particular how to add plugins to an existing python application. 

So I'm learning from others' experiences (such as your's!).

You'll find a few answers to your question by google searching ..

"python ImportError: No module named"

[http://stackoverflow.com/questions/7587457/importerror-no-module-named-python](http://stackoverflow.com/questions/7587457/importerror-no-module-named-python)

I found this only today ..

[http://stackoverflow.com/questions/932069/building-a-minimal-plugin-architecture-in-python](http://stackoverflow.com/questions/932069/building-a-minimal-plugin-architecture-in-python)

see last post in the thread for a very simple plugin framework ..

[https://github.com/samwyse/sspp](https://github.com/samwyse/sspp)

I'm not sure if this will help you.   But it helps me as a lesson in importing python plugins.

---

### Post by historyb on 2014-02-23
Thank you for the help. I found out looking at the other files that it was a permissions problem. The other files with .py ext had group rights set as read and graphics.py didn't so I changed  it and now it works perfectly

---

### Post by Topsiho on 2014-02-23
Hello historyb,

In python a module should be imported without the .py extension.
Think this is the answer for you :)
Of course Python should be able to find the module, but I think you already took care for that.

Topsiho

---

