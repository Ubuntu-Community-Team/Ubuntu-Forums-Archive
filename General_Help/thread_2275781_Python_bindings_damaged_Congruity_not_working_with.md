---
title: "Python bindings damaged? Congruity not working within Firefox. Ubuntu 14.04"
date: 2015-04-28
forum: General Help
---

### Post by Robbyx on 2015-04-28
I have followed the following to reinstall python and python bindings, but I fear that I may have messed up the installation.
Is there a conflict within what I am trying to install and what Ubuntu 14.04 needs?

> mkdir -p ~/bin ~/src ~/lib/python3.4
cd ~/src
wget [http://oligarchy.co.uk/xapian/1.3.2/...e-1.3.2.tar.xz](http://oligarchy.co.uk/xapian/1.3.2/...e-1.3.2.tar.xz)
tar -zvJf xapian-core-1.3.2.tar.xz
cd xapian-core-1.3.2
./configure --prefix=$HOME
make
make install
cd ..
wget [http://oligarchy.co.uk/xapian/1.3.2/...s-1.3.2.tar.xz](http://oligarchy.co.uk/xapian/1.3.2/...s-1.3.2.tar.xz)
tar -zvJf xapian-bindings-1.3.2.tar.xz
cd xapian-bindings-1.3.2
./configure --prefix=$HOME \
PYTHON=/usr/bin/python3.4 \
PYTHON_LIB=$HOME/lib/python3.4 \
--with-python --without-ruby \
--without-php --without-tcl
make
make install 

I have got as far as
./configure --prefix=$HOME \PYTHON=/usr/bin/python3.4 \PYTHON_LIB=$HOME/lib/python3.4 \--with-python --without-ruby
--without-php --without-tcl

The error messages are 
checking /usr/bin/python3.4 version... 3.4 (too new - use --with-python3 for Python 3 support)
configure: error: Use --with-python3 for Python 3 support (/usr/bin/python3.4 is 3.4)

I have not tried to make the xapian-bindings because of the error messages.

[LIST=1]
[*]Is using xapian 1.3.2 with python3.4 causing the error messages?
[*]Are they the right versions for Ubuntu 14.04?
[*]How do I resolve the error messages?
[/LIST]
R

---

### Post by ian-weisser on 2015-04-28
FYI, those bindings should already be provided by the python-xapian package in the Ubuntu repositories.

The error message seem to be simply telling you to try the '--with-python3' flag.

---

### Post by mc4man on 2015-04-28
What possible connection is there between python-xapian & congruity??

---

### Post by Robbyx on 2015-04-29
> **mc4man said:**
> What possible connection is there between python-xapian & congruity??

I guessed it was connected because one of the packages  used  by concordance/ congruity  is python-libconcord.

I have reinstalled my o/s  and still I can not update my harmony remote using congruity.  I think that Congruity should be followed by  Concordance from within Firefox when updating my  remote . I can not see anything happening at the end of congruity's operation.. The remote although recognised by Congruity is not being updated by I assume concordance which should be called after congruity is finished its part. 

R

---

