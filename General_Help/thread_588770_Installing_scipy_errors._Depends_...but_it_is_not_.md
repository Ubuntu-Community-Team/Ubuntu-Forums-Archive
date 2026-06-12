---
title: "Installing scipy errors. Depends: ...but it is not installable."
date: 2007-10-23
forum: General Help
---

### Post by flyeng4 on 2007-10-23
I am attempting to install scipy on Gutsy from [these instructions]("http://www.scipy.org/Installing_SciPy/Linux#head-c462578a786f049e03e6bba0e759a97fdd29c6ae").

After setting up the repository: deb [http://debs.astraw.com/](http://debs.astraw.com/) dapper/

And attempting to: sudo apt-get install python-numpy

I get:

python-numpy: Depends: python2.4 but it is not installable
                Depends: atlas3-base but it is not going to be installed or
                         lapack3 but it is not installable or
                         liblapack.so.3
                Depends: atlas3-base but it is not going to be installed or
                         refblas3 but it is not installable or
                         libblas.so.3
                Depends: libg2c0 (>= 1:3.4.4-5) but it is not installable

I have tried to go through and install each of the Depends:.... but have not had any luck.  I don't know what libg2c0 is and cannot find it any where.

---

### Post by zvacet on 2007-10-23
Don´t mix repositories.Change deb [http://debs.astraw.com/](http://debs.astraw.com/) dapper/  to 

 deb [http://debs.astraw.com/](http://debs.astraw.com/) gutsy/

in your source list. If you stil have problems with dependencies look here

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")


Be sure that you have all repositories open.**System>administration>software sources>tick all boxes**

---

### Post by flyeng4 on 2007-10-23
Worked perfectly!  Thanks for the help.

---

