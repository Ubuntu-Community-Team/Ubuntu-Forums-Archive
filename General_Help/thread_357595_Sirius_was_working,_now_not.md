---
title: "Sirius was working, now not"
date: 2007-02-09
forum: General Help
---

### Post by AndrewB on 2007-02-09
I had been running the sipie program to listen to Sirius on the internet, that is until today after the Edgy 6.10 updates. Now it crashes.

Can some-one help me out , I don't really program.

Here's the 'crash' as reported in the sipie terminal:
```
Enter the captcha from the popup: c8lj6k
 Enter stream: jamon
Traceback (most recent call last):
  File "/usr/bin/sipie", line 961, in ?
    playing = sipie.nowplaying()
  File "/usr/bin/sipie", line 437, in nowplaying
    fd = self.geturl('http://sirius.criffield.net/now_playing.html')
  File "/usr/bin/sipie", line 164, in geturl
    handle = urllib2.urlopen(req)
  File "/usr/lib/python2.4/urllib2.py", line 130, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.4/urllib2.py", line 364, in open
    response = meth(req, response)
  File "/usr/lib/python2.4/urllib2.py", line 471, in http_response
    response = self.parent.error(
  File "/usr/lib/python2.4/urllib2.py", line 402, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.4/urllib2.py", line 337, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.4/urllib2.py", line 480, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found


```

Thanks, Andrew

---

### Post by AndrewB on 2007-02-10
i removed and reinstalled (sounds windows-ish, no?) . It's working again. Sure would like to know why. Oh well, at least it's working.

---

### Post by llamakc on 2007-02-10
I have been looking for something like sipie. Thanks, it is working great for me here.

---

### Post by myname on 2007-02-19
> **AndrewB said:**
> i removed and reinstalled (sounds windows-ish, no?) . It's working again. Sure would like to know why. Oh well, at least it's working.

You removed and reinstalled what?  All the sipie components (python setup, beautiful soup, etc)??

I'm getting the same thing and need to know what to remove/reinstall

--Kevin

[edit]A post from the developer about this in another forum

> Sorry about that, My website was down and that caused sipie to bomb on startup when it checked for an update. 
 
 My website is backup and theres a new version at [http://eli.criffield.net/sipie/sipie](http://eli.criffield.net/sipie/sipie) that doesn't reply on my website to be up.
 
 Eli Criffield[/edit]

---

