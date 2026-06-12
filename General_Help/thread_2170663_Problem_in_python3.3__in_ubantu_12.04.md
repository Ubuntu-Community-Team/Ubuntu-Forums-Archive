---
title: "Problem in python3.3  in ubantu 12.04"
date: 2013-08-27
forum: General Help
---

### Post by Munu_Sairamesh on 2013-08-27
I am getting this error. I have installed python3.3 using aptitute.



File "/usr/local/lib/python3.3/urllib/request.py", line 156, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/local/lib/python3.3/urllib/request.py", line 469, in open
    response = self._open(req, data)
  File "/usr/local/lib/python3.3/urllib/request.py", line 492, in _open
    'unknown_open', req)
  File "/usr/local/lib/python3.3/urllib/request.py", line 447, in _call_chain
    result = func(*args)
  File "/usr/local/lib/python3.3/urllib/request.py", line 1310, in unknown_open
    raise URLError('unknown url type: %s' % type)
urllib.error.URLError: <urlopen error unknown url type: https>


Suggestions plz.

---

### Post by lukeiamyourfather on 2013-08-27
Please be more specific about your problem. What did you do to get that error?

---

### Post by oldfred on 2013-08-27
Did you uninstall python 2.7? Or change default python link to the 3.3 version.
Ubuntu 12.04 runs on 2.7 and has to have it as default.
To run 3.3 you have to then specify python3.

---

