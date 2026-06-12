---
title: "pip install &lt;lib&gt; installs lib in a non-standard location in bionic?"
date: 2018-08-13
forum: General Help
---

### Post by harisund2 on 2018-08-13
When I run "pip install <some library>", pip installs it in /usr/lib/python27/site-packages. 

However, the default import path of python2 does not have /usr/lib/python27/site-packages at all.  Which means I can do a "pip install <foo>", but then if I have a "import foo" in my python script by default it doesn't import at all (I can work around by changing PYTHONPATH or PYTHONUSERBASE or modifying sys.path etc but it should work by default, no?) 

Is this a known bug?

---

