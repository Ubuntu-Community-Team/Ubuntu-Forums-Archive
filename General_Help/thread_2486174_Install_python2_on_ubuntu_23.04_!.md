---
title: "Install python2 on ubuntu 23.04 ?!"
date: 2023-04-21
forum: General Help
---

### Post by fairbird on 2023-04-21
I need to use python2 with python3 for my works ...
I try to install python2 but I can not
```
~/$ sudo apt install python2Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package python2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'python2' has no installation candidate



```

I have try more things but no luck

---

### Post by #&amp;thj^% on 2023-04-21
Looks like your stuck with python3:
```
sudo update-alternatives --config python
There is 1 choice for the alternative python (providing /usr/bin/python).

  Selection    Path              Priority   Status
------------------------------------------------------------
* 0            /usr/bin/python3   10        auto mode
  1            /usr/bin/python3   10        manual mode

Press <enter> to keep the current choice[*], or type selection number: 


```
Also see: [https://ubuntuforums.org/showthread.php?t=2485257&p=14136242](https://ubuntuforums.org/showthread.php?t=2485257&p=14136242)

---

### Post by fairbird on 2023-04-21
I'm just try now to install Python-2.7.9 manually
```
wget https://www.python.org/ftp/python/2.7.9/Python-2.7.9.tgz
sudo tar xzf Python-2.7.9.tgz
cd Python-2.7.9
sudo ./configure --enable-optimizations
sudo make altinstall

```

```
[FONT=Verdana]python2.7 -V[/FONT]
[FONT=Verdana]~ Python 2.7.9[/FONT]
[FONT=Verdana]sudo ln -sfn '/usr/local/bin/python2.7' '/usr/bin/python2'
[/FONT][FONT=Verdana]sudo update-alternatives --install /usr/bin/python python /usr/bin/python2 1[/FONT][FONT=Verdana]
[/FONT]
```

```

sudo update-alternatives --config python
* 0            /usr/bin/python3   2         auto mode
  1            /usr/bin/python2   1         manual mode
  2            /usr/bin/python3   2         manual mode


Press <enter> to keep the current choice
[*], or type selection number:

```

And I start to build my project without any error message ... And I will later to see what happens ...

---

### Post by #&amp;thj^% on 2023-04-21
Good Job please keep us updated, **particularly on system updates**

---

### Post by fairbird on 2023-04-22
Every things are fine ... No more problems after my steps here
[https://ubuntuforums.org/showthread.php?t=2486174&p=14140057#post14140057](https://ubuntuforums.org/showthread.php?t=2486174&p=14140057#post14140057)

---

### Post by MAFoElffen on 2023-04-22
> **fairbird said:**
> Every things are fine ... No more problems after my steps here
[https://ubuntuforums.org/showthread.php?t=2486174&p=14140057#post14140057](https://ubuntuforums.org/showthread.php?t=2486174&p=14140057#post14140057)
The correct verbiage would be: "No problems yet..."

1fallen was just being very kind. Linux Distributions are built around many Python Scripts for it's framework and foundation. It's taken over 4 years to convert from Python2 to Python3 and make that work... There are deep ingrained differences between the two, where things are just not going to work with Python2 being the primary version. (There is not longer a capability layer present either.) 

Remember the steps you took and keep a record of any dependencies that it brought in with what you did... Because what you did, broke your system. If you cannot back off the changes, you will end of having to reinstall your OS, like many others who have done that,and had to try to recover from that. You are not the first to try or do this. You don't see that there is a problem yet, but here is... and it is functionally broken.

Say what you will. Good luck.

---

### Post by monkeybrain20122 on 2023-04-22
> **MAFoElffen said:**
> The correct verbiage would be: "No problems yet..."

1fallen was just being very kind. Linux Distributions are built around many Python Scripts for it's framework and foundation. It's taken over 4 years to convert from Python2 to Python3 and make that work... There are deep ingrained differences between the two, where things are just not going to work with Python2 being the primary version. (There is not longer a capability layer present either.) 

Remember the steps you took and keep a record of any dependencies that it brought in with what you did... Because what you did, broke your system. If you cannot back off the changes, you will end of having to reinstall your OS, like many others who have done that,and had to try to recover from that. You are not the first to try or do this. You don't see that there is a problem yet, but here is... and it is functionally broken.

Say what you will. Good luck.

Therefore, I suggest installing alternative versions of python in a separate environment in $HOME instead of using update-alternatives to mess with system python. In fact I use a separate version of python for development and my own projects even when the version is the same as the system's and I never use apt to install python modules, instead I use pip which allows me to upgrade or downgrade modules easily (advice like "sudo apt install python3-numpy" makes  me cringe unless it is a dependency for some other packages installed with apt)

I use a script called python310.conf to invoke python 3.10.9 in Ubuntu 22.04. 

Python is installed in $HOME/opt/python310. 

I think OP can modify it in a trivial way for his python2 installation

```
export PREFIX=/home/mb/opt/python310

export HOME=$PREFIX #optional, I want different profile for browser in order to use jupyter notebook

export PYTHONHOME=$PREFIX

export PATH=$PYTHONHOME/bin:$PATH

export LD_LIBRARY_PATH=$PYTHONHOME/lib:$PYTHONHOME/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH

export PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig:$PKG_CONFIG_PATH

export PYTHONUSERBASE=$PYTHONHOME

export PYTHONPATH=$PYTHONHOME/lib/python3.10/site-packages



```

To invoke python just source the script first in terminal

```
source /path/to/python310.conf
```

(obviously, don't put this in .bashrc or .profile)

Maybe some of these are not necessary, or maybe you need to add more...

Most people use conda or pyenv to install separate python but I don't like either way as conda installs a lot of junks I either don't need or have already installed system wide and create unnecessary dependency issues and pyenv can only create python virtual environment of the same mayor version (so in 22.04 you can't make pyenv for python 3.8 or python 3.11, but my method works) In OP cases neither would work as python2 is no longer supported by conda.

---

### Post by fairbird on 2023-04-22
> **MAFoElffen said:**
> The correct verbiage would be: "No problems yet..."

1fallen was just being very kind. Linux Distributions are built around many Python Scripts for it's framework and foundation. It's taken over 4 years to convert from Python2 to Python3 and make that work... There are deep ingrained differences between the two, where things are just not going to work with Python2 being the primary version. (There is not longer a capability layer present either.) 

Remember the steps you took and keep a record of any dependencies that it brought in with what you did... Because what you did, broke your system. If you cannot back off the changes, you will end of having to reinstall your OS, like many others who have done that,and had to try to recover from that. You are not the first to try or do this. You don't see that there is a problem yet, but here is... and it is functionally broken.

Say what you will. Good luck.

Before those steps i did i got this error 
[https://ubuntuforums.org/showthread.php?t=2486174&p=14140057#post14140057](https://ubuntuforums.org/showthread.php?t=2486174&p=14140057#post14140057)

```
ERROR: The following required tools (as specified by HOSTTOOLS) appear to be unavailable in PATH, please install them in order to proceed:  python2
make: *** [Makefile:110: image] Error 1

```

But after that I can use my built environment to build E2 image without any issues

Thank you

---

### Post by monkeybrain20122 on 2023-04-22
> **fairbird said:**
> I'm just try now to install Python-2.7.9 manually
```
wget https://www.python.org/ftp/python/2.7.9/Python-2.7.9.tgz
sudo tar xzf Python-2.7.9.tgz
cd Python-2.7.9
sudo ./configure --enable-optimizations
sudo make altinstall

```

```
[FONT=Verdana]python2.7 -V[/FONT]
[FONT=Verdana]~ Python 2.7.9[/FONT]
[FONT=Verdana]sudo ln -sfn '/usr/local/bin/python2.7' '/usr/bin/python2'
[/FONT][FONT=Verdana]sudo update-alternatives --install /usr/bin/python python /usr/bin/python2 1[/FONT][FONT=Verdana]
[/FONT]
```

```

sudo update-alternatives --config python
* 0            /usr/bin/python3   2         auto mode
  1            /usr/bin/python2   1         manual mode
  2            /usr/bin/python3   2         manual mode


Press <enter> to keep the current choice
[*], or type selection number:

```

And I start to build my project without any error message ... And I will later to see what happens ...


I don't know why you use sudo so many times. When you perform operations in your $HOME you don't need sudo (uncompressing tar file, configure and make don't require sudo)

Also you don't need to link /usr/local/bin/foo to /usr/bin/foo, /usr/local/bin is already in your $PATH 

If you were to install in /usr/local, only the last step (make install)  requires sudo. It is not recommended to do it anyway. See my post.

Finally it is an exceedingly bad idea to use update-alternatives to change your python version as MAFoElffen already said, and I don't think you get his point. He is not saying whether you would get error in running or building your python2 program, but you may mess up other parts of your system because many components will stop working with the wrong version of python.

---

### Post by MAFoElffen on 2023-04-23
+1 with MonkeyBrain20122 --

Please look at his first post (#7)... Please follow his directions. 

'Installing' and 'Using' another version of Python in virtualenv in the home folder is a lot different than installing it directly to the system. I myself, do that. I also have multiple versions of Python and Java installed to use with Eclipse, for development in both languages. 

But I say, like MonkeyBrain20122... they are installed as "User only" in scope, and only used by those specific toolsets. They are *isolated* from the system. Not installed as for use by the system as a replacement version for the System to operate on. Does that make sense to you?

I applaud your enthusiasm, and determination. I sincerely do. I just think you might have not been aware of the impact of that, and how it should have been done to do that without causing problems to the system itself.

---

