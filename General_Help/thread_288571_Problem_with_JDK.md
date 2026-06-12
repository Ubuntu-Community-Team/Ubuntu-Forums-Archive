---
title: "Problem with JDK"
date: 2006-10-30
forum: General Help
---

### Post by Zdravko on 2006-10-30
I used to have Eclipse installed and in order to develop JAVA applications I  installed JDK also. Now after updating with apt-get I get always this:
> 
Setting up sun-java5-doc (1.5.0-08-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of J2SDK documentation
dpkg: error processing sun-java5-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java5-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)


Actually I don't need JAVA anymore. Is there  way I can remove it completely from the computer?

---

### Post by Zdravko on 2006-10-30
I would appreciate any help regarding removing JDK from my computer.

---

### Post by Zdravko on 2006-11-03
Any help out there?

---

### Post by ebash on 2006-11-03
You can use apt-get to remove a package.

Try to do:
```
sudo apt-get remove sun-java5-doc
```

This should remove the documentation package for Java. Use the same procedure to remove any other package related to Java.

PS: You can provide the option -s to the command apt-get, the flag will simulate a removal. Quite useful when dealing with unknown packages.

Hope that it helps.

---

### Post by Zdravko on 2006-11-03
[ebash]("http://ubuntuforums.org/member.php?u=9278"), thank you very much for the help! I believe everything is OK now. I didn't really know the features apt-get allowed.

---

