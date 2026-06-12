---
title: "Installing firstclass"
date: 2005-07-29
forum: General Help
---

### Post by zeuz on 2005-07-29
I downloaded this package:
[http://dsv.su.se/datorer/download/fcc_8.043-2_i386.deb](http://dsv.su.se/datorer/download/fcc_8.043-2_i386.deb)

And then tried to install it with 'dpkg -i fcc_8.043-2_i386.deb' but i'm having problems with dependencies:

> dpkg: beroendeproblem förhindrar konfigurering av fcc:
 fcc beror på libc6 (>= 2.3.2.ds1-21), men:
  Versionen av libc6 på systemet är 2.3.2.ds1-20ubuntu13.
 fcc beror på libqt3c102-mt (>= 3:3.3.4), men:
  Paket libqt3c102-mt är ej installerat.


Any help is appriciated, thanks. :)

---

### Post by Zelut on 2005-07-29
have you tried #sudo apt-get install -f to 'fix' any dependencies that are needed?  You might give that a try...  otherwise maybe try & see if the package you are looking for is available via apt-get thru the backports.

---

### Post by zeuz on 2005-07-29
'apt-get install -f' didn't work. Trough backports? I'm new to ubuntu. :)

---

### Post by Zelut on 2005-07-29
if you're new you'll definitely want to check out [www.ubuntuguide.org](www.ubuntuguide.org).  It'll tell you how to add additional repositories for programs (ie; backports).  Take a look at the first listing there & update your /etc/apt/sources.list.  After that go thru the page & check out anything else you may need.

---

### Post by Kimm on 2005-07-29
I have just tested that version of FirstClass that you provided (I use it and needed an upgrade anyway) and I can tell you that it wount work, even with the backports enabled!

(make sure you have libqt3c102-mt installed along with backports enabled before doing this...)

What you need to do is extract the files, make some slight changes and rebuild that package (I tried it, and it still works perfectly fine).

First we want a temporary directory where we can build the package from. Lets call it fcc. Then we need to extract the existing package into that directory.

Type this into the terminal:

```

mkdir fcc
file-roller fcc_8.043-2_i386.deb -e fcc

```

Note that we didnt use dpkg --extract to do this, since we need more then just the data files.

now, if you navigate to the folder "fcc" you will see two archives "data.tar.gz" and "control.tar.gz" along with a file called "debian-binary"

The file data.tar.gz contains the acctuall program, and control.tar.gz some information about it, that is where the file that doesnt want to work with uss exists.

Now, we need to extract these archives to change some package information, then rebuild the package.
Type this in your terminal:

```

cd fcc
tar -xvzf data.tar.gz
mkdir DEBIAN
cd DEBIAN
tar -xvzf ../control.tar.gz

```

now we have all the files extracted, but we need to change the data in the control file, this is where all the dependency information is contained.

Open the file in gedit (gedit control) and find this line (after depends):

> 
libqt3c102-mt (>= 3:3.3.4)


and change that to:

> 
libqt3c102-mt (>= 3:3.3.3-7ubuntu3)


That should fix the dependency problem. Now, lets remove the archives that we extracted from the original package as we dont want them included in the new one.

```

cd ..
rm -f data.tar.gz
rm -f control.tar.gz

```

And rebuild the package:

```

cd ..
dpkg-deb -b fcc

```

and finaly... install it:

```

sudo dpkg -i fcc.deb

```

I realize I am realy bad at writing HOWTOs but I hope this will get you going! :)

[i]PS.
This procedure can be used on practicly any debian package, but I stronly recommend you dont do it unless the change is minimal and I would avoid doing it on important system packages.[/i]

---

### Post by zeuz on 2005-08-01
That worked great, thanks! :)

---

### Post by Kakistos on 2005-10-08
I can't install libqt3c102-mt because it conflicts with libqt3-mt, and that is required for amarok. 

Any ideas?

:???:

---

### Post by _linux_ on 2006-04-10
[QUOTE=Kakistos]I can't install libqt3c102-mt because it conflicts with libqt3-mt, and that is required for amarok. 

Any ideas?

:???:[/QUOTE]
Go here:
[http://ubuntuforums.org/showthread.php?t=114165&highlight=firstclass]("http://ubuntuforums.org/showthread.php?t=114165&highlight=firstclass")

---

