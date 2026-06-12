---
title: "Screenlets python error"
date: 2008-06-02
forum: General Help
---

### Post by dbbolton on 2008-06-02
When I execute certain screenlets, I get an error like this:

```

Traceback (most recent call last):
  File "/usr/local/share/screenlets/Weather/WeatherScreenlet.py", line 6, in <module>
    from Numeric import *
ImportError: No module named Numeric

```

There are a few other strange errors, such as:
```

AttributeError: 'module' object has no attribute 'cpu_get_nb_cpu'

```

However, other screenlets work fine. What's causing this? Is there a problem with my python setup?

---

### Post by mac143_01 on 2008-06-03
What is Python?

---

### Post by dbbolton on 2008-06-03
> **mac143_01 said:**
> What is Python?
The programming language that screenlets are written in...

---

### Post by Roti78 on 2009-07-10
you have to install the *python-numeric* package

---

### Post by dbbolton on 2009-07-16
> **Roti78 said:**
> you have to install the *python-numeric* package

 Well that was a year ago. But anyway, it seems like some maintainer fudged the control file.

---

