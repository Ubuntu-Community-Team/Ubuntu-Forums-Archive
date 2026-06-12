---
title: "why is Anki crashing ?"
date: 2013-02-16
forum: General Help
---

### Post by sinaphysics on 2013-02-16
I installed anki 6 months ago and it worked great for me. When I update it to 1.2.11, it crashes when I want to download plugin or deck. I googled and some users claim that by installing new verson 2 through anki website all this bugs would be solved. I install anki 2, but now it crashes in opening. The crash error for 1.2.11 is

```
Error was:
Traceback (most recent call last):
  File "/usr/share/anki/ankiqt/ui/getshared.py", line 67, in fetchData
    URL + "search?t=%d&c=1" % self.type)
  File "/usr/lib/python2.7/urllib2.py", line 127, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 407, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 520, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 439, in error
    result = self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 379, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 626, in http_error_302
    return self.parent.open(new, timeout=req.timeout)
  File "/usr/lib/python2.7/urllib2.py", line 407, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 520, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 445, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 379, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 528, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
HTTPError: HTTP Error 404: Not Found
```

What's your suggestion ? I'm using ubuntu12.10 gnome desktop.

---

### Post by sinaphysics on 2013-02-17
I'm adding the error when I'm running Anki2

```
Traceback (most recent call last):
  File "/usr/bin/anki", line 5, in <module>
    import aqt
  File "/usr/share/anki/aqt/__init__.py", line 7, in <module>
    import anki.lang
  File "/usr/share/anki/anki/__init__.py", line 12, in <module>
    raise Exception("Anki requires a UTF-8 locale.")
Exception: Anki requires a UTF-8 locale.

```

There are some tricks in this website .
[http://napsnack.blogspot.com/2012/09/anki-20-and-crunchbang.html](http://napsnack.blogspot.com/2012/09/anki-20-and-crunchbang.html)
But I don't know what to do :(

---

### Post by sinaphysics on 2013-02-17
I find the answer in this [LINK]("http://askubuntu.com/questions/76013/how-do-i-add-locale-to-ubuntu-server"). Just in first answer replace "ru_RU" with "en_US" and then do 
```

locale-gen en_US
locale-gen en_US.UTF8 
```

---

