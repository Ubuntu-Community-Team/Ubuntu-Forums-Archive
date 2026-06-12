---
title: "upgrade to newer version of python"
date: 2020-04-09
forum: General Help
---

### Post by Unguidedone on 2020-04-09
heres the issue: i am running Python 2.7.17 and not anything newer and more secure.  I tried updating python to a 3.x++ a few months ago and was left with 2 installs of python 2.x and 3.x and the interperter wanted to run the oldest version.  all versions of ubuntu need to roll out with a working but upgraded version of python by default so it does not ship with insecure packages.   [https://developers.slashdot.org/story/19/08/24/2242248/uk-cybersecurity-agency-urges-devs-to-drop-python-2](https://developers.slashdot.org/story/19/08/24/2242248/uk-cybersecurity-agency-urges-devs-to-drop-python-2)   im on 18.04 how do i remove my current install and put something new like python 3.x +++   there are countless guides on the internet but they all seem to break my install.

---

### Post by TheFu on 2020-04-09
NEVER try to replace the system python2/python3 systems.

Use something like **pyenv** to keep your desired python and modules completely separate from the system versions.

---

### Post by Impavidus on 2020-04-10
Python 2.7 and Python 3.* are both fully supported. Both get bugfixes if needed and on Ubuntu 18.04 both are installed by default.

Python 2 scripts are not compatible with the Python 3 interpreter, so while all Python scripts used by Ubuntu get ported to Python 3, both versions of Python must be installed. And as the Python 2 scripts may not explicitly state they need Python 2 (but the Python 3 scripts state that they need Python 3), Python 2 must be the default. You can run Python 3 using the python3 command:```
$ python --version
Python 2.7.17
$ python3 --version
Python 3.7.5
```
That's on Ubuntu 19.10. You'll get slightly different versions on 18.04, but still with all the critical bugfixes backported.

Many core components of Ubuntu use Python. When you manually mess with Python, you can easely break Ubuntu. This can also break the tools you would normally use to repair it, so you quickly get to the point that a fresh install is the only sensible option.

---

### Post by mikewhatever on 2020-04-10
Here is python3 on 18.04:
```

python3 --version
Python 3.6.9

```

---

### Post by oldfred on 2020-04-10
With 20.04 there is only python3.
```
red@fred-Z170N-focal:~$ python --version

Command 'python' not found, did you mean:

  command 'python3' from deb python3
  command 'python' from deb python-is-python3

fred@fred-Z170N-focal:~$ python3 --version
Python 3.8.2

```

I still have a couple of apps I typically install that still required python2, but I prevented those from installing the minute they tried to install python2.

---

### Post by Redalien0304 on 2020-04-10
With Ubuntu 20.04 Ubuntu CinnamonRemix

```
craig@craig-Latitude-E6500:~$ python --versionPython 2.7.17
craig@craig-Latitude-E6500:~$ python3 --version
Python 3.6.9
craig@craig-Latitude-E6500:~$ 
```

---

### Post by Unguidedone on 2020-04-11
> **TheFu said:**
> NEVER try to replace the system python2/python3 systems.  Use something like **pyenv** to keep your desired python and modules completely separate from the system versions.  i tested it in a vm and just broke the install thats why i posted the thread.   > **Impavidus said:**
> Python 2.7 and Python 3.* are both fully supported. Both get bugfixes if needed and on Ubuntu 18.04 both are installed by default.  Python 2 scripts are not compatible with the Python 3 interpreter, so while all Python scripts used by Ubuntu get ported to Python 3, both versions of Python must be installed. And as the Python 2 scripts may not explicitly state they need Python 2 (but the Python 3 scripts state that they need Python 3), Python 2 must be the default. You can run Python 3 using the python3 command:```
$ python --version Python 2.7.17 $ python3 --version Python 3.7.5
``` That's on Ubuntu 19.10. You'll get slightly different versions on 18.04, but still with all the critical bugfixes backported.  Many core components of Ubuntu use Python. When you manually mess with Python, you can easely break Ubuntu. This can also break the tools you would normally use to repair it, so you quickly get to the point that a fresh install is the only sensible option.  :( thats why i test in a vm and not on my working system    > **oldfred said:**
> With 20.04 there is only python3. ```
red@fred-Z170N-focal:~$ python --version  Command 'python' not found, did you mean:    command 'python3' from deb python3   command 'python' from deb python-is-python3  fred@fred-Z170N-focal:~$ python3 --version Python 3.8.2 
```  I still have a couple of apps I typically install that still required python2, but I prevented those from installing the minute they tried to install python2.   How can i restrict what runs depending on what version of python is running apparmor or selinux profile update of some kind?

---

### Post by The Cog on 2020-04-11
> How can i restrict what runs depending on what version of python is running apparmor or selinux profile update of some kind? 
I don't think I understand the question. What are you trying to restrict, and on what basis?

---

### Post by Unguidedone on 2020-04-12
Ill just need to upgrade from 18.04 -> 20.04 maybe the security issues will be solved.  tyvm for the input people much love

---

