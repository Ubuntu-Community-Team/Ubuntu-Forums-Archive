---
title: "Secure HTTP connection from Ubuntu??"
date: 2006-07-06
forum: General Help
---

### Post by AlliumPorrum on 2006-07-06
Hi!

I have my own Java program that creates a HTTPS connection to one server in internet. It works just OK both in my Win XP and Win 98 machines, but when I run the application in Ubuntu I always get the following exception:

 javax.net.ssl.SSLPeerUnverifiedException: peer not authenticated
javax.net.ssl.SSLPeerUnverifiedException: peer not authenticated
        at com.sun.net.ssl.internal.ssl.SSLSessionImpl.getPeerCertificateChain(SSLSessionImpl.java:394)
        at HTTPClient.HTTPConnection.sendRequest(HTTPConnection.java:2954)
        at HTTPClient.HTTPConnection.handleRequest(HTTPConnection.java:2772)
        at HTTPClient.HTTPConnection.setupRequest(HTTPConnection.java:2564)
        at HTTPClient.HTTPConnection.Post(HTTPConnection.java:1064)
        at HTTPClient.HTTPConnection.Post(HTTPConnection.java:1029)
        at HTTPClient.HTTPConnection.Post(HTTPConnection.java:956)

Is there something that I should now about using secure connections in Ubuntu? Why couldn't I create a connection just as I do in both Windowses??

---

### Post by nanotube on 2006-07-06
[QUOTE=AlliumPorrum]Hi!

I have my own Java program that creates a HTTPS connection to one server in internet. It works just OK both in my Win XP and Win 98 machines, but when I run the application in Ubuntu I always get the following exception:

 javax.net.ssl.SSLPeerUnverifiedException: peer not authenticated
javax.net.ssl.SSLPeerUnverifiedException: peer not authenticated
        at com.sun.net.ssl.internal.ssl.SSLSessionImpl.getPeerCertificateChain(SSLSessionImpl.java:394)
        at HTTPClient.HTTPConnection.sendRequest(HTTPConnection.java:2954)
        at HTTPClient.HTTPConnection.handleRequest(HTTPConnection.java:2772)
        at HTTPClient.HTTPConnection.setupRequest(HTTPConnection.java:2564)
        at HTTPClient.HTTPConnection.Post(HTTPConnection.java:1064)
        at HTTPClient.HTTPConnection.Post(HTTPConnection.java:1029)
        at HTTPClient.HTTPConnection.Post(HTTPConnection.java:956)

Is there something that I should now about using secure connections in Ubuntu? Why couldn't I create a connection just as I do in both Windowses??[/QUOTE]

are you using the official sun java, or the oss java implementation that comes with ubuntu? there are still some differences in the two implementations, and it may be that this is what you are running into.
try it with the sun java, and see if that helps...

---

### Post by AlliumPorrum on 2006-07-06
Bit more information about this issue... I'm handling a secure keystore in my code like this:

java.security.Security.addProvider(new com.sun.net.ssl.internal.ssl.Provider());
System.setProperty("javax.net.ssl.keyStore", keystore);
System.setProperty("javax.net.ssl.keyStorePassword", keystorePassword);

And then I just have my keystore file in the root directory of the application. This seems to work in Windows, but should this be done somehow differently in Linux??

---

### Post by AlliumPorrum on 2006-07-06
> are you using the official sun java, or the oss java implementation that comes with ubuntu? there are still some differences in the two implementations, and it may be that this is what you are running into.
try it with the sun java, and see if that helps...

I'm using SUN's java:

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode)

---

### Post by AlliumPorrum on 2006-07-07
Doesn't anyone really have a clue about this problem?? I have been surfing the web for a day now and tried everything, but I just can't create HTTPS connection from my app. 

If I can't get this working, I'm afraid that I have to move back to the Windows world on my server installation, even that I really wouldn't want to...:(

---

### Post by AlliumPorrum on 2006-07-09
Ok, I found out the problem! 

First of all, I had to generate a new keystore file on the Linux machine, file that was generated on my Windows computer did not work with Ubuntu. 

Secondly, my old laptop's BIOS battery seems to be dead, so the date is always set to somewhere 1999. Now when I generated the new keystore file for Ubuntu, it was dated to that year -> it propably was already "old" when I created it.

Why didn't I see this right away...;)

---

