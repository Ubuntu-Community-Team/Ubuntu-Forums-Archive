---
title: "Need to revert python from 3.8.5 back to 3.8.2"
date: 2020-10-29
forum: General Help
---

### Post by sremick on 2020-10-29
So I believe my upgrade issue (trying to go from 20.04 -> 20.10) is related to my python version now being 3.8.5 when 3.8.2 is what 20.04 shipped with. Unfortunately the upgrade was a while back so I don't recall all the various things I found online that ultimately got me to 3.8.5. I do appear to be using "alternatives" however.

Some hints:

```
$ /usr/bin/python3 --version
Python 3.8.5

$ ls -l /usr/bin/python3
lrwxrwxrwx 1 root root 25 Jun 3 21:21 /usr/bin/python3 -> /etc/alternatives/python3

$ sudo update-alternatives --config python3
There is only one alternative in link group python3 (providing /usr/bin/python3): /usr/bin/python3.8
Nothing to configure.
```

Would ```
sudo apt-get install --reinstall python
``` be the correct course of action?

(I'm using Xubuntu but I'm not sure that's relevant)

---

### Post by CelticWarrior on 2020-10-29
Why do you think you need to revert? In other words, are there a reason for needing 3.8.2?
If there's something you really shouldn't mess with in a Linux distro that thing is python.

---

### Post by guiverc on 2020-10-29
also related [https://askubuntu.com/questions/1287560/python3-problem-upgrading-20-04-20-10](https://askubuntu.com/questions/1287560/python3-problem-upgrading-20-04-20-10)

---

### Post by sremick on 2020-11-01
> **CelticWarrior said:**
> Why do you think you need to revert? In other words, are there a reason for needing 3.8.2?

I believe it's the source of me not being able to upgrade from 20.04 -> 20.10.  See here:
[https://ubuntuforums.org/showthread.php?t=2452470](https://ubuntuforums.org/showthread.php?t=2452470)

> If there's something you really shouldn't mess with in a Linux distro that thing is python.
I am learning that. :( Something in the past needed a newer version of Python. If I knew then that Python was special and unlike other things should not be upgraded, I would've just went without the app.

---

### Post by The Cog on 2020-11-01
I don't know how to fix your current pickle I'm afraid. 

But there are several tools for allowing you to choose different versions of python (once you have sorted your current pickle out). See this page: [https://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe](https://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe)
I have only ever used virtualenv which puts a copy of the wanted version of python into a directory, and you puyt your application in there. It forms a standalone application+python folder.
As you want to use a different version to the systme version by default, maybe pyenv would be better for you though: [https://github.com/pyenv/pyenv](https://github.com/pyenv/pyenv)

---

### Post by sremick on 2020-11-01
OK I might have found potential steps to fix this, but wanted to check here before I risk making things worse (trying to use a solution I found online is what got me into this mess).

Steps lifted from: [https://unix.stackexchange.com/questions/218911/repairing-python-setup](https://unix.stackexchange.com/questions/218911/repairing-python-setup)

> In order to repair your system, you need to allow APT to perform downgrades. To do that, define APT preferences. Create a file /etc/apt/preferences.d/allow-downgrade containing

```
Package: *
Pin: release o=Ubuntu
Pin-Priority: 1001
```

The files in /etc/apt/preferences.d (plus /etc/apt/preferences) contain priority declarations that override the default selection when multiple versions of a package are available, which is “prefer the latest version from the target distribution”. Giving a package a priority over 1000 causes it to be preferred even if it's an older version that a package with a lower priority. Installed packages have priority 500 so the package from Ubuntu wins. For more information see:

```
man apt_preferences
```

I think once you've set these priorities you can run

```
apt-get update
apt-get upgrade
```

to downgrade all your packages to the version in Ubuntu (packages not in Ubuntu won't be removed). Also run ```
apt-get -f install 
``` and don't try to install any other software until this completes successfully.

Once everything is downgraded, remove the preferences file and run ```
apt-get update
``` again.

---

### Post by sremick on 2020-11-01
This can be closed. 

It turns out the problem was not that I had python 3.8.5 instead of  3.8.2. Instead, it was the symbolic linking that update-alternatives  does to /usr/bin/python3. Removing the chained symbolic links and  linking directly to /usr/bin/python3.8 like it would be without  update-alternatives resolved the 20.10 upgrade problem, even though  python was still 3.8.5 and ultimately still referring to the same  binary.


 I didn't have to change python versions and am now on Xubuntu 20.10.

---

### Post by wildmanne39 on 2020-11-01
We do not close threads when they are solved, but please use thread tools at the top of the page to mark this thread solved so other users with this issue will find it marked as solved when searching for a solution.

Thanks

---

