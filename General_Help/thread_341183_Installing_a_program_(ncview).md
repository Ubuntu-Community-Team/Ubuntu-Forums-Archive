---
title: "Installing a program (ncview)"
date: 2007-01-18
forum: General Help
---

### Post by col_b on 2007-01-18
Hello,

How would I go about installing a program on Ubuntu?  I've downloaded ncview, untarred and unzipped it.  But I can't seem to install it.  There is a configure file and an install-sh file.  I guess there is a configure or install command.  Not sure what it is though...

Any help much appreciated.

Cheers,
Col

---

### Post by highneko on 2007-01-18
Usually you have to do this:

./configure
make
sudo make install

But, you should check around for a document or a file named install and read it.

---

### Post by an.echte.trilingue on 2007-01-18
Also, you will need to install build-essential to compile this:

```
sudo apt-get install build-essential
```

Also, I would recommend that you use checkinstall to create a .deb that you install instead of make / make install.  This makes removing and updating the program much, much easier, helps prevent broken packages, and allows you to manage the program in synaptic:
```

sudo apt-get install checkinstall
./configure
checkinstall
dpkg -i <package-name>

```
where <package-name> is whatever you named the package.


Take care
-mat

---

### Post by meanmrmustard on 2007-01-18
Oops!

---

### Post by col_b on 2007-01-18
thanks for the replies folks, i'll get right on it.

col

---

### Post by col_b on 2007-01-19
OK, I tried doing ./configure.  It said permission denied (see below).  So, I tried sudo ./configure, and I got the following:

cjbeaney@flux:~/Desktop/ncview-1.93b$ ./configure
./configure: line 975: config.log: Permission denied
cjbeaney@flux:~/Desktop/ncview-1.93b$ sudo ./configure
Password:
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for X... no
Error, ncview requires the X libraries and development headers to be installed!
cjbeaney@flux:~/Desktop/ncview-1.93b$                         

I thought X libraries were already installed with ubuntu?  The program package is sitting on the Desktop at the moment - does it need moved elsewhere?  Below is a list of all the files that come with the package.  There are several install files, but INSTALL gives basically the same instructions as given by you folks.

Any help much appreciated.
Cheers,
Colin

---

### Post by col_b on 2007-01-19
I've played around with this but am still stuck ](*,) 

Does the package need to be in a different location?  It's on the desktop at the moment.

Still getting the X library error.

Any other thoughts most welcome.

Cheers,
Col

---

### Post by Littleweseth on 2007-01-19
> I thought X libraries were already installed with ubuntu? 

Not necessarily. The X windowing system is installed, but not the development libraries you need to install (iirc.)

Try looking for packages with names like 'lib-x ....' and so forth?

---

### Post by lamego on 2007-01-19
You will need to install the following 2 packages:
libx11-dev, libxt-dev

---

### Post by Gerippter on 2007-01-26
I have the same problem.
Both libs are installed via Synaptic Package Manager, but I still have the same error message.
Very strange and a bit annoying.
Ubuntu first installed a treat, WLAN support, Inet, no problem.
But installing more sophisticated stuff is becoming a pain.
Everything that is easy using SuSE appears a major issue here and vice versa...
Well..
Maybe its just me, I was raised a windows kid...

I'd be glad for any help

Cheers
Felix

---

### Post by Gerippter on 2007-01-27
The ncview README says it needs the Athena Widget Set, and expects headers and libs, 
in a dir 'Xaw' of  the standard X11 dir.
I installed it, no use.
Sigh...

---

### Post by Tuoppi on 2007-02-14
Try to configure it with option --x-libraries. For example:
```
./configure --x-libraries=/usr/X11R6/lib
```
It worked fine in my Ubuntu.

Cheers,
Tuomas

---

### Post by stfields on 2007-07-05
> **Gerippter said:**
> The ncview README says it needs the Athena Widget Set, and expects headers and libs, 
in a dir 'Xaw' of  the standard X11 dir.
I installed it, no use.
Sigh...

I had the same problem.  You have to install the packages libxaw7-dev and libxaw-headers.  Worked for me!

---

### Post by Mehmet Karatay on 2007-11-08
Thanks for the tip. I needed both libxaw7-dev and libxaw-headers and probably wouldn't have realised otherwise. 

You also need netcdfg-dev, not simply netcdf3 as I was attempting. Without netcdfg-dev the file netcdf.h that is needed to make ncview is missing. That might be obvious to a lot of people, but it caused me problems for a while.

Mehmet

---

