---
title: "python3 vs python 3.7 vs python3.8 on 20.04"
date: 2020-06-05
forum: General Help
---

### Post by cnbiz850 on 2020-06-05
I am on Xubuntu 20.04.

A lot of python packages installed from the repository are placed under /usr/lib/python3/dist-packages/.  This becomes a problem after I installed python3.7 from a PPA.  Package python3-numpy, for instance, is under /usr/lib/python3/dist-packages/.  When I tried to "import numpy" from python3.7, it failed.  And I can't install another copy of numpy just for python3.7.  I wonder what's the best way to clean this up?  Can I simply remove the packages from /usr/lib/python3/dist-packages/ and reinstall them with 3.8 and 3.7 respectively?  I am not sure if those packages were installed by Ubuntu or by myself.

---

### Post by dragonfly41 on 2020-06-05
I suggest trying conda for managing multiple python versions / environments.

---

### Post by cnbiz850 on 2020-06-05
I actually used Miniconda3 before.  But somehow there is a conflict that causes OpenGL to not use the correct drivers when I tried to run Kivy.  Installing 3.7 separately caused the conflict to go away, and plus, it's less bloated than conda.  I hope to keep it clean.

---

### Post by monkeybrain20122 on 2020-06-05
> **cnbiz850 said:**
> I actually used Miniconda3 before.  But somehow there is a conflict that causes OpenGL to not use the correct drivers when I tried to run Kivy.  Installing 3.7 separately caused the conflict to go away, and plus, it's less bloated than conda.  I hope to keep it clean.

That is because when you installed conda you answered yes to adding this line to your .bashrc
```
export PATH=$ANACONDA_INSTALL_DIR/bin:$PATH
``` 

This will allows conda's python to override the system's, hence creating problem for you.  To fix it just reverse the order 

```
export PATH=$PATH:$ANACONDA_INSTALL_DIR/bin
```

---

### Post by monkeybrain20122 on 2020-06-05
You can't import modules from your ppa python because the environmental variables are still pointing to the system version. 

Don't install python or python modules (like numpy) from ppa. It makes your file system very confusing and installing python modules like numpy with sudo apt install python3-numpy is bad idea anyway. I never install python modules from repo,-- except as dependencies for other things installed with apt. There is no need to install them system wide and you get stuck with old versions, and you can't have multiple versions like you have observed.

My advice: Never use your system python and modules from repository for development. Over time it just becomes very hard to manage.

I have multiple versions of pythons on my 16.04 system. I installed python from source and invoke each with a script like this (for python3.8.2)

```
export PREFIX=/home/monkeybrain/opt/python38

export HOME=$PREFIX  #for spyder to create separate config instead of  using a single config for my user

export PATH=$PREFIX/bin:$PATH

export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH


export PYTHONUSERBASE=$PREFIX

export PYTHONPATH=$PREFIX/lib/python3.8/site-packages:$PYTHONPATH



```

I call this python38.conf and place it in /home/monkeybrain/Scripts, so to use python3.8.2 (installed in /home/monkeybrain/opt/python38)

I open the terminal and do

```
source ~/Scripts/python38.conf

python
```

 (I made a symlink "ln -s  /home/monkeybrain/opt/python38/bin/python3  /home/monkeybrain/opt/python38/bin/python", so I don't have to type  python3)

This way each python is separate and self contained and I don't need to install a lot of overheads like conda or use something clumsy like virtualenv (you need one version of python to install other sub-python systems and there are version restrictions)

I install python modules (e.g numpy) for each with pip (or pip3 but I made a symlink so don't need to type "3") It will install the module in the proper places for the version of python in question.

**P.S **Building python from source is really simple, if you need help I can give you step by step instructions.

---

### Post by cnbiz850 on 2020-06-06
I can't see how reversing of order in PATH can help avoid version mixing.  In both of the cases, it searches in the first, and if not there, it uses the one in the second.

---

### Post by cnbiz850 on 2020-06-06
Excellent advice.  Thanks.  I will experiment.

> **monkeybrain20122 said:**
> You can't import modules from your ppa python because the environmental variables are still pointing to the system version. 

Don't install python or python modules (like numpy) from ppa. It makes your file system very confusing and installing python modules like numpy with sudo apt install python3-numpy is bad idea anyway. I never install python modules from repo,-- except as dependencies for other things installed with apt. There is no need to install them system wide and you get stuck with old versions, and you can't have multiple versions like you have observed.

My advice: Never use your system python and modules from repository for development. Over time it just becomes very hard to manage.

I have multiple versions of pythons on my 16.04 system. I installed python from source and invoke each with a script like this (for python3.8.2)

```
export PREFIX=/home/monkeybrain/opt/python38

export HOME=$PREFIX  #for spyder to create separate config instead of  using a single config for my user

export PATH=$PREFIX/bin:$PATH

export LD_LIBRARY_PATH=$PREFIX/lib:$LD_LIBRARY_PATH


export PYTHONUSERBASE=$PREFIX

export PYTHONPATH=$PREFIX/lib/python3.8/site-packages:$PYTHONPATH



```

I call this python38.conf and place it in /home/monkeybrain/Scripts, so to use python3.8.2 (installed in /home/monkeybrain/opt/python38)

I open the terminal and do

```
source ~/Scripts/python38.conf

python
```

 (I made a symlink "ln -s  /home/monkeybrain/opt/python38/bin/python3  /home/monkeybrain/opt/python38/bin/python", so I don't have to type  python3)

This way each python is separate and self contained and I don't need to install a lot of overheads like conda or use something clumsy like virtualenv (you need one version of python to install other sub-python systems and there are version restrictions)

I install python modules (e.g numpy) for each with pip (or pip3 but I made a symlink so don't need to type "3") It will install the module in the proper places for the version of python in question.

**P.S **Building python from source is really simple, if you need help I can give you step by step instructions.

---

### Post by monkeybrain20122 on 2020-06-06
> **cnbiz850 said:**
> I can't see how reversing of order in PATH can help avoid version mixing.  In both of the cases, it searches in the first, and if not there, it uses the one in the second.

Your system will search for $PATH and get the first instance of python it finds, so if you have reversed the order it would be the system's python. On the other hand when you load conda it will look for something in conda-directory/bin from the way it is written, it only requires this to be in your $PATH (unlike the system it won't just go for the first python) so reversing works. I have tried it, I won't tell you things if I don't know that it works. ;)

---

