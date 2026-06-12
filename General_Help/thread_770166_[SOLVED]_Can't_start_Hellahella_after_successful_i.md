---
title: "[SOLVED] Can't start Hellahella after successful install in Hardy"
date: 2008-04-27
forum: General Help
---

### Post by Jungleboss on 2008-04-27
Hellanzb and HellaHella worked fine for me in Gutsy. I have successfully installed Hellanzb in Hardy but I can't get hellahella to work.

The installation went fine and I use the my old hella.ini, so it should be fine also.

When I try to start it with [FONT="Courier New"]**sudo paster serve hella.ini**[/FONT] I get the following error:

**[FONT="Courier New"]TypeError: import_module() takes at most 4 arguments (5 given); got ({'userna...pe'}, app_instance_uuid=..., cache_dir=..., session_key=..., session_secret=...), wanted (global_conf, full_stack=True, **app_conf)[/FONT]**

---

### Post by Coollie on 2008-05-17
> **Jungleboss said:**
> Hellanzb and HellaHella worked fine for me in Gutsy. I have successfully installed Hellanzb in Hardy but I can't get hellahella to work.

The installation went fine and I use the my old hella.ini, so it should be fine also.

When I try to start it with [FONT="Courier New"]**sudo paster serve hella.ini**[/FONT] I get the following error:

**[FONT="Courier New"]TypeError: import_module() takes at most 4 arguments (5 given); got ({'userna...pe'}, app_instance_uuid=..., cache_dir=..., session_key=..., session_secret=...), wanted (global_conf, full_stack=True, **app_conf)[/FONT]**

Did anyone helped you out with this? I have the same problem. Hellanzb working fine but can't get hellahella to work!

Anyone?

Thanks!

---

### Post by xmltok on 2008-05-27
hellahella does not work with python 2.5, switch to 2.4

---

### Post by Jungleboss on 2008-06-01
I have installed Python 2.4 now too (as well as the default 2.5). How do I get Hellahella to use the older version rather than the default 2.5?

---

### Post by Trekster on 2008-06-11
I have the same issues as you guys...any help would be appreciated

---

### Post by Trekster on 2008-06-11
"Fixed" it..

As suggested switch to python 2.4.5. I just changed the symlink to point to 2.4 and redid the installation of hellahella...now everything is working

---

### Post by Jungleboss on 2008-06-12
Where did you find the symlinks, if I may ask?

---

### Post by Jungleboss on 2008-06-14
I found it!

I changed the symlink /usr/bin/python to point to /usr/bin/python2.4 instead of python2.5.

```
cd /usr/bin
sudo rm python
sudo ln -s python2.4 ./python
```


Now it works for me as well.

---

### Post by Jungleboss on 2008-06-16
Some applications that requires Python 2.5 may stop working if you change the symlink though.

---

### Post by BassKozz on 2008-12-09
> **Jungleboss said:**
> Some applications that requires Python 2.5 may stop working if you change the symlink though.
I am having the same problem, are there any other (possibly better) solutions to getting this to work properly?
I wouldn't want to setup a symlink if it's only gonna cause me headaches in the future, any suggestions?
> **Jungleboss said:**
> I found it!

I changed the symlink /usr/bin/python to point to /usr/bin/python2.4 instead of python2.5.

```
cd /usr/bin
sudo rm python
sudo ln -s python2.4 ./python
```


Now it works for me as well.
I followed your post Jungleboss, and now I've got a new set of errors:
```
paster serve hella.ini 
Traceback (most recent call last):
  File "/usr/bin/paster", line 5, in ?
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 2562, in ?
    working_set.require(__requires__)
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 626, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 524, in resolve
    raise DistributionNotFound(req)  # XXX put more info here
pkg_resources.DistributionNotFound: PasteScript==1.7.3

```

---

### Post by BassKozz on 2008-12-09
> **BassKozz said:**
> I am having the same problem, are there any other (possibly better) solutions to getting this to work properly?
I wouldn't want to setup a symlink if it's only gonna cause me headaches in the future, any suggestions?

I followed your post Jungleboss, and now I've got a new set of errors:
```
paster serve hella.ini 
Traceback (most recent call last):
  File "/usr/bin/paster", line 5, in ?
    from pkg_resources import load_entry_point
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 2562, in ?
    working_set.require(__requires__)
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 626, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 524, in resolve
    raise DistributionNotFound(req)  # XXX put more info here
pkg_resources.DistributionNotFound: PasteScript==1.7.3

```
Nevermind, I figured it out, Hellanzb was using Python2.5 and HellaHella was using 2.4, so Hellanzb wasn't running which caused my errors with HellaHella, so I had to reinstall Hellanzb & HellaHella with the symlink in place for python2.4.

Anyone have a better solution to this problem (rather then using the Symlink for Python2.4), I am sure many would like to know?

---

### Post by BassKozz on 2008-12-17
> **BassKozz said:**
> Nevermind, I figured it out, Hellanzb was using Python2.5 and HellaHella was using 2.4, so Hellanzb wasn't running which caused my errors with HellaHella, so I had to reinstall Hellanzb & HellaHella with the symlink in place for python2.4.

Anyone have a better solution to this problem (rather then using the Symlink for Python2.4), I am sure many would like to know?

This is **[COLOR="Red"]NOT[/COLOR]** a good solution at all, I later have found out that this causes GDebi to Crash
[quote=synaptic package manager - GDebi]Simple tool to install deb files
gdebi lets you install local deb packages resolving and installing
its dependencies. apt does the same, but only for remote (http, ftp)
located packages.

This package contains the graphical user interface.[/quote]
This also means that the 'add/remove' function of the Applications tab is [COLOR="Red"]**BROKEN**[/COLOR] !!!

I am sure this isn't the only package that relies on Python 2.5, so pointing to 2.4 is not a good solution for this...
I've submitted a ticket to HellaHella's trac: [http://www.hellanzb.com/trac/hellanzb/ticket/412](http://www.hellanzb.com/trac/hellanzb/ticket/412)
So does someone PLEASE have another solution to getting hellanzb & hellahella working with python 2.5?

---

### Post by BassKozz on 2008-12-17
> **BassKozz said:**
> This is **[COLOR="Red"]NOT[/COLOR]** a good solution at all, I later have found out that this causes GDebi to Crash

This also means that the 'add/remove' function of the Applications tab is [COLOR="Red"]**BROKEN**[/COLOR] !!!

I am sure this isn't the only package that relies on Python 2.5, so pointing to 2.4 is not a good solution for this...
I've submitted a ticket to HellaHella's trac: [http://www.hellanzb.com/trac/hellanzb/ticket/412](http://www.hellanzb.com/trac/hellanzb/ticket/412)
So does someone PLEASE have another solution to getting hellanzb & hellahella working with python 2.5?

Fixed!!!
Simply issue: ```
sudo easy_install -v "Myghty==dev,>=1.1.1dev-r2155" 
```
Thanks pjenvey :D

Remember to reset python back to 2.5:
```
cd /usr/bin
sudo rm python
sudo ln -s python2.5 ./python
```

---

