---
title: "Extract and install tar.xz"
date: 2014-07-17
forum: General Help
---

### Post by findingthebalance on 2014-07-17
Hi there,

Ubuntu 14.04. Could someone walk through the steps for extracting and installing a tar.xz file? Using terminal I have extracted the file, but I cannot seem to install it.

Thank you

---

### Post by yancek on 2014-07-17
After extracting a tar file you will usually have a directory of the same name which contains several files.  Often one is a README file or you may have an install file and they should include instructions.  Indicating what exactly the tar file is might enable someone familiar with to help.

---

### Post by findingthebalance on 2014-07-17
The file is Cinelerra video editor. The read me file say's "Run ./cinelerra from this directory".  That's it.

---

### Post by ibjsb4 on 2014-07-17
If you can't get it to work, you could opt for **CV** and load the ppa.

[http://cinelerra-cv.org/about.php](http://cinelerra-cv.org/about.php)

[https://launchpad.net/~cinelerra-ppa/+archive/ubuntu/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ubuntu/ppa)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+install+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+install+ppa&sa=Search&cof=FORID:9)

---

### Post by buzzingrobot on 2014-07-17
> **findingthebalance said:**
> The file is Cinelerra video editor. The read me file say's "Run ./cinelerra from this directory".  That's it.

Open a Terminal, move to the "cinelerra" directory created when you expanded the archive, enter ```

./cinelerra

```

If it complains that you are aren't authorized to run the command, preface it with "sudo" and you'll be prompted for a password.

Be aware that relatively very few Ubuntu programs are packaged in tar archives.  The most common seem to be Windows programs ported to Linux but not packaged appropriately for Linux. 

Installing software packaged for Ubuntu, either from Ubuntu repositories or from PPA's, means updates to that software will be rolled into your system's regular updates.  When packages are installed from tar archives, they are not.

---

### Post by yancek on 2014-07-17
You might also verify that the cinelerra script is executable although it probably will be.

---

