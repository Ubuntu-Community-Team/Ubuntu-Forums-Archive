---
title: "Locatoin of documentation confusion"
date: 2008-05-27
forum: General Help
---

### Post by Breadstick on 2008-05-27
Hi everyone


Upon installing php5 through synaptic, I noticed an interestingly named file: "php-doc" which claimed to be documentation for php.

Interested, I installed it, but I am at a total loss as to where it is located :confused: or how to view it.

Any suggestions on where to look?



Thanks in advance

---

### Post by pointone on 2008-05-27
Documentation is usually installed to "/usr/share/doc/<package>".

To view the location of all files installed by a package, use "dpkg -L <package>".

---

### Post by mali2297 on 2008-05-27
You can see a list of the files included in the package [here]("http://packages.ubuntu.com/hardy/all/php-doc/filelist"). Try opening [/usr/share/doc/php-doc/html/index.html](/usr/share/doc/php-doc/html/index.html) in a web browser. 

There are probably other ways to find it as well.

---

### Post by Breadstick on 2008-05-27
Hi,

Thank you both for such quick and helpful replies (and to think I was going to leave this till tomorrow before I checked :grin: ).

I found the files under urs/share/doc/ like you said.

Thanks again,
Luke

---

