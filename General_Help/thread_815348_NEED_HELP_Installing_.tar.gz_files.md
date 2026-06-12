---
title: "NEED HELP: Installing .tar.gz files"
date: 2008-06-01
forum: General Help
---

### Post by WeEatVista on 2008-06-01
I am new to linux, and used to windows. Earlier today I wanted to download a program, only to find out it was in .tar.gz format. After searching google and different forums for hours, none of the tutorials helped me because they were confusing or it wouldn't work for me. Can anyone supply an EASY step-by-step instructions on how to install .tar.gz files?

Thanks in advance,
We Eat Vista

---

### Post by robertchahine on 2008-06-01
.tar.gz aren't installer files. they are just pacages like .zip and .rar ...
usually extarct files from the .tar.gz and there should be and install file or make file

---

### Post by Dougie187 on 2008-06-01
You cant really install a tar.gz file. tar.gz file is similar to a zip file, it is called a gzipped tar file, for future reference, and is the similar extension to .tgz

If you downloaded a program like that it is most likely source code, which would include a make file, and probably a configure script.

To begin, you need to start up a command line, and cd to the folder containing the tar.gz file.

Then you need to unzip the tar.gz file.
To do this, type the following, replacing file_name with the file name.
```
tar xvzf file_name.tar.gz
```

After this, you need to cd into the new directory created, probably similar to the name of the tar.gz file.

At this point, there should be a file called INSTALL or README that contains the instructions on how to complete the installation, because its different for every piece of software.

Most likely, you need to run a configure script
```
./configre.sh
```

Then you need to make the program
```
make
```

If this fails, try to install the build-essential package
```
sudo apt-get install build-essential
```

Now you need to re-make your program
```
make
```

Then try to install the app
```
sudo make install
```

now your app should be installed.

---

### Post by OliverW on 2008-06-01
Also check out this page, it does have a pretty good explaination about all things you want to install on Ubuntu:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by forestpixie on 2008-06-01
> **WeEatVista said:**
> I am new to linux, and used to windows. Earlier today I wanted to download a program, only to find out it was in .tar.gz format.

It might be an idea to say what the program is - it might be available in the repos - in which case you don't want to be installing it like that anyway.

---

### Post by Dougie187 on 2008-06-01
Did any of this help? or did you have more issues? or what happened?

---

