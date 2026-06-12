---
title: "List possible install config options for any package?"
date: 2008-04-30
forum: General Help
---

### Post by Xteven on 2008-04-30
Hello,

I am using apt-get to try and install the package "zoneminder". Apparently this package has several different optional configuration parameters that can be specified during the install process.

In general, is there a way for apt-get (or any other tool) to list all possible optional configuration parameters during an install process?

Thanks,

Steven

---

### Post by ryanhaigh on 2008-04-30
Those install options may actually be compile time options that you would use when compiling from source. You can probably download the source and change the options in the debian rules files as I did in this howto for nautilus [http://backports.ubuntuforums.com/showthread.php?t=725734](http://backports.ubuntuforums.com/showthread.php?t=725734)

Alterantely there may be options which could be configured through dpkg. For example to allow users to control cpu scaling through the gnome panel applet this must be used to enable suid.
```

sudo dpkg-reconfigure gnome-applets

```

---

### Post by Xteven on 2008-04-30
Well, in my case I am not trying to compile this package from source. I am using apt-get to automagically install this package for me. 

I suppose what I gather is that when using apt-get you get exactly what has been determined for the package install (based on debian rules file and such...?) and if I would like to specify optional parameters I am required to compile the software myself?

Correct me if I am wrong please!!

Thanks!

Steven

---

### Post by ryanhaigh on 2008-04-30
Thats correct if the options you want to use are compile time options then they need to be set at that point. There are however many packages that do have options that you can set post compile and these should mostly be accessible using dpkg-reconfigure.

---

### Post by Xteven on 2008-04-30
Excellent. 

Thanks,

Steven

---

