---
title: "MIME file types editor assogiate and .mht files"
date: 2015-03-03
forum: General Help
---

### Post by heyup on 2015-03-03
The graphical MIME file types editor assogiate seems to have been dropped from the repositories, so .mht files are listed as unknown in Trusty. Why has assogiate been dropped?

I can open .mht files using Opera, but I'd like to use assogiate to edit the file type. 

Is there any alternative to assogiate in the Trusty repositories? 

Could assogiate be built from source and installed in Trusty, or would that not work?

---

### Post by heyup on 2015-03-04
Building from source doesn't seem likely as  build-depend libgnome-vfsmm-2.6-dev is not in Trusty repository.

Any ideas?

---

### Post by heyup on 2015-03-30
Assogiate is not in Trusty repository due to bugs that have not been solved. See here: 
[https://answers.launchpad.net/ubuntu/+source/assogiate/+question/256697]("https://answers.launchpad.net/ubuntu/+source/assogiate/+question/256697")
[http://bugs.debian.org/708762]("http://bugs.debian.org/708762")

I was unable to build assogiate from source due to build error, but there is a way to install from deb files.

1. Download deb builds of assogiate and dependancy libgnome-vfsmm-2.6-1c2a
```
wget http://launchpadlibrarian.net/103674609/assogiate_0.2.1-5_i386.deb
``` 
```
wget http://launchpadlibrarian.net/40221684/libgnome-vfsmm-2.6-1c2a_2.26.0-1build1_i386.deb
```

2. Install assogiate_0.2.1 and libgnome-vfsmm-2.6-1c2a dependencies that are not installed.
```
sudo apt-get --no-install-recommends install libgconf2-4 libgnomevfs2-0 libxml++2.6-2
```

3. Install dependancy libgnome-vfsmm-2.6-1c2a from deb file.
```
sudo dpkg -i libgnome-vfsmm-2.6-1c2a_2.26.0-1build1_i386.deb
```

4. Install assogiate_0.2.1 from deb file.
```
sudo dpkg -i assogiate_0.2.1-5_i386.deb
```

---

