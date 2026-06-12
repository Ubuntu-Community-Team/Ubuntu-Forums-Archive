---
title: "Sun JDK uninstall"
date: 2008-06-17
forum: General Help
---

### Post by anand77 on 2008-06-17
Hi,

I have two instances of Sun JDK installed. The first one I downloaded from java.sun.com and installed it manually in the following directory:

/usr/jdk/jdk<version #>

I was trying to use javac from the command line and it did not work. Also I tried to execute javaws from command line and got the message that java is not installed in the system.

I hoped installing the JDK (Sun Java 6) via the Applications->Add/Remove program will rectify the problem and installed it. But this screwed up some of the links. If I start Netbeans, the menus do not appear properly. It appears like a list of items on a white rectangle.

Please let me know how I can uninstall the version I installed manually at the above mentioned directory. And in general how to uninstall programs in ubuntu that were installed from the command line using shell scripts.

Thanks,
Anand.

---

### Post by RealPSL on 2008-06-17
Shell script installs are generally difficult to uninstall which is why packages are so GREAT! The Sun Java install though does not fall into the difficult category. The .sh Java install just extracts all the files to a single directory and calls it an install so you should be able to just delete the directory with the files.

---

### Post by anand77 on 2008-06-18
> **RealPSL said:**
> Shell script installs are generally difficult to uninstall which is why packages are so GREAT! The Sun Java install though does not fall into the difficult category. The .sh Java install just extracts all the files to a single directory and calls it an install so you should be able to just delete the directory with the files.
Thanks for your reply. Will give that a try. But is there any way to find broken links in Ubuntu? Going by the color of the text, I presume the ones listed in red are broken whereas the ones in green are good. Am I right???

---

### Post by jamesstansell on 2008-06-18
> **anand77 said:**
> Thanks for your reply. Will give that a try. But is there any way to find broken links in Ubuntu? Going by the color of the text, I presume the ones listed in red are broken whereas the ones in green are good. Am I right???

Not sure about the color question.  But if it points to a file/directory that doesn't exist then I guess you would call it broken.  Do you have an example?

Once you've installed the sun java packages you may need to run this command```
$ sudo update-java-alternatives -s java-6-sun
```

Netbeans may record a separate JDK to use than the system JDK so there may be a config file or startup script to adjust for it.

---

### Post by anand77 on 2008-06-18
Thanks a lot 'RealPSL' and 'jamesstansell'. I removed the directory in which I did the first install and updated the java alternatives. Things are in good shape now. I also did an uninstall of netbeans and did a fresh install to make it use the updated java packages. Thanks a lot once again!

---

