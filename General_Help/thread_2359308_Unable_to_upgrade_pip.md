---
title: "Unable to upgrade pip"
date: 2017-04-22
forum: General Help
---

### Post by charkel2 on 2017-04-22
I am unable to upgrade pip to the newest version. I have tried multiple things as suggested [here]("https://askubuntu.com/questions/775942/how-to-install-the-latest-version-of-pip-when-i-already-installed-the-provided-b") but nothing seems to work.

```
charlie@Ubuntu ~/pip-8.1.2 $ sudo -H  python -m  pip install --upgrade pip
Collecting pip
  Using cached pip-9.0.1-py2.py3-none-any.whl
Installing collected packages: pip
  Found existing installation: pip 8.1.2
    Uninstalling pip-8.1.2:
      Successfully uninstalled pip-8.1.2
Successfully installed pip-8.1.2
You are using pip version 8.1.2, however version 9.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
charlie@Ubuntu ~/pip-8.1.2 $ ^C

charlie@Ubuntu ~/pip-8.1.2 $ sudo -H pip install --upgrade pip
Requirement already up-to-date: pip in /usr/local/lib/python2.7/dist-packages

```

---

### Post by Habitual on 2017-04-22
```
pip install --upgrade pip
```

---

