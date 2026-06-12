---
title: "Can't get Time.Gov website to work"
date: 2007-02-23
forum: General Help
---

### Post by TheRingmaster on 2007-02-23
time.gov's website uses java and I can't seem to get it to work. Here is a screenshot. Maybe there is an easy fix for this. here is what the java error console says:> load: class utcnist4.class not found.
java.lang.ClassNotFoundException: utcnist4.class
    at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:168)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:119)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:599)
    at sun.applet.AppletPanel.createApplet(AppletPanel.java:721)
    at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1781)
    at sun.applet.AppletPanel.runLoader(AppletPanel.java:650)
    at sun.applet.AppletPanel.run(AppletPanel.java:324)
    at java.lang.Thread.run(Thread.java:595)
Caused by: java.io.IOException: open HTTP connection failed.
    at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:271)
    at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:44)
    at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:158)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:155)
    ... 9 more


---

### Post by Maestro23 on 2007-02-23
Hmm... I just went there and it worked fine for me.  Do you have problems at any other sites using java?

---

### Post by TheRingmaster on 2007-02-23
> **Maestro23 said:**
> Hmm... I just went there and it worked fine for me.  Do you have problems at any other sites using java?

no, I actually just got done playing runescape (uses java only) and it worked fine, I go here and no dice.

---

### Post by gtratter on 2007-02-23
there might be a couple of reasons:
[COLOR="Blue"][/COLOR]
1.) do you you have Java enabled in your browser?
2.) do you have Java RE (runtime edition) installed?

To check #1 in FireFox: *Edit* - *Preferences* - *Content* - and assure **enable javascript & enable java is checked**

To check #2 at the command line: type * locate libjavaplugin*.so* to see if you have the plugin installed 

Alternately you could also go here [[COLOR="Blue"]Sun Java runtime check page[/COLOR] ]("http://www.java.com/en/download/installed.jsp") to test if java is a) installed and b) part of your browser environment.

---

### Post by TheRingmaster on 2007-02-23
> **gtratter said:**
> there might be a couple of reasons:

1.) do you you have Java enabled in your browser?
2.) do you have Java RE (runtime edition) installed?

To check #1 in FireFox: *Edit* - *Preferences* - *Content* - and assure **enable javascript & enable java is checked**

To check #2 at the command line: type * locate libjavaplugin*.so* to see if you have the plugin installed 

Alternately you could also go here [[COLOR=Blue]Sun Java runtime check page[/COLOR] ]("http://www.java.com/en/download/installed.jsp") to test if java is a) installed and b) part of your browser environment.

I went to the java runtime check page and I do have java installed and working.
> petey@petey-desktop:~$ locate libjavaplugin.so
/usr/lib/firefox/plugins/libjavaplugin.so
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/mozilla-snapshot/plugins/libjavaplugin.so


I installed my java with automatix.

---

### Post by Maestro23 on 2007-02-23
> **TheRingmaster said:**
> I went to the java runtime check page and I do have java installed and working.

I looked at your fist screenshot again.  There is an adblock tab in the top right corner where the time display should be in the java applet window.  Are you running an ad-blocker?

---

### Post by TheRingmaster on 2007-02-23
> **Maestro23 said:**
> I looked at your fist screenshot again.  There is an adblock tab in the top right corner where the time display should be in the java applet window.  Are you running an ad-blocker?

I am using adblock plus, but nothing is being blocked on the page.

---

### Post by TheRingmaster on 2007-02-23
I got a feeling that my java installation is too old to work on this page. When will the automatix repos update? The current java version is 1.5.0_update 11, mine is update 8.

EDIT: I GOT IT TO WORK. All I had to do I check "direct connection" in the internet tab of the java control center.

---

