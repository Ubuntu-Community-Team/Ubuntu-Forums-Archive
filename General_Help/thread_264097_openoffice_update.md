---
title: "openoffice update"
date: 2006-09-24
forum: General Help
---

### Post by Nora on 2006-09-24
Hello,
 
I updated quite a few packages yesterday among which openoffice (to openoffice.org2). Now I have serious problems: it takes about 5 minutes for openoffice to load, and it's extremely slow after as well. 

Other problems (maybe related to the previous ones): when I load synaptic package manager it gives me the following error message:

W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

Can you help,please?

---

### Post by arkangel on 2006-09-24
try reisntalling again, open System>>synaptic  and  look for open office and mark all its entries for reinstall.

if that doesnt work ,why dont install directly from its  website , that will give you more control  over the package [http://www.openoffice.org/](http://www.openoffice.org/)

to avoid double installation  remove the openoffice  via synaptic (it will ask if you want to remove ubuntu desktop,  these are only the icons)

and follow the  installer  instrunctions (i dumped into the /opt folder then i know waht i have installed  )


2. Navigating in  [ftp://ftp.free.fr](ftp://ftp.free.fr)   in /pub/Distributions_Linux, there is no Ubuntu folder 
maybe they are doing maintenance or changing the mirror 

open the list sources and comment  it  untill they are back, console  
# sudo gedit /etc/apt/sources.list

and add a '#' in from of any line that contains 'ftp://ftp.free.fr'

---

### Post by Nora on 2006-09-24
Thanks a lot, a simple reinstalling worked. Openoffice loads quite fast now, and seems to work fine.

When I run Synaptic package manager I still have the strange error message though. I don't know if that's important.

---

### Post by arkangel on 2006-09-24
no it only tells you that the repository doesnt have the  folder ubuntu in its path 

try doing  the following 
open the list sources in a console type:
# sudo gedit /etc/apt/sources.list

and add a '#' in from of any line that contains 'ftp://ftp.free.fr' 


from time to time click in  this repository [ftp://ftp.free.fr](ftp://ftp.free.fr) and  navigate to pub/Distributions_Linux    ,uncomment your source.list when  they have a ubuntu folder

---

### Post by Fantec on 2006-09-27
> W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_p lf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
Check [plf mirror]("ftp://ftp.free.fr/mirrors/plf.zarb.org/ubuntu/"), as ubuntu subdirectory is empty (excepted for a readme file saying ubuntu/plf team has resigned which could explain why you can not find any package).

Ubuntu mirror on ftp.free.fr is located at :
[ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/](ftp://ftp.free.fr/mirrors/ftp.ubuntu.com/)

Fantec

---

