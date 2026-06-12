---
title: "How to install GDC and Tango, on Ubuntu 8.04 64bit (Hardy Heron)"
date: 2008-06-10
forum: General Help
---

### Post by adilbaig on 2008-06-10
I've had my share of problems getting a DMD compiler to run on Ubuntu x86_64.

First off, this will allow you to install GDC and Tango on a 64bit Ubuntu. Note that DMD has no 64bit version, so dont try to make it work. It wont.


Go to shell type the following :

1) ```
sudo wget http://downloads.dsource.org/projects/tango/ubuntu/<version>.list -O /etc/apt/sources.list.d/dpackages.list
```

Replace <version> with "hardy" or gutsy


2) ```
wget -q [http://downloads.dsource.org/projects/tango/ubuntu/public.key](http://downloads.dsource.org/projects/tango/ubuntu/public.key) -O- | sudo apt-key add -
```

3) ```
sudo apt-get update
```

4) ```
sudo apt-get install gdc dsss tango-gdc
```


Now you're all set. To compile use "rebuild". Here's how :

```
rebuild myfile.d
```


Thats it!

And finally, i need to give credit where credit is due. These instructions were copied in their wholesome nutritious form from :

[http://codeblog.palos.ro/2008/04/06/ubuntu-dpackages-repository/](http://codeblog.palos.ro/2008/04/06/ubuntu-dpackages-repository/)

Good luck!

---

