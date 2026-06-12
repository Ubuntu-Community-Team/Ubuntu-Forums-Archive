---
title: "Javascripts not working (or Java?)"
date: 2014-01-28
forum: General Help
---

### Post by mamboknave on 2014-01-28
All of a sudden, I've discovered that Java and/or Javascripts on my system *may* not work (I'm with Ubuntu 10.04).

When I try to check what Java version I have through

[http://java.com/en/download/installed.jsp?detect=jre](http://java.com/en/download/installed.jsp?detect=jre)
or
[http://javatester.org/version.html](http://javatester.org/version.html)  (see the enclosed 1st pic)

firefox 20.00 just freezes, to the point that I must kill it with the kill command.

I see that icedtead-6 is properly installed and Javascripts are enabled (see the enclosed 2nd pic).
Therefore, I don't get why the gray box (in the 1st pic) that asks for clicking and activating icedtea.

Finally, I add this info just in case, taken from about:config "pref.advanced.javascript.disable_button.advanced; false"

Can someone please help me fixing/resolving this? I need Javascripts rinning fine.

Thanks a lot!

---

### Post by ubudog on 2014-01-28
JavaScript is [not]("http://www.java.com/en/download/faq/java_javascript.xml") part of the Java framework.

You may wish to install the lastest version of Firefox.
```
sudo add-apt-repository ppa:mozillateam/firefox-next
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by mamboknave on 2014-01-28
>> JavaScript is not part of the Java framework

I see what you mean. That's not my bread & butter at all.

Anyhow, those 3 lines did not help. Ended up with: "firefox is already the newest version"

which is 20.0. And the problem I described persists. Any other idea?

---

### Post by Impavidus on 2014-01-29
Part of your problem is that 10.04 is unsupported, except for the server edition, which doesn't contain firefox. That's why you have firefox 20 instead of 26 (which is the newest version). Can't say whether a PPA would solve this, as it may rely on specific versions of libraries or may not support 10.04. I can say that a supported version of Ubuntu will be easier to work with.

---

### Post by ubudog on 2014-01-29
> **Impavidus said:**
> Part of your problem is that 10.04 is unsupported, except for the server edition, which doesn't contain firefox. That's why you have firefox 20 instead of 26 (which is the newest version). Can't say whether a PPA would solve this, as it may rely on specific versions of libraries or may not support 10.04. I can say that a supported version of Ubuntu will be easier to work with.

+1

Upgrading to Ubuntu 12.04 or above would definitely be helpful.

---

