---
title: "Openxenmanager with GTK issues"
date: 2023-09-04
forum: General Help
---

### Post by jbenini on 2023-09-04
Dear all,

I am running a Ubuntu MATE 22.04.3 LTS x86_64, with Python3 and I would like to run Openxenmanager.
I followed the steps at [https://github.com/OpenXenManager/openxenmanager?search=1#readme](https://github.com/OpenXenManager/openxenmanager?search=1#readme), but when I run the ```
sudo apt-get install python2.7 python-gtk2 glade python-gtk-vnc python-glade2 python-configobj python-setuptools python-raven
```, it claims that it's impossible to find the following packages:
[SIZE=2][I]-python-gtk2
-python-gtk-vnc
-python-glade2
-python-configobj
-python-raven[/I][/SIZE]


Even with this problem, I tried to look for other step to install the software and also I attempt to run the openxenmanager script, but this error appeared:
```
jbenini@pc~$ openxenmanager 
/usr/local/bin/openxenmanager:4: DeprecationWarning: pkg_resources is deprecated as an API. See https://setuptools.pypa.io/en/latest/pkg_resources.html
  __import__('pkg_resources').run_script('openxenmanager==0.1b1', 'openxenmanager')
Traceback (most recent call last):
  File "/usr/local/bin/openxenmanager", line 4, in <module>
    __import__('pkg_resources').run_script('openxenmanager==0.1b1', 'openxenmanager')
  File "/usr/local/lib/python3.10/dist-packages/pkg_resources/__init__.py", line 722, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/local/lib/python3.10/dist-packages/pkg_resources/__init__.py", line 1561, in run_script
    exec(code, namespace, namespace)
  File "/usr/local/lib/python3.10/dist-packages/openxenmanager-0.1b1-py3.10.egg/EGG-INFO/scripts/openxenmanager", line 23, in <module>
    import gtk
ModuleNotFoundError: No module named 'gtk'

```

As I understand, the actual Ubuntu Mate in which I'm running on my PC cannot download the Python-GTK2 instances needed to run the openxenmanager, so I am requesting a support from someone whose could know how to bypass this problem.

I appreciate any help from you.

---

### Post by TheFu on 2023-09-04
The python development team stopped supporting Python2 on 1/1/2020.  After that time, nobody should be using any python2 programs.  There isn't any real workaround on the OS you've selected.

You could install 18.04 and get ESM support, since standards support ended last April on 18.04, and install the software into it.  GTK2 is also really, really, really, really, old and unsupported. The EoL date for it was in 2020 too. They are deploying GTK v4 stuff these days after coding for GTK v3.x for a long time.

Running applications that have effectively been dead for 3 yrs isn't a good idea.  There hasn't been any update since 2021 and their repo points to a non-existent Qt version built with Python3.  Basically, the project is dead.  Software doesn't live forever.

---

### Post by jbenini on 2023-09-05
> **TheFu said:**
> The python development team stopped supporting Python2 on 1/1/2020.  After that time, nobody should be using any python2 programs.  There isn't any real workaround on the OS you've selected.

You could install 18.04 and get ESM support, since standards support ended last April on 18.04, and install the software into it.  GTK2 is also really, really, really, really, old and unsupported. The EoL date for it was in 2020 too. They are deploying GTK v4 stuff these days after coding for GTK v3.x for a long time.

Running applications that have effectively been dead for 3 yrs isn't a good idea.  There hasn't been any update since 2021 and their repo points to a non-existent Qt version built with Python3.  Basically, the project is dead.  Software doesn't live forever.

Thank you for your reply and advice. For this case I will run XenManager inside a virtualized W10.

---

### Post by TheFu on 2023-09-05
> **jbenini said:**
> Thank you for your reply and advice. For this case I will run XenManager inside a virtualized W10.

Have you considered using virt-manager?  I've been using it since 2010. I think it supports Xen stuff, though we moved Off Xen when Amazon did around 2010-2011. We've been on KVM/QEMU since and never regretted that change. At the same time, we dumped VMware ESXi and Virtualbox for our hypervisor needs. It has been a great decision.

Didn't Xen XM die long ago?  The new Xen is [https://xcp-ng.org/](https://xcp-ng.org/) which has a webapp GUI that will impress any PHB [https://www.gocomics.com/comics/lists/1628640/dilbert-pointy-haired-boss-comics](https://www.gocomics.com/comics/lists/1628640/dilbert-pointy-haired-boss-comics) sufficiently.  I know a few people who run Xen-Ng in their home labs.

Disclosure: I was a Citrix stockholder for a very long time.

---

