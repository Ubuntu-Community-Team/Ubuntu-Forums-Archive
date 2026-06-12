---
title: "Installing Python Sybase Module and FreeTDS"
date: 2012-10-16
forum: General Help
---

### Post by burntwater on 2012-10-16
Hi all,

I am attempting to install the Python Sybase module in conjunction with FreeTDS on Ubuntu 12.04 with limited success. Installing FreeTDS from the repositories is a simple exercise with well documented examples, I used ```
sudo apt-get install freetds-dev
``` and let it pull in all the dependencies itself.

Next I downloaded ```
python-sybase-0.40pre2.tar.gz
``` from [http://python-sybase.sourceforge.net/download.html]("http://python-sybase.sourceforge.net/download.html") and following the instructions at [http://python-sybase.sourceforge.net/install.html]("http://python-sybase.sourceforge.net/install.html") results in issues.

```

python setup.py build_ext -D HAVE_FREETDS -U WANT_BULKCOPY
python setup.py install

```

For the first command I get:
> Please define the Sybase installation directory in the SYBASE environment variable.
This can be fixed by ```
export SYBASE=/usr
``` and then it runs through (took a bit of Googling to figure that out). Contrary to some posts on the net there is no ```
/usr/local/freetds
``` directory.

For the second (install) command though I get the same error as before. Running ```
echo $SYBASE
``` returns > /usr as expected. Ditto for ```
sudo echo $SYBASE
```.

I set the **$SYBASE** variable in the **.bashrc** file, opened a new terminal and tried again, no luck.

UPDATE:
By adding **SYBASE=/usr** in **/etc/environment** it was possible to then install the Sybase module. The issue was that when running the install command **sudo** did not see the environment variable. By using **sudo -i** it is possible to see the **$SYBASE** variable but then other issues arise.

The next issue is that:
```
import Sybase
```
results in
> 
Traceback (most recent call last):
  File "./test_main.py", line 27, in <module>
    test_sybase.test_sybase()
  File "/home/rbu/Documents/Projects/Python_DB_extractor/src/test_sybase.py", line 10, in test_sybase
    import Sybase
  File "/usr/local/lib/python2.7/dist-packages/python_sybase-0.40pre2-py2.7-linux-x86_64.egg/Sybase.py", line 15, in <module>
    from sybasect import *
ImportError: libsybblk_r64.so: cannot open shared object file: No such file or directory


Any assistance would be greatly appreciated, thanks!

---

