---
title: "Question About Java With 16.04.1"
date: 2016-11-14
forum: General Help
---

### Post by scottinpa40 on 2016-11-14
Hi, I had a question about installing Java for the latest version of Ubuntu, which I installed on my wife's computer recently.  Is there an easy way to run Java with the Chromium web browser?  My wife mainly uses her computer to do online training for work and she used to use Windows 7 with no problems (she used Google Chrome)  She tried to sign in to training for the first time with Ubuntu installed with Chromium browser and a message saying that Java needed to be installed came up.  I'm just wondering if there is an easy way around this because when I did a Google search of "How To Install Java On Ubuntu", it is complicated for me at least!  Is there a different browser that she could use that I wouldn't have to install Java?  Thanks for any help.

-Scott

---

### Post by QIII on 2016-11-14
Hello!

By far the easiest way to install Java (and the browser plug-in, which is what you want) is by following the instructions [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

In particular, you are looking for this:  

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

### Post by scottinpa40 on 2016-11-23
Thank you very much!

---

