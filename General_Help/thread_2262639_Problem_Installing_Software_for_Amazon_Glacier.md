---
title: "Problem Installing Software for Amazon Glacier"
date: 2015-01-26
forum: General Help
---

### Post by webmanoffesto on 2015-01-26
How do I resolve the below error so that I can use Amazon Glacier for backups?

I'm running some installs because I want to use Amazon Glacier for backups
I'm following the instructions at [http://linuxconfig.org/installation-and-getting-started-guide-with-amazon-glacier-storage-on-the-linux-system](http://linuxconfig.org/installation-and-getting-started-guide-with-amazon-glacier-storage-on-the-linux-system)

But when I enter 
```
sudo cd amazon-glacier-cmd-interface/; python setup.py install 
```

I get the error

```
[Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/test-easy-install-18392.write-test'

error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/test-easy-install-18392.write-test'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /usr/local/lib/python2.7/dist-packages/

```

I'm able to view the contents of /usr/local/lib/python2.7/dist-packages/ in Dolphin. I don't understand what the problem is. 

Ubuntu 14

---

### Post by ajgreeny on 2015-01-26
Do you also need to use sudo for the python script?  I've hardly used python for anything directly, so I say this from a viewpoint of no knowledge of its needs when writing to a system folder, but I presume it will be the same as bash or any other utility.

---

### Post by webmanoffesto on 2015-01-26
I don't know. I could try. How would I run the Python script in sudo?

---

### Post by ajgreeny on 2015-01-26
Perhaps ```
sudo cd amazon-glacier-cmd-interface/; sudo python setup.py install
```
or you could open a terminal with root permissions using command ```
sudo -i
```then try ```
cd amazon-glacier-cmd-interface/; python setup.py install
```

As I say, I don't know anything about python or exactly what you're trying to do, so make sure you know exactly why you neeed to do whatever it is first, and if all is still correct, go ahead.

---

### Post by webmanoffesto on 2015-01-26
Thanks, I'm not making progress though. 

tom@Toms-Laptop-K55A:~$ sudo cd amazon-glacier-cmd-interface/; sudo python setup.py install
[sudo] password for tom: 
sudo: cd: command not found
python: can't open file 'setup.py': [Errno 2] No such file or directory

tom@Toms-Laptop-K55A:~$ sudo -i
root@Toms-Laptop-K55A:~# cd amazon-glacier-cmd-interface/; python setup.py install
-bash: cd: amazon-glacier-cmd-interface/: No such file or directory
python: can't open file 'setup.py': [Errno 2] No such file or directory

tom@Toms-Laptop-K55A:/usr/local/lib/python2.7/dist-packages$ sudo cd amazon-glacier-cmd-interface/; sudo python setup.py install
[sudo] password for tom: 
sudo: cd: command not found
python: can't open file 'setup.py': [Errno 2] No such file or directory
tom@Toms-Laptop-K55A:/usr/local/lib/python2.7/dist-packages$ sudo cd ^Cazon-glacier-cmd-interface/; sudo python setup.py install
tom@Toms-Laptop-K55A:/usr/local/lib/python2.7/dist-packages$

---

### Post by webmanoffesto on 2015-01-26
This seems to have worked:
```
tom@Toms-Laptop-K55A:~$ cd amazon-glacier-cmd-interface/     
tom@Toms-Laptop-K55A:~/amazon-glacier-cmd-interface$ sudo python setup.py install
running install
running bdist_egg
```

---

