---
title: "Pidgin core dumped after last security update"
date: 2007-09-02
forum: General Help
---

### Post by soctu on 2007-09-02
I've been using Pidgin for my instant messaging client for some time now...until the
last security update. I tried using it and it core dumped. I uninstalled it and reinstalled it
and the same thing happens.

I'm using fiesty fawn 64 bit.

any suggestions?

---

### Post by michael37 on 2007-09-02
What is the source of pidgin that you use?  Third-party?  Custom build?

---

### Post by soctu on 2007-09-03
I got the source file directly from the pidgin website. I compiled it on my computer. It worked before
now nada. [http://www.pidgin.im/]("http://www.pidgin.im/")

---

### Post by michael37 on 2007-09-03
I am guessing that some of your dev libraries are stale.  Given that a third party .deb package is available, try uninstalling your manual version and installing the binary version from [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

---

### Post by soctu on 2007-09-03
Thanks for the direction I tried the deb files from [http://www.getdeb.net]("http://www.getdeb.net") ah to no avail. same
thing happens: core dump.

---

### Post by michael37 on 2007-09-03
My next guess is broken GTK libraries and/or GTK engine which pidgin gladly builds for you and can easily overwrite the standard Ubuntu libraries.  If you know where they are, try uninstalling them.  If you don't know where they are, hopefully someone else will help you since I haven't built Pidgin myself.  Maybe try asking on pidgin forums [http://developer.pidgin.im/](http://developer.pidgin.im/)?

---

### Post by soctu on 2007-09-04
I went to the Pidgin website and submitted my debug files and you know their server was full.
I hope someday pidgin makes it the repositories. Is it included with gutsy gibbon?

thanks for your help!

---

### Post by atlfalcons866 on 2007-09-04
i just tryed gutsy alpha and pidgin is included in the install

---

