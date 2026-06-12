---
title: "pip install broken in Artful"
date: 2017-11-02
forum: General Help
---

### Post by monkeybrain20122 on 2017-11-02
It seems that pip install  for python is broken in 17.10

e.g 
```

 sudo pip install -U sympy

Exception:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/pip/basecommand.py", line 215, in main
    status = self.run(options, args)
  File "/usr/lib/python2.7/dist-packages/pip/commands/install.py", line 342, in run
    requirement_set.prepare_files(finder)
  File "/usr/lib/python2.7/dist-packages/pip/req/req_set.py", line 380, in prepare_files
    ignore_dependencies=self.ignore_dependencies))
  File "/usr/lib/python2.7/dist-packages/pip/req/req_set.py", line 487, in _prepare_file
    req_to_install, finder)
  File "/usr/lib/python2.7/dist-packages/pip/req/req_set.py", line 428, in _check_skip_installed
    req_to_install, upgrade_allowed)
  File "/usr/lib/python2.7/dist-packages/pip/index.py", line 465, in find_requirement
    all_candidates = self.find_all_candidates(req.name)
  File "/usr/lib/python2.7/dist-packages/pip/index.py", line 423, in find_all_candidates
    for page in self._get_pages(url_locations, project_name):
  File "/usr/lib/python2.7/dist-packages/pip/index.py", line 568, in _get_pages
    page = self._get_page(location)
  File "/usr/lib/python2.7/dist-packages/pip/index.py", line 683, in _get_page
    return HTMLPage.get_page(link, session=self.session)
  File "/usr/lib/python2.7/dist-packages/pip/index.py", line 792, in get_page
    "Cache-Control": "max-age=600",
  File "/usr/share/python-wheels/requests-2.12.4-py2.py3-none-any.whl/requests/sessions.py", line 501, in get
    return self.request('GET', url, **kwargs)
  File "/usr/lib/python2.7/dist-packages/pip/download.py", line 386, in request
    return super(PipSession, self).request(method, url, *args, **kwargs)
  File "/usr/share/python-wheels/requests-2.12.4-py2.py3-none-any.whl/requests/sessions.py", line 488, in request
    resp = self.send(prep, **send_kwargs)
  File "/usr/share/python-wheels/requests-2.12.4-py2.py3-none-any.whl/requests/sessions.py", line 609, in send
    r = adapter.send(request, **kwargs)
  File "/usr/share/python-wheels/CacheControl-0.11.7-py2.py3-none-any.whl/cachecontrol/adapter.py", line 47, in send
    resp = super(CacheControlAdapter, self).send(request, **kw)
  File "/usr/share/python-wheels/requests-2.12.4-py2.py3-none-any.whl/requests/adapters.py", line 423, in send
    timeout=timeout
  File "/usr/share/python-wheels/urllib3-1.19.1-py2.py3-none-any.whl/urllib3/connectionpool.py", line 643, in urlopen
    _stacktrace=sys.exc_info()[2])
  File "/usr/share/python-wheels/urllib3-1.19.1-py2.py3-none-any.whl/urllib3/util/retry.py", line 315, in increment
    total -= 1
TypeError: unsupported operand type(s) for -=: 'Retry' and 'int'

```

These errors happen for all python packages. Tried on two clean 17.10  installs. My work machine running 16.04 LTS has no problem whatsoever.

Suggestions and help appreciated.

---

### Post by monkeybrain20122 on 2017-11-03
bump

---

### Post by ian-weisser on 2017-11-03
If it fails on a clean install, have you checked the bug reports?

---

### Post by again? on 2017-11-03
Using 17.04 as my default desktop but booted into my 17.10 install to test.
Ran an upgrade and rebooted.
Installed python-pip then
```
sudo pip install -U sympy
```

Installed without problem.
```
glen@arty:~$ pip show sympy
Name: sympy
Version: 1.1.1
Summary: Computer algebra system (CAS) in Python
Home-page: http://sympy.org
Author: SymPy development team
Author-email: sympy@googlegroups.com
License: BSD
Location: /usr/local/lib/python2.7/dist-packages
Requires: mpmath
wheel (0.29.0)

```

---

### Post by monkeybrain20122 on 2017-11-07
> **guber2 said:**
> Using 17.04 as my default desktop but booted into my 17.10 install to test.
Ran an upgrade and rebooted.
Installed python-pip then
```
sudo pip install -U sympy
```

Installed without problem.



Sorry, there was a typo, I meant 17.10.

---

### Post by monkeybrain20122 on 2017-11-07
I think the issue might lie somewhere else, maybe some internet settings in 17.10 (if I am correct the errors meant can't connect to server) I took my laptop to a my office and it worked, but it fails 100% at home. However, it works at home and office 100% on the 16.04 partition and it worked 100% at home for 17.04 before (which I have removed since) So maybe between 17.04 and 17.10 some internet settings (something related to systemd?) have changed? 

Any idea how to diagnose that? Thanks.

---

### Post by again? on 2017-11-07
> **monkeybrain20122 said:**
> Sorry, there was a typo, I meant 17.10.
My test was in 17.10.

> **monkeybrain20122 said:**
> I think the issue might lie somewhere else, maybe some internet settings in 17.10 (if I am correct the errors meant can't connect to server) I took my laptop to a my office and it worked, but it fails 100% at home. However, it works at home and office 100% on the 16.04 partition and it worked 100% at home for 17.04 before (which I have removed since) So maybe between 17.04 and 17.10 some internet settings (something related to systemd?) have changed? 

Any idea how to diagnose that? Thanks.
No sorry. Don't really know python. Just install a couple of things with pip.

---

### Post by again? on 2017-11-07
This seems related.
[https://askubuntu.com/questions/924564/installing-python-packages-using-pip](https://askubuntu.com/questions/924564/installing-python-packages-using-pip)

---

### Post by monkeybrain20122 on 2017-11-08
> **guber2 said:**
> This seems related.
[https://askubuntu.com/questions/924564/installing-python-packages-using-pip](https://askubuntu.com/questions/924564/installing-python-packages-using-pip)


It seems that it is not really related to my problem here. I think in my case the errors mean unable to connect to server or something (maybe someone can confirm that) Since pip works on the same installation at office it is probably not a pip issue after all but 17.10 not able to shakehand with the sever (or timed out early)

Since pip install -U works in 16.04 (and 17.04) at home too so it seems some changes of defaulting network settings between 17.04 and 17.10 may be responsible. Does anyone have any info?

---

### Post by monkeybrain20122 on 2017-11-10
I stumbled upon the solution when trying to fix another problem ( apt update always stuck at "waiting for headers" in Artful  and daily iso of Bionic even for a clean install, it has been extremely annoying)

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

Now suddenly pip also works, I tested this fix on two different Artful and one Bionic installations, before pip works in none of them at home but now they all work. I don't know why this works since I thought apt has nothing to do with pip install (and the curious fact that pip did work in Artful at my office before, just not at home, now it works at both)

---

### Post by monkeybrain20122 on 2017-11-10
darn, upon reboot it stops working again. It has to do with network connectivity. I thought apt clean worked but it turned out to be an accident that I had good connection briefly. The true culprit turns out to be Debian/Ubuntu's patch of pip which screws up the retry download when network connectivity is poor
[https://github.com/pypa/pip/issues/3943](https://github.com/pypa/pip/issues/3943)
[https://github.com/pypa/pip/issues/4779](https://github.com/pypa/pip/issues/4779)
[https://github.com/pypa/pip/issues/4847](https://github.com/pypa/pip/issues/4847)

and a bug report [https://bugs.launchpad.net/ubuntu/+source/python-pip/+bug/1586859](https://bugs.launchpad.net/ubuntu/+source/python-pip/+bug/1586859)

Real solution: uninstall python-pip package and use the [get-pip.py]("https://pip.pypa.io/en/stable/installing/") script to install the unadulterated version of pip from upstream. Now everything works.

---

### Post by shteinb on 2017-11-12
This is what worked for me:
- remove all traces of system pip and virtualenv
sudo rm -rf /home/<user>/.cache/pip
sudo apt-get remove python-pip-whl virtualenv
sudo 'rm' -rf /usr/local/lib/python2.7/dist-packages/*
-reinstall
wget [https://bootstrap.pypa.io/get-pip.py](https://bootstrap.pypa.io/get-pip.py)
sudo -H python get-pip.py
sudo -H pip install virtualenv

---

