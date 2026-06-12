---
title: "Pytick"
date: 2008-01-21
forum: General Help
---

### Post by Kashyap on 2008-01-21
Hello, I am trying to use PYTICK as an alternative for "invest" gnome-app on Ubuntu -Gutsy.
The installation went just fine (installed pytick version 0.03), but for some reason I cant include stock ticker symbols. When I add the ticker name (say IBM for instance) and click 'update', it gives me the following error on terminal:

```

 Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/pytick.py", line 401, in update_cb
    self.update()
  File "/usr/lib/python2.5/site-packages/pytick.py", line 305, in update
    self.tracker.update()
  File "/usr/lib/python2.5/site-packages/pytick.py", line 57, in update
    lines = self.urlfile.open(url).readlines()
  File "/usr/lib/python2.5/urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.5/urllib.py", line 338, in open_http
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.5/urllib.py", line 355, in http_error
    return self.http_error_default(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.5/urllib.py", line 361, in http_error_default
    raise IOError, ('http error', errcode, errmsg, headers)
IOError: ('http error', 301, 'Moved Permanently', <httplib.HTTPMessage instance at 0x875f82c>)


```

Any help/suggestions would be appreciated.

-Kashyap

---

### Post by pkundu on 2008-06-18
hi,
   pytic use urllib to fetch data from yahoo. urllib is giving error. so i used urllib2.download the attached file and replace /usr/lib/python2.5/site-packages/pytick.py as root.

- Prosenjit

---

