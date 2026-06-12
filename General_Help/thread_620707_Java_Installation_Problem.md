---
title: "Java Installation Problem"
date: 2007-11-22
forum: General Help
---

### Post by the23rd on 2007-11-22
In trying to install Java, I encounter the following situation. I download the bin file from this site.
[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com)
I have tried both the regular and the RPM file, although I do not know the difference. The same thing happens either way. I double click, the file attempts to open in Text Editor, and it claims that the encoding is not recognized. Verbatem:

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I select each of the two encodings: UTF-8 and ISO-8859-15, but they both result in the same error. What's going on and how do I fix it?

---

### Post by Schalken on 2007-11-22
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by taurus on 2007-11-22
You know that sun's java is available from the repos!

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by the23rd on 2007-11-22
Thanks a whole bunch, taurus. Worked like a charm.

---

