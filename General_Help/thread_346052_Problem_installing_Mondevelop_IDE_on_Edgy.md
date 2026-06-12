---
title: "Problem installing Mondevelop IDE on Edgy"
date: 2007-01-25
forum: General Help
---

### Post by zenwalker on 2007-01-25
I want to know why Edgy is not supporting Monodevelop package in its repositories?
I used to install Monodevelop IDE package successfully from the Dapper drake repositories. But edgy has deprecated that option.  So whats wrong with Edgy and Monodevelop??

And so to get over it, i downloaded the Monodevelop Installer package (.bin) file from Mono site.  And installed it on Edgy. And now i can not launch from double clicking on icon. Only way through is from konsole. 

And again from konsole i get alot of errors in loading boo bindings and other addins. Totally i have a problem to use Mono on Edgy..

So can any body guide to get a good working package of Nonodevelop package for edgy. 
Even i read that Rpm file of monodevelop can be converted to debian file and then installed. But i want a simple straight way from apt-get or synaptic. :confused: 


Thanks

---

### Post by gavinjb on 2007-01-25
Not sure what repositories you are using, but I can install MonoDevelop, have you used [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) to generator a list of sources

---

### Post by zenwalker on 2007-01-25
Here is the content of my source.lst file:

> deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


If you have any better repos for downloading Mono and installing it and making it to work perfectly, then please get them for me.

And the link, you gave. Ill check it out..

Thanks

---

### Post by nrgtek on 2007-03-02
I'm also looking for good mono repo's if anyone found these?

---

