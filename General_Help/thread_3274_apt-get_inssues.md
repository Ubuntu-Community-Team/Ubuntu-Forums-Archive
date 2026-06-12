---
title: "apt-get inssues"
date: 2004-11-04
forum: General Help
---

### Post by eladio on 2004-11-04
How do I get around this... Just trying to install gftp but it gives me dependency issues I don't know how to resolve.

root@astro:/etc/apt # apt-get install gftp
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.17-6) but it is not installable
        Depends: gftp-text (= 2.0.17-6) but it is not going to be installed
E: Broken packages
root@astro:/etc/apt #

---

### Post by TekMate on 2004-11-04
[QUOTE=eladio]How do I get around this... Just trying to install gftp but it gives me dependency issues I don't know how to resolve.

root@astro:/etc/apt # apt-get install gftp
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.17-6) but it is not installable
        Depends: gftp-text (= 2.0.17-6) but it is not going to be installed
E: Broken packages
root@astro:/etc/apt #[/QUOTE]
 You need to have universe enabled to get gftp.

---

### Post by eladio on 2004-11-04
I modified the source.list and uncommented all repository locations.  One one them was universe.  I'm posting the source.list 

This is the sources.list found in the /etc/apt directory.  Anything wrong with this file?
------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

---

### Post by FLeiXiuS on 2004-11-04
Looks fine and dandy to me, have you tried installing the program?

---

