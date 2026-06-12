---
title: "How do i install python-wxgtk2.8 on Ubuntu 16.04.3"
date: 2017-09-18
forum: General Help
---

### Post by kerrygee on 2017-09-18
Hi,

i am trying to run SOFA Statistics 

[http://www.sofastatistics.com/](http://www.sofastatistics.com/)

on my 16.04.03 box, but installing the DEB package fails with unresolved dependencies on python-wxgtk2.8. Running "apt-get install -f" wont fix anything. Looks like the 16.04 repositories do not have the python-wxgtk2.8 package. Any ideas how to put the python-wxgtk2.8 (and its dependencies) on my 16.04 box?

any help yould be really nice

tia

K.

---

### Post by dragonfly41 on 2017-09-18
This link should help you ...

[https://wiki.wxpython.org/InstallingOnUbuntuOrDebian](https://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

I have not used Sofa.
Incidentally for stats applications have you tried RStudio (rstudio in Software Centre) and [http://www.shinyapps.io/?](http://www.shinyapps.io/?)

---

### Post by kerrygee on 2017-09-18
> **dragonfly41 said:**
> This link should help you ...

[https://wiki.wxpython.org/InstallingOnUbuntuOrDebian](https://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

I have not used Sofa.
Incidentally for stats applications have you tried RStudio (rstudio in Software Centre) and [http://www.shinyapps.io/?](http://www.shinyapps.io/?)

The wxpython stuff ooks nice! Ill give it a try and tell then whether it worked or not. I know RStudio. Its very powerful and also recommended by me here!

Thanks!

---

### Post by kerrygee on 2017-09-18
> **dragonfly41 said:**
> This link should help you ...

[https://wiki.wxpython.org/InstallingOnUbuntuOrDebian](https://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

I have not used Sofa.
Incidentally for stats applications have you tried RStudio (rstudio in Software Centre) and [http://www.shinyapps.io/?](http://www.shinyapps.io/?)

Hi,

it fails in the very early stage when running the curl command on "http://apt.wxwidgets.org/key.asc" by returning a http error 302.

best

K.

---

### Post by mc4man on 2017-09-19
you could probably gather all the packages needed from wily or vivid, put in a folder & install with apt. But i'd take a look at this ppa  here 1st.
[https://launchpad.net/~codeblocks-devs/+archive/ubuntu/release](https://launchpad.net/~codeblocks-devs/+archive/ubuntu/release)

---

### Post by dragonfly41 on 2017-09-19
It seems that the downloads site has been moved ...

[https://askubuntu.com/questions/569137/something-wicked-happened-resolving-apt-wxwidgets-orghttp-5-no-address-as](https://askubuntu.com/questions/569137/something-wicked-happened-resolving-apt-wxwidgets-orghttp-5-no-address-as)

---

### Post by kerrygee on 2017-09-19
> **dragonfly41 said:**
> It seems that the downloads site has been moved ...

[https://askubuntu.com/questions/569137/something-wicked-happened-resolving-apt-wxwidgets-orghttp-5-no-address-as](https://askubuntu.com/questions/569137/something-wicked-happened-resolving-apt-wxwidgets-orghttp-5-no-address-as)

The solution there gives me:

Executing: /tmp/tmp.noUNHMnLOM/gpg.1.sh --fetch-keys
[http://repos.codelite.org/CodeLite.asc](http://repos.codelite.org/CodeLite.asc)
gpg: Schlüssel 1AC82609: "David Hart (codelite key) <david@codelite.co.uk>" nicht geändert
gpg: Anzahl insgesamt bearbeiteter Schlüssel: 1
gpg:              unverändert: 1
deb [http://repos.codelite.org/wx3.0.2/ubuntu/](http://repos.codelite.org/wx3.0.2/ubuntu/)   xenial universe
Ign:1 [http://repos.codelite.org/wx3.0.2/ubuntu](http://repos.codelite.org/wx3.0.2/ubuntu) xenial InRelease
Fehl:2 [http://repos.codelite.org/wx3.0.2/ubuntu](http://repos.codelite.org/wx3.0.2/ubuntu) xenial Release 
  404  Not Found
OK:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease         
OK:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease 
OK:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease
OK:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Paketlisten werden gelesen... Fertig                
E: The repository 'http://repos.codelite.org/wx3.0.2/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by dragonfly41 on 2017-09-19
Third attempt.   This is an old dependency and you will need to search around to find it.

[https://askubuntu.com/questions/789302/install-python-wxgtk2-8-on-ubuntu-16-04](https://askubuntu.com/questions/789302/install-python-wxgtk2-8-on-ubuntu-16-04)

I see that I already have libwxgtk2.8-0 library installed as package in my Ubuntu 16.04 but not python-wxgtk2-8
which is the python binding.

[COLOR=#ff0000]**[Correction]**[/COLOR]
Note that the link given above refers to python-wxgtk2-8 and* not *python-wxgtk2.8 (note the subtle difference in syntax).

I have just used Synaptic Package Manager to search "wxwidgets" and I see python-wxgtk2.8 ..

You can install Synaptic Package Manager for managing packages by ..

```
sudo apt-get update && sudo apt-get install synaptic
```

---

### Post by kerrygee on 2017-09-21
Million thanks for all the answers. Very helpful and informative. :thumbup:

best regards

K.

---

