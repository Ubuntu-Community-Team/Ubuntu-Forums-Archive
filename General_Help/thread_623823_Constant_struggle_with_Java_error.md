---
title: "Constant struggle with Java error"
date: 2007-11-26
forum: General Help
---

### Post by MikeyXX on 2007-11-26
"GNU Classpath's security implementation is not complete.
HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!"

I installed Java from the [www.java.com](www.java.com) site, that didn't work and the Java test failed.

Then I opened Synaptic and searched for Java and found a JRE reference and installed that, as well as the Firefox plugin! So I thought I was set. Went to the Java.com test page and it passed!!!

Then went back to the game site ([www.pogo.com](www.pogo.com)) and I keep getting errors like one above. It offers that you can accept and whitelist it, but it won't run. Then when I go back, it asks again (so much for whitelisting).


Suggestions?

---

### Post by xjgnsdof on 2007-11-27
I get the same problem, except I can't see my streaming quotes in Scottrade. Oddly, I have Gutsy installed on my custom-built rig, and Java works perfectly. I will try to find the differences between the two and post what I discover.

---

### Post by Ber P on 2007-11-27
I also have problems with java and firefox. I too constantly have to whitelist, and my homebanking check-pc feature states that java is not support by my browser.

Just tried the java.com test page, and I didn't pass???

I had no problems in Feisty......

---

### Post by xjgnsdof on 2007-11-27
In Mozilla Firefox, input ```
about:plugins
``` in the address bar. Check what Java plugins you have in that list. If you have plugins other than the Java 6 plugin (which, on my laptop, is called "Java(TM) Plug-in 1.6.0_03-b05"), then search for the extraneous plugins in Synaptic and remove them.

In the end, you should have only one Java (in my case, the Java 6) plugin. When I went through these steps, my Java applets worked impeccably in Mozilla Firefox.

---

### Post by Ber P on 2007-11-27
I've uninstalled all java 1.4 stuff, and running an about:plugins returns only "Java(TM) Plug-in 1.6.0_03-b05". But the java [test page ]("http://www.java.com/en/download/installed.jsp?detect=jre&try=2") tells me that I'm running java 1.4? 
I've also cheked that the j2se folder containg java 1.4 is gone - and Opera has no java support anymore, so I'm pretty sure that the original java 1.4 is gone.

Still I can't run homebanking etc. because my java is not up to date!?!?!

---

### Post by xjgnsdof on 2007-11-27
Search for Java 1.6 under "Add/Remove" or under "Synaptic" and install the latest plugins. I have sun-java6-bin, sun-java6-jre, and sun-java6-plugin as well as ubuntu-restricted-extras. See if that works for you.

---

### Post by Ber P on 2007-11-28
> **elgilicious said:**
> Search for Java 1.6 under "Add/Remove" or under "Synaptic" and install the latest plugins. I have sun-java6-bin, sun-java6-jre, and sun-java6-plugin as well as ubuntu-restricted-extras. See if that works for you.

I had all the java6 pakages you mention, but I missed the ubuntu-restricted-extras. So I installed....and it still tells me I got java 1.4 :(

I can somewhat understand that java 1.6 is not working, but why does it keep detecting java 1.4, when every java 1.4 package is uninstalled??? Where does it hide? Which packages? Does anyone know? I suspect (hope) that java 1.4 is somehow blocking the 1.6 installation.

---

### Post by xjgnsdof on 2007-12-01
This may sound overly simple, but have you checked your browser settings to see if "Enable Java" is ticked? It was off on my machine...

---

### Post by Ber P on 2007-12-01
Yes - it is enabled. Java also works, but for some reason it is java 1.4 and not java 1.6. I'm really lost, so any suggestions are welcome.

Maybe I should remove and re-install firefox?

---

### Post by Ber P on 2007-12-01
hmmm..... tried to remove and re-install firefox - still telling me it is 1.4?!?!?!

---

### Post by xjgnsdof on 2007-12-01
What version of Ubuntu are you using? Also, list what you have installed when you type "java" into Synaptic. If we have the same versions, then we can try comparing dependencies.

---

### Post by Ber P on 2007-12-03
> **elgilicious said:**
> What version of Ubuntu are you using? Also, list what you have installed when you type "java" into Synaptic. If we have the same versions, then we can try comparing dependencies.

I'll do that when I come home tonight. Appreciate your help - it's driving me nuts!

In Opera you just type in the path to the java version you want to use. Does anyone know if it is possible to do something similar in firefox?

---

### Post by Ber P on 2007-12-03
I'm running Gutsy Gibbon and searching for "java" (description and name) in synaptic returns the following as installed (my ubuntu is Danish, so some names may be mistranslated )

bsh   2.0b4-6ubuntu1
cacao   0.97-4
classpath   2:0.92-4ubuntu2
classpath-common   2:0.92-4ubuntu2
classpath-gtkpeer 
dbus   1.1.1-3ubuntu4
gcjwebplugin   2:0.92-4ubuntu2
gcj-4.2-base   4.2.1-5ubuntu5
gdb   6.6.dfsg-1ubuntu7
gij   4:4.2.1-4ubuntu2
gij-4.2   4.2.1-5ubuntu5
java-common   0.26ubuntu1
libdbus-1-3   1.1.1-3ubuntu4
libgcj8-1   4.2.1-5ubuntu5
libgcj-common 1:4.2.1-4ubuntu2
libgnome-speech7   1:0.4.16-0ubuntu2
libgtksourceview2.0-common   2.0.1-0ubuntu1
libgtksourceview-common   1.8.5-1
libhsqldb-java 1.8.0.8-1ubuntu1
libjaxp1.3-java   1.3.03-5
libjline-java   0.9.5-3ubuntu2
libmozjs0d   1.8.1.4-2ubuntu5
libservlet2.4-java   5.0.30-6ubuntu1
libtool   1.5.24-1ubuntu1
libxalan2-java   2.7.0-4
libxerces2-java   2.8.1-2
libxul0d   1.8.1.4-2ubuntu5
libxul-common   1.8.1.4-2ubuntu5
openoffice.org   1.2.3.0-1ubuntu5
openoffice.org-base   1.2.3.0-1ubuntu5
openoffice.org-java-common   1.2.3.0-1ubuntu5
sun-java6-bin   6-03-0ubuntu2
sun-java6-jdk   6-03-0ubuntu2
sun-java6-jre   6-03-0ubuntu2
sun-java6-plugin   6-03-0ubuntu2
ubuntu-restricted-extras   10

---

### Post by Ber P on 2007-12-03
Found it at last! Removed "gcjwebplugin" and it now uses the correct version!

---

### Post by xjgnsdof on 2007-12-05
That is indeed a plugin that you have installed that I don't have installed. Glad you found the problem.

---

