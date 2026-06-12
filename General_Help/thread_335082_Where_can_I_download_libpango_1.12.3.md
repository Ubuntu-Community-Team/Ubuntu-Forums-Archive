---
title: "Where can I download libpango 1.12.3?"
date: 2007-01-09
forum: General Help
---

### Post by Interestedinthepenguin on 2007-01-09
Does anyone know where I can download the package, libpango 1.12.3?  

Thanks.

---

### Post by scrooge_74 on 2007-01-09
There is a libpango 1.12.3-0ubuntu3 in the repositories

---

### Post by Interestedinthepenguin on 2007-01-09
I know that. :)   

...but my Ubuntu PC doesn't have internet access.  

I'm looking to download it on another PC, to port to my Ubuntu PC.

Thanks, anyway.

---

### Post by scrooge_74 on 2007-01-09
If you had said so in the first place, you can do that and then use dpkg to install it , but you should check the dependencies for that package which you are going to need for it to install properly.  

Check in synaptics for the list of dependencies you have to fullfill

---

### Post by Interestedinthepenguin on 2007-01-10
> **scrooge_74 said:**
> ...you can do that and then use dpkg to install it , but you should check the dependencies for that package which you are going to need for it to install properly.  

Check in synaptics for the list of dependencies you have to fullfill

I know.  Thanks.

...but right now, I'm just looking for the package to download, and I can't check its dependencies if I don't have it.

---

### Post by scrooge_74 on 2007-01-10
Check in synaptic, look at the properties of the package and there is a list of dependencies there

---

### Post by Interestedinthepenguin on 2007-01-10
I wasn't clear in my last post.

I am looking for the package (*libpango 1.12.3*) to download. (I can't check its dependencies if I don't have it, right?)


Also:  When I searched for libpango 1.12.3, I found this:  

[http://www.linuxfromscratch.org/blfs/view/svn/x/pango.html](http://www.linuxfromscratch.org/blfs/view/svn/x/pango.html)

If the libpango package can't be found to be downloaded, will this package (after building it), contain libpango (1.12.3)?:-k

---

### Post by scrooge_74 on 2007-01-10
Sorry I think I was not clear also, in the repositories even if a package has not been you will find the detail for the dependencies you need to fulfill in order to install even from a .deb

you could try downloading packages from the [Debian]("http://www.debian.org") site from the testing repositories.

At least if you [check the dependencies]("http://www.debian.org/distrib/packages#view") even in the Debian site you can know which other packages you need to put in the CD

Here is the list of dependencies you are going to meet, in the long run is easier to carry the equipment somewhere else and dowload what you need because you dont know which other packages you need to download to fullfil the dependencies of the dependencies

[http://packages.debian.org/testing/libs/libpango1.0-0](http://packages.debian.org/testing/libs/libpango1.0-0)

---

### Post by Interestedinthepenguin on 2007-01-12
Yes!  I found it!!:p 

I appreciate your help, scrooge_74, but I found the exact package (libpango 1.12.3) at this site:  

[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)

The weird thing about it, is that it was the first result in my search this morning...and it wasn't there during the first days I'd searched for it (using the *exact* same phrase as the other times)...:-k

---

### Post by scrooge_74 on 2007-01-12
search engines, specially google (from what I read) they will put first the most popular ones.  So for example if in the next few days the link that is #7 gets more hits comming from google  than #1 then it will jump in the list

---

### Post by Interestedinthepenguin on 2007-01-13
I know, but it's weird that I went through a lot of pages of the results, and never found it.:)

---

