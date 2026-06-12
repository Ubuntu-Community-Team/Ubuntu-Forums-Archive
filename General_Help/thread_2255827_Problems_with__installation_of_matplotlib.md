---
title: "Problems with  installation of matplotlib"
date: 2014-12-07
forum: General Help
---

### Post by stuckubu on 2014-12-07
I want to install the matplotlib-1.4.2 with python. The python's version in my laptop is 2.7.5+. I solved all the dependence problems, but it failed with "python setup.py build" .
the result is:
```
lem@lemlap:~/Downloads/matplotlib-1.4.2$ python setup.py build============================================================================
Edit setup.cfg to change the build options


BUILDING MATPLOTLIB
            matplotlib: yes [1.4.2]
                python: yes [2.7.5+ (default, Feb 27 2014, 19:37:08)  [GCC
                        4.8.1]]
              platform: yes [linux2]


REQUIRED DEPENDENCIES AND EXTENSIONS
                 numpy: yes [version 1.7.1]
                   six: yes [using six version 1.8.0]
              dateutil: yes [dateutil was not found. It is required for date
                        axis support. pip/easy_install may attempt to
                        install it after matplotlib.]
                  pytz: yes [pytz was not found. pip will attempt to install
                        it after matplotlib.]
               tornado: yes [tornado was not found. It is required for the
                        WebAgg backend. pip/easy_install may attempt to
                        install it after matplotlib.]
             pyparsing: yes [pyparsing was not found. It is required for
                        mathtext support. pip/easy_install may attempt to
                        install it after matplotlib.]
                 pycxx: yes [Couldn't import.  Using local copy.]
                libagg: yes [pkg-config information for 'libagg' could not
                        be found. Using local copy.]
              freetype: yes [version 2.5.3]
                   png: yes [version 1.6.15]
                 qhull: yes [pkg-config information for 'qhull' could not be
                        found. Using local copy.]


OPTIONAL SUBPACKAGES
           sample_data: yes [installing]
              toolkits: yes [installing]
                 tests: yes [nose 0.11.1 or later is required to run the
                        matplotlib test suite.  pip/easy_install may attempt
                        to install it after matplotlib. / mock is required
                        to run the matplotlib test suite.  pip/easy_install
                        may attempt to install it after matplotlib.]
        toolkits_tests: yes [nose 0.11.1 or later is required to run the
                        matplotlib test suite.  pip/easy_install may attempt
                        to install it after matplotlib. / mock is required
                        to run the matplotlib test suite.  pip/easy_install
                        may attempt to install it after matplotlib.]


OPTIONAL BACKEND EXTENSIONS
                macosx: no  [Mac OS-X only]
                qt5agg: no  [PyQt5 not found]
                qt4agg: yes [installing, Qt: 4.8.4, PyQt: 4.8.4]
                pyside: no  [PySide not found]
               gtk3agg: yes [installing, version 3.6.8]
             gtk3cairo: yes [installing, version 3.6.8]
                gtkagg: no  [The C/C++ header for gtk (gtk/gtk.h) could not
                        be found.  You may need to install the development
                        package.]
                 tkagg: no  [TKAgg requires Tkinter.]
                 wxagg: no  [requires wxPython]
                   gtk: no  [The C/C++ header for gtk (gtk/gtk.h) could not
                        be found.  You may need to install the development
                        package.]
                   agg: yes [installing]
                 cairo: yes [installing, pycairo version 1.8.8]
             windowing: no  [Microsoft Windows only]


OPTIONAL LATEX DEPENDENCIES
                dvipng: no
           ghostscript: yes [version 9.10]
                 latex: no
               pdftops: yes [version 0.24.1]


running build
running build_py
copying lib/matplotlib/mpl-data/matplotlibrc -> build/lib.linux-x86_64-2.7/matplotlib/mpl-data
running build_ext
building 'matplotlib.ft2font' extension
x86_64-linux-gnu-gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -fPIC -DPY_ARRAY_UNIQUE_SYMBOL=MPL_matplotlib_ft2font_ARRAY_API -DPYCXX_ISO_CPP_LIB=1 -I/usr/lib/python2.7/dist-packages/numpy/core/include -I/usr/local/include/libpng16 -I/usr/local/include/freetype2 -I/usr/local/include -I/usr/include -I. -Iextern -I/usr/include/python2.7 -c src/ft2font.cpp -o build/temp.linux-x86_64-2.7/src/ft2font.o
In file included from extern/CXX/Extensions.hxx:37:0,
                 from src/ft2font.h:6,
                 from src/ft2font.cpp:3:
extern/CXX/WrapPython.h:58:20: fatal error: Python.h: No such file or directory
 #include <Python.h>
                    ^
compilation terminated.
error: command 'x86_64-linux-gnu-gcc' failed with exit status 1

```
But I found the "Python.h":
```
/usr/local/include/python3.3m/Python.h

```
What do I suppose to do to fix  this error ?

---

### Post by Bucky Ball on 2014-12-07
*Thread moved to **General Help**.*

You may have more luck here. ***Installations & Upgrades*** is for installing and upgrading the Ubuntu OS. ;)

Good luck.

---

### Post by stuckubu on 2014-12-07
:shock:, I'm sorry about that, thx a lot.

---

### Post by Bucky Ball on 2014-12-07
All good. Hope someone who knows jumps in for you. ;)

---

### Post by stuckubu on 2014-12-08
I googled a solution:
```
sudo apt-get build-dep python-matplotlib
```
It actually worked, but I don't why it works. It's very kind if someone tell me the reason.

---

