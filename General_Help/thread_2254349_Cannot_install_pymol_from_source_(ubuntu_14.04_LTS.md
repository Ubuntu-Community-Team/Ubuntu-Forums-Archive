---
title: "Cannot install pymol from source (ubuntu 14.04 LTS)"
date: 2014-11-26
forum: General Help
---

### Post by Karlsmart on 2014-11-26
Hello everyone
 
i am fairly new to ubu ntu/linux and i am trying to install my first program from source. The program is PyMOL and the guide i have tried to follow is here: [http://www.pymolwiki.org/index.php/Linux_Install](http://www.pymolwiki.org/index.php/Linux_Install)


i have downloaded all the prerequisites using

```
sudo apt-get install subversion build-essential python-dev python-pmw libglew-dev freeglut3-dev libpng-dev libfreetype6-dev
```

and downloaded the latest source files using

```
cd /tmp
svn co svn://svn.code.sf.net/p/pymol/code/trunk/pymol
cd pymol
```

but when i run the following script (sudo bash install.sh) i run into problems:
```

#!/bin/bash -e

 
prefix=/opt/pymol-svn
modules=$prefix/modules
 
python setup.py build install \
    --home=$prefix \
    --install-lib=$modules \
    --install-scripts=$prefix

```

the problem i get is that the installation suddenly stops without throwing an error message. i just stops and CPU activity drops to baseline and stays there. i have attached two screenshots of what it looks like. Interestingly, the installer writes that numpy is not available but i have both numpy and scipy installed and use them both without problems (i have used the typical canopy installation).

i have no idea how to proceed - has anyone any suggestions? is there anyway i can check was halted the installation? any suggestions will be highly appreciated :)

ps. i also tried the more complicated install script linked in guide above - that did also not work:

```
tail: cannot open ‘/home/martin/pymol/pymol’ for reading: No such file or directory
installpymol.sh: line 45: /home/martin/pymol/modules/pymol/pymol_path/run_on_startup.py: No such file or directory
installpymol.sh: line 46: /home/martin/pymol/modules/pymol/pymol_path/run_on_startup.py: No such file or directory
installpymol.sh: line 47: /home/martin/pymol/modules/pymol/pymol_path/run_on_startup.py: No such file or directory
installpymol.sh: line 48: /home/martin/pymol/modules/pymol/pymol_path/run_on_startup.py: No such file or directory
installpymol.sh: line 49: /home/martin/pymol/modules/pymol/pymol_path/run_on_startup.py: No such file or directory
installpymol.sh: line 50: /home/martin/pymol/modules/pymol/pymol_path/run_on_startup.py: No such file or directory

```


the modules folder have not been created

---

