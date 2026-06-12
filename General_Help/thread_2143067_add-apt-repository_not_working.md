---
title: "add-apt-repository not working"
date: 2013-05-07
forum: General Help
---

### Post by MaZaMo on 2013-05-07
I have Ubuntu 13.04. Trying to do this: 

[I][B]sudo add-apt-repository ppa:noobslab/themes

[/B][/I]I get this error in terminal:

[I]Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in get_ppa_info_from_lp
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.3/urllib/request.py", line 148, in urlopen
    context.load_verify_locations(cafile, capath)
ssl.SSLError: unknown error (_ssl.c:2158)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 129, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 105, in get_ppa_info_from_lp
    import pycurl
ImportError: No module named 'pycurl'[/I]

---

### Post by Vaphell on 2013-05-08
sounds like a package is missing, look for pycurl

```
apt-cache search pycurl
```
*python3-pycurl* sounds about right, install it.
```
sudo apt-get install python3-pycurl
```

---

### Post by MaZaMo on 2013-05-09
How did this happen? Is there any way to tell if anything else important was removed from my computer?

---

### Post by Vaphell on 2013-05-09
no idea, maybe package dependencies were flagged incorrectly and weren't pulled when add-apt-repository was being installed. Either way I wouldn't worry too much about that.

---

