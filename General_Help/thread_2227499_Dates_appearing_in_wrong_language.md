---
title: "Dates appearing in wrong language"
date: 2014-06-02
forum: General Help
---

### Post by yuanzhoulu on 2014-06-02
So I installed Xubuntu 14.04, Chinese (Traditional, locale is zh_TW) version. Everything looks good except that all my dates on the entire system are appearing in some strange language. (Seriously, how do these kinds of bugs happen ...)

Can anyone please enlighten me on how I might go about fixing this?

[IMG]http://i2.minus.com/jAQX5eLoEki08.png[/IMG]

[IMG]http://i.minus.com/jSlAJoZjYIwNj.png[/IMG]

---

### Post by Lars Noodén on 2014-06-02
What's in /etc/default/locale for LC_TIME?

---

### Post by yuanzhoulu on 2014-06-02
Thank you!! I didn't know of this file. I guess I can fix the problem now, although I have no idea how it happened.

$ cat /etc/default/locale 
LANG="zh_TW.UTF-8"
LANGUAGE="zh_TW:zh:en_US:en"
LC_NUMERIC="fo_FO.UTF-8"
LC_TIME="fo_FO.UTF-8"
LC_MONETARY="fo_FO.UTF-8"
LC_PAPER="fo_FO.UTF-8"
LC_NAME="fo_FO.UTF-8"
LC_ADDRESS="fo_FO.UTF-8"
LC_TELEPHONE="fo_FO.UTF-8"
LC_MEASUREMENT="fo_FO.UTF-8"
LC_IDENTIFICATION="fo_FO.UTF-8"

---

### Post by davidvandoren on 2014-06-02
Open System-setting the click on Language-support  then click on Regional-Formats

There choose your desired language.
If you get a message Not all languages are installed yet while opening Language-support, do so and return to that setting again.

---

