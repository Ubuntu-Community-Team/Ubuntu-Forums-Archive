---
title: "java not working on hardy - tried everything!"
date: 2008-05-14
forum: General Help
---

### Post by jdforsythe on 2008-05-14
i upgraded to hardy and java broke. i have another machine with a fresh install from a cd and java is broken on it as well.

i've been searching the forum for 2 days and i've tried everything i've found.

i've tried icedtea, sun, icedtea-java7. i've tried all the command line update-alternatives. it never changes the java version. it doesn't work. i've tried the post where you uninstall gcj-web-plugin to no avail. i've tried uninstalling and reinstalling all the sun packages.

i'm running hardy with firefox3.0b5.

please help.  thanks.

---

### Post by macaholic on 2008-05-14
Do any of the java plugisn show up in the firefox addons prompt?

---

### Post by skiold on 2008-05-14
I'm in the same situation. Java is broken.
Does anybody know any solution?
In Gutsy there wasn't that problem. After the upgrade to Hardy, Java doesn't work.

Please help!

---

### Post by JimmyHopkins on 2008-05-14
Go in synaptic, search for "jdk" and remove any package with jdk in its name, such as "free-java-jdk" or "open-jdk". This should work (it did for me). This happens because ubuntu has two different versions of java running at the same time.

---

### Post by perlluver on 2008-05-14
Type into the terminal ```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by skiold on 2008-05-15
I removed all JDK packages and nothing happens. Is there any other solution?

---

### Post by jdforsythe on 2008-05-18
Sorry for the delayed response, I had to unexpectedly leave town.  But thanks for your replies.

I've tried everything from only running icedtea to only running sun-java.

As per your suggestions I removed everything except sun-java6.  I ran the terminal command to update the alternatives.  Still no java and still no java in about:plugins.

I love Ubuntu and here's hoping these problems get solved!  Hopefully someone is working on an update to solve this java problem.  There are no good online pool games for flash! And I can't find a good one for Linux. The only decent one I've found doesn't even allow you to put english on the ball!

---

### Post by erginemr on 2008-05-18
Did you try:
```
sudo aptitude install sun-java6-jre
```

---

### Post by jdforsythe on 2008-05-26
> **erginemr said:**
> Did you try:
```
sudo aptitude install sun-java6-jre
```


not to be a jerk, but if you read any of the posts above you'll see that we've tried sun-java.

i really hope this gets fixed in an update sometime soon. i'm really considering going back to gutsy, but other than the java and a few other minor things, i like hardy a lot more. my compiz doesn't crash anymore like it did ALL THE TIME in gutsy.

---

### Post by erginemr on 2008-05-26
I see, but the sun-java packages in the repositories are quite numerous and confusing, so I thought maybe I needed to come up with my two cents by pointing out the exact name of the package. Well, if you have tried that already...

---

### Post by skiold on 2008-05-26
I've found a solution:

Backup all your files and login as root. Reinstall all java packages, delete your user and create it again, that solved the issue with java.

---

### Post by h0me5k1n on 2008-05-27
Mine is working after removing the icedtea-gcjwebplugin and openjdk-6-jre packages and restarting firefox

sudo apt-get remove icedtea-gcjwebplugin
sudo apt-get remove openjdk-6-jre

make sure you have sun java installed (i already installed these before removing the above packages)
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin

---

