---
title: "Java and Chromium"
date: 2012-11-01
forum: General Help
---

### Post by gmseed on 2012-11-01
Hi

Just installed Ubuntu 12.10 and immediately installed Chromium and Java 1.7_u9.

A way to test Java is by typing the following in a browser:

[http://www.java.com/en/download/testjava.jsp](http://www.java.com/en/download/testjava.jsp)

which shows my Java setup ok for Firefox but fails for Chromium.

Via Dash Home I can view the Java settings in the Oracle 7 Plugin Control Panel.

What additional settings does Chromium require?

Thanks

Graham

---

### Post by tornadof3 on 2012-11-01
I used the PPA from webupd8 and when it was installed it 'just worked' in Chromium. There is an 'allow' button that pops up for applets in Chromium at the top under address bar.

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Beyond that I'm not sure why it wouldn't work...

---

### Post by jim_deadlock on 2012-11-01
Chromium checks the mozilla plugins directory for the java plugin, so do:

```
ls -l ~/.mozilla/plugins/libnpjp2.so
```

If it's not found, do:

```
mkdir ~/.mozilla/plugins
sudo updatedb
locate libnpjp2.so
cd ~/.mozilla/plugins
ln -s /full/path/to/libnpjp2.so

```

(substitute the full path of course)

Restart chromium and go to url about: plugins (no spaces)

which will show you all your installed plugins, including your java hopefully.

Note: if you're trying to play Pogo games in chromium, forget it, it has never worked for some reason.

Further reading: [https://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU]("https://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-64-BIT-UBUNTU")

---

