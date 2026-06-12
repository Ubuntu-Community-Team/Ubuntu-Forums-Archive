---
title: "No medium security setting for Java?"
date: 2015-01-16
forum: General Help
---

### Post by d4m1r on 2015-01-16
Hey all, I recently updated my java client to the latest version (Oracle **Version 8 Update 25**) but now you basically can't run any java applets under Ubuntu....

Appearently, they recently made a change that by default blocked all self-signed java applets from being able to be run within a browser. The problem is most java applets I access through my browser of choice (Firefox 35) are self signed and **there is no way to disable this under Ubuntu**....At least no working method. The problem? It seems Windows and OS X users can restore the previous functionality of getting those java applets to run after hitting OK on a warning popup by lowering their java security setting from the default "High" to "Medium".


Their java control panels look like this;

[https://www.java.com/ga/images/en/java_security.jpg](https://www.java.com/ga/images/en/java_security.jpg)

BUT Ubuntu can't do this because our java control panel looks like this;

[https://i.imgur.com/VOxPkxI.png](https://i.imgur.com/VOxPkxI.png)


No medium setting :( According to [THIS]("http://askubuntu.com/questions/381746/java-blocked-due-to-security-level-on-ubuntu-13-10") post however, we should be able to add a line to our "~/.java/deployment/deployment.properties" file (specifically, adding deployment.security.level=MEDIUM to the file) but I have tried this method by putting that line at the top of the file, at the bottom, editing the file as a normal user, with elevated permissions, etc but it does nothing...All java applets are still BLOCKED and the file just seems to get overwritten (that line gets removed automatically). Even something like [THIS]("http://javatester.org/version.html") java version checker doesn't work for me...So how do the rest of you do it?

---

### Post by nerdtron on 2015-01-16
Isn't java the Iced tea plugin from the software center? I'm seeing the Iced Tea web panel on my machine:
[ATTACH=CONFIG]259313[/ATTACH]

First I installed chromium from the software center (since java only works for chromium and not firefox). I also installed the pepper flash plugin for running flash on chromium along with the ubuntu restricted extras. All packages from the software center. Java plugins on chromium running fine on my end.

---

### Post by QIII on 2015-01-16
Icedtea is the browser plugin for OpenJDK -- which is the open source reference implementation for Java.

Oracle Java 8 has its own browser plugin.

I didn't know about a general change in Java 8 vis-a-vis Firefox, except that there was a time during the "October of Java browser exploits" when Firefox was updated to keep the Java browser plugin from running.  I must not have run into it yet.  Java 7 still works fine with FF.

I won't be in a position to do much research for a couple of days, but when I can get to it I'll do some research.

---

### Post by d4m1r on 2015-01-17
> **QIII said:**
> I must not have run into it yet.  Java 7 still works fine with FF.

I won't be in a position to do much research for a couple of days, but when I can get to it I'll do some research.

Please do, and that is exactly the case. Java 7 works fine with Firefox but Java 8 now does not, at least not under Ubuntu anymore because we have no way to lower the security level from high to medium. We can only raise it to very high as shown in my screenshot :(

---

### Post by d4m1r on 2015-01-24
Any updates on this? Maybe I was too hasting when I manually removed JRE7 and installed JR8 but as more and more people update....They will be facing the exact same problem.

All those people that use Java applets in browsers daily, under Ubuntu, will be affected.

---

### Post by d4m1r on 2015-02-08
> **QIII said:**
> 
I won't be in a position to do much research for a couple of days, but when I can get to it I'll do some research.

Any updates on this QIII? :)

I found a "workaround" but unfortunately....It doesn't work. Apparently, adding sites to your exception list should automatically skip the certificate warnings etc and should make them work. Well, this workaround doesn't work under Ubuntu with the official Java 8 JRE...I used "http://www.pingtest.net" for testing and when I added it to my exception list (via Java Control Panel), I got this warning;

[IMG]http://i.imgur.com/Lof1Xez.png[/IMG]

Ok fine, I went back and added "http://cdn.pingtest.net" as well but then a) I still got the warning to accept the java applet from vendor XYZ, b) The applet still did not run (so exact same behaviour without putting the site on the exception list).

Something is totally broken with the official Java JRE under Ubuntu and I am wondering if the other open source flavours (ex: IcedTea) would be better....

I also noticed my Java installation seems to be in a custom location? I don't think I choose this location at will (following a guide) but basically, to launch the Java Control Panel people usually use something like;

```
/usr/bin/jre1.8.0_25/bin/ControlPanel
```

But I had to use the below because that is where my Java is located and I am also wondering if that could make a difference?

```
/opt/java/64/jre1.8.0_25/bin/ControlPanel
```

---

### Post by d4m1r on 2015-02-21
As I slight update, this still wasn't solved 1 month on so I installed JRE7 (1.7.0_76) and set it as the default Java environment via the Java Control Panel. Then I was able to relaunch the Java Control Panel, set it to "Medium" security settings, and use Java applets normally under Firefox as I have for years...

JRE8 is basically useless under Ubuntu for now so stay way from it people! Grab the latest version of the JRE7 instead!

---

