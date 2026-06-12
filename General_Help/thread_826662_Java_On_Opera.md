---
title: "Java On Opera"
date: 2008-06-12
forum: General Help
---

### Post by Vince4Amy on 2008-06-12
I Cannot get Java to work on Opera, and it doesn't show on the ```
about:plugins
``` page either. I have installed JRE 6 from the Repo's and I've also installed the browser plugin but no dice. Is there any way to get JRE to work with Opera 9.5?

---

### Post by Xavier Oddmon on 2008-06-25
I'd like to know how to do this as well (Opera 9.5, Hardy Heron.) Before (Gusty Gibbon, opera 9.5 alpha,) this worked fine.

---

### Post by squashpup on 2008-06-25
I had no luck installing Java in Opera until I actaully went to the Java page, downloaded and extracted the .bin file from here:

[http://www.java.com/en/download/manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/manual.jsp?locale=en&host=www.java.com:80)

You'll want to scroll down until you see: "Linux (self-extracting file) filesize: 18.83 MB".  Download that file.  Then, at a command line, just navigate to the directory where you downloaded it and type "./jre-6u6-linux-i586.bin"

It should extract into the same directory where you downloaded it, in my case, /home/user. I then pointed Opera to it from Tools>Preferences>Advanced>Content>Java Options>Java Path.

Just show Opera the top level of your extracted file (mine reads jre1.6.0_06).  When I did that, Opera suggested which folder to use.  I went with that suggestion, then tested it, and Java worked fine.

Keep in mind that this method did NOT work with the Opera version in the repos...I uninstalled that one and got the current version direct from the Opera website.  The Flash plugin didn't work with the repo version either.

Good luck.

---

