---
title: "I cant add kde ppa repository"
date: 2013-04-10
forum: General Help
---

### Post by glaubersm on 2013-04-10
Hello

I use kubuntu 12.10 and when I run this command...
> sudo add-apt-repository ppa:kubuntu-ppa/backports

I have the error message below...
> Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in get_ppa_info_from_lp
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.2/urllib/request.py", line 139, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.2/urllib/request.py", line 370, in open
    response = self._open(req, data)
  File "/usr/lib/python3.2/urllib/request.py", line 388, in _open
    '_open', req)
  File "/usr/lib/python3.2/urllib/request.py", line 348, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.2/urllib/request.py", line 1176, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.2/urllib/request.py", line 1140, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.2/http/client.py", line 970, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.2/http/client.py", line 998, in _send_request
    self.putrequest(method, url, **skips)
  File "/usr/lib/python3.2/http/client.py", line 862, in putrequest
    self._output(request.encode('ascii'))
UnicodeEncodeError: 'ascii' codec can't encode character '\u1e55' in position 39: ordinal not in range(128)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 126, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 105, in get_ppa_info_from_lp
    import pycurl
ImportError: No module named pycurl
glauber@glauber-VirtualBox:~$ clear
glauber@glauber-VirtualBox:~$ sudo add-apt-repository ppa:kubuntu-ppa/back&#7765;orts
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in get_ppa_info_from_lp
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.2/urllib/request.py", line 139, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.2/urllib/request.py", line 370, in open
    response = self._open(req, data)
  File "/usr/lib/python3.2/urllib/request.py", line 388, in _open
    '_open', req)
  File "/usr/lib/python3.2/urllib/request.py", line 348, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.2/urllib/request.py", line 1176, in https_open
    context=self._context, check_hostname=self._check_hostname)
  File "/usr/lib/python3.2/urllib/request.py", line 1140, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.2/http/client.py", line 970, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.2/http/client.py", line 998, in _send_request
    self.putrequest(method, url, **skips)
  File "/usr/lib/python3.2/http/client.py", line 862, in putrequest
    self._output(request.encode('ascii'))
UnicodeEncodeError: 'ascii' codec can't encode character '\u1e55' in position 39: ordinal not in range(128)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 126, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 105, in get_ppa_info_from_lp
    import pycurl
ImportError: No module named pycurl

Any solution?

---

### Post by QDR06VV9 on 2013-04-10
> **glaubersm said:**
> Hello

I use kubuntu 12.10 and when I run this command...


I have the error message below...


Any solution?



That is Very Odd?
Anyway try adding them with synaptic, undr settings> then Repositories, 
Then add them one at a time

deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) quantal main 
deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) quantal main 

Or use your text editor and add them to
etc/apt/sources


By the way I had no errors adding them in terminal!

---

### Post by lisati on 2013-04-11
*Thread moved to **General Help**.*
Not a "+1" support request.

---

### Post by oldos2er on 2013-04-11
Do you have the package python-software-properties installed?

---

### Post by glaubersm on 2013-04-11
> **runrickus said:**
> 
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) quantal main 
deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) quantal main 

Or use your text editor and add them to
 etc/apt/sources

thanks, your tip + the command below solved my problem
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2836CB0A8AC93F7A

> **oldos2er said:**
> Do you have the package python-software-properties installed?
No.

Thanks, guys. ;)

---

### Post by Aide9aic on 2013-04-21
> **oldos2er said:**
> Do you have the package python-software-properties installed?
In 12.10, **add-apt-repository** has been moved, and now requires Python 3:
```
steve@t520:~$ dpkg -S add-apt-repository
software-properties-common: /usr/bin/add-apt-repository
software-properties-common: /usr/share/man/man1/add-apt-repository.1.gz

steve@t520:~$ apt-cache depends software-properties-common
software-properties-common
  Depends: python3
  Depends: python3-gi
  Depends: gir1.2-glib-2.0
  Depends: python3-dbus
  [COLOR="#FF0000"]Depends: python3[/COLOR]-software-properties
  Depends: ca-certificates
  Breaks: python-software-properties
  Breaks: <python-software-properties:i386>
  Breaks: python3-software-properties
  Breaks: <python3-software-properties:i386>
  [COLOR="#FF0000"]Replaces: python[/COLOR]-software-properties
  Replaces: <python-software-properties:i386>
  Replaces: python3-software-properties
  Replaces: <python3-software-properties:i386>
```

---

