---
title: "Java with Ubuntu is messed up!"
date: 2006-08-10
forum: General Help
---

### Post by RonB123123 on 2006-08-10
I checked the forums, I don't think any one else is having the same problem.

I use java to play a game called RuneScape and in the first 10-15 min everything is working fine, but then later, I am not able to use my arrow keys and I'm not able to type anything. The only thing I can then do is move around or click on things using the mouse.

I normally play on Windows XP and I have never seen this error before. Does this problem only exist in Ubuntu or Java? 

One of them has bugs in it or can't do something. It's not the site, it's definitely Java or Ubuntu. Is there any way to fix this? 

Oh and I installed Java using ubuntuguide.org and I used the following lines in the terminal.
> sudo apt-get install sun-java5-jre sun-java5-plugin
Then I configured java using this line.
> sudo update-alternatives --config java
The output from the previous line is this.
> 
  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java


Could someone please help? Should I uninstall the java existing on Ubuntu and go to [www.java.com](www.java.com) and download theirs? What should I do? Please reply soon. Thank you. :sad: 

~Ron

---

### Post by Ramses de Norre on 2006-08-10
You need to select option 3 in the update-alternatives command.
Or even better: run ```
sudo update-java-alternatives -s java-1.5.0-sun 
```

---

### Post by RonB123123 on 2006-08-10
Thank you so much!! Finally no more problems with java. :D

---

