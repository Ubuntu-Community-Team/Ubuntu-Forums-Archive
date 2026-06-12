---
title: "Running Update on pip Broke pip"
date: 2018-07-22
forum: General Help
---

### Post by rebeltaz on 2018-07-22
I just installed python-pip using apt-get on Ubuntu 16.04LTS. When I ran 'sudo pip install --upgrade setuptools', it said that I had v8.1.1 install while v18.x.x was available and that I should update pip using 'pip install --upgrade pip', which I did. Now, I cannot get any pip command to work. It keeps telling me:

```

Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main

```

I have tried purging python-pip, autoremove, autoclean and reinstalling python-pip, but I still get that error no matter what I do. I have noticed that there is no /usr/bin/pip file.... How can I fix this?

-=[ EDIT ]=-
As usual... just asking for help allowed me to find the answer, even though I'd already been looking for a hour before asking. [https://stackoverflow.com/questions/16237490/i-screwed-up-the-system-version-of-python-pip-on-ubuntu-12-10](https://stackoverflow.com/questions/16237490/i-screwed-up-the-system-version-of-python-pip-on-ubuntu-12-10) 

It was because I installed as sudo, but upgraded as user. Leaving this here in case anyone else needs it.

---

