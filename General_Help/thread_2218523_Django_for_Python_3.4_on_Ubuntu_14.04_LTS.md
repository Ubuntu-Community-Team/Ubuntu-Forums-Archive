---
title: "Django for Python 3.4 on Ubuntu 14.04 LTS"
date: 2014-04-21
forum: General Help
---

### Post by wannabelinuxgeek on 2014-04-21
I want to configure django framework with python 3.4 on Ubuntu 3.4.
But default python on ubuntu is version 2.7. So I am not able to configure django for python 3.4.


I am very new to python.
So can anyone guide me how to do that ?


Thanks in advance.

---

### Post by toypilot on 2014-04-21
What version of Django do you use? If you are on the latest, I dont think you will have any issues?

---

### Post by dragonfly41 on 2014-04-21
Recently I had the same requirement to switch python versions for test purposes (but not for django)  ..

I found this ..

[http://askubuntu.com/questions/320996/make-default-python-to-python3-3-on-13-04](http://askubuntu.com/questions/320996/make-default-python-to-python3-3-on-13-04)

and so added this alias to my ~/.bashrc

```
# alias python=python3.3

alias python=python2.7
```

Just comment out the version to be disabled.

---

