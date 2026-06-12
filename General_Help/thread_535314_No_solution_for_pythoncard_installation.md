---
title: "No solution for pythoncard installation"
date: 2007-08-26
forum: General Help
---

### Post by nagius on 2007-08-26
Hello,

I posted below  message in the programming talk section but I have not received any replies, still struggling to find out how to make pythoncard work but there is no information around apart from the'solution' below

Tried to install python (instead of using synaptic)  from source but, but no success tried ./configure make, make install. 

 I have installed many program from source before successfully, but this one is different, puzzled why it should be, because I have only heard of one way to install from source, maybe someone can help me please. I prefer to fix synaptic installation rather than try to install from source though.

thks

nagius



-------------------------------------------------------------------------------------------------------------
I am still getting error message ' Unable to find PythonCard installation' when I type either codeEditor or resourceEditor, changed /usr/bin/resourceEditor as follows:

#!/bin/sh

# A simple command-line wrapper for PythonCard's resourceEditor tool.
# Copyright (c) Kenneth J. Pronovici <pronovic@debian.org>; use as you wish.

if [ -d /usr/lib/python2.4/site-packages/PythonCard ]; then
exec /usr/bin/python2.4 \
/usr/lib/python2.4/site-packages/PythonCard/tools/resourceEditor/resourceE dit
or.py "$@"
else
echo "Unable to find PythonCard installation."
fi

This is from an old post still getting same problems after fix, reinstalled program 2 times via synaptic and change /usr/bin file again.

---

### Post by nagius on 2007-08-26
Can anyone give me any advice?

---

### Post by garolou on 2008-03-04
It's usually better to install packages through synaptic for maintenance and updates. But if you choose to do otherwise, here is what worked for me on Ubuntu 7.10. As things get outdated very quickly, verify that it is still relevant to you and modify paths & such accordingly.

From the synaptic package manager get wxPython; or from a terminal command line:
```
sudo apt-get python-wxgtk2.8
```

Download PythonCard and save in a temporary directory (/tmp in this example).
Open a terminal and enter the following:
```

cd /tmp
sudo gunzip PythonCard-0.8.2.tar.gz
sudo tar xf PythonCard-0.8.2.tar
cd PythonCard-0.8.2/
sudo python setup.py install

```
Now lets test it...
```

cd /usr/lib/python2.5/site-packages/PythonCard/samples/minimal
./minimal.py

```
If you get a "Permission denied" error then change the permission to that file and all the other ones in the sample folder...
```

cd ..
sudo chmod -R +x *.py *.pyw ./*/*.py

```
Lets try it again...
```

minimal/minimal.py

```
A small window should appear.

Launch the sample application from anywhere by entering:
```

/usr/lib/python2.5/site-packages/PythonCard/samples/samples.pyw

```

Utilities can be found in the tools folder. For example to launch 'codeEditor' and 'resourceEditor' type the following:
```

/usr/lib/python2.5/site-packages/PythonCard/tools/codeEditor/codeEditor.py
/usr/lib/python2.5/site-packages/PythonCard/tools/resourceEditor/resourceEditor.py

```

If you had permission issues earlier, you probably still had some here. Correct those...
```

sudo chmod +x /usr/lib/python2.5/site-packages/PythonCard/tools/*/*.py

```

Change the permissions as needed for the other folders.

cheers

---

